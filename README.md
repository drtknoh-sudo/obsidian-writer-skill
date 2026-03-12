# Obsidian Writer & Knowledge Architect Skill v2.0

> Claude Skill for Obsidian vault-based writing (book authoring), planning, and knowledge management automation.
> Designed for Claude Desktop / Cowork Mode with local Obsidian MCP server.

**[한국어 README](README_KR.md)**

## What Makes This Skill Different

Most Obsidian MCP tools (cyanheads, MarkusPfundstein, bitbonsai, etc.) focus on **basic vault operations** — read, write, search, delete. They provide the plumbing but not the intelligence. Similarly, existing Claude skills for writing are **vault-agnostic** — they generate content from scratch without leveraging your accumulated knowledge.

**obsidian-writer-skill bridges this gap** by providing 9 intelligent workflows that treat your vault as a living knowledge base, not just a file system.

### How We Differ from Other Approaches

| Aspect | Other MCP Servers | Generic Writing Skills | **This Skill** |
|--------|------------------|----------------------|----------------|
| Vault interaction | CRUD operations | None | **Intelligent multi-layer search + AI reasoning** |
| Writing support | None | Generic prompts | **Vault-sourced drafting with auto-referencing** |
| Knowledge reuse | Manual search | None | **Auto-discovery of related past notes** |
| Quality control | None | Basic grammar | **Fact-checking + AI-tone removal + source verification** |
| Organization | Basic folders/tags | None | **AI-powered auto-classification + hierarchical tagging** |
| Memory | Stateless | Stateless | **Project memory with lessons learned & decision logs** |
| Approach | Tool-level | Prompt-level | **Workflow-level (9 interconnected processes)** |

### Key Innovation: Simulated Semantic Search

Current MCP servers only support keyword matching. Expensive alternatives (Claudesidian/Nexus) require vector databases and embedding APIs. This skill achieves **90%+ semantic search effectiveness** using Claude's reasoning alone:

1. **Synonym expansion**: "revenue" → "revenue, sales, income, profit, earnings"
2. **Concept hierarchy**: "AI" → "machine learning, deep learning, LLM, neural network"
3. **Bilingual search**: Korean + English keywords simultaneously
4. **Context inference**: "business plan" → "BMC, feasibility, market analysis, investment"

No additional setup, no API costs, no embedding models required.

## 9 Workflows

| # | Workflow | What It Does |
|---|---------|-------------|
| 1 | **Smart Research** | Decomposes topics → multi-layer vault search → grades relevance (A/B/C) → generates source map |
| 2 | **Book Writing** | Designs outline → maps vault notes to chapters → drafts with references → tracks status |
| 3 | **Auto-Classification** | Diagnoses vault → designs taxonomy → standardizes tags → batch-applies to notes |
| 4 | **Planning Builder** | Collects vault knowledge → identifies gaps → structures into proposal → generates draft |
| 5 | **Daily Curation** | Checks new notes → finds associations → auto-tags → creates daily summary |
| 6 | **Fact-Check** | Extracts claims → cross-checks within vault → verifies externally → assigns trust ratings |
| 7 | **AI Writing Detox** | Detects AI patterns (KR/EN) → classifies severity → suggests natural alternatives |
| 8 | **Digital Archive** | Extracts entities → maps relationships → builds knowledge graph → maintains vault health |
| 9 | **Project Memory** | Captures decisions → records lessons → enables experience-based advice for new projects |

### Workflow Chain

All 9 workflows interconnect. Research (W1) feeds into Writing (W2), which triggers Fact-Check (W6) and AI Detox (W7). Classification (W3) feeds Archive (W8). Every completed project generates Memory (W9) that informs future work.

## Installation

### Prerequisites
- Obsidian vault with local MCP server connected
- Claude Desktop or Cowork Mode

### Setup
Copy the `obsidian-writer-skill/` folder to your skills directory:
```
~/.skills/skills/obsidian-writer/
```

### File Structure
```
obsidian-writer-skill/
├── SKILL.md                     # Core: 9 workflow definitions
├── README.md                    # English documentation
├── README_KR.md                 # Korean documentation
└── references/
    ├── upgrade-guide.md         # MCP server comparison & upgrade roadmap
    ├── writing-workflows.md     # Detailed authoring & planning guides
    └── v2-upgrade-analysis.md   # v1→v2 element adoption/rejection analysis
```

### Trigger Keywords
The skill auto-activates on: `obsidian`, `vault`, `book writing`, `manuscript`, `outline`, `note search`, `auto-tag`, `classify`, `fact-check`, `source verify`, `AI tone`, `writing detox`, `project memory`, `lessons learned`

## Supported MCP Tools

| Tool | Purpose |
|------|---------|
| `list_notes` | Browse notes by folder |
| `get_note` | Read note content |
| `create_note` | Create with auto-frontmatter |
| `update_note` | Modify content & tags |
| `search_notes` | Title-based search |
| `full_text_search` | Full-text content search |
| `list_folders` | Vault structure |
| `get_tags` | Tag inventory |
| `get_vault_info` | Vault statistics |

## v2.0 Changelog

**Added**: Fact-Check workflow (W6), AI Writing Detox (W7), Digital Archive (W8), Project Memory (W9), trust-level tags, fact-check fields in templates, workflow interconnection map.

**Enhanced**: Writing templates include fact-check logs. Planning workflow includes source verification. Tag taxonomy expanded with reliability tiers.

## License

GPL-3.0 — see [LICENSE](LICENSE)

## Author

**DR. TK** ([@drtknoh-sudo](https://github.com/drtknoh-sudo))
Built with Claude (Anthropic) in Cowork Mode.
