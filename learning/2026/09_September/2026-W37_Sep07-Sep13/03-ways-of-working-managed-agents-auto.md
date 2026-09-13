# Managed Agents — `auto` permission mode

- **Category:** ③ New way of working
- **Date:** 2026-09-10  ·  **What it affects:** how agent/MCP tool calls get approved at runtime (Managed Agents)
- **Sources:** [Developer Platform release notes](https://docs.claude.com/en/release-notes/overview)

## In one line
Instead of your app approving every tool call by hand, you can now hand a **policy** to Anthropic's Managed Agents and have **the server decide each call in real time — run it, deny it, or pause for a human** — so the safe 90% flows automatically and only the risky calls stop for you.

## What actually changed
- Managed Agents permission policies gained an **`auto`** mode: **"the server evaluates each agent or MCP tool call and runs it, denies it, or pauses for your approval."** Three outcomes, evaluated centrally, per call.
- Every decision is **observable**: `agent.tool_use` and `agent.mcp_tool_use` events now report the outcome in an **`evaluation`** field alongside **`evaluated_permission`** — so you can see *why* each call ran, was denied, or paused.
- This replaces the pattern where the **client** had to intercept and approve/deny each tool call itself, with a **server-side policy** that does it for you.

## Why it matters
Permissioning is the hard, load-bearing part of shipping an autonomous agent, and it's a genuine dilemma: approve everything and it's unsafe; approve nothing (human-in-the-loop on every call) and it's too slow to be worth automating. `auto` mode is the middle path — **policy-driven autonomy**: you encode once which calls are safe to run, which to block, and which are worth a human's attention, and the server enforces it consistently on every call. The `evaluation` field matters as much as the enforcement: it turns permissioning from an invisible yes/no into an **auditable trail** of what the agent tried and how it was judged — which is exactly what you need to trust an agent in production and to answer "what did it do and why" after the fact.

## Your point of view
- "The right question for an agent isn't 'autonomous or human-in-the-loop' — it's **'what's the permission policy,'** and `auto` mode makes that policy a first-class, server-enforced thing instead of ad-hoc client code."
- "**Centralized enforcement + a logged `evaluation` field = the governance story** you need before an agent touches anything that matters. Autonomy you can't audit is a liability."
- "This is the practical answer to the **'lethal trifecta'** risk (untrusted input + tool access + exfiltration): scope the policy so the dangerous *combinations* pause for a human."
- "Don't over-pause. If everything stops for approval you've just rebuilt the slow path — the value is drawing the line deliberately."

## What to do
1. **Define an explicit tool-permission policy** for any managed agent: enumerate which tool calls auto-run, which are denied outright, and which pause for a human — then set it to `auto`.
2. **Log and review the `evaluation` / `evaluated_permission` fields** — feed them into your observability so you can see the deny/pause rate and tune the policy.
3. **Put the pauses where the risk is** — writes, spends, external sends, and anything acting on untrusted input — not on read-only calls.
4. **Review the policy like code** (ideally via [`ant apply`](02-ways-of-working-ant-apply.md)) so permission changes are versioned, not silent.

## Connects to
[Agentic systems](../../../../agents/agentic-systems.md) · [Tool calling](../../../../agents/tool-calling.md) · [AI security](../../../../safety-trust/ai-security.md) · [Guardrails](../../../../safety-trust/guardrails.md) · [LLM observability](../../../../production-ops/observability.md)
