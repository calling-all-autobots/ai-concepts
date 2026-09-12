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
  primers/         ← standing glossary (e.g. ml-vocabulary.md); never numbered 00
  01-foundations/ … 11-product-strategy/   ← 11 category folders, numbered 01–11
```

Lesson files are numbered globally `01`–`55` inside their category folder (e.g. `01-foundations/01-transformers.md`). **Never a `00` prefix.** ToC and Tracker are separate files with separate jobs.

## The syllabus
The full 55-topic list, its 11 categories, and the file path for each lesson are in `references/syllabus.md`. Read it to know what to write next and where it goes. Cross-link related lessons; a concept with its own entry is linked, never taught inline in another lesson.

## Working rhythm
1. If the book doesn't exist yet, scaffold `README.md` (ToC), `TRACKER.md`, the 11 folders, and `primers/ml-vocabulary.md` — after the user approves the structure.
2. Write one lesson per turn using lesson-prep.
3. Run lesson-eval; fix until PASS.
4. Tick the lesson in both TRACKER.md and README.md; update the progress count.
5. Continue to the next syllabus item, or jump to whichever topic the user asks for.

The user's saved lesson standard (in memory, `ai-interview-prep-lesson-spec`) is authoritative if any detail here is unclear.
