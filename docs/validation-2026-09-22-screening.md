# 摘要筛选、正式版本与近期论文分流实测

执行日期：2026-09-22。研究题目：视觉语言模型／多模态大模型的隐私泄露与保护。近期窗口：2026-06-22 至 2026-09-22；窗口外论文仅用于背景及版本替换验证。

## 文献筛选结果

本轮实际打开出版机构、会议论文集和 arXiv 原始页面，阅读公开摘要及元数据。得到 **2 篇窗口内正式发表论文、2 篇窗口外正式背景论文、4 篇窗口内首次提交 arXiv 的前沿线索**，并排除 1 篇关键词相近但研究问题不相符的候选。没有阅读全文，也没有复核实验数据。

这里的“近期正式发表”与“近期首次公开”分开计数：两篇 2026 年 7 月正式论文早已有预印本，不称为近三个月首次出现的研究。月份证据足以判断 7 月落在本窗口内，但不据此编造某日发表。

### 核心参考：窗口内正式发表

#### 1. Leave My Images Alone: Preventing Multi-Modal Large Language Models from Analyzing Images via Visual Prompt Injection

- **作者与主记录**：Zedian Shao、Hongbin Liu、Yuepeng Hu、Neil Zhenqiang Gong；ACL 2026 主会长文，1588–1604 页，DOI `10.18653/v1/2026.acl-long.72`。正式引用采用 [ACL Anthology 条目](https://aclanthology.org/2026.acl-long.72/)，不再另列一篇 arXiv 论文。
- **已读摘要事实**：ImageProtector 在发布前向图片加入视觉提示注入扰动，使 MLLM 拒绝未经授权的图片分析。
- **筛选判断**：直接相关；研究对象为图片中的身份、位置等敏感信息，适合“用户侧输入保护”路线。
- **日期与版本**：正式出版月份为 **2026-07**；[arXiv 原始记录](https://arxiv.org/abs/2604.09024)的 v1 为 **2026-04-10**，本次未见后续版本。归类为“旧工作在窗口内正式发表”。题名、四位作者及研究内容一致，合并为一个条目。
- **阅读与引用量**：已读官方摘要，全文未读；引用量未查询，不作为入选门槛。arXiv 作为附加阅读链接。

#### 2. PII-VisBench: Evaluating Personally Identifiable Information Safety in Vision Language Models Along a Continuum of Visibility

- **作者与主记录**：G M Shahariar、Zabir Al Nazi、Md Olid Hasan Bhuiyan、Zhouxing Shi；Findings of ACL 2026，10294–10316 页，DOI `10.18653/v1/2026.findings-acl.501`。[官方出版与摘要](https://aclanthology.org/2026.findings-acl.501/)。场所标为 **Findings**，不写成 ACL 主会。
- **已读摘要事实**：按照人物在互联网上的信息可见程度，评估 VLM 对个人可识别信息请求的拒绝和泄露行为。
- **筛选判断**：直接相关；适合“PII 泄露评测”，可用于组织不同人群可见度下的隐私评测问题。
- **日期与版本**：正式出版月份为 **2026-07**；[arXiv 记录](https://arxiv.org/abs/2601.05739) v1 为 **2026-01-09**，本次未见后续版本。归类为“旧工作在窗口内正式发表”。题名及四位作者一致，引用合并至正式条目。
- **阅读与引用量**：已读官方摘要，全文未读；引用量未查询，不作为入选门槛。

### 核心参考：窗口外背景与版本替换

#### 3. Membership Inference Attacks Against Vision-Language Models

- **作者与正式记录**：Yuke Hu、Zheng Li、Zhihao Liu、Yang Zhang、Zhan Qin、Kui Ren、Chun Chen；USENIX Security 2025，1589–1608 页，出版月份 **2025-08**。[官方条目、摘要与 BibTeX](https://www.usenix.org/conference/usenixsecurity25/presentation/hu-yuke)。
- **摘要事实与筛选判断**：研究 VLM 指令微调数据的成员推断，利用样本集合与温度敏感性识别训练数据使用情况；直接相关，作为“训练数据暴露”路线背景。
- **版本替换**：[arXiv](https://arxiv.org/abs/2501.18624) v1 为 **2025-01-27**，v2 为 **2025-02-07**；正式条目的题名和作者一致。保留一个 USENIX 主记录及一个可读版本链接，不将 arXiv-issued DOI 误写成正式论文 DOI。
- **阅读与引用量**：已读官方摘要，全文未读；引用量未查询。首次公开与正式发表均在近期窗口之外。

#### 4. Defeating Cerberus: Privacy-Leakage Mitigation in Vision Language Models

- **作者与正式记录**：Boyang Zhang、Istemi Ekin Akkus、Ruichuan Chen、Alice Dethise、Klaus Satzke、Ivica Rimac、Yang Zhang；Findings of EACL 2026，2952–2965 页，出版月份 **2026-03**，DOI `10.18653/v1/2026.findings-eacl.154`。[官方条目及摘要](https://aclanthology.org/2026.findings-eacl.154/)。
- **摘要事实与筛选判断**：通过调整与 PII 概念关联的内部状态，促使 VLM 拒绝敏感任务；直接相关，作为“模型内部干预”路线背景。
- **版本替换**：[arXiv](https://arxiv.org/abs/2509.25525) v1 为 **2025-09-29**，预印本题名为 *Defeating Cerberus: Concept-Guided Privacy-Leakage Mitigation in Multimodal Language Models*。七位作者、方法描述及摘要中的结果相符，判定为同一工作的版本；采用正式标题与出版记录，保留旧标题供检索。
- **阅读与引用量**：已读两处摘要，全文未读；引用量未查询。两种日期均在近期窗口之外。

### 前沿线索：窗口内新预印本

以下四篇都重新打开了原始摘要和版本历史。引用量缺失记为“未知”，不等于零；作者自报接收与官方确认分开。它们的 arXiv v1 日期证明该版本在窗口内公开，不保证不存在更早的其他公开渠道。

#### 5. Revealing Training Data Exposure in Vision Language Large Models via Parameter Gradients

- **作者与来源**：Zhihao Zhu、Hongyi Tang、Yi Yang、Ahmed Abbasi；[arXiv:2606.24774](https://arxiv.org/abs/2606.24774)。
- **摘要事实与筛选判断**：GradAudit 以梯度特征审计图文关联是否被模型训练使用；涉及医疗图文和数据来源，直接相关，归入“训练数据暴露”。
- **日期与状态**：首次提交及最新版本均为 **2026-06-23，v1**。未取得正式发表或官方接收证据，按预印本处理。
- **引用量**：**0**，来自 [Semantic Scholar 原始 API](https://api.semanticscholar.org/graph/v1/paper/ARXIV:2606.24774?fields=title,year,citationCount,publicationVenue,url,externalIds)，查询日期 **2026-09-22**；返回题名和 ArXiv ID 一致。只放入前沿线索，不能以相关性代替引用影响证据升入核心参考。
- **阅读范围**：原始摘要及元数据，全文未读。

#### 6. PPE-Bench: A Benchmark for Evaluating MLLM Unlearning under Private-Public Entanglement

- **作者与来源**：Xianren Zhang、Delvin Ce Zhang、Dongwon Lee、Suhang Wang；[arXiv:2607.02897](https://arxiv.org/abs/2607.02897)。
- **摘要事实与筛选判断**：评估遗忘图片中私人信息时能否保留同图中的公众人物、地标等公共内容；直接相关，归入“隐私遗忘评测”。
- **日期与状态**：v1 **2026-07-03**，v2 **2026-08-27**；修订不另算新论文。arXiv comments 标注 EMNLP 2026；[作者新闻页](https://sites.google.com/view/delvincezhang/news)在 **2026-08-21** 明确写 EMNLP Findings 接收。本轮未获得会议方接收记录或正式出版条目，标为“预印本；作者自报 Findings 接收，官方状态待核验”。
- **引用量与阅读**：引用量未知，原始摘要已读，全文未读；保留前沿线索。

#### 7. PriMobiBench: Characterizing Visual Privacy Leakage in VLM-Driven Mobile GUI Agents

- **作者与来源**：Qihang Cen、Tianshuo Cong、Da Song、Xinlei He、Jiaxing Song、Ke Xu、Qi Li；[arXiv:2609.13873](https://arxiv.org/abs/2609.13873)。
- **摘要事实与筛选判断**：围绕手机 GUI agent 的截图序列，评估显式敏感信息泄露与用户画像推断，并研究遮挡无关隐私元素；直接相关，归入“应用场景隐私评测与保护”。
- **日期与状态**：v1 **2026-09-12**，本轮未见后续版本。作者 comments 写已被 ACM CCS 2026 接收；页面列出相关 DOI `10.1145/3830454.3846776`，本轮 DOI 页面未能取得出版记录。标为“预印本；作者自报 CCS 接收，官方状态待核验”，不写正式发表。
- **引用量与阅读**：引用量未知，原始摘要已读，全文未读；保留前沿线索。

#### 8. Hiding in Plain Sight: A Diffusion-based Mitigation of Geolocation Privacy Leakage in Vision-Language Models

- **作者与来源**：Yining Wang、Xi Li、Mi Zhang、Xiaohan Zhang、Xiaoyu You、Zhenxing Qian、Mi Wen；[arXiv:2609.21363](https://arxiv.org/abs/2609.21363)。
- **摘要事实与筛选判断**：研究照片地理位置推断，采用扩散模型潜空间干预减少位置线索；直接相关，归入“位置隐私输入保护”。
- **日期与状态**：v1 **2026-09-18**，本轮未见后续版本；距检索日四天。comments 仅写 NDSS 2027，不能据此判为已接收或正式发表。
- **引用量与阅读**：引用量未知，原始摘要已读，全文未读；保留前沿线索。

## 排除、换源与引用影响实测

### 关键词接近但摘要不相关

检索返回 *HiViS: Hiding Visual Tokens from the Drafter for Speculative Decoding in Vision-Language Models*。初次打开 CVF 页面失败后，继续获取 [arXiv 原始摘要](https://arxiv.org/abs/2509.23928)。摘要说明“隐藏视觉 token”的目标是减轻投机解码的计算负担，保持生成质量；没有研究个人信息泄露或隐私保护，因此**从本课题参考文献中排除**。这是根据对象、任务和方法作出的筛选判断，不由标题中的 “Hiding” 决定。

该记录 v1 为 **2025-09-28**，v3 为 **2026-08-23**。即使主题相符，也不能把 8 月版本更新算作窗口内首次公开的新工作。CVF 页面失效后仍取得公开摘要，完成了实际换源；没有把入口错误当成没有论文内容。

### “高引用预印本进入核心参考”尚无合格阳性实例

尝试查找较早的相关 arXiv 候选 *Doxing via the Lens: Revealing Location-related Privacy Leakage on Multi-modal Large Reasoning Models*。实际读取 [arXiv 摘要与版本历史](https://arxiv.org/abs/2504.19373)，v1 为 **2025-04-27**，v5 为 **2026-03-03**，研究图像位置隐私，属于相关背景候选。

[Semantic Scholar API](https://api.semanticscholar.org/graph/v1/paper/ARXIV:2504.19373?fields=title,year,citationCount,publicationVenue,url,externalIds)在 **2026-09-22** 实际返回 `citationCount: 13`，题名和 ArXiv ID 一致，但 `publicationVenue: null`。此字段为空不证明它尚未出版：arXiv 已指向 ICLR 2026，并标明 camera-ready、poster 接收。正式 ICLR 链接本轮未取得页面，OpenReview 出现浏览器验证后停止该入口。

本轮没有建立同领域、同龄论文的引用比较，不能把 13 次机械称为“高引用”，也不能把该候选硬充为“高引用未发表预印本”。该阳性场景记为**未完成验证**。已实际验证的是引用数为 0 和引用数未知的近期预印本均不进入核心参考。其他近期论文的 Semantic Scholar 请求遇到限流，没有得到可用计数，不补造数据、不跨数据库相加。

## 实际检索记录

使用工具：普通联网搜索与网页打开；Semantic Scholar 公共 API。搜索结果先用于发现，入选条目均读取原始摘要。检索日期均为 2026-09-22；以下查询没有冒用 Scholar 的专用语法，也不证明 Scholar 过滤能力。

代表性实际查询：

```text
site.usenix.org vision language models privacy leakage
site:openaccess.thecvf.com vision language privacy 2025 2026
site:aclanthology.org multimodal privacy 2026
site:aclanthology.org/2026 "privacy" "vision" "July"
site:usenix.org/conference/usenixsecurity26 "vision" "privacy"
"Membership Inference Attacks Against Vision-Language Models" arxiv
"PII-VisBench" arxiv
"Leave My Images Alone" arxiv
"HiViS" "Hiding Visual Tokens" arxiv
"PPE-Bench" "2026" publication
"PPE-Bench" site:aclanthology.org
"PriMobiBench" "CCS" 2026
"PriMobiBench" site:sigsac.org
"Hiding in Plain Sight" "Diffusion-based" NDSS 2027
"Revealing Training Data Exposure" conference
"The Phantom Menace" "Unmasking Privacy" published citations
"Doxing via the Lens" citations
"Doxing via the Lens" site:openreview.net/forum
```

第一个查询实际输入为 `site.usenix.org`，不是有效的 `site:` 域名限定；其结果只按普通搜索线索使用。四篇近期 arXiv 候选源于历史测试，本轮逐篇重新核验，未假称重新发现四篇全新结果。当前官方状态查询未确认的条目仍保留明确状态。

| 验证项目 | 实际结果 |
| --- | --- |
| 近期正式成果发现 | 通过：两篇 2026-07 ACL／Findings 出版记录；不混同主会与 Findings |
| 正式版本替换与去重 | 通过：四组 arXiv／正式记录；包括题名发生变化的 Defeating Cerberus |
| 摘要相关性筛选 | 通过：核心条目直接相关；HiViS 按摘要排除 |
| 近期日期区分 | 通过：首次公开、正式发表、版本更新分别处理 |
| 低引用／未知引用预印本分流 | 通过：GradAudit 为 0，另三篇未知，均为前沿线索 |
| 高引用未发表预印本进入核心 | 未完成：没有取得符合条件且有相对引用依据的阳性实例 |
| 页面失败后的摘要获取 | 通过：CVF 页失败后读取 HiViS 的 arXiv 原始摘要 |
| 仅凭摘要完成初筛 | 通过：正式论文未阅读全文也完成相关性判断；“全文确定不可获取”的单独场景未测试 |

以上是本课题的小规模行为实测，不能推出全领域召回率。

## Scholar 与 Consensus 入口实测

### Google Scholar

先用浏览器控制读取本机会话，初次及一次重试均未取得浏览器清单，返回 `nodeRepl.fetch request failed`，没有据此执行页面输入。

随后通过网页读取工具提交 [Scholar 主题与年份查询](https://scholar.google.com/scholar?hl=en&q=%22vision+language%22+privacy&as_ylo=2024&as_yhi=2026)，查询为 `"vision language" privacy`，年份为 2024–2026。初次及一次重试均未读取到结果页，工具报告该 URL 不可访问。没有取得结果，不把请求中的年份参数当作筛选已生效的证据。

**状态：Scholar 结果页实测未完成。** 出版物字段、单场所 `source:`、`+` 和多场所 `OR` 对照均未执行，保留为实验模板。未遇到可操作的验证码，也未轮换镜像。之后通过上述官方论文页继续完成摘要筛选和版本核对。

### Consensus

使用[官方 MCP 入口](https://docs.consensus.app/consensus-mcp)完成本机配置，用户完成 OAuth 登录，客户端返回登录成功；未在公开仓库保存账户或认证信息。

第一次新会话未加载出工具，未执行搜索。第二次只在测试进程中等待该服务完成初始化，实际读到了 `search` 工具，其参数支持 `year_min`、`year_max`、`exclude_preprints` 和 `page_size`。执行两次查询：

```json
{
  "query": "privacy leakage in vision-language models and multimodal large language models",
  "year_min": 2024,
  "year_max": 2026,
  "exclude_preprints": true,
  "page_size": 3
}
```

```json
{
  "query": "PII-VisBench",
  "page_size": 3
}
```

两次调用均返回 `Unexpected response type`，未返回可读取的论文元数据、摘要、引用量或来源链接，也没有返回配额耗尽提示。停止进一步调用，没有把其他来源的文献记成 Consensus 结果。

**状态：本机配置与认证完成，工具已加载并实际调用；检索返回与论文核验尚未通过。** 错误仅定位到客户端接收响应阶段，本轮未确定根因，不据此判断论文不存在或账户额度不足。未新增订阅或开启额外计费；测试进程的启动等待设置没有写入用户配置。

## 受控行为检查与格式校验

另由独立代理读取更新后的技能，对六条明确标注为虚构的候选材料作只读分类。此检查验证指令如何决策，不是新增真实论文检索证据。

- 已有正式版本的候选只保留正式主记录，并将较早首次公开与近期发表分开。
- 零引用新预印本进入前沿线索；只有 AI 概述、没有原始摘要的候选进入待核验。
- 有同数据库、同期同领域引用比较依据的相关预印本可进入核心参考，并保留“正式版本未确认”；这补测了分类行为，没有补足上文真实高引用预印本阳性样本的缺口。
- 主题不符的高引用正式论文不因引用量而进入核心参考；旧稿近期修订不计为新论文。

技能格式校验通过；名称、元数据、自动调用设置和支持文档锚点有效。校验使用 UTF-8 模式，避免 Windows 默认编码影响中文文件读取。
