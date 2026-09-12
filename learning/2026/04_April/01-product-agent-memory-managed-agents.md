# Agent Memory for Managed Agents → public beta

- **Category:** ① Product release
- **Date:** 2026-04-23  ·  **What it affects:** Claude Managed Agents (hosted agent API); beta header `managed-agents-2026-04-01`
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview · https://platform.claude.com/docs/en/managed-agents/memory

## In one line
Hosted Claude agents can now carry durable, categorized memory across sessions without you building the storage yourself — it is a managed part of the Managed Agents runtime, in public beta.

## What actually changed
Two weeks after Managed Agents launched (Apr 8), Anthropic put **agent memory for Managed Agents into public beta** on Apr 23, 2026. It ships under the same `managed-agents-2026-04-01` beta header, so no new gate — if you are already calling Managed Agents you can turn memory on. The integration guide lives at `platform.claude.com/docs/en/managed-agents/memory`. The point: memory is now a first-class runtime concern the platform manages (persisted outside Claude's context window, alongside the durable session log), not something you bolt on with your own database and retrieval glue. This mirrors the standalone memory tool from Opus 4.5, but here Anthropic owns the persistence layer.

## Why it matters
Long-horizon agents are only as useful as what they remember between runs. Before this, if you wanted a Managed Agent to recall a user's preferences, prior decisions, or project state across sessions, you built and secured that store yourself. Folding memory into the managed harness removes a whole category of undifferentiated infrastructure — and keeps memory consistent with the session-log architecture the platform already runs (see the brain/hands post from Apr 8).

## Your point of view
- "Managed Agents is maturing fast — the harness, sandbox, and now memory are all things Anthropic operates so you don't have to."
- "It's still beta and header-gated, so treat it as a strong default for prototypes, not yet a compliance-grade system of record."
- "Owning your own memory store still makes sense when you need portability across providers or strict data-residency control."

## What to do
- If you run Managed Agents, read the memory integration guide and try replacing any bespoke cross-session store with the managed one — you already have the header.
- Decide deliberately what belongs in managed memory vs. your own database (regulated or portable data likely stays yours).
- Watch for GA and any pricing that attaches to memory storage before betting production on it.

## Connects to
- [agent memory](../../../06-agents/35-agent-memory.md)
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [production architecture](../../../10-production-ops/48-production-architecture.md)
