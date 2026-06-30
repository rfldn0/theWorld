---
title: "Vibe Coding and Interview Readiness"
date: 2026-06-26
tags: [programming, interview, ai-tools, python, career]
status: in-progress
source: "https://youtu.be/c2PTp0Oi-Es"
related: ["[[Vibe Coding]]", "[[RAG Pipeline]]", "[[Docker]]"]
---

## Summary

A student who built a [[RAG Pipeline]] using AI tools failed a technical interview because they could not explain their own codebase. The failure exposes a structural risk in [[Vibe Coding]]: using AI to generate code without building the foundational understanding needed to defend, debug, or extend it.

## Main Content

### The Core Failure Pattern

The student built a functional RAG application using:
- [[ChromaDB]] for vector storage and retrieval
- [[Hybrid Search]] (semantic similarity + keyword matching) for retrieval
- [[Chunking]] to split documents into indexed pieces
- [[SQLite]] as the database backend
- [[Docker]] for containerized, consistent deployment

Despite the working system, the student:
- Could not explain what specific functions did
- Could not identify logical errors in AI-generated code
- Did not understand basic Python constructs (e.g., `continue`, `enumerate`)
- Took credit for implementations they could not describe

### Interviewer's Assessment

The interviewer's critique was not about the stack choice or package knowledge. It was about **foundational gaps**:
- No basic Python knowledge (loops, data structures, control flow)
- Cannot trace how [[Chunking]] actually runs in the code
- Cannot spot logical errors in AI-generated output
- Can define RAG at a high level but cannot explain the implementation

> [!WARNING] Key Risk
> AI tools let you build things you don't understand. Interviews test whether you understand them.

### Why ChromaDB?

The student's answer: "it can be run locally." This is a valid operational reason but reveals no understanding of *why* a vector database is appropriate for semantic retrieval — a gap that signals surface-level tool familiarity.

### The Vibe Coding Trap

[[Vibe Coding]] produces working code but no transferable understanding. The compounding problem:
- AI handles the complexity → developer never encounters it
- Developer ships confidently → mental model stays shallow
- Interview or production bug surfaces → no tools to respond

### How to Avoid This

From the video's recommendations, ordered by priority:

1. **Understand the code before calling it yours** — trace every function, know what it does
2. **Know your external packages** — not just how to import them, but what problem they solve and why you chose them over alternatives
3. **Write some code yourself** — especially data structures, basic algorithms, control flow
4. **Build foundational Python first** — AI usage for efficiency is valid only *after* you have a working mental model
5. **Have a base in [[Algorithm Complexity — Big O Notation|DSA]]** — easy to medium LeetCode-equivalent problems
6. **Interview your own resume** — ask yourself what an interviewer would ask; answer it cold

> [!NOTE] Practical Rule
> If you cannot explain what a function does without running it, you don't own that code.

## Key Insights

- [[Model Context Length]] affects how much context an AI coding tool can hold — small context windows require task fragmentation across sessions
- The `finally` block in Python runs after every execution regardless of errors — a basic Python behavior the student couldn't explain
- One bad interview does not define all future performance — but unaddressed knowledge gaps compound
- The interviewer's standard: understand the code you submit, not just the packages you chose

## Questions / Open Threads

- [ ] What is the threshold of "understanding" required before using AI for efficiency — how do you self-assess?
- [ ] Does this gap scale? Do senior developers who vibe-code face the same brittleness in production incidents?
- [ ] What does a structured "interview your own project" review look like as a pre-application practice?

## Related

- [[Vibe Coding]] — the root behavior pattern this note diagnoses
- [[RAG Pipeline]] — the technical project the student built
- [[Algorithm Complexity — Big O Notation]] — DSA foundation recommended as prerequisite
- `60-ClaudeProjects/imports/ollama-summary-rag-vibe-coding-2026-06-26.md` — full Ollama output and source
