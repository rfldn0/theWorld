# Analysis Patterns — Copy-Ready Prompts

Copy-paste these directly into a Claude Projects session. Replace bracketed placeholders.

---

## Cross-Source Synthesis
```
Synthesize the key arguments across all loaded sources on [topic].
Identify: (1) where they converge, (2) where they contradict, (3) what none address.
Format as a vault-ready Obsidian note with:
- YAML front matter (title, date, tags, status: draft)
- [[wikilinks]] on every concept with a likely vault note
- ## headings and bullet points
- > [!NOTE], > [!WARNING], > [!QUESTION] callout blocks where relevant
- End with ## Next Actions — no closing paragraph
```

---

## Methodological Critique
```
Evaluate the methodological quality of the loaded papers on [topic].
For each paper, assess: sample size, study design, confounds, replication status,
and whether claims outrun the evidence.
Use > [!WARNING] Issue: [name] callout blocks for each specific problem found.
Cite the paper and page/section when flagging an issue.
End with a verdict: how much weight should each paper carry in a research argument?
```

---

## Argument Map
```
Map the core argument of [paper title / author year].
Structure your output as:
## Core Claim
## Supporting Evidence (cite specific sections)
## Logical Gaps
## Unstated Assumptions
## Strongest Counterargument
## My Assessment (leave blank for me to fill)
Use [[wikilinks]] for every concept. Format for direct Obsidian paste.
```

---

## Original Argument Development
```
Based on the loaded sources, help me develop an original argument about [topic].
My current draft position: [your position in 1–2 sentences].

Produce:
1. What the sources directly support in my position
2. What I must argue from first principles (sources don't cover it)
3. The strongest objection to my position and how to counter it
4. What additional evidence or research would most strengthen it

Format as a working draft note with ## sections and [[wikilinks]].
```

---

## Contradiction Surfacing
```
Identify every significant point where the loaded sources contradict each other on [topic].
For each contradiction:
- Name the sources and their conflicting positions
- Assess which has the stronger evidentiary basis
- Flag unresolved contradictions with > [!QUESTION] Open Thread callout blocks
Format as an Obsidian note with YAML front matter and [[wikilinks]].
```

---

## Literature Gap Analysis
```
Based on the loaded sources, identify the key gaps in the existing literature on [topic].
What questions do these sources collectively fail to answer?
What methodological approaches are missing?
What populations, contexts, or time periods are underrepresented?
Format as a gap analysis note with ## headings and > [!QUESTION] callouts for each gap.
```

---

## Concept Extraction
```
Extract all significant concepts, frameworks, and named theories from the loaded sources.
For each concept:
- One-sentence definition
- Which source(s) introduce or develop it
- How it relates to [central topic]
Format as a Markdown table, then as individual stub notes ready for filing to 00-Inbox/.
Each stub should use the standard vault front matter with status: draft.
```

---

## Comparative Analysis
```
Compare [source A] and [source B] on [specific dimension].
Structure the comparison as:
- Point of agreement
- Point of disagreement
- Who has the stronger argument on each point of disagreement, and why
- What a synthesis of both positions would look like
Generate both a comparison table (for scanning) and a prose synthesis note (for the vault).
```
