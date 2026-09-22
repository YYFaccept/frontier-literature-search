# 检索指南

按当前任务读取相关段落：选择场所时读“目标会议与期刊”，生成或执行查询时读“查询方法与示例”，整理结果时读“证据与分类模板”。Scholar 页面操作为可选路径。

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

仅生成组合时，提供主题词与场所组合及建议时间范围即可，不要求读取网页。实际检索时使用当前可用工具，不要求先打开 Scholar。

| 入口 | 查询或筛选方式 | 结果证据 |
| --- | --- | --- |
| Google Scholar | 下面保留的 `source:` 组合，或可选高级检索的出版物、年份字段 | 未执行的组合标为未执行；语法是否有效需以该入口真实结果判断 |
| 普通联网 / AI 搜索 | 简短主题词 + 会议名 + 年份；按工具支持情况设置原始来源域名和日期条件 | 打开具体论文页面核验，不能把 Scholar `source:` 直接移植到此入口 |
| 学术搜索工具 / API | 语义或关键词查询，以及该工具支持的日期、场所等字段 | 对照出版条目或预印本版本历史核验 |
| 官方论文集 / 预印本目录 | 当前年度或月份目录中的主题检索 | 明确具体论文的首次发布、版本更新、正式发表日期 |

例如普通搜索可分别尝试 `"vision language model" privacy 2026`、`"multimodal" "membership inference" 2026`、`"multimodal" privacy "ICML 2026"`，配合 arxiv.org、proceedings.mlr.press、usenix.org 等相关原始来源筛选。这些是查询建议，只有提交后才可写入“实际检索记录”。

“最近几个月”默认最近三个日历月。以 2026-09-22 执行为例，窗口为 2026-06-22 至 2026-09-22；下次执行应重新计算。查询中的年份及搜索引擎日期过滤不能代替逐篇日期核验。

### 可选的 Scholar 页面操作

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

根据需要用年份限制保持相关性排序，再切换按日期排序补查新结果。“被引用”和“相关文章”适合从锚点扩展，但高被引不是新近研究的替代标准。

### 组合模板：待验证示例

以下提供核心式与五个场所限定式。将核心式与任意一个限定式用空格连接，即得到对应组的完整示例。**这些 Scholar 专用表达式尚未通过该入口验证，提供为可复制组合，不保证实际过滤效果。生成组合不要求页面实测；实际检索优先选择当前可用的搜索路径并适配其语法。**

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

只有当前任务确实需要这类语法时，才用简短单场所查询核对其效果：看实际返回论文及官方场所，必要时与高级检索出版物字段的结果比较。能提交查询或返回结果本身不证明运算符有效，单场所可用也不证明复杂 OR 嵌套有效。无需为使用本技能逐个测试所有表达式。

### 已核实的官方依据

核验日期：2026-09-22。

- [Google Scholar Search Help](https://scholar.google.com/intl/en/scholar/help.html)：说明高级检索可按作者、标题、出版物和日期检索，支持年份限制及日期排序；覆盖不保证完整。该帮助页未明确说明模板中 `source:`、`AND`、`OR`、`+` 及其复杂组合的语义，这不等于已证明它们不可用。
- [Google 异常流量说明](https://support.google.com/websearch/answer/86640?hl=en)：描述自动查询等流量导致限制的情况，没有给出查询长度导致封禁的规则或安全频率阈值。短查询是检索质量建议。

官方帮助未确认“遇封禁切换镜像”的建议。遵循主技能的暂停与备用入口规则；操作界面发生变化且影响任务时再核实帮助文档，不为稳定事实重复查证。

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
| 与课题的关系 | 一句话说明论文解决的问题或提供的相关证据 |
| 原始来源 | 具体出版条目、接收决定或预印本链接；有 DOI 则保留 |
| 可读版本与阅读范围 | 全文链接及实际已读部分，或“仅摘要”“全文未获取” |
| 版本关系 | 与预印本或正式条目的对应关系；有实质差异时说明 |

原文事实与推断分开写，例如“作者报告……”需对应原文证据；“据此判断适合与某类方法比较……”属于自己的分析，不能写成论文已验证的结论。仅搜索不到正式记录时，不能断言从未发表。

### 分类方式

```text
课题：视觉语言模型隐私泄露
  技术路线子集合（按实际读到的论文建立）
  背景与经典论文
  待核验线索

标签：场所、年份、发表状态、阅读状态
```

需要按会议级别分类时，查询当前官方目录并注明目录版本。Zotero 中同一条目可属于多个集合，不为每个标签复制一篇论文。已有个人分类时优先沿用。

### 简短检索记录

- 课题、检索日期、覆盖年份及截至日期。
- AI 摸底使用的工具或搜索入口及形成的主要关键词。
- 实际使用的搜索工具及入口；每个有用查询的词语、场所、日期筛选及结果摘要。若操作 Scholar 页面，再记录官方站或镜像、排序和页面链接。
- 查过的官方会议期刊来源，以及哪些有本年度已公布成果。
- 公众号或动态线索实际覆盖情况。
- Scholar 组合式是否执行；页面为“已使用／未使用／不可用”。只生成但没提交的组合单独标注，不把其他工具的搜索结果写成 Scholar 语法验证。
- 近几个月的结果逐篇列出日期证据，不能用旧论文修订或只有年份的记录充作近期新论文。
- 尚缺的全文、发表状态或主题覆盖，及其对结论的实际影响。

结果只代表所记范围内的检索，避免声称穷尽全领域。若已经找到足以回答用户问题的证据且约定范围已覆盖，结束检索。
