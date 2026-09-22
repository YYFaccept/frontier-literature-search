# Scholar 页面检索与分类复测

执行日期：2026-09-22。课题：视觉语言模型隐私泄露与保护。近期窗口：2026-06-22 至 2026-09-22。2025 年论文用于查询对照和正式版本验证，不计入近期新论文。

本轮通过屏幕／浏览器控制实际操作本地 **Codex 内置浏览器** 中的 Google Scholar 页面：输入查询、填写高级检索出版物及年份、提交并读取结果。该成功入口不是先前的 Chrome 扩展会话。历史测试记录保留原状，以下为后续实际结果。

## 查询及对照

### 主题与高级检索

1. 主题查询 `"vision language" privacy`：实际返回论文，包括 *Membership Inference* 相关方向之外的视觉隐私评估、脱敏及输入保护工作；搜索片段不作为已读摘要。
2. 高级检索：所有字词 `vision language models membership inference`；完整字句 `vision language`；出版物 `USENIX Security`；年份 2025–2025。其他输入为空。完整字句条件实际保留，不能将此次写成只有“所有字词”的查询。
3. 提交后搜索框显示 `vision language models membership inference "vision language" source:USENIX source:Security`，页面显示 2025–2025，返回下表七篇论文。

| 编号 | 论文题名 | Scholar 的场所／年份及原始条目 |
| --- | --- | --- |
| U1 | Membership Inference Attacks Against Vision-Language Models | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/hu-yuke) |
| U2 | Unlocking the Power of Differentially Private Zeroth-Order Optimization for Fine-Tuning LLMs | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/bao-ergute) |
| U3 | Dormant: Defending Against Pose-Driven Human Image Animation | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/zhou) |
| U4 | Self-Interpreting Adversarial Images | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/zhang-tingwei) |
| U5 | Private Investigator: Extracting Personally Identifiable Information from Large Language Models Using Optimized Prompts | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/keum) |
| U6 | SelfDefend: LLMs Can Defend Themselves Against Jailbreaking in a Practical Manner | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/wang-xunguang) |
| U7 | Investigating the Impact of Online Community Involvement on Safety Practices and Perceived Risks Among People Who Use Drugs | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/li-jiliang) |

上述七条的页面元数据均符合指定场所与年份。其中 U1、U7 另读官方出版页及摘要；其他五条仅作为查询集合对照，不声称完成摘要筛选。

### 运算符对照

以下均保留页面显示的 2025–2025 年条件，逐条提交并读取全部返回条目。查询中 `B` 仅为此表缩写，实际输入时展开为 `vision language models membership inference "vision language"`。

| 实际查询（展开 B） | 返回集合 | 可得结论 |
| --- | --- | --- |
| `B source:"USENIX Security"` | U1–U7；U2、U3 排序与高级检索不同 | 该名称、主题和年份下与高级检索得到同一集合，没有观察到其他场所误入 |
| `vision language models membership inference + "vision language" + source:"USENIX Security"` | 与上条集合及排序相同 | 未能辨别 `+` 的独立作用，不能据此声称已证明其逻辑语义 |
| `B source:"Findings of the Association for Computational Linguistics"` | 无结果 | 只说明这条查询未命中，不能断言 Findings 没有相关论文 |
| `B (source:"USENIX Security" OR source:"Findings of the Association for Computational Linguistics")` | U1–U7 | 没有遗漏非空单场所集合中的论文；另一对照为空，未验证两个非空集合合并效果 |

这是一个名称和固定条件下的小规模对照。安全四大、AI、CV、其他会议和期刊的长模板没有逐一执行，仍为实验示例；不把结果数量或上述重合视为所有组合有效的证据。

### 近期论文检索

实际在 Scholar 页面打开主题查询 `"vision language" geolocation privacy`，年份 2026–2026，确认可见年份条件并读取首页十条结果。其中包括：

- **GeoShield**：链接到 AAAI 正式论文页。
- **GeoAgent**：链接到 arXiv:2608.29483。
- 其他结果涉及位置推断、综述和环境视频描述，未全部完成摘要筛选，不全数列为相关参考。

随后在同一年份条件下提交 `"Hiding in Plain Sight" "Geolocation"`：页面显示 18 条结果，已读首页十条，目标论文不在该页。再提交完整题名 `"Hiding in Plain Sight: A Diffusion-based Mitigation of Geolocation Privacy Leakage in Vision-Language Models"`：页面明确返回无匹配文章。该观察不等于证明论文未被 Scholar 收录；原始 arXiv 页面仍能提供摘要及日期。

## 摘要、版本及分类交付

研究路线可分为训练数据成员推断、公开图片位置隐私保护、位置推断能力评估。下面的相关性和参考类别是基于已读摘要作出的判断；未阅读全文或复核实验结果。

### 核心参考（窗口外的正式成果）

