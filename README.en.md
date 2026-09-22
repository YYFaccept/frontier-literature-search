# Frontier Literature Search

[中文](README.md) · [Skill instructions](SKILL.md) · [Search guide](references/search-guide.md)

`frontier-literature-search` turns a research question into reproducible search combinations, recent-paper results, publication-status evidence, and a small classification index. It is designed for new directions, recent literature checks, targeted top-conference or journal searches, and classification of papers the user already has.

## Capabilities

- Build short queries for Google Scholar, web search, academic search tools, and official proceedings.
- Search a recent time window and distinguish first public release, version updates, later acceptance, and formal publication.
- Verify candidate records against conference, journal, publisher, acceptance-list, or preprint pages.
- Classify papers by technical route, venue, year, publication status, and reading status.
- Report what was searched, what was verified, and what remains unconfirmed.

The skill instructions are currently written in Chinese. You can ask for English output; the skill does not include a separate English instruction set.

## Installation

The current Codex skill directories are the personal directory `~/.agents/skills` and the project directory `.agents/skills`. The official installation documentation also supports installing a skill from another repository with `$skill-installer`: [Build skills](https://learn.chatgpt.com/docs/build-skills).

```text
$skill-installer Install frontier-literature-search from the root of https://github.com/YYFaccept/frontier-literature-search.
```

For a manual clone into the personal skill directory:

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/YYFaccept/frontier-literature-search.git "$HOME/.agents/skills/frontier-literature-search"
```

If the skill is already installed, update its existing location instead of installing duplicate copies. For a customized environment, use its configured skill directory. Codex detects new skills automatically; restart it if the installed skill does not appear.

This skill adds no package dependency and does not require an API key in this repository.

## Usage examples

### Generate a search combination

```text
$frontier-literature-search Generate Google Scholar and web-search combinations for privacy leakage in vision-language models. Do not run the searches yet.
```

This produces entry-specific queries and labels them as generated rather than executed.

### Search the latest three months

```text
$frontier-literature-search Search for vision-language-model privacy leakage papers first made public in the last three months. Open the original paper pages, verify each date and publication status, and report the search record.
```

The default recent window is recalculated from the execution date. A paper's arXiv version history or official publication record must support its date; a search-engine crawl date or conference event date is not enough.

### Classify papers already supplied

```text
$frontier-literature-search Classify these papers on multimodal-model privacy by technical route, venue, year, publication status, and reading status. Do not start a new search unless a supplied record needs source verification.
```

## Put it to work

Start with a research question and turn it into keywords, relevant venues, recent papers, and an organized reading list with traceable sources.

- **Explore a new direction:** map key concepts and technical approaches, then build an initial reading list.
- **Follow recent advances:** search a chosen time window, conference, or journal and add new work to your literature map.
- **Prepare a research meeting or proposal:** organize representative papers around research questions and compare their approaches.
- **Build related work:** verify publication details, consolidate paper versions, and group references into a structure for writing.

Use the search tools available in your environment. Google Scholar page interaction and screen control are optional.

## Contributing

Please keep changes focused on search scope, source evidence, publication-status handling, classification, or documentation. When adding a validation claim, record the actual query, date window, source page, and evidence. Do not turn a small test into a claim of comprehensive coverage. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Released under the [MIT License](LICENSE). Linked papers and third-party content retain their own licenses.

The Chinese README is the primary interface document: [`README.md`](README.md).
