# Multi-agent orchestration + Outcomes (public beta) + Dreaming (research preview)

- **Category:** ① Product release
- **Date:** 2026-05-06  ·  **What it affects:** Claude Managed Agents platform
- **Sources:** https://thenewstack.io/anthropic-managed-agents-dreaming-outcomes/ · https://www.developersdigest.tech/blog/claude-managed-agents-dreaming-outcomes-multi-agent

## In one line
Three platform-level additions to Claude Managed Agents: a lead agent fanning work out to parallel specialist subagents (orchestration), a separate grader agent scoring work against a rubric until it passes (Outcomes), and a between-sessions memory-consolidation pass (Dreaming).

## What actually changed
Shipped May 6, 2026 (candidate list logs this early-May item as May 4; multiple sources confirm the May 6 ship date):
- **Multi-agent orchestration (public beta):** a lead agent delegates to up to **20 unique specialist subagents**, with up to **25 concurrent threads**, running in parallel on a **shared filesystem**. This is orchestration as a *platform primitive*, not something you hand-roll.
- **Outcomes (public beta):** you write an explicit **rubric** describing success; a **separate grader agent** (its own context window) scores the working agent's output and iterates with it until criteria are met or the iteration budget runs out. Reported gains: **up to +10 points** task success overall, e.g. **+8.4%** on `.docx` and **+10.1%** on `.pptx` generation, with the biggest wins on the hardest tasks. Early customers: Wisedocs ~50% faster medical-doc review.
- **Dreaming (research preview):** a scheduled, between-sessions **non-parametric memory consolidation** — reads an existing memory store plus up to **100 prior sessions**, then writes a new store that reorganizes memories, merges duplicates, replaces stale entries, and surfaces cross-session patterns (Anthropic likens it to hippocampal replay during sleep). Harvey reported ~6x higher task completion with dreaming on.

## Why it matters
This moves three things that teams used to build by hand — fan-out orchestration, LLM-as-judge self-correction loops, and long-horizon memory — into the managed platform. Outcomes is the notable one: it's a built-in evaluator-in-the-loop, turning "write a good prompt" into "write a good rubric and let a grader enforce it." Dreaming attacks the hardest agent problem, memory that improves over time, without retraining (non-parametric = stored memory, not weights).

## Your point of view
- "Outcomes is LLM-as-judge productized: the leverage moves from prompt-crafting to rubric-writing. Your eval rubric becomes the spec."
- "Orchestration limits are concrete — 20 specialists / 25 threads / shared filesystem — plan decomposition around them rather than assuming infinite fan-out."
- "Dreaming is self-improvement without fine-tuning; treat the consolidated memory store as a new, auditable artifact (and attack surface)."

## What to do
- Pilot Outcomes on a task with a checkable rubric (document generation, extraction) and measure the success delta yourself before trusting the +10-point claim.
- Design multi-agent jobs within the 20-subagent / 25-thread budget; use the shared filesystem as the coordination channel.
- If you adopt Dreaming, review the consolidated memory it writes — stale-entry replacement and pattern-surfacing need human spot-checks.

## Connects to
- [multi-agent](../../../agents/multi-agent.md) · [planning & orchestration](../../../agents/planning-orchestration.md) · [agent memory](../../../agents/agent-memory.md) · [agentic systems](../../../agents/agentic-systems.md)
