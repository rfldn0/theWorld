# TheWorld — Second Brain Vault Template

A structured Obsidian second brain built on the PARA method, powered by a Claude Projects + Ollama + Gemini research pipeline.

---

## Vault Structure

```
vault/
├── 00-Inbox/          # Raw captures, unprocessed fleeting notes
├── 10-Projects/       # Active projects with defined outcomes
├── 20-Areas/          # Ongoing responsibilities (no end date)
├── 30-Resources/      # Reference notes by topic/domain
├── 40-Archive/        # Completed, inactive, or deprecated notes
├── 50-Templates/      # Note templates
├── 60-ClaudeProjects/ # AI session outputs before processing
│   ├── imports/       # Raw outputs (Ollama, Claude, Gemini)
│   └── sessions/      # Full session logs
└── 90-Meta/           # Vault config, handoffs, indexes, MOCs
    └── Handoffs/      # Session continuity notes
```

---

## Research Pipeline

| Engine | Role | When to use |
|--------|------|-------------|
| **Claude Projects** | Deep synthesis, argument development, cross-source analysis | Multi-document analysis via claude.ai |
| **Ollama (deepseek-r1:8b)** | Local processing — summarize, chunk, extract concepts | Any content before vault ingestion |
| **Gemini (free tier)** | Q&A, topic exploration, making connections | Second perspective or specific queries |

See `SKILL.md` for full pipeline details and usage commands.

---

## Key Config Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Vault operating manual — conventions, formatting, workflow |
| `SKILL.md` | Research engine definitions and ingestion pipeline |
| `claude-projects-templates.md` | Import templates for AI session outputs |
| `analysis-patterns.md` | Prompt patterns for deep analysis |
| `MOTIVATION.md` | Daily motivation board — what I learned, who I am becoming |

---

## Setup

1. Clone this repo and open the folder as an Obsidian vault
2. Install Ollama locally and pull `deepseek-r1:8b`
3. Clone `TheWorld-Scripts` and configure `config.json`
4. (Optional) Set a Gemini API key for `gemini_query.py`
5. Read `CLAUDE.md` before your first session

---

## Note Conventions

- **One idea per note** — split if two concepts emerge
- **Front matter required** on every note (`title`, `date`, `tags`, `status`, `source`, `related`)
- **Wikilinks everywhere** — `[[Note Name]]` for all internal references
- **Inbox first** — new notes go to `00-Inbox/` unless location is obvious
- **Status flow:** `draft` → `in-progress` → `evergreen` → `archived`