| 论文 | 正式记录与版本关系 | 摘要依据及相关性判断 |
| --- | --- | --- |
| Membership Inference Attacks Against Vision-Language Models — Yuke Hu 等 | [USENIX Security 2025](https://www.usenix.org/conference/usenixsecurity25/presentation/hu-yuke)，2025-08，1589–1608 页；[arXiv:2501.18624](https://arxiv.org/abs/2501.18624) 首投 2025-01-27，合并为一个正式主条目 | 官方摘要研究指令微调数据的成员推断，使用样本集合及温度敏感性；直接相关，归为训练数据泄露评测。Scholar 本轮显示引用 45 次（2026-09-22），入选依据是正式发表且摘要相关，不依赖该计数 |
| GeoShield: Safeguarding Geolocation Privacy from Vision-Language Models via Adversarial Perturbations — Xinwei Liu 等 | [AAAI 2026](https://ojs.aaai.org/index.php/AAAI/article/view/40877)，40(42)，35653–35661，DOI `10.1609/aaai.v40i42.40877`，正式发表 2026-03-14；[arXiv:2508.03209](https://arxiv.org/abs/2508.03209) 首投 2025-08-05，v2 为 2025-12-08，合并至正式条目 | 官方摘要提出地理与非地理特征解耦、泄露元素定位和多尺度扰动；直接相关，归为位置隐私输入保护。Scholar 显示引用 4 次（2026-09-22） |

两篇均已读官方摘要，全文未读。都不计入最近三个月首次公开或正式发表的成果。

### 前沿及背景线索

| 论文 | 原始日期与状态 | 摘要事实、分类与引用依据 |
| --- | --- | --- |
| Hiding in Plain Sight: A Diffusion-based Mitigation of Geolocation Privacy Leakage in Vision-Language Models — Yining Wang 等 | [arXiv:2609.21363](https://arxiv.org/abs/2609.21363)，v1 2026-09-18；正式发表未确认。作者 Comments 仅写 NDSS 2027，不视为官方接收证据 | 原始摘要提出扩散潜空间干预以减弱照片位置线索；直接相关，列为位置隐私保护前沿线索。引用量未知。来自原始来源补检，本轮 Scholar 完整题名查询未命中 |
| GeoAgent: Evaluating VLM Geolocalization Through Embodied Navigation — Arka Mukherjee 等 | [arXiv:2608.29483](https://arxiv.org/abs/2608.29483)，v1 2026-08-30；作者自报 Accepted to EMNLP 2026 Findings，尚无本轮取得的官方接收或出版记录 | 原始摘要评测 Street View 中序列导航的位置推断能力；属于风险能力背景线索，未提出隐私保护方法。引用量未知，Scholar 无计数不能记为零。本轮由 Scholar 主题检索发现 |

两篇原始摘要及元数据已读，全文未读。日期证明 arXiv v1 在近期窗口内，不保证不存在更早的其他公开渠道；不依据低引用／未知引用的新稿建立核心证据。

### 排除实例

U7 的[官方摘要](https://www.usenix.org/conference/usenixsecurity25/presentation/li-jiliang)研究在线社区与用药安全，采用访谈和社区内容分析，与本课题的 VLM 隐私泄露／防护无关。因此虽然符合 USENIX Security 2025 的场所及年份条件，仍从课题参考文献排除。

## Consensus 后续实测

历史记录中的首次调用失败事实不变。用户完成后续授权后，本机连接已实际成功返回以下查询结果；本节只保留检索证据，不记录账户信息或排障操作。

- `query: "PII-VisBench", page_size: 1`：返回 PII-VisBench 的题名、2026 年、摘要及引用数 3，场所字段为 `Unknown Journal`。回到[ACL Anthology](https://aclanthology.org/2026.findings-acl.501/)核验为 Findings of ACL 2026，2026-07 正式出版；原始摘要与工具摘要对应，正式记录优先。
- `query: "privacy leakage in vision-language models and multimodal large language models", year_min: 2024, year_max: 2026, exclude_preprints: true, page_size: 3`：实际返回三篇：*Privacy-Preserving Multimodal Reasoning for Internet of Things*（2026，引用 3）、*Defeating Cerberus*（2026，引用 0）、*A survey on privacy risks and protection in large language models*（2025，引用 60）。引用量均为 Consensus 提供、查询日 2026-09-22，不与其他数据库相加。
- *Defeating Cerberus* 的摘要字段实际只有逗号，不能视为已读摘要；继续读取[Findings of EACL 官方摘要](https://aclanthology.org/2026.findings-eacl.154/)，确认研究 PII 隐私泄露防护及 2026-03 正式记录。另两篇本节仅作为工具返回实例，不声称逐篇出版核验完成。

**状态：Consensus 实际返回及选定条目的原始来源核验已完成。** 排除预印本参数本身不证明返回条目全为正式论文；未知场所及缺失摘要仍需回到原始页面补全。

## 本轮完成状态

| 项目 | 结果 |
| --- | --- |
| Scholar 真实页面操作、出版物及年份条件 | 已完成；实际入口为本地内置浏览器 |
| 单场所 `source:` | 已完成小规模集合对照，仅限 USENIX Security 与本轮条件 |
| `+` 与多场所 `OR` | 已实际提交并比较；独立作用／两边非空集合合并仍未确认 |
| 近三个月公开工作 | Scholar 找到 8 月 GeoAgent；9 月 18 日的保护方法由 arXiv 补检，入口分别记录 |
| 摘要筛选与正式版本 | 正式论文优先、两个版本合并；无关结果排除，风险能力与保护方法分开 |
| Consensus | 成功返回论文；PII-VisBench 和 Cerberus 已核对原始出版记录 |

本轮未新增“高引用且无正式版本的预印本”阳性实例，不覆盖全领域召回率。没有订阅公众号、创建定时任务或修改 Zotero 库。详细测试留在本文件，README 保留使用场景与说明。
