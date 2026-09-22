# 检索指南

按当前任务读取相关段落：选择场所时读“目标会议与期刊”，生成或执行查询时读“查询方法与示例”，使用已连接工具时读“Consensus 协作检索”，整理结果时读“证据与分类模板”。实际检索优先尝试 Scholar；屏幕控制不是唯一入口。

## 目标会议与期刊

以下五组是初始检索目标；按课题选择，不代表各学科完整列表或已核验的 CCF 等级。出版物名称的缩写和全称可能影响匹配；结果过少时分别尝试，并用官方条目核实真实场所。

| 分组 | 目标 | 出版物字段候选名称 |
| --- | --- | --- |
| 安全四大 | CCS、USENIX Security、IEEE S&P、NDSS | ACM SIGSAC Conference on Computer and Communications Security；USENIX Security Symposium；IEEE Symposium on Security and Privacy；Network and Distributed System Security Symposium |
| AI 三大会 | ICLR、NeurIPS、ICML | International Conference on Learning Representations；Advances in Neural Information Processing Systems；International Conference on Machine Learning |
| CV 三大会 | CVPR、ICCV、ECCV | Computer Vision and Pattern Recognition；International Conference on Computer Vision；European Conference on Computer Vision |
| 其他重点会议 | AAAI、IJCAI、ACL、ACM MM | AAAI Conference on Artificial Intelligence；International Joint Conference on Artificial Intelligence；Annual Meeting of the Association for Computational Linguistics；ACM International Conference on Multimedia |
| 重点期刊 | TIFS、TDSC、TPAMI | IEEE Transactions on Information Forensics and Security；IEEE Transactions on Dependable and Secure Computing；IEEE Transactions on Pattern Analysis and Machine Intelligence |

官方核验入口可从会议官网进入当前年度论文集或接收列表；相关常见来源包括 USENIX、NDSS 官方论文页、ACM Digital Library、IEEE Xplore、OpenReview 的正式决定、NeurIPS Proceedings、PMLR、CVF Open Access、ECCV 官方论文集、AAAI Proceedings、IJCAI Proceedings 和 ACL Anthology。检索时打开具体条目，不只引用入口首页。OpenReview 投稿页不等于录用证明，ACL Findings、workshop 与主会条目按实际场所注明。

## 查询方法与示例

### 通用查询与搜索入口适配

仅生成组合时，提供主题词与场所组合及建议时间范围即可，不要求读取网页。实际检索优先在 Scholar 提交主题、出版物和年份条件，再通过其他来源补检；不能用已生成的查询或其他引擎结果代替 Scholar 实测。

| 入口 | 查询或筛选方式 | 结果证据 |
| --- | --- | --- |
| Google Scholar | 默认简短主题查询 + 高级检索出版物、年份字段，每次一个场所 | 核对实际应用字段和具体论文；实验运算符按下文单独验证 |
| 普通联网 / AI 搜索 | 简短主题词 + 会议名 + 年份；按工具支持情况设置原始来源域名和日期条件 | 打开具体论文页面核验，不能把 Scholar `source:` 直接移植到此入口 |
| Consensus / 其他学术工具 | 先读实际工具参数，使用其支持的年份、出版类型等条件 | 保留原始摘要、论文标识和引用量来源，回到出版记录核验 |
| 官方论文集 / 预印本目录 | 当前年度或月份目录中的主题检索 | 明确具体论文的首次发布、版本更新、正式发表日期 |

例如普通搜索可分别尝试 `"vision language model" privacy 2026`、`"multimodal" "membership inference" 2026`、`"multimodal" privacy "ICML 2026"`，配合 arxiv.org、proceedings.mlr.press、usenix.org 等相关原始来源筛选。这些是查询建议，只有提交后才可写入“实际检索记录”。

“最近几个月”默认最近三个日历月。以 2026-09-22 执行为例，窗口为 2026-06-22 至 2026-09-22；下次执行应重新计算。查询中的年份及搜索引擎日期过滤不能代替逐篇日期核验。

### Scholar 查询与页面操作

以“视觉语言模型隐私泄露”为例，先用少量组合探索术语：

