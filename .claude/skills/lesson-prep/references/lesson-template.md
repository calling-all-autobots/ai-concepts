# Lesson Template

Use this shape for every lesson. Headings are fixed; prose is yours. Keep it discourse-depth — teach, don't define.

```markdown
# <Concept name>

## The problem it solves
Open with the pain or the question nobody could answer before this concept
existed. Make the reader feel why it was needed. No "in this lesson".

## <Title the section for the idea — e.g. "The model reads the way you do">
One memorable everyday scene the learner can reuse to explain the concept to
anyone — written as flowing prose, **not** labeled sub-parts. Do NOT use
`**The picture:** / **The mapping:** / **Why it holds:** / **Say it like this:**`
headers; that worksheet scaffold is banned. Instead:

- Paint the everyday scene in a sentence or two.
- **Show it on a concrete instance** — run the same worked example the lesson
  uses through the scene so the correspondence appears in front of the reader.
  A `thing = part-of-concept` mapping list is banned; demonstrate, don't tabulate.
- Land a sayable one-liner in the prose.
- Note the one place the analogy leaks, if there's a genuinely misleading seam.

The analogy must reach the mechanism: if a later section needs a *second*
metaphor to explain the core mechanism, this analogy is wrong — replace it, don't
add the second one.

## <Discourse body — one or more substantive sections>
Explain the concept as an expert would in conversation: the core insight, the
mechanism at a conceptual level, and — critically — the tradeoffs and the "so
what". Give prerequisite terms a short inline primer as they appear; reserve a
`> [!NOTE]` box for the rare term that genuinely needs a stop-and-orient callout
(see the alert-box restraint rule in SKILL.md).

Wherever entities relate — a pipeline, hierarchy, flow, or before/after — draw a
small **Mermaid** diagram (` ```mermaid ` block) right where you introduce the
relationship; it renders as a real diagram in most Markdown viewers. For example:

```mermaid
flowchart LR
  D[Dataset] -->|train| M[Model = weights]
  M -->|inference| O[output]
```

Surface the takeaway the reader can actually say out loud in an interview
("the sharp framing is …"). Reference — do not re-teach — concepts that have
their own lesson; link them.

## Summary / Points to Remember
- 4–7 bullets, each a sayable talking point, not a dictionary definition.
- Include the one causal chain or framing that separates a knowledgeable answer
  from a memorized one.

## Interview Questions That Stump People
See references/interview-questions.md for the transcript format and the
clarify-back convention. Stumpers only — no "what is X".
```

## Checklist before you consider a lesson done
- Would the reader survive a "why?" and a "what breaks?" follow-up? If not, go deeper.
- Exactly one memorable everyday analogy, **shown on a concrete worked instance** (no mapping list), in prose with no labeled sub-parts, and a sayable one-liner. It reaches the mechanism — no second metaphor rescues it later.
- Every acronym expanded on first use; prerequisites primed inline, with a `[!NOTE]` box only where one truly earns it (few per lesson).
- A Mermaid diagram appears wherever entities genuinely relate.
- Nothing taught that belongs to another lesson (linked instead).
- Summary bullets are talking points, not definitions.
- Interview questions are non-obvious, in transcript form, and each ends with a rationale.
- No hypothesis dressed up as fact.
