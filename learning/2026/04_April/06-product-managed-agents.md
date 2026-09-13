# Claude Managed Agents (public beta) + the `ant` CLI

- **Category:** ① Product release
- **Date:** 2026-04-08  ·  **What it affects:** New hosted agent platform (`managed-agents-2026-04-01` header); `ant` command-line client
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview · https://platform.claude.com/docs/en/cli-sdks-libraries/cli/quickstart · https://www.infoq.com/news/2026/04/anthropic-managed-agents/

## In one line
Managed Agents is a fully managed agent harness — Anthropic runs the loop, the sandbox, the tools, and the state so you don't build them — and `ant` is a new CLI that puts the whole Claude API in your terminal.

## What actually changed
On **Apr 8, 2026** Anthropic launched **Claude Managed Agents in public beta**: a hosted harness to run Claude as an autonomous agent with **secure sandboxing, built-in tools (bash, file ops, web search), server-sent-event streaming, persistent-state sessions, and tracing**. You create agents, configure containers, and run sessions through the API; all endpoints require the **`managed-agents-2026-04-01`** beta header. Pricing is standard Claude API token rates **plus ~$0.08 per session-hour** for the managed runtime.

Note on the candidate label: the master worklist tagged this "Managed Agents GA (Apr 9)." Per the official platform release notes it was **public beta, dated Apr 8** — the Apr 9 date belongs to Cowork's GA (nugget 05). Written here as public beta.

Alongside it, the **`ant` CLI** shipped (Apr 8): a command-line client for the Claude API offering faster API interaction, native Claude Code integration, and **versioning of API resources in YAML files** (agents/configs as code). It installs via `brew install anthropics/tap/ant`.

## Why it matters
Managed Agents removes the hardest, most undifferentiated parts of shipping an autonomous agent: the sandbox, the execution loop, state persistence, and recovery. That is a build-vs-buy inflection — teams that were writing their own agent runtime can now rent Anthropic's. The `ant` CLI + YAML resource versioning pushes agent configuration toward *infrastructure-as-code*, which is how these systems become reviewable, diffable, and CI-deployable rather than click-configured.

## Your point of view
- "Managed Agents is Anthropic renting you the boring-but-hard 90% of an agent platform — sandbox, loop, state, recovery."
- "It's beta and header-gated with a per-session-hour fee, so it's for prototypes and early production, not yet a locked-in bet."
- "`ant` + YAML means agents-as-code — treat agent definitions like Terraform, in version control and code review."

## What to do
- If you were about to build your own agent sandbox/harness, prototype on Managed Agents first with the `managed-agents-2026-04-01` header and compare total cost including the ~$0.08/session-hour.
- Install `ant` and keep agent/config resources as versioned YAML in your repo.
- Budget for the session-hour charge in any always-on scenario before committing production traffic.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [agent memory](../../../agents/agent-memory.md)
- [production architecture](../../../production-ops/production-architecture.md)
