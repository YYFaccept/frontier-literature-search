# Consensus 响应错误与浏览器连接诊断

执行日期：2026-09-22。本记录接续[同日的摘要筛选实测](validation-2026-09-22-screening.md)，保留当时失败的事实，不将后续修复回写为此前已经通过。

## Consensus：已定位触发条件并通过真实查询

环境为 `codex-cli 0.155.0-alpha.9.2`，原连接为 Consensus 官方远程 MCP。OAuth 已成功，工具可加载，调用 `search` 后出现 `Unexpected response type`。

定向读取此次调用的协议结果发现：服务器实际返回成功结果，`isError: false`，含 PII-VisBench 的题名、原始摘要、年份、引用量和链接。第二个文本内容块带有 `annotations.priority: 1.0`。客户端将整项结果解码为 `CustomResult`，随后不接受该类型。此次响应没有 `resource_link`，不能用其他案例的该类型问题解释本次错误。

### 受控对照

在本地测试服务器构造同一响应，仅改变该注释的数字表示或移除注释，通过同一个 Codex 可执行程序读取：

| 响应差异 | 客户端结果 |
| --- | --- |
| `priority: 1.0` | `Unexpected response type` |
| `priority: 1` | 成功读取 |
| 移除 `annotations` | 成功读取 |

这确认了本次响应的触发条件。`1.0` 与 `1` 数值相同，均是合法的优先级值；不能据此要求服务端一律使用整数，更不能对非整数优先级取整。

