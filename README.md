# 前沿文献检索 · Frontier Literature Search

[English](README.en.md) · [技能指令](SKILL.md) · [检索模板](references/search-guide.md) · [测试记录](docs/validation-2026-09-22.md)

一个用于 Codex 的文献检索技能：生成顶会顶刊查询组合，查找近期研究，核实论文日期与发表状态，再按技术路线整理结果。

它关注一个常见问题：搜索结果容易集中在旧论文和便于获取的预印本，而“最近更新”又可能只是旧稿修订。技能要求分别记录首次公开、版本更新、接收和正式发表的证据。

## 能做什么

- 生成安全四大、AI、CV、其他重点会议及期刊的组合检索式。
- 使用宿主已有的联网、AI 或学术搜索工具查找论文，并按搜索入口适配语法。
- 查询“近几个月”时默认最近三个月，明确起止日期；背景摸底则覆盖前两个年度及本年度。
- 区分正式发表、已接收、预印本和待核验线索，合并同一工作的不同版本。
- 输出研究概述、分类论文表和实际检索记录；按需准备 BibTeX 或 RIS。
- 支持仅生成组合、仅分类已有文献；Google Scholar 页面操作和屏幕控制均为可选路径。

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

## 使用示例

只生成组合：

```text
$frontier-literature-search 为“多模态大模型隐私泄露”生成安全四大与 AI 三大会的检索组合，分别给出 Scholar 和普通联网搜索版本，不执行检索。
```

搜索最近三个月：

```text
$frontier-literature-search 检索最近三个月视觉语言模型隐私泄露的研究。使用可用搜索工具，核实首次公开日期与发表状态，区分新工作、近期正式发表和旧稿更新，并给出原始来源。
```

整理已有论文：

```text
$frontier-literature-search 仅整理我提供的论文列表，按技术路线分类，核对发表状态并合并预印本与正式版本，不扩展新论文检索。
```

需要其他时间范围、会议或语言时，直接写进请求。

## 检索流程与输出

研究问题 → 关键词与场所组合 → 可用工具检索 → 原始记录核验 → 分类与检索记录。

| 输出 | 内容 |
| --- | --- |
| 研究现状 | 技术路线、近期变化、优先阅读建议及依据 |
| 分类论文表 | 题名、作者、日期、场所、发表状态、相关性、原始来源及阅读范围 |
| 检索记录 | 实际执行的查询、工具、时间范围、覆盖场所和未核实信息 |

五组会议期刊和查询模板见 [search-guide.md](references/search-guide.md)。这些分组是检索起点，不等于实时核验后的 CCF 等级目录。

## 已验证的范围

[2026-09-22 的小规模检索记录](docs/validation-2026-09-22.md)包含实际查询、四篇近期 arXiv 论文及逐篇日期证据。检索窗口为 2026-06-22 至 2026-09-22，最新稿件的首次 arXiv 提交日期为 2026-09-18。

该记录验证了发现近期公开论文的路径，没有验证全领域召回率。Scholar 的 `source:`、`+` 和多会议 `OR` 组合仍是待验证模板；作者自报接收与会议方确认在记录中分开说明。测试记录保留当时的事实，重新执行应使用新的截止日期和来源状态。

## 仓库结构

```text
SKILL.md                         技能入口
agents/openai.yaml               界面信息与自动调用设置
references/search-guide.md      场所清单、组合模板与记录格式
docs/validation-2026-09-22.md    带日期的实际检索记录
README.md / README.en.md         中英文使用说明
CONTRIBUTING.md                  贡献方式
LICENSE                         MIT 许可证
```

## 贡献与许可

欢迎通过 Issue 或 Pull Request 补充有原始证据的查询方法、场所名称和检索案例。提交方法见 [CONTRIBUTING.md](CONTRIBUTING.md)。

本仓库以 [MIT License](LICENSE) 开源。论文、出版方内容和公众号文章仍适用各自的许可；仓库中的链接不改变其版权，也不代表相关机构为本项目背书。
