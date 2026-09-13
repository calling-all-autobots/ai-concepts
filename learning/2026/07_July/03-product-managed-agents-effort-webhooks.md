# Managed Agents gain persistent effort, lifecycle webhooks, and session seeding

- **Category:** ① Product release
- **Date:** 2026-07-22  ·  **What it affects:** Claude Managed Agents (agent config, webhooks, sessions API)
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview · https://platform.claude.com/docs/en/managed-agents/webhooks

## In one line
Managed Agents can now carry an `effort` level baked into their model config, fire webhooks on environment and memory-store lifecycle events, and start a session pre-seeded with up to 50 events in a single call.

## What actually changed
Three concrete additions on 2026-07-22:
- **Persistent effort on the agent.** You can set an `effort` level inside the `model` object when you create an agent, so the reasoning-compute dial is a property of the agent rather than something you pass per request.
- **Lifecycle webhooks widened.** Webhooks now cover the environment and memory-store lifecycle: four `environment.*` event types and three `memory_store.*` event types. You can react to these changes without polling. (This builds on earlier session- and vault-lifecycle webhooks shipped mid-2026.)
- **Session seeding.** When creating a session you can pass `initial_events` on `POST /v1/sessions` — up to 50 `user.message` and `user.define_outcome` events. A non-empty list starts the agent loop in the same call, so you skip the separate send-events request to kick off work.

## Why it matters
These are the plumbing pieces that move Managed Agents from "runnable" to "operable at scale." Persisting `effort` on the agent means cost/quality is configured once, not re-argued on every call. Environment and memory-store webhooks close the observability gap — you get pushed the events you previously had to poll for, which is how you build reliable orchestration and alerting. Session seeding removes a round trip and lets you launch an agent already loaded with context and a defined outcome.

## Your point of view
- Webhooks over polling is the real unlock: event-driven orchestration is cheaper and lower-latency than a poll loop, and now covers environment + memory lifecycle.
- Baking `effort` into the agent config is the right default-management pattern — set the cost/quality posture per agent, not per request.
- Session seeding with a `define_outcome` event nudges you toward outcome-oriented agent design from the first call.

## What to do
- Move any polling of agent state to `environment.*` / `memory_store.*` webhook subscriptions.
- Set `effort` on the agent's `model` config to lock a cost/quality posture per agent role.
- Use `initial_events` to seed sessions with context + a defined outcome and save the extra round trip.

## Connects to
- [Agentic systems](../../../agents/agentic-systems.md)
- [Planning & orchestration](../../../agents/planning-orchestration.md)
- [Observability](../../../production-ops/observability.md)
