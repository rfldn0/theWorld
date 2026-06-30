---
name: second-brain-skills
description: >
  All research, ingestion, and analysis skills for the Second Brain vault.
  Covers: Claude Projects deep analysis, local Ollama processing (deepseek-r1),
  Gemini free-tier Q&A, YouTube/web/PDF content fetching, and the full ingestion
  pipeline. Claude is the orchestrator — scripts in ../TheWorld-Scripts/ are the tools.
compatibility:
  requires:
    - Claude Pro subscription (for Claude Projects)
    - Ollama running locally with deepseek-r1:8b
    - Python 3.11+ with ../TheWorld-Scripts/requirements.txt installed
    - ../TheWorld-Scripts/config.json configured (copy from config.example.json)
  optional:
    - Gemini API key (free tier) for gemini_query.py
  python: ">=3.11"
---

# Second Brain Skills

Two complementary research engines + one ingestion pipeline:

| Engine                      | Role                                                        | When to use                                            |
| --------------------------- | ----------------------------------------------------------- | ------------------------------------------------------ |
| **Claude Projects**         | Deep synthesis, argument development, cross-source analysis | Multi-document analysis sessions via claude.ai         |
| **Ollama (deepseek-r1:8b)** | Local processing — summarize, chunk, extract concepts       | Any content before vault ingestion                     |
| **Gemini (free tier)**      | Q&A, topic exploration, quizzes, indexing                   | When you want a second perspective or specific queries |

---

## Skill 1: Research Ingestion Pipeline

**Trigger words:** "fetch", "ingest", "save this to my vault", "process this URL", "get this YouTube video", "read this PDF", "research this article"

Claude orchestrates via `../TheWorld-Scripts/ingest.py`. The pipeline:

```
Source → Fetch → Ollama processing → (optional) Gemini → Vault-ready note
```

### Usage

```bash
# YouTube video — full pipeline, print to stdout
python ../TheWorld-Scripts/ingest.py https://www.youtube.com/watch?v=xxxxx

# Web article — save directly to 00-Inbox
python ../TheWorld-Scripts/ingest.py https://example.com/article --save

# PDF (local or URL) with specific tasks
python ../TheWorld-Scripts/ingest.py paper.pdf --tasks summarize concepts outline --save

# Any source + Gemini follow-up question
python ../TheWorld-Scripts/ingest.py <source> --gemini-query "How does this connect to X?" --save

# Skip Ollama, run only Gemini exploration
python ../TheWorld-Scripts/ingest.py <source> --skip-ollama --gemini-query "Explore the main themes" --gemini-task explore

# Override title and add tags
python ../TheWorld-Scripts/ingest.py <source> --title "My Custom Title" --tags theology philosophy --save
```

### Available `--tasks` (Ollama)

| Task | Output |
|------|--------|
| `summarize` | Core thesis + key points + conclusions |
| `concepts` | Markdown table of key concepts |
| `outline` | Hierarchical outline of the content |
| `questions` | Research questions (clarifying, critical, extension) |
| `extract` | Most significant passages with context |
| `critique` | Strengths, weaknesses, gaps, contradictions |

Default tasks: `summarize concepts questions`

### Available `--gemini-task`

| Task | Output |
|------|--------|
| `qa` | Precise answer to a specific question |
| `explore` | Deep thematic exploration |
| `connections` | Connections to a topic/concept |
| `quiz` | Comprehensive quiz with answer key |
| `index` | Structured research index |

---

## Skill 2: Fetch Only (No Processing)

Use when you need raw content for manual review or custom processing.

```bash
# YouTube transcript + metadata → JSON
python ../TheWorld-Scripts/fetch_youtube.py https://youtu.be/xxxxx

# YouTube transcript only (just the text)
python ../TheWorld-Scripts/fetch_youtube.py https://youtu.be/xxxxx --format transcript

# Web page → clean Markdown
python ../TheWorld-Scripts/fetch_web.py https://example.com/article

# Web page → JSON with metadata
python ../TheWorld-Scripts/fetch_web.py https://example.com/article --format json

# PDF → extracted text
python ../TheWorld-Scripts/fetch_pdf.py paper.pdf

# PDF with page range
python ../TheWorld-Scripts/fetch_pdf.py paper.pdf --pages 1-25

# Remote PDF
python ../TheWorld-Scripts/fetch_pdf.py https://arxiv.org/pdf/xxxx.pdf --pages 1-10
```

All fetch scripts write to **stdout**. Pipe or redirect as needed:

```bash
python ../TheWorld-Scripts/fetch_web.py https://example.com > content.txt
python ../TheWorld-Scripts/fetch_youtube.py https://youtu.be/xxxx | python ../TheWorld-Scripts/ollama_process.py --task summarize
```

---

## Skill 3: Ollama Local Processing

**Model:** `deepseek-r1:8b` (installed). Runs fully offline.

```bash
# Summarize any text file
python ../TheWorld-Scripts/ollama_process.py --task summarize --input content.txt

# Generate research questions from piped content
cat article.txt | python ../TheWorld-Scripts/ollama_process.py --task questions

# Extract key concepts as a table
python ../TheWorld-Scripts/ollama_process.py --task concepts --input paper.txt

# Answer a specific question about a document
python ../TheWorld-Scripts/ollama_process.py --task qa --input paper.txt --context "What methodology did the authors use?"

# Full critique
python ../TheWorld-Scripts/ollama_process.py --task critique --input paper.txt

# Use a different Ollama model
python ../TheWorld-Scripts/ollama_process.py --task summarize --model llama3.2 --input content.txt
```

