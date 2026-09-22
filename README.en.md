# Frontier Literature Search

[中文](README.md) · [Skill instructions](SKILL.md) · [Search guide](references/search-guide.md)

Turn a research question into a focused, source-backed reading list. `frontier-literature-search` starts with Google Scholar when a live search is requested, supplements it with available academic and official sources, reads abstracts for relevance, and keeps published work separate from new leads.

## Quick start

Install it in Codex:

```text
$skill-installer Install frontier-literature-search from the root of https://github.com/YYFaccept/frontier-literature-search.
```

Then ask:

```text
$frontier-literature-search Research privacy leakage in vision-language models from the last three months. Search Google Scholar first, use official proceedings and connected Consensus where available, screen abstracts for relevance, prefer published versions, and return a research overview, core references, frontier leads, and a short search log.
```

Invoke it by name or let Codex select it automatically for a matching request. Specify your topic, time window, venues, and output language in the prompt. Live searches use tools available in your Codex environment; Consensus is optional.

## Three ways to use it

### Research a topic

Use this when you need a literature map for a new direction, proposal, or research meeting.

```text
$frontier-literature-search Research recent watermarking methods for generative images, focusing on relevant security and machine-learning venues. Screen abstracts, verify publication status from original records, and organize the results by technical route.
```

### Generate queries only

Use this when you want to choose or refine searches yourself. It produces short, entry-specific queries and time filters without claiming that a search was run.

```text
$frontier-literature-search Generate Google Scholar and web-search queries for membership inference against multimodal models, covering the security Big Four and major AI venues. Do not run the searches.
```

### Organize papers you already have

Use this to clean up a paper list without widening its scope.

```text
$frontier-literature-search Classify these papers on multimodal-model privacy by technical route, venue, year, publication status, and reading status. Check supplied records when needed, merge duplicate versions, and do not add new candidates.
```

## How it works

1. Define the research object, question, methods, time window, and relevant venues.
2. Build concise topic queries, then search Scholar first and supplement with official proceedings, publication pages, and other available academic sources.
3. Read original abstracts to keep directly relevant papers, set aside background work, and mark uncertain records for follow-up.
4. Find the formal publication or acceptance record, merge matching preprints and published versions, and preserve a readable link.
5. Deliver an overview, organized references, and a brief log of the sources and conditions that shaped the result.

This keeps screening grounded in paper evidence, citation records aligned with formal publications, and recent preprints visible without presenting them as settled literature.

An unspecified recent window defaults to the last three calendar months; background exploration covers the previous two years and the current year. Dates are recalculated for each run. Screen control is one way to use Scholar; an explicit request to use a local page requires actual page interaction and an accurate execution record. Query-only mode needs no browsing.

## Venue starting points

Select groups that fit the topic; the list is a practical starting set, not a complete field directory.

| Group | Venues |
| --- | --- |
| Security Big Four | CCS, USENIX Security, IEEE S&P, NDSS |
| Major AI conferences | ICLR, NeurIPS, ICML |
| Major computer-vision conferences | CVPR, ICCV, ECCV |
| Other key conferences | AAAI, IJCAI, ACL, ACM MM |
| Key journals | TIFS, TDSC, TPAMI |

See the [search guide](references/search-guide.md#目标会议与期刊) for publication-field names and source notes.

## What the output means

| Section | Meaning |
| --- | --- |
| Research overview | Main technical routes, recent changes, and suggested reading priorities, with interpretation identified as such. |
| Core references | Directly relevant papers with a confirmed formal publication or acceptance record; exceptional preprints require documented evidence of citation influence. |
| Frontier leads | Highly relevant new preprints or records that are promising but do not yet meet the core-reference criteria. |
| Background and follow-up | Classical context and records whose abstract, status, or version relationship still needs checking. |
| Search log | The time window, sources and queries actually used, venue conditions, and material gaps that affect the result. |

An abstract can support initial screening without downloading the full paper; each record states what was read. Citation influence is considered in context of the field and paper age, without a universal count threshold. The skill can also prepare BibTeX or RIS from verified metadata when requested.

## Optional: use Consensus

Consensus is optional. When it is connected, the skill can use its returned paper data alongside Scholar and original publication records. Follow the [official Consensus MCP instructions](https://docs.consensus.app/consensus-mcp):

```sh
codex mcp add consensus --url https://mcp.consensus.app/mcp
codex mcp login consensus
```

Complete account authorization in the browser and confirm that the tools are loaded in Codex. Searches use the tool's actual parameters, and publication details are checked against original records. Installing the skill does not activate a paid service.

<details>
<summary>Reusable research prompt</summary>

```text
Use $frontier-literature-search to research [TOPIC] within [TIME WINDOW], focusing on relevant leading conferences and journals. Search Google Scholar first and supplement it with connected Consensus tools and official proceedings where available. Screen papers against the research object, question, and method.

Prefer formally published versions. Merge an arXiv preprint and its published version into one record, citing the publication. For work without a confirmed published version, use documented citation evidence in the context of the field and paper age before including it in core references. List recent low-citation or uncited preprints separately as frontier leads.

Return a research overview, core references, frontier leads, and a short search log. For each included paper, explain its relevance, publication status, original source, and what was actually read. Distinguish first public release, formal publication, and version updates.
```

</details>

<details>
<summary>Manual installation</summary>

macOS / Linux:

```bash
mkdir -p "$HOME/.agents/skills"
git clone https://github.com/YYFaccept/frontier-literature-search.git "$HOME/.agents/skills/frontier-literature-search"
```

Windows PowerShell:

```powershell
$skillsDir = Join-Path $HOME '.agents/skills'
New-Item -ItemType Directory -Force -Path $skillsDir | Out-Null
git clone https://github.com/YYFaccept/frontier-literature-search.git (Join-Path $skillsDir 'frontier-literature-search')
```

The usual skill locations are `~/.agents/skills` for personal use and `.agents/skills` for a project; see the [Codex installation documentation](https://learn.chatgpt.com/docs/build-skills). For a customized environment, use its configured skill directory. If you already have an installation, update that copy rather than creating another one. Restart Codex if a new installation has not appeared.

</details>

## Contributing and license

The instructions are written in Chinese; you can request English output. Detailed search examples and test records live in [docs/](docs/).

Contributions are welcome for concrete improvements to queries, venue names, date handling, classification, or documentation. Please read [CONTRIBUTING.md](CONTRIBUTING.md).

Released under the [MIT License](LICENSE).
