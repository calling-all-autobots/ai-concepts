---
name: ai-concepts
description: >-
  Build and maintain the user's AI-concepts interview study book — a 55-topic
  syllabus covering transformers, attention, embeddings, RAG, agents, tool
  calling, MCP, fine-tuning, reasoning models, evals, guardrails, AI security,
  cost/unit economics and more — living in E:\ai-concepts and written with the
  lesson-prep method and gated by lesson-eval. Use this whenever the user works
  on their AI/LLM interview prep, asks for the next AI lesson, wants a specific
  AI concept taught for interviews, or wants the AI syllabus, table of contents,
  or change-registry tracker created or updated. Resume this project whenever
  the user returns to studying AI concepts.
---

# AI Concepts (Interview Study Book)

The specific instance: a structured book of AI/LLM concepts for a product manager preparing for an AI-heavy interview. Depth target is **conceptual clarity — explain, defend the choice, know the failure mode** — not architect/SME depth. The learner has no ML background.

## Method
Apply the **lesson-prep** skill for every lesson (discourse depth, prerequisite primers in alert boxes, scope discipline, Summary section, transcript-style stumper questions with clarify-back). Gate every lesson with **lesson-eval** — it must PASS before being shared. Do not restate those standards here; follow them.

## Location and structure
Everything lives in `E:\ai-concepts`.

```
E:\ai-concepts\
  README.md        ← Table of Contents (linked, read the book from here)
  TRACKER.md       ← change registry: done / left / what changed when
  primers/         ← standing glossary (e.g. ml-vocabulary.md)
  foundations/ … agent-engineering/   ← 12 category folders (no number prefix)
```

**Numbering: there is none.** Neither category folders nor lesson files carry a number prefix — a folder is its slug (`foundations/`), a lesson is its slug (`foundations/tokenization.md`). This is deliberate: global numbers used to cascade on every insert/reorder. Two rules follow:
- **Reading order lives only in the README ToC** (the filesystem sorts alphabetically and does *not* encode order). When you add or move a lesson, fix its position in the ToC.
- **Refer to a lesson by its title, never a number** — in prose ("see the [Retrieval](../retrieval-knowledge/retrieval.md) lesson"), in the ToC, and in the Tracker (its status table is keyed by category + title). ToC display numbers restart at 1 within each section and are purely presentational.

ToC and Tracker are separate files with separate jobs.

## The syllabus
The full topic list, its 12 categories, and the file path for each lesson are in `references/syllabus.md`. Read it to know what to write next and where it goes. Cross-link related lessons; a concept with its own entry is linked, never taught inline in another lesson.

## Working rhythm
1. If the book doesn't exist yet, scaffold `README.md` (ToC), `TRACKER.md`, the 12 category folders, and `primers/ml-vocabulary.md` — after the user approves the structure.
2. Write one lesson per turn using lesson-prep.
3. Run lesson-eval; fix until PASS.
4. Tick the lesson in both TRACKER.md and README.md; update the progress count.
5. Continue to the next syllabus item, or jump to whichever topic the user asks for.

The user's saved lesson standard (in memory, `ai-interview-prep-lesson-spec`) is authoritative if any detail here is unclear.
