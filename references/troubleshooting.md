# Scholar 与 Consensus 连接排障

仅在入口故障影响任务、或用户明确要求修复时读取。普通文献检索先继续可用来源；不要把下述本机修复当成所有用户的安装前提。

## 先确定失败阶段

| 观察到的现象 | 可支持的判断与处理 |
| --- | --- |
| 浏览器清单读取失败，如 `nodeRepl.fetch request failed` | 控制工具尚未连接到浏览器，不能归因于 Scholar。按工具文档恢复一次会话，仍失败则停止 UI 重试并换源。 |
| 已到 Scholar，但页面加载失败 | 普通失败最多重试一次；验证码或明确访问限制立即停止该入口。 |
| MCP 已配置，但当前会话没有工具 | 检查服务是否启用、是否已完成初始化；新连接可能需要新会话。不能据此认定未登录。 |
| 明确的 401、失效认证提示 | 按对应连接方式重新认证，不把所有工具错误都当成认证问题。 |
| 已加载工具，搜索返回 `Unexpected response type` | 检查响应解析阶段。服务器可能已完成搜索，不以此判为无结果、配额不足或关键词错误。 |
| 搜索成功但没有摘要或场所 | 用题名、作者等定位原始出版页；这是元数据补充问题。 |

浏览器连接持续失败时，交付已有文献，并给出具体恢复动作：重启桌面应用，在“设置 → Computer Use”检查 Chrome 连接，使用安装了扩展的浏览器配置，再通过 `@Chrome` 或标签页关联任务。Chrome 进程在运行不代表控制连接可用。[官方说明](https://learn.chatgpt.com/docs/chrome-extension#troubleshooting)

## 已复现的 Consensus 数字解析问题

2026-09-22 在 `codex-cli 0.155.0-alpha.9.2` 复现：Consensus 返回成功的论文内容，但附加内容的 `annotations.priority` 写成 `1.0` 后，客户端将整项结果归为 `CustomResult`，随后报 `Unexpected response type`。

本地对照只改变数字表示：`1.0` 失败，数值相同的 `1` 成功；去掉该注释也成功。`1.0` 是合法数据，不能写成 Consensus 必须返回整数，也不能对任意小数四舍五入。这个结论只覆盖已复现版本和响应形态。

源码依据：该版本 [rmcp-client 的响应分支](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/rmcp-client/src/rmcp_client.rs#L864)只接受预期类型；[Annotations 定义](https://github.com/modelcontextprotocol/rust-sdk/blob/rmcp-v3.2.0/crates/rmcp/src/model/annotated.rs#L17)支持浮点数。Codex 的 [arbitrary_precision 依赖](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/exec-server-protocol/Cargo.toml#L22)及[同类解码冲突说明](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/rollout/src/lib.rs#L36)与此次表现一致；编译层原因属于结合源码作出的判断。

## 针对此问题的连接方式

正常环境仍优先使用 [Consensus 官方远程 MCP 连接](https://docs.consensus.app/consensus-mcp)。只在已确认上述兼容问题、且用户要求修复时，使用现成的 [`mcp-remote`](https://github.com/punkpeye/mcp-remote) 转接：远程响应经过 JavaScript JSON 序列化后，`1.0` 写为等值的 `1`，保留论文内容、注释含义与其他小数。

有 Node.js 与 npx 的环境可注册：

```sh
codex mcp add consensus -- npx -y mcp-remote@0.14.3 https://mcp.consensus.app/mcp --transport http-only --resource https://mcp.consensus.app
```

没有 npx 的环境可用现有包管理器将同版本安装到本机工具目录，再用 Node 的绝对路径启动包内 `dist/proxy.js`，传入相同参数；工具目录和账户文件不放进本技能仓库。

转接工具有独立 OAuth 会话，首次启动后由用户完成它打开的 Consensus 授权。stdio 模式下不再运行 `codex mcp login consensus`；该命令适用于原来的直接远程连接。不要读取或复制其他客户端的令牌来代替正常授权。

在新会话中实际调用一次小结果集查询，确认标题、摘要和链接能被客户端正常读取，再核对官方出版记录。工具加载或登录成功不能代替这一步。已恢复后停止排障，继续文献任务。

2026-09-22 已通过同一 Codex 客户端的真实题名查询和带年份、排除预印本条件的主题查询；执行经过及论文核验见[诊断记录](https://github.com/YYFaccept/frontier-literature-search/blob/main/docs/diagnosis-2026-09-22.md)。此结果只覆盖记录中的客户端与转接版本，正常用户无需切换连接。

未来客户端修复后，可恢复官方直连并重新测试：

```sh
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

仅在需要查明响应结构时做定向诊断；不公开认证信息、OAuth 回调或整份运行日志。正常检索不启用协议跟踪。
