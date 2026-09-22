# 贡献指南 / Contributing

欢迎补充检索模板、纠正会议名称、改进日期核验规则，以及提交可以复查的使用案例。

## 提交修改

1. 先阅读 [SKILL.md](SKILL.md) 和相关的 [检索指南](references/search-guide.md)。
2. 每个 Pull Request 处理一个具体问题，说明修改前后的行为；文字改动保持简洁，维护中英文 README 的一致性。
3. 修改核心指令或搜索模板时，用一个实际课题试用，说明使用的搜索入口、日期范围、查询和观察到的结果。

如发现检索表达式不起作用，请在 Issue 中附上实际查询、所用工具或网站、筛选条件和原始来源链接。不要只提供结果数量：需要说明具体哪些论文被错误纳入或遗漏。

论文案例请区分首次公开、版本更新、接收和正式发表。只有作者备注时标明来源，不把它写成会议方确认。历史测试记录保留其测试日期；新的检索案例请另写带日期的记录。

修改说明文件时，检查 `SKILL.md` 的名称与描述、相对链接，以及 `agents/openai.yaml` 的调用示例。实际使用行为比与某段固定措辞完全一致更重要。

## English

Open an issue or pull request for a concrete improvement to queries, venue names, date verification, or a reproducible research example. Describe the behavior before and after the change, and keep both READMEs aligned.

For query changes, include the search engine or tool, exact query, date filters, and primary-source links. Show a specific false positive or missed paper instead of relying only on result counts. Separate first public availability, revision, acceptance, and publication dates. Preserve historical test dates and add a new dated record for new experiments.

Contributions are distributed under the repository's [MIT License](LICENSE). Linked third-party papers retain their own licenses.
