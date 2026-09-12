---
name: lesson-eval
description: >-
  Quality-gate a drafted study lesson before it is shown to the user. Use this
  immediately after writing any lesson with the lesson-prep or ai-concepts
  skills, and before sharing a lesson in any study/interview-prep workflow. It
  audits the draft against the standard — discourse depth (not definitions),
  prerequisite primers with expanded acronyms, no scope leakage into other
  lessons, transcript-style non-obvious interview questions, clarify-back
  formatting, a Summary section, and no hypotheses stated as fact — and returns
  a PASS or FAIL verdict with concrete required fixes. A lesson must PASS this
  gate before it is shared with the user.
---

# Lesson Eval

A gate. Run it on a drafted lesson before showing that lesson to the user. Its job is to catch the defects that make study material shallow or misleading, and to force a fix before the learner ever sees it.

## How to run it

Read the drafted lesson in full. Then score it against every rubric item in `references/rubric.md`. Each item is PASS or FAIL with a one-line justification. Be adversarial — assume the lesson is flawed and look for the flaw. The most common real defect is **scope leakage** (teaching a concept that belongs to another lesson) and the second is **definition-depth instead of discourse-depth**.

## Verdict

- **PASS** only if every rubric item passes.
- **FAIL** if any item fails. Output the failing items with the *specific* fix required (quote the offending text and say what to change), then apply the fixes and re-run. Do not share the lesson with the user until it PASSes.

## Output format

```
LESSON-EVAL: <lesson name>
Verdict: PASS | FAIL

[if FAIL]
Failed items:
- <rubric item>: <what's wrong, quoting the text> → <required fix>
...
```

Keep the report terse. The point is the fix, not the prose.
