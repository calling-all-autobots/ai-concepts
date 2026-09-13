# Claude Opus 4.7 — coding, high-res vision, Task Budgets

- **Category:** ① Product release
- **Date:** 2026-04-16  ·  **What it affects:** Model `claude-opus-4-7`; effort param; vision; Task Budgets beta (`task-budgets-2026-03-13`)
- **Sources:** https://www.anthropic.com/news/claude-opus-4-7 · https://platform.claude.com/docs/en/release-notes/overview · https://platform.claude.com/docs/en/build-with-claude/task-budgets

## In one line
Opus 4.7 (`claude-opus-4-7`) is Anthropic's new flagship — better agentic coding, ~3x higher image resolution, a new `xhigh` effort level, and advisory Task Budgets — all at the same $5/$25 per MTok as Opus 4.6.

## What actually changed
Released Apr 16, 2026. **Same price** as Opus 4.6: **$5/M input, $25/M output**. Headline benchmarks (Anthropic's own numbers): **SWE-bench Verified 92.3%** (up from 87.3%), **CursorBench 70%** (up from 58%), **BigLaw Bench (Harvey) 90.9%** at high effort, and "3x more production tasks resolved" on Rakuten-SWE-Bench vs 4.6.

New/changed capabilities:
- **`xhigh` effort level** — a new "extra high" setting slotted between `high` and `max`. Opus 4.7 also "thinks more at higher effort levels, particularly on later turns in agentic settings."
- **High-resolution vision** — max image input raised from **1,568px to 2,576px on the long edge (~3.75 MP)**, aimed at computer use, screenshot understanding, and document analysis.
- **Task Budgets (beta)** — give Claude an advisory token budget for a *full agentic loop* (thinking + tool calls + tool results + output); the model sees a running countdown and finishes gracefully instead of getting cut off. Requires header `task-budgets-2026-03-13`.
- **File-system memory** — "better at using file system-based memory" across multi-session work; plus an `/ultrareview` slash command for dedicated code review.

## Why it matters
The economics are the story: a real capability jump (SWE-bench Verified crossing ~92%) at unchanged price means the cost-per-solved-task drops. Task Budgets attack the biggest operational risk in long-running agents — unbounded, unpredictable token spend — by making the model a cooperative budget-aware planner rather than something you cap with a hard external limit that truncates mid-thought.

## Your point of view
- "Same price, materially better coding — the sensible default for agentic dev work is now Opus 4.7."
- "Task Budgets change agent cost from 'hope it stops' to 'tell it the budget and it plans around it' — that's a real ops lever."
- "Higher vision resolution makes computer-use and document/screenshot pipelines meaningfully more reliable."

## What to do
- Pin `claude-opus-4-7` for agentic coding and re-run your evals; expect to spend less per solved task.
- Add the `task-budgets-2026-03-13` header to long-running agent calls and set advisory budgets instead of relying only on `max_tokens` truncation.
- Reserve `xhigh`/`max` effort for genuinely hard turns; use lower effort elsewhere to control cost.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [agent memory](../../../agents/agent-memory.md)
- [structured outputs](../../../reasoning-generation/structured-outputs.md)
