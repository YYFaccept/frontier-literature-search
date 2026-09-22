# 前沿文献检索：最近三个月检索测试

测试日期：2026-09-22。主题：视觉语言模型／多模态大模型的隐私泄露与保护。时间窗口：2026-06-22 至 2026-09-22。

## 结果

使用联网检索、arXiv 提交日期查询及原始页面核验，找到了 4 篇在窗口内首次提交 arXiv 的相关论文，最新一篇提交于 2026-09-18。下表日期均来自原始页面的 Submission history 中 v1，不是搜索引擎抓取日期；PPE-Bench 的 8 月更新没有另算作新论文。

本次验证的是“不依赖本地浏览器也能发现近期论文”的路径。没有操作 Google Scholar 页面，也没有验证 Scholar 的 `source:`、`+` 或多会议 OR 表达式实际如何过滤结果。

| 论文 | 首次 arXiv 提交 | 最新版本 | 技术路线与相关性 | 发表状态证据 |
| --- | --- | --- | --- | --- |
| [Revealing Training Data Exposure in Vision Language Large Models via Parameter Gradients](https://arxiv.org/abs/2606.24774)；Zhihao Zhu、Hongyi Tang、Yi Yang、Ahmed Abbasi | 2026-06-23 | 同日，v1 | GradAudit 通过参数梯度审计模型是否学到特定图文训练关联，涉及训练数据暴露与隐私 | 已确认预印本；该记录未给出正式会议期刊信息 |
| [PPE-Bench: A Benchmark for Evaluating MLLM Unlearning under Private-Public Entanglement](https://arxiv.org/abs/2607.02897)；Xianren Zhang、Delvin Ce Zhang、Dongwon Lee、Suhang Wang | 2026-07-03 | 2026-08-27，v2 | 评估在删除私人信息时能否保留同图中的公共人物、地标等内容 | 已确认预印本；arXiv 标注 EMNLP 2026。作者[新闻页](https://sites.google.com/view/delvincezhang/news)于 2026-08-21 明确写 EMNLP Findings 接收；本轮未核实会议方接收条目，不能写成主会正式发表 |
| [PriMobiBench: Characterizing Visual Privacy Leakage in VLM-Driven Mobile GUI Agents](https://arxiv.org/abs/2609.13873)；Qihang Cen、Tianshuo Cong、Da Song、Xinlei He、Jiaxing Song、Ke Xu、Qi Li | 2026-09-12 | 同日，v1 | 测量手机 GUI agent 从截图提取敏感信息、推断用户画像的风险 | 已确认预印本；作者在 arXiv 标注 ACM CCS 2026 已接收。本轮未获得会议方接收证据；页面所列 ACM DOI 访问返回 404，正式出版未确认 |
| [Hiding in Plain Sight: A Diffusion-based Mitigation of Geolocation Privacy Leakage in Vision-Language Models](https://arxiv.org/abs/2609.21363)；Yining Wang、Xi Li、Mi Zhang、Xiaohan Zhang、Xiaoyu You、Zhenxing Qian、Mi Wen | 2026-09-18 | 同日，v1 | 研究照片地理位置隐私泄露，使用扩散模型潜空间扰动抑制位置线索 | 已确认预印本；arXiv 仅写 NDSS 2027，没有明确接收证明，不按已接收处理 |

以上研究内容只依据原始摘要；本次核验了元数据、摘要及版本历史，没有阅读全文或复核实验数据。首次 arXiv 提交日期证明该版本在窗口内公开，不保证排除更早的其他渠道发布。

## 实际检索记录

arXiv API 查询使用提交日期限制：

```text
all:(privacy) AND (all:"vision-language" OR all:"multimodal large language" OR all:"vision language model") AND submittedDate:[202606220000 TO 202609222359]

(all:"membership inference" OR all:"training data extraction" OR all:"model inversion" OR all:"privacy leakage") AND (all:multimodal OR all:visual OR all:vision) AND submittedDate:[202606220000 TO 202609222359]
```

官方场所定向补查使用普通联网搜索，按其适用方式组合主题词、会议和年份：

```text
site:proceedings.mlr.press 2026 vision language privacy ICML
site:usenix.org conference usenixsecurity26 vision language privacy
site:eccv.ecva.net 2026 vision language privacy leakage
ICML 2026 privacy multimodal large language model
ECCV 2026 accepted papers privacy multimodal vision language
```

本轮打开了 [USENIX Security 2026 技术议程](https://www.usenix.org/conference/usenixsecurity26/technical-sessions)、[ECCV 2026 接收列表](https://eccv.ecva.net/Conferences/2026/AcceptedPapers) 及 [ICML 2026 下载入口](https://icml.cc/Downloads/2026)。没有得到同时满足主题、官方发表状态和三个月内具体日期证据的额外条目。此结果不等于这些会议不存在相关论文。

对候选的会议信息进一步查询：

```text
"PriMobiBench" "CCS" 2026
"PPE-Bench" "EMNLP" 2026
"PriMobiBench" site:sigsac.org
"PPE-Bench" site:2026.emnlp.org
"PPE-Bench" site:aclanthology.org
```

已打开四篇 arXiv 原始页和 PPE-Bench 作者新闻页；没有把搜索结果中的镜像网页作为日期或发表依据。PPE-Bench 搜索还返回了名称相似的旧基准条目，因题名与研究对象不同未纳入。

## 技能修改与验证

- 保留安全四大、AI、CV、其他重点会议和重点期刊五组 Scholar 组合。
- 取消必须读取本地 Scholar 或使用屏幕控制的要求；生成组合、实际检索、可选页面操作分开描述。
- 实际检索使用当前可用的搜索工具，并按入口适配语法；不跨工具假定 `source:` 等操作符有效。
- “近几个月”默认三个月；分别记录首次公开、修订和正式发表／接收日期。
- 技能格式校验通过，原先强制 Scholar 的流程与调用示例已同步更新。

结论：本次测试支持“能发现近三个月新公开的相关论文，包括四天前的稿件”。它不证明已全面覆盖顶会顶刊，也不证明 Scholar 专用组合语法有效。