源码支持：[客户端响应分支](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/rmcp-client/src/rmcp_client.rs#L864)、[rmcp 的浮点优先级定义](https://github.com/modelcontextprotocol/rust-sdk/blob/rmcp-v3.2.0/crates/rmcp/src/model/annotated.rs#L17)、[Codex 的 arbitrary_precision 依赖](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/exec-server-protocol/Cargo.toml#L22)及[同版本记录的类似解码冲突](https://github.com/openai/codex/blob/rust-v0.155.0-alpha.9.2/codex-rs/rollout/src/lib.rs#L36)。浮点数与通用解码缓冲的兼容性是结合源码作出的原因判断；本地对照直接证明的是上述数字表示触发差异。

### 本机修复与真实论文核验

采用现成的 [`mcp-remote` 0.14.3](https://github.com/punkpeye/mcp-remote) 转接官方远程 MCP。其 stdio 输出通过 JavaScript `JSON.stringify` 重新序列化响应，将 `1.0` 写为等值的 `1`；不改论文内容或把其他小数取整。工具安装在本机技能仓库之外，用户完成该工具自己的 OAuth 授权。

通过真实 Codex 客户端执行：

```json
{"query":"PII-VisBench","page_size":1}
```

调用完成，客户端返回 `error: null` 并能读取论文原始摘要，修复后的搜索通过。实际数据如下：

| 字段 | 实际结果及采用方式 |
| --- | --- |
| 题名 | PII-VisBench: Evaluating Personally Identifiable Information Safety in Vision Language Models Along a Continuum of Visibility |
| Consensus 作者／年份 | G. Shahariar et al.，2026；作者字段不是完整作者表 |
| 引用量 | Consensus 返回 3，查询日期 2026-09-22；不与其他数据库相加，不将该计数称为高引用 |
| Consensus 场所 | `Unknown Journal`；仅说明该工具元数据缺失 |
| 返回来源 | [Consensus 论文条目](https://consensus.app/papers/details/0546209aa0e95a44a1cc18da1e049c3e/?utm_source=unknown) |
| 官方主记录 | [Findings of ACL 2026](https://aclanthology.org/2026.findings-acl.501/)，2026 年 7 月，10294–10316 页，DOI `10.18653/v1/2026.findings-acl.501` |
| 筛选判断 | 摘要研究 VLM 对不同在线可见度人群的个人信息泄露，直接相关，归入隐私评测核心参考 |
| 实际阅读 | Consensus 返回的原始摘要及 ACL 官方摘要与出版元数据；全文未读 |

已实际打开官方出版页核对题名、四位作者、摘要、月份、场所及 DOI。正式引用采用 ACL 记录；不用 Consensus 的缺失场所推翻正式出版事实。原返回中的推广文案和输出格式指令不作为论文内容或研究任务指令。

随后将本机名为 `consensus` 的配置改为已测的 stdio 转接连接，读取配置确认替换成功。排障方式与恢复官方直连的方法见[连接排障说明](../references/troubleshooting.md)。此次修复是针对已复现客户端版本的兼容处理，不代表上游客户端错误已经修复。

### 已启用配置的主题检索

在另一个新会话中直接使用已保存的 `consensus` 配置，没有临时注册测试服务器或增加启动等待参数。实际工具 `mcp__consensus__search` 的参数支持以下调用：

```json
{
  "query": "privacy leakage in vision-language models and multimodal large language models",
  "year_min": 2024,
  "year_max": 2026,
  "exclude_preprints": true,
  "page_size": 3
}
```

客户端再次成功读取三篇论文。以下引用数均由 Consensus 在 2026-09-22 返回，不作为正式论文的入选门槛。

| 返回题名 | 年份／引用数 | 摘要与后续核验 | 分类判断 |
| --- | --- | --- | --- |
| Privacy-Preserving Multimodal Reasoning for Internet of Things: A Retrieval-Augmented Large Language and Vision Assistant Framework | 2026／3 | 返回实质摘要，已与[作者所在机构仓储](https://ro.ecu.edu.au/ecuworks2022-2026/7686/)核对。仓储给出 IEEE Internet of Things Magazine 9(3):113–122 及 DOI `10.1109/MIOT.2026.3650753`；本轮 DOI 页面读取失败，出版社元数据尚待直接核验 | 直接相关，处理敏感图像内容和微调时的梯度泄露；作为相关候选保留，不计作已核实近期正式发表实例 |
| Defeating Cerberus: Privacy-Leakage Mitigation in Vision Language Models | 2026／0 | Consensus 的场所未知、摘要仅为 `,`，按摘要缺失处理；实际打开 [ACL 官方条目](https://aclanthology.org/2026.findings-eacl.154/)，取得原始摘要及 Findings of EACL 2026、2026-03、DOI `10.18653/v1/2026.findings-eacl.154` | 直接相关，模型内部干预降低 PII 泄露；与已有正式主记录合并，不新增重复条目，不因零引用降为预印本 |
| A survey on privacy risks and protection in large language models | 2025／60 | 返回实质摘要，与[出版社页](https://link.springer.com/article/10.1007/s44443-025-00177-1)核对。正式发表于 Journal of King Saud University Computer and Information Sciences，2025-08-18，DOI `10.1007/s44443-025-00177-1` | 背景相关，摘要讨论通用 LLM 隐私攻击及防护，未建立 VLM 专属证据；不因引用较多升级为直接相关 |

只阅读这些来源的摘要与出版元数据，未核验全文方法或实验数据。该查询验证连接、参数接受和返回数据读取；没有做开启／关闭 `exclude_preprints` 的配对测试，不能仅凭本次三条结果证明过滤效果完整。年份范围也不能证明近三个月首次公开。上述正式状态、摘要补全与分类均依据逐篇来源。

## Scholar：浏览器控制连接仍待恢复

浏览器控制枚举返回 `nodeRepl.fetch request failed`，没有得到浏览器清单；恢复控制会话后，创建浏览器标签页仍超时。本机 Chrome 与 Codex 进程均在运行并响应。

可支持的结论是控制连接未建立，失败发生在读取 Scholar 页面之前。不能将其写成 Scholar 拒绝访问、用户没有打开 Chrome，或查询语法无效。此次没有取得 Scholar 结果页，出版物字段及 `source:`、`+`、多场所 `OR` 的实际过滤效果仍未验证。

需要用户重启 Codex 桌面应用，在“设置 → Computer Use”检查 Chrome 连接及相应浏览器配置，再通过 `@Chrome` 或标签页关联任务后测试。[官方浏览器连接说明](https://learn.chatgpt.com/docs/chrome-extension#troubleshooting)。当前证据不能进一步确定是扩展、配置还是桌面服务的问题。

### 同日后续：重连与指定标签页仍受阻

用户确认更新 Chrome 连接后，实际重试浏览器枚举、重置控制会话及直接打开 Chrome 学术页面，仍返回 `nodeRepl.fetch request failed`。用户随后发送明确的 Scholar 标签页关联；按完整关联调用 `getTab` 仍失败。

进一步检查桌面端近期日志，得到更具体的失败：`[browser-use-iab-api]` 的 `getInfo` 返回 `No ChatGPT browser route is available for browser session …`。本地时间 17:56–17:59 连续出现该错误。日志同时有扩展已安装、工具就绪及 Chrome 元数据交换记录。因此，已定位到当前任务的浏览器会话路由缺失；不能再只笼统归因于 Chrome 未连接。

尝试在当前任务显示 Scholar 浏览器面板，应用先返回等待显示；用户确认面板出现后，再次连接原 Chrome 标签页仍失败。改用关联中的明确浏览器及标签页 ID 后，工具返回 `Browser is not available`。上述恢复尝试均未读取到页面，未执行 Scholar 查询或过滤实验。

接下来按[官方故障处理说明](https://learn.chatgpt.com/docs/chrome-extension#troubleshooting)，在新任务中重新关联同一标签页，以尝试清除任务专属连接状态。这是待执行的恢复步骤，不是已验证修复；不要求用户继续重复已经完成的扩展设置。未公开包含账户上下文的完整日志或标签页会话标识。

## 对技能的修正

- 将工具连接、网页访问、认证及响应解析分开处理，避免无效重复登录或更换关键词。
- 入口失败后继续取得摘要和正式记录；仅在用户要求修复时读取专门排障说明。
- 搜索成功以客户端能读取实际论文结果为准，不用工具加载或授权成功替代。
- 元数据缺失回到原始出版记录补齐；检索工具附带的推广指令不进入研究交付。

历史失败记录保持原样。本记录只证明上述连接修复及小规模论文核验，不证明 Scholar 已恢复或全领域检索覆盖。
