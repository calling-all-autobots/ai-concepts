# Evaluating agents: grade outcomes not paths, and design tests AI can't shortcut

- **Category:** ② New best practice
- **Date:** 2026-01-09 and 2026-01-21 · **What it affects:** how you eval agents in CI, and how you assess human/technical skill in an AI-assisted world
- **Sources:** https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents (Jan 9) · https://www.anthropic.com/engineering/AI-resistant-technical-evaluations (Jan 21)

## In one line
Two January engineering posts: the first is Anthropic's playbook for evaluating agents (grade the end state, not the step sequence; calibrate LLM judges; run evals as CI), and the second shows how to design technical evaluations that stay meaningful as models get better.

## What actually changed
**"Demystifying evals for AI agents" (Jan 9)** — the operating manual:
- Evaluating an agent ≠ grading a chat reply. Agents act over many turns, call tools, and mutate external state, so grade the **outcome / environment state** (e.g. "does a reservation row exist in the SQL DB?") over the **transcript/trajectory** (tool calls, reasoning). Don't enforce a rigid step sequence — agents "regularly find valid approaches eval designers didn't anticipate."
- Three grader types: **code-based** (string/binary/static-analysis — fast, brittle), **model-based** (rubric scoring — flexible, needs calibration), **human** (gold standard, reserve for calibrating LLM judges and subjective outputs). LLM-as-judge must be **closely calibrated to human experts**.
- Reliability math for non-determinism: **pass@k** (≥1 success in k) vs **pass^k** (all k succeed). At 75% per-trial success, passing all 3 is 0.75³ ≈ **42%** — use pass^k for customer-facing agents.
- Isolate every trial in a **clean environment**; shared state (leftover files, caches) causes correlated failures.
- 8-step roadmap: start with 20–50 tasks from real failures; convert manual checks to tests; write unambiguous tasks with reference solutions; balance positive/negative cases; build a stable harness; design graders that allow **partial credit**; read transcripts to validate graders; refresh tasks as scores saturate. Run automated evals in **CI/CD** on every agent change and model upgrade.

**"Designing AI-resistant technical evaluations" (Jan 21)** — the hiring/skill-testing corollary:
- Anthropic's performance-engineering take-home kept getting solved by each new Claude. Opus 4 (May 2025) beat most humans in the 4-hour limit; Opus 4.5 matched the best human in 2 hours and reached 1,487 cycles with heavy test-time compute (best human: 1,363).
- Fixes: use **out-of-distribution** problems (they moved to Zachtronics-style constraint puzzles over realistic accelerator tasks); test **judgment over volume** (choosing/building the right debugging tools is part of the test); use realistic time horizons; accept that "realism may be a luxury we no longer have."

## Why it matters
Together they reframe evaluation for the agent era: for machines, stop grading the words and grade what changed in the world; for humans, stop testing what a model can now do for the candidate. Both hinge on the same idea — measure judgment and end-state, not surface behavior.

## Your point of view
- "Outcome-and-state grading is the headline: our agent evals should assert on the database/filesystem, not on the final message."
- "Report pass^k for anything customer-facing — a 75% agent is a 42% agent over three turns."
- "AI-resistant hiring means out-of-distribution, judgment-heavy problems; banning AI in interviews is the wrong lever."

## What to do
- Rebuild agent evals around environment-state assertions + calibrated LLM-judge rubrics; add partial credit; isolate each trial.
- Track pass^k, not just averages; wire the eval suite into CI to gate every agent/model change.
- Redesign any coding take-home toward novel, judgment-testing problems; publish/rotate tasks as models saturate them.

## Connects to
- [evaluation methods](../../../09-evaluation/45-evaluation-methods.md)
- [benchmarks](../../../09-evaluation/46-benchmarks.md)
- [regression testing](../../../09-evaluation/47-regression-testing.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [observability](../../../10-production-ops/50-observability.md)