```text
"vision language model" privacy
"multimodal large language model" privacy
"vision language model" "membership inference"
"large language model" "visual privacy"
```

这些是可调整的起始查询，不保证穷尽同义词；精确短语过窄时去除引号或改用已发现论文的术语。每个组合单独提交，观察结果后决定是否需要下一条。

在高级检索中使用：

| 字段 | 示例 |
| --- | --- |
| 所有字词 / all of the words | privacy |
| 完整字句 / exact phrase | vision language model |
| 至少一个字词 / at least one of the words | image visual multimodal（确有需要才填） |
| 出版物 / return articles published in | USENIX Security（每次一个场所，按结果尝试全称或短名） |
| 日期 / return articles dated between | 当前年份减 2 至当前年份；具体截至日另记在检索记录中 |

先检查页面是否实际应用字段。过多条件会减少召回；无结果时先放宽出版物或短语，再按论文标题和官方条目核对，不把出版物筛选当作完整收录保证。

根据需要用年份限制保持相关性排序，再切换按日期排序补查新结果。“被引用”和“相关文章”适合从锚点扩展；引用量用于判断预印本是否进入核心参考，不能替代近期线索检索。

普通加载失败最多重试一次，仍失败则转到官方论文集、出版页和其他学术工具。验证码或明确限制立即停止该入口。将这一状态放入检索记录，继续获取题名与摘要并完成筛选，不以一条“页面访问超时”结束交付。

### 组合模板：待验证示例

以下提供核心式与五个场所限定式。将核心式与任意一个限定式用空格连接，即得到对应组的完整示例。**这些表达式保留为待验证的实验模板，默认使用单场所高级检索。只有实际检查某个组合的过滤结果后，才能说明该次观察到的效果；不保证其他组合有效。仅生成组合不要求页面实测。**

核心式：

```text
("Large Language Model" OR LLM OR GPT) + ("Privacy") + ("visual" OR "image" OR "picture" OR "Multi-Modal" OR "Multi Modal" OR "face" OR "facial")
```

安全四大限定式：

```text
(source:"ACM SIGSAC" OR source:"USENIX SECURITY" OR source:"IEEE Symposium on Security and Privacy" OR source:"Network and Distributed System Security Symposium")
```

AI 三大会限定式：

```text
(source:"International Conference on Learning Representations" OR source:"Neural Information Processing Systems" OR source:"International Conference on Machine Learning")
```

CV 三大会限定式：

```text
(source:"Computer Vision and Pattern Recognition" OR source:"International Conference on Computer Vision" OR source:"European Conference on Computer Vision")
```

其他重点会议限定式：

```text
(source:"AAAI" OR source:"Joint Conference on Artificial Intelligence" OR source:"Association for Computational Linguistics" OR source:"ACM International Conference on Multimedia")
```

重点期刊限定式：

```text
(source:"IEEE Transactions on Information Forensics and Security" OR source:"IEEE Transactions on Dependable and Secure Computing" OR source:"IEEE Transactions on Pattern Analysis and Machine Intelligence")
```

需要验证语法时，一次改变一个条件；先从官方来源确认一篇相关正式论文及其场所，作为对照。记录实际结果题名、正式场所和具体误纳入或遗漏，不只比较页面估计数量。

| 待测项 | 与什么比较 | 观察什么 |
| --- | --- | --- |
| 单场所 `source:` | 同主题 + 高级检索单一出版物字段 | 目标场所论文是否出现，有无其他场所条目；无结果时检查名称匹配 |
| `+` | 完全相同词语、去掉 `+` 的查询 | 返回论文是否实际满足所需主题；少量重合结果不能证明运算符语义 |
| 多场所 `OR` | 分别执行两个单场所查询后合并的论文清单 | 各场所已知相关论文是否仍被纳入，有无其他场所误入 |

能提交查询或返回结果本身不证明过滤有效；单场所可用也不证明复杂 OR 嵌套有效。结果不足以辨别效果时写“未能确认”，保留默认高级检索路径。无需为每次文献任务重测所有实验表达式。

### 已核实的官方依据

核验日期：2026-09-22。

