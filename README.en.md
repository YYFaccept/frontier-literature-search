# Frontier Literature Search

[中文](README.md) · [Skill instructions](SKILL.md) · [Search guide](references/search-guide.md)

`frontier-literature-search` turns a research question into a source-backed reading list. It tries Google Scholar first, screens public titles and abstracts, finds published versions, and separates core references from emerging work. Use it to explore a new direction, prepare a research meeting, or organize related work.

## Capabilities

- Build short queries across the security Big Four, AI, computer vision, other major conferences, and journals; search individual venues and deduplicate the results.
- Try Google Scholar first, with connected Consensus tools, official proceedings, and other available search sources for additional coverage.
- Read abstracts and screen candidates against the research object, question, and method; explain each paper's relevance.
- Search a recent time window and distinguish first public release, version updates, later acceptance, and formal publication.
- Prefer published records for citations and exports, merging preprints into the same record while retaining accessible reading links.
- Separate core references from emerging work. Consider a preprint's verified citation influence in its field and relative to its age, without imposing a universal citation threshold.
- Report the research overview, core references, emerging work, and a short search log; prepare BibTeX or RIS when requested.
- Generate queries without searching, or classify supplied papers without expanding the search. Screen control is optional; an unavailable source triggers a switch to other sources.

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

## Use with Consensus

Consensus can supply paper titles, abstracts, and citation information. Connect it to Codex using the [official MCP instructions](https://docs.consensus.app/consensus-mcp):

```sh
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

Complete account sign-in and authorization in the browser, then confirm the tools are available in Codex; reopen the session if they have not loaded. The skill uses the connected tool's actual parameters and returned fields, and verifies publication status against original publication records. Consensus is optional. Other search tools remain usable without it, and installing this skill does not activate paid services.

## Usage examples

### Generate a search combination

```text
$frontier-literature-search Generate Google Scholar and web-search combinations for privacy leakage in vision-language models. Do not run the searches yet.
```

This produces entry-specific queries and labels them as generated rather than executed.

### Search the latest three months

```text
$frontier-literature-search Search for vision-language-model privacy leakage research from the last three months. Try Google Scholar first and use connected Consensus tools and official proceedings. Screen abstracts for relevance, prefer published versions, and separate core references from emerging work. Verify first-public dates and publication status, and link to original sources.
```

The default recent window is recalculated from the execution date. A paper's arXiv version history or official publication record must support its date; a search-engine crawl date or conference event date is not enough.

### Classify papers already supplied

```text
$frontier-literature-search Classify these papers on multimodal-model privacy by technical route, venue, year, publication status, and reading status. Do not start a new search unless a supplied record needs source verification.
```

### Reusable research prompt

```text
Use $frontier-literature-search to research [TOPIC] within [TIME WINDOW], focusing on relevant leading conferences and journals. Try Google Scholar first and supplement it with connected Consensus tools and official proceedings. If a source is unavailable, use other sources to retrieve titles and abstracts. Screen papers against the research object, question, and method.

Prefer formally published versions. Merge an arXiv preprint and its published version into one record, citing the publication. For work without a confirmed published version, consider verified citation counts in context of the field and paper age before including it in core references. List recent low-citation preprints separately as emerging work.

Return a research overview, core references, emerging work, and a short search log. For each included paper, explain its relevance, publication status, original source, and what was actually read. Distinguish first public release, formal publication, and version updates.
```

## Put it to work

Start with a research question and turn it into keywords, relevant venues, recent papers, and an organized reading list with traceable sources.

- **Explore a new direction:** map key concepts and technical approaches, then build an initial reading list.
- **Follow recent advances:** search a chosen time window, conference, or journal and add new work to your literature map.
- **Prepare a research meeting or proposal:** organize representative papers around research questions and compare their approaches.
- **Build related work:** verify publication details, consolidate paper versions, and group references into a structure for writing.

Start with Google Scholar when running searches, then use the other sources available in your environment. Screen control is an optional way to interact with the page.

## Contributing

Please keep changes focused on search scope, source evidence, publication-status handling, classification, or documentation. When adding a validation claim, record the actual query, date window, source page, and evidence. Do not turn a small test into a claim of comprehensive coverage. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

Released under the [MIT License](LICENSE). Linked papers and third-party content retain their own licenses.

The Chinese README is the primary interface document: [`README.md`](README.md).