**Claude orchestration pattern:**
1. Pipe fetch output directly into `ollama_process.py`
2. Run multiple tasks sequentially and combine results
3. Use `--task qa --context "question"` for targeted document Q&A

---

## Skill 4: Gemini Free-Tier Analysis

**Model:** `gemini-1.5-flash` (free tier — 15 requests/min, 1M tokens/request)

**Setup required:** Add Gemini API key to `../TheWorld-Scripts/config.json`
Get free key at: https://aistudio.google.com/app/apikey

```bash
# Q&A: answer a question using a context file
python ../TheWorld-Scripts/gemini_query.py --query "What is the central argument?" --context content.txt

# Q&A: pipe content
cat content.txt | python ../TheWorld-Scripts/gemini_query.py --query "What methodology is used?"

# Deep topic exploration
python ../TheWorld-Scripts/gemini_query.py --query "consciousness" --context notes.txt --task explore

# Find connections between content and a concept
python ../TheWorld-Scripts/gemini_query.py --query "cognitive load theory" --context article.txt --task connections

# Generate a quiz
python ../TheWorld-Scripts/gemini_query.py --query "New Testament theology" --context notes.txt --task quiz

# Build a research index
python ../TheWorld-Scripts/gemini_query.py --query "for academic literature review" --context paper.txt --task index
```

---

## Skill 5: Claude Projects Deep Research

Claude Projects (Claude Pro) handles multi-document synthesis that exceeds what local tools can do. Use for: cross-source argument development, methodological critique across papers, generating vault deliverables.

### Session Opener Template

```
Project: [Project Name]
Session goal: [specific question or deliverable]
Sources loaded: [list of files]
Requested output: [note / synthesis / critique / argument map]
Target location: [00-Inbox / 10-Projects / 30-Resources]
```

### Analysis Patterns (quick reference)

See `analysis-patterns.md` for full prompts. Summary:

| Pattern | When to use |
|---------|-------------|
| Cross-Source Synthesis | Multiple sources, need integrated view |
| Methodological Critique | Evaluate evidence quality |
| Argument Mapping | Decompose one source's logic |
| Original Argument Dev | Build your own position from sources |
| Contradiction Surfacing | Sources conflict, need resolution |
| Literature Gap Analysis | What research is missing |
| Concept Extraction | Pull frameworks and terms |
| Comparative Analysis | Two sources on same topic |

### Vault Output Rules

Every Claude Projects deliverable must include:
1. YAML front matter (title, date, tags, status: draft, source, related)
2. `[[wikilinks]]` on all concepts
3. Obsidian callout blocks (`> [!NOTE]`, `> [!WARNING]`, `> [!QUESTION]`)
4. End with `## Next Actions` or `## Related` (never closing prose)

Filing locations:
- Raw output → `60-ClaudeProjects/imports/`
- Synthesis note → `00-Inbox/`
- Source reference → `30-Resources/`
- Session log → `60-ClaudeProjects/sessions/`

---

## Setup & Configuration

### First-Time Setup

```bash
# 1. Install Python dependencies
pip install -r ../TheWorld-Scripts/requirements.txt

# 2. Copy and configure
cp ../TheWorld-Scripts/config.example.json ../TheWorld-Scripts/config.json
# Edit config.json: add Gemini API key, verify vault_path

# 3. Verify Ollama is running
ollama serve  # run in separate terminal if not already running
ollama list   # should show deepseek-r1:8b

# 4. Test the pipeline
python ../TheWorld-Scripts/ollama_process.py --task summarize --input CLAUDE.md
```

### `../TheWorld-Scripts/config.json` Reference

```json
{
  "gemini_api_key": "your_key_here",
  "ollama_base_url": "http://localhost:11434",
  "ollama_model": "deepseek-r1:8b",
  "gemini_model": "gemini-1.5-flash",
  "vault_path": "C:/Users/tabun/OneDrive - Western Michigan University/Documents/Vaults/TheWorld",
  "vault_inbox": "00-Inbox"
}
```

### Claude's Orchestration Role

When a user says "research this", "process this URL", or "save this to my vault":

1. Identify source type (YouTube / web / PDF / file)
2. Call appropriate `fetch_*.py` via Bash tool
3. Pipe result to `ollama_process.py` with relevant tasks
4. If user has a specific question → call `gemini_query.py`
5. Combine results into a vault note using CLAUDE.md formatting standards
6. Offer to save with `--save` flag or show the note for manual copy-paste

Claude does **not** summarize the scripts' output — it synthesizes, formats, and links it.

---

## Post-Ingestion Checklist

After any note lands in `00-Inbox/`:

```
- [ ] Front matter complete and accurate
- [ ] Summary rewritten in own words (not raw script output verbatim)
- [ ] Key insights extracted as atomic bullets
- [ ] [[wikilinks]] added to recognized concepts
- [ ] Stub notes created for new concepts
- [ ] Source filed in 30-Resources/ if it warrants a reference note
- [ ] Tags match vault conventions
- [ ] Next actions listed
```

Status progression: `draft` → `in-progress` → `evergreen`
