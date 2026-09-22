# 前沿文献检索 · Frontier Literature Search

**从一个研究问题，整理出有摘要依据、有正式出处、可以继续阅读的参考文献。**

一个用于 Codex 的研究技能：优先使用 Google Scholar，结合官方论文集、公开摘要和可选的 Consensus，把关键词设计、相关性筛选与版本核对连起来。适合新方向摸底、追踪近期工作、准备组会和组织 Related Work。

[English](README.en.md) · [快速开始](#快速开始) · [使用方式](#三种使用方式) · [技能指令](SKILL.md) · [检索指南](references/search-guide.md)

## 为什么使用它

- **按研究问题筛选**：阅读摘要，说明每篇论文与课题的具体关系，区分风险评测、攻击方法与防护方法。
- **正式版本优先**：找到出版记录后采用正式题名、年份和场所，同一工作的 arXiv 与正式版本合并为一条。
- **核心参考与前沿线索分开**：既为 Related Work 准备稳定的参考，也保留刚公开、引用尚少的新研究。
- **让检索可以继续**：输出原始链接、分类和阅读范围，按需提供 Zotero 可导入的 BibTeX 或 RIS。

## 快速开始

**1. 在 Codex 中安装：**

```text
$skill-installer 请从 https://github.com/YYFaccept/frontier-literature-search 安装仓库根目录中的 frontier-literature-search 技能。
```

**2. 给出一个研究问题：**

```text
使用 $frontier-literature-search 检索最近三个月视觉语言模型隐私泄露与保护的论文，重点关注安全四大及 AI、CV 相关会议。优先实际使用 Google Scholar，结合已连接的 Consensus 和官方论文集，阅读摘要筛选相关工作，优先引用正式版本。输出研究概述、核心参考、前沿线索和简短检索记录。
```

安装后可用 `$frontier-literature-search` 显式调用，也支持 Codex 根据请求自动选择。主题、时间范围、目标场所和输出语言都可以直接在请求中指定。实际搜索使用当前 Codex 环境提供的工具；Consensus 为可选入口。

<details>
<summary>手动安装（macOS / Linux / Windows）</summary>

按 [Codex 技能安装文档](https://learn.chatgpt.com/docs/build-skills)，可将仓库放入个人技能目录 `~/.agents/skills`，或项目目录 `.agents/skills`。已有同名技能时更新现有安装；自定义环境使用其实际技能目录，避免重复安装。

macOS / Linux：

```sh
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/YYFaccept/frontier-literature-search.git "$HOME/.agents/skills/frontier-literature-search"
```

Windows PowerShell：

```powershell
$skillsDir = Join-Path $HOME '.agents/skills'
New-Item -ItemType Directory -Force -Path $skillsDir | Out-Null
git clone https://github.com/YYFaccept/frontier-literature-search.git (Join-Path $skillsDir 'frontier-literature-search')
```

如果新安装尚未出现在 Codex 中，重启后再调用。

</details>

## 三种使用方式

| 模式 | 适合的任务 | 交付内容 |
| --- | --- | --- |
| 实际检索 | 新方向摸底、近期论文、顶会顶刊补检 | 研究概述、筛选后的文献、来源及检索记录 |
| 仅生成查询 | 自己在 Scholar 或其他搜索工具中检索 | 短查询、单场所条件、时间范围与实验组合 |
| 仅整理已有文献 | 整理收藏、准备组会、组织 Related Work | 分类索引、正式版本核对与重复条目合并 |

**只生成组合，不执行检索：**

```text
$frontier-literature-search 为“多模态大模型隐私泄露”生成安全四大与 AI 三大会的检索组合，分别给出 Scholar 和普通联网搜索版本，不执行检索。
```

**只整理现有论文：**

```text
$frontier-literature-search 仅整理我提供的论文列表，按技术路线分类，核对发表状态并合并预印本与正式版本，不扩展新论文检索。
```

仅生成查询时无需联网或打开浏览器。实际检索优先尝试 Scholar；屏幕控制是可用方式，明确要求本地页面时会实际操作该页面并记录执行状态。

<details>
<summary>复制完整研究 Prompt</summary>

```text
使用 $frontier-literature-search 检索【研究主题】，重点关注【时间范围】及相关顶会顶刊。优先实际使用 Google Scholar，并结合已连接的 Consensus 和官方论文目录补检。某个入口不可用时，继续从其他来源获取论文标题和摘要，按研究对象、问题和方法筛选真正相关的文献。

优先采用正式发表版本；同一工作的 arXiv 与正式版本合并为一条，以正式出版信息引用。尚未正式发表的预印本，结合领域、论文年龄和可核实的引用量判断是否进入核心参考；低引用的新稿单列为前沿线索。

输出研究概述、核心参考、前沿线索及简短检索记录。逐篇说明相关性、发表状态、原始来源和实际阅读范围；近期论文区分首次公开、正式发表与版本更新。
```

</details>

## 检索流程

**明确问题 → Scholar 优先检索 → 多来源获取摘要 → 筛选相关性 → 核对正式版本 → 分类交付**

默认采用短查询，逐个场所设置出版物和年份条件，再汇总去重。Google Scholar、官方论文集与 Consensus 各按实际支持的参数使用；一个入口不可用时继续从其他来源获取标题、摘要和出版信息。

“最近几个月”未指定月数时采用最近三个日历月；背景摸底覆盖前两个年度及本年度。按执行当天计算窗口，逐篇区分首次公开、正式发表和旧稿更新。

### 五组目标会议与期刊

| 分组 | 初始目标 |
| --- | --- |
| 安全四大 | ACM CCS、USENIX Security、IEEE S&P、NDSS |
| AI | ICLR、NeurIPS、ICML |
| 计算机视觉 | CVPR、ICCV、ECCV |
| 其他重点会议 | AAAI、IJCAI、ACL、ACM Multimedia |
| 重点期刊 | IEEE TIFS、TDSC、TPAMI |

按课题选择相关场所，也可自行指定其他会议期刊。出版物名称、短查询和实验组合见 [检索指南](references/search-guide.md)；这些分组是检索起点，会议等级按需要另查当前目录。

## 你会得到什么

| 输出 | 内容 |
| --- | --- |
| 研究概述 | 主要技术路线、近期变化、建议优先阅读的工作及依据 |
| 核心参考 | 正式成果优先，逐篇说明相关性、发表状态、版本关系、来源与阅读范围 |
| 前沿线索 | 高度相关的新预印本及尚未满足核心参考条件的工作，保留日期与引用依据 |
| 背景与待核验条目 | 经典方法、能力评测背景，以及仍缺摘要或发表证据的候选，按需要单列 |
| 简短检索记录 | 实际入口、查询、筛选条件和会影响结论的信息缺口 |

摘要足够支持初筛时即可纳入，并标注“仅摘要”；只有实际读过全文才报告相应细节。预印本进入核心参考时，结合领域、公开时长和可核实的引用影响判断，不使用统一引用数门槛。默认交付分类索引，需要时再导出 BibTeX 或 RIS。

## 配合 Consensus

Consensus 可补充论文标题、摘要和引用信息。**已经连接时直接使用，跳过下面的安装和登录命令。** 仅首次接入时，按[官方 MCP 文档](https://docs.consensus.app/consensus-mcp)连接到 Codex：

```sh
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

首次完成账户授权后，后续检索复用现有连接，由客户端管理凭据与刷新。技能先调用已加载的工具；确需重新认证时只保留一个授权流程，在已授权范围内处理普通确认按钮，需要用户输入或新增权限时再请求协助。

检索时使用工具实际提供的参数，正式发表信息回到出版记录核对。未连接 Consensus 也可以使用本技能；安装技能不会自动开通付费服务。

## 文档与贡献

- [SKILL.md](SKILL.md)：技能流程与交付规则。
- [检索指南](references/search-guide.md)：五组场所、查询模板、公众号线索、分类格式与完整 Prompt。
- [agents/openai.yaml](agents/openai.yaml)：中文界面信息与自动调用设置。
- [docs/](docs/)：独立的检索案例与实测记录。
- [贡献指南](CONTRIBUTING.md)：通过 Issue 或 Pull Request 补充场所、查询方法和有来源的案例。

技能指令以中文编写，可要求用英文输出。本项目采用 [MIT License](LICENSE)；链接中的论文及第三方内容仍适用各自的许可。