- [Google Scholar Search Help](https://scholar.google.com/intl/en/scholar/help.html)：说明高级检索可按作者、标题、出版物和日期检索，支持年份限制及日期排序；覆盖不保证完整。该帮助页未明确说明模板中 `source:`、`AND`、`OR`、`+` 及其复杂组合的语义，这不等于已证明它们不可用。
- [Google 异常流量说明](https://support.google.com/websearch/answer/86640?hl=en)：描述自动查询等流量导致限制的情况，没有给出查询长度导致封禁的规则或安全频率阈值。短查询是检索质量建议。

官方帮助未确认“遇封禁切换镜像”的建议。遵循主技能的暂停与备用入口规则；操作界面发生变化且影响任务时再核实帮助文档，不为稳定事实重复查证。

## Consensus 协作检索

[Consensus 官方 MCP 说明](https://docs.consensus.app/consensus-mcp)提供入口 `https://mcp.consensus.app/mcp`。Consensus 是可选协作工具，不作为技能强制依赖。用户要求接入时按当前客户端支持的方式配置，由用户完成所需账户认证；不自动新增付费订阅或开启额外计费。

已连接时：

1. 读取当前暴露的工具说明与参数，再按研究对象、问题和方法查询。不要把 REST API 文档中的字段直接套给 MCP。
2. 核心参考检索优先使用工具实际支持的年份和排除预印本条件；前沿线索需要时另查预印本。工具不提供某项过滤时，在结果筛选阶段完成，不编造参数。
3. 区分返回的原始论文摘要与 AI 生成的答案。摘要用于相关性初筛；结论、引用数据及场所仍需保留相应来源。逐篇追到官方出版记录，采用正式版本。
4. 有引用量时记录数值、提供方和查询日期；没有时写未知。月份依靠逐篇原始日期证据，年份过滤不能证明“最近三个月”。
5. 未连接、认证未完成或工具失败时继续其他来源。在检索记录中区分“未使用／调用失败／实际返回结果”；只有真实返回论文并完成相应核验后才能记为 Consensus 实测完成。

## 可复制 Prompt

```text
使用 $frontier-literature-search 检索【研究主题】，重点关注【时间范围】及相关顶会顶刊。优先实际使用 Google Scholar，并结合已连接的 Consensus 和官方论文目录补检。某个入口不可用时，继续从其他来源获取论文标题和摘要，按研究对象、问题和方法筛选真正相关的文献。

优先采用正式发表版本；同一工作的 arXiv 与正式版本合并为一条，以正式出版信息引用。尚未正式发表的预印本，结合领域、论文年龄和可核实的引用量判断是否进入核心参考；低引用的新稿单列为前沿线索。

输出研究概述、核心参考、前沿线索及简短检索记录。逐篇说明相关性、发表状态、原始来源和实际阅读范围；近期论文区分首次公开、正式发表与版本更新。
```

仅要组合式时，可改为：“使用 $frontier-literature-search，为视觉语言模型隐私泄露生成安全四大和 AI 三大会的简短查询及时间条件，不执行检索；实验运算符单列。”仅整理已有文献时，可改为：“使用 $frontier-literature-search，阅读以下论文摘要并分类，核对正式版本、合并重复条目，分列核心参考与前沿线索，不扩展候选集合。”

## 微信公众号线索

可按主题选取的候选名称：Security for Al、具身智能之心、PaperAgent、Ai安全论文研究、智能计算与通信网络、Today读什么、安全学术圈、隐者联盟、复旦白泽战队、新智元、机器之心、为机器立心、模安局、量子位。

这份初始名单未独立核实账号身份、拼写或活跃状态。按课题选择可访问的推文；相似名称不能作为账号身份依据，不要求关注全部账号，也不自动订阅。

推文导读可提供题名、作者、会议信息和技术词汇。将这些用于定位论文，之后以官方接收或出版记录核实场所，以原文核实研究结论。没有可访问内容时在记录中写明未覆盖。

## 证据与分类模板

### 单篇记录

记录下列字段；表格太宽时将详细证据放在论文条目下，不强求单张大表。

| 字段 | 记录内容 |
| --- | --- |
| 题名与作者 | 原始页面的题名、主要作者或作者列表 |
| 年份与场所 | 正式发表年份、实际会议或期刊；尚无正式记录时写预印本年份 |
| 日期与新近性 | 首次公开、最新版本、正式发表或接收日期及证据；区分窗口内新工作、近期正式发表、仅版本更新、月份未确认 |
| 发表状态 | 正式发表 / 已接收 / 预印本且正式发表未确认 / 待核验 |
| 技术路线 | 按读到的方法归类；仅凭摘要不足以细分时保留较粗分类 |
| 摘要筛选 | 直接相关 / 背景相关 / 排除；以研究对象、问题和方法说明一句具体理由，并附摘要来源 |
| 参考类别 | 核心参考 / 前沿线索 / 背景论文 / 待核验；排除条目不进入入选表 |
| 原始来源 | 具体出版条目、接收决定或预印本链接；有 DOI 则保留 |
| 可读版本与阅读范围 | 全文链接及实际已读部分，或“仅摘要”“全文未获取” |
| 引用影响 | 预印本进入核心参考时必填：引用量、数据库、查询日期，以及结合领域和公开时长的判断依据；未知不记为零，不跨库相加 |
| 版本关系 | 正式记录为主，预印本作为阅读链接；记录题名变更或明确对应依据，有实质差异时说明 |

原文事实与推断分开写，例如“作者报告……”需对应原文证据；“据此判断适合与某类方法比较……”属于自己的分析，不能写成论文已验证的结论。仅搜索不到正式记录时，不能断言从未发表。

### 摘要与版本的筛选示例

- 题名出现“privacy”但摘要研究普通视觉分类中的图像脱敏、没有涉及所需视觉语言模型问题：按当前课题排除或列为背景，不能凭题名进入核心参考。
- 官方出版页能读到相关摘要而全文不可获取：可作为“仅摘要”的正式核心参考，不补造方法细节。
- arXiv 页给出正式 DOI，出版页与作者、题名相符：以出版条目引用，只保留一个主条目；有疑问的题名变化核实后再合并。
- 预印本已有可核实引用影响且直接相关：记录数值、来源和日期，结合相近领域与公开时长解释为何值得进入核心参考；“看起来经典”不是引用证据。
- 新预印本直接相关但引用低或未知：列为前沿线索；摘要仍不可得的候选列待核验，二者不混为一类。

这些是行为示例，不是已完成的实测记录。

### 分类方式

```text
课题：视觉语言模型隐私泄露
  核心参考（按技术路线组织）
  前沿线索（按技术路线组织）
  背景与经典论文
  待核验线索

标签：场所、年份、发表状态、阅读状态
```

需要按会议级别分类时，查询当前官方目录并注明目录版本。Zotero 中同一条目可属于多个集合，不为每个标签复制一篇论文。已有个人分类时优先沿用。

### 简短检索记录

- 课题、检索日期、覆盖年份及截至日期。
- AI 摸底使用的工具或搜索入口及形成的主要关键词。
- 实际使用的搜索工具及入口；每个有用查询的词语、场所、日期筛选及结果摘要。Scholar 记录实际页面或工具、官方站或用户备用入口、排序和链接。
- 查过的官方会议期刊来源，以及哪些有本年度已公布成果。
- 公众号或动态线索实际覆盖情况。
- Scholar 是否真实执行，出版物和年份筛选是否实际应用；实验组合的对照和具体纳入、遗漏结果。只生成但没提交的组合单独标注，不把其他工具的结果写成 Scholar 语法验证。
- Consensus 是否已连接、实际使用的参数及返回结果；工具原始摘要与原始出版页分别注明。未实际调用时不声称已通过。
- 会影响结果的入口失败与换源路径集中在此简述，无需重复故障堆栈。
- 近几个月的结果逐篇列出日期证据，不能用旧论文修订或只有年份的记录充作近期新论文。
- 尚缺的全文、发表状态或主题覆盖，及其对结论的实际影响。

结果只代表所记范围内的检索，避免声称穷尽全领域。若已经找到足以回答用户问题的证据且约定范围已覆盖，结束检索。
