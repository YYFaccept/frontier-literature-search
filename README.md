# 前沿文献检索 · Frontier Literature Search

[English](README.en.md) · [技能指令](SKILL.md) · [检索模板](references/search-guide.md)

一个用于 Codex 的文献检索技能：优先用 Google Scholar 查找论文，结合公开摘要和 Consensus 等学术工具筛选相关研究，引用正式发表版本，整理核心参考与前沿线索。

从一个研究问题出发，把关键词、顶会顶刊检索、摘要阅读和版本核对串起来，为选题、组会和 Related Work 准备有来源、能继续阅读的文献清单。

## 能做什么

- 覆盖安全四大、AI、CV、其他重点会议及期刊，按单个场所生成简短查询并汇总去重。
- 实际检索优先尝试 Google Scholar；结合已连接的 Consensus、官方论文集和其他搜索工具补检。
- 阅读公开标题与摘要，按研究对象、问题和方法筛选，每篇说明与课题的具体关系。
- 查询“近几个月”时默认最近三个月，明确起止日期；背景摸底则覆盖前两个年度及本年度。
- 查找并优先引用正式发表版本，合并同一工作的预印本，保留方便阅读的链接。
- 核心参考与前沿线索分列；预印本结合领域、论文年龄和可核实的引用影响选择。
- 输出研究概述、分类结果和简短检索记录；按需准备 BibTeX 或 RIS。
- 支持仅生成组合、仅分类已有文献；屏幕控制为可选操作方式，单个入口受阻时继续换源检索。

这是一个以说明文件组成的技能。实际检索需要 Codex 环境提供搜索工具；仓库本身不提供论文数据库或搜索服务。技能指令以中文编写，可以要求用英文输出。

## 安装

在 Codex 中使用内置安装器：

```text
$skill-installer 请从 https://github.com/YYFaccept/frontier-literature-search 安装仓库根目录中的 frontier-literature-search 技能。
```

也可以手动安装。按当前 [OpenAI 官方文档](https://learn.chatgpt.com/docs/build-skills)，个人技能目录为 `~/.agents/skills`，项目技能目录为 `.agents/skills`。已有同名技能时更新现有安装，避免在多个目录重复安装；自定义环境以其实际技能目录为准。

**macOS / Linux：**

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/YYFaccept/frontier-literature-search.git "$HOME/.agents/skills/frontier-literature-search"
```

**Windows PowerShell：**

```powershell
$skillsDir = Join-Path $HOME '.agents/skills'
New-Item -ItemType Directory -Force -Path $skillsDir | Out-Null
git clone https://github.com/YYFaccept/frontier-literature-search.git (Join-Path $skillsDir 'frontier-literature-search')
```

安装后使用 `$frontier-literature-search` 调用。Codex 也可根据请求自动选择该技能；如果新安装没有出现，重启 Codex。

## 配合 Consensus

Consensus 可补充论文标题、摘要和引用信息。按[官方 MCP 文档](https://docs.consensus.app/consensus-mcp)连接到 Codex：

```sh
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

在浏览器中完成账户登录与授权，随后在 Codex 中确认工具可用；如果当前会话尚未加载，重新打开会话。技能使用连接后实际提供的参数与返回字段，正式发表信息仍回到出版记录核对。Consensus 为可选入口，未连接时也可使用其他搜索工具；安装本技能不会自动开通付费服务。

## 使用示例

只生成组合：

```text
$frontier-literature-search 为“多模态大模型隐私泄露”生成安全四大与 AI 三大会的检索组合，分别给出 Scholar 和普通联网搜索版本，不执行检索。
```

搜索最近三个月：

```text
$frontier-literature-search 检索最近三个月视觉语言模型隐私泄露的研究。优先尝试 Google Scholar，结合已连接的 Consensus 和官方论文集，阅读摘要筛选相关工作，优先引用正式版本。输出核心参考与前沿线索，核实首次公开日期、发表状态，并给出原始来源。
```

整理已有论文：

```text
$frontier-literature-search 仅整理我提供的论文列表，按技术路线分类，核对发表状态并合并预印本与正式版本，不扩展新论文检索。
```

需要其他时间范围、会议或语言时，直接写进请求。

可复制的完整提示词：

```text
使用 $frontier-literature-search 检索【研究主题】，重点关注【时间范围】及相关顶会顶刊。优先实际使用 Google Scholar，并结合已连接的 Consensus 和官方论文目录补检。某个入口不可用时，继续从其他来源获取论文标题和摘要，按研究对象、问题和方法筛选真正相关的文献。

优先采用正式发表版本；同一工作的 arXiv 与正式版本合并为一条，以正式出版信息引用。尚未正式发表的预印本，结合领域、论文年龄和可核实的引用量判断是否进入核心参考；低引用的新稿单列为前沿线索。

输出研究概述、核心参考、前沿线索及简短检索记录。逐篇说明相关性、发表状态、原始来源和实际阅读范围；近期论文区分首次公开、正式发表与版本更新。
```

## 检索流程与输出

研究问题 → Scholar 优先检索 → 多来源获取摘要 → 相关性筛选 → 正式版本核对 → 核心参考与前沿线索。

| 输出 | 内容 |
| --- | --- |
| 研究现状 | 技术路线、近期变化、优先阅读建议及依据 |
| 核心参考 | 正式成果优先，列出摘要筛选理由、版本关系、来源与阅读范围；预印本另附引用影响依据 |
| 前沿线索 | 高度相关的新预印本与尚未满足核心参考条件的工作，保留日期与发表状态 |
| 检索记录 | 实际执行的查询、工具、时间范围、覆盖场所和未核实信息 |

五组会议期刊和查询模板见 [search-guide.md](references/search-guide.md)。这些分组是检索起点，不等于实时核验后的 CCF 等级目录。

## 用在这些研究任务中

从一个研究问题出发，完成关键词设计、目标场所筛选、近期论文发现和分类整理，为阅读、选题和写作准备可追溯的文献材料。

- **开启新方向**：梳理核心概念与技术路线，建立首批阅读清单。
- **追踪前沿进展**：按指定月份、会议或期刊检索近期工作，把新论文加入已有研究地图。
- **准备组会与开题**：按研究问题组织代表性论文，整理方法之间的联系与差异。
- **组织 Related Work**：核对发表信息、合并论文版本，按技术路线形成可用于写作的分类索引。

## 仓库结构

```text
SKILL.md                         技能入口
agents/openai.yaml               界面信息与自动调用设置
references/search-guide.md      场所清单、组合模板与记录格式
README.md / README.en.md         中英文使用说明
CONTRIBUTING.md                  贡献方式
LICENSE                         MIT 许可证
```

## 贡献与许可

欢迎通过 Issue 或 Pull Request 补充有原始证据的查询方法、场所名称和检索案例。提交方法见 [CONTRIBUTING.md](CONTRIBUTING.md)。

本仓库以 [MIT License](LICENSE) 开源。论文、出版方内容和公众号文章仍适用各自的许可；仓库中的链接不改变其版权，也不代表相关机构为本项目背书。
