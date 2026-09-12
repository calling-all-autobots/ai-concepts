# Scaling Managed Agents: decouple the brain from the hands

- **Category:** ③ New way of working
- **Date:** 2026-04-08  ·  **What it affects:** Architecture pattern for long-running/hosted agents (brain / hands / session split)
- **Sources:** https://www.anthropic.com/engineering/managed-agents

## In one line
Anthropic's engineering post on the Managed Agents architecture: stop putting the reasoning engine, the execution sandbox, and the event log in one container — split them into three independent interfaces so any part can fail, scale, or be replaced on its own.

## What actually changed
Published Apr 8, 2026 alongside the Managed Agents beta, this post explains the design. The first version was a **monolith**: brain (Claude + harness), hands (code-execution sandbox), and the event log all lived in **one container**. That made every container a **"pet"** — if it died, the session died; if it hung, someone intervened manually; and you couldn't tell a harness bug from packet loss from a container crash. The harness also assumed resources were local, forcing customers into VPC peering.

The redesign virtualizes an agent into **three interfaces**, borrowing the OS analogy that "abstractions outlasted the hardware — `read()` doesn't care if it's a 1970s disk pack or a modern SSD":
- **Brain** — Claude and its harness, now **stateless**; recovers via `wake(sessionId)` → `getSession(id)` → resume from the last event.
- **Hands** — sandboxes/tools, now disposable **"cattle"**, invoked through a simple `execute(name, input)` tool interface; created/destroyed on demand, even provisioned only if a session actually needs a container.
- **Session** — a durable, append-only log of every event, stored **outside** both Claude's context window and the harness.

Result: **p50 time-to-first-token dropped ~60%, p95 dropped over 90%**, because inference starts immediately instead of waiting on container provisioning.

## Why it matters
This is a reusable blueprint for anyone building long-running agents, whether or not they use Managed Agents. The core lesson — **state belongs in an external, durable session log, not inside the compute** — is what lets you treat execution as stateless and disposable, scale to N sessions by starting N stateless harnesses, and recover from crashes with a reboot instead of a "recovery ceremony." It is the agent-world version of twelve-factor / stateless-service design.

## Your point of view
- "The durable session log is the whole trick: put state outside the compute and the compute becomes cattle you can kill and restart freely."
- "Pets-vs-cattle finally applies to agents — a hung sandbox should be replaceable, never something you nurse back to health."
- "Even if I use my own stack, I'd copy this three-interface split (brain / hands / session) rather than co-locating reasoning and execution."

## What to do
- Audit your agent architecture: is session state trapped inside the container running the tools? If so, extract it into an external append-only log.
- Make the harness stateless and recoverable from that log (`wake` → `getSession` → resume) so a crashed worker just reboots.
- Provision sandboxes lazily and treat them as disposable; don't pay boot cost for sessions that never touch code execution.

## Connects to
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [production architecture](../../../10-production-ops/48-production-architecture.md)
- [agent memory](../../../06-agents/35-agent-memory.md)
