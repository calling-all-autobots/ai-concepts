# Routines in Claude Code (research preview)

- **Category:** ③ New way of working
- **Date:** 2026-04-14  ·  **What it affects:** Claude Code (web/desktop/CLI); scheduled & triggered cloud automation; all paid plans
- **Sources:** https://claude.com/blog/introducing-routines-in-claude-code · https://code.claude.com/docs/en/desktop-scheduled-tasks

## In one line
A routine is a Claude Code automation you configure once — prompt, repo, connectors — and then run on a schedule, from an API call, or on an event, entirely on Anthropic's cloud, so nothing depends on your laptop being open.

## What actually changed
Shipped in **research preview on Apr 14, 2026**, on all paid plans (Pro, Max, Team, Enterprise). A routine bundles a prompt + repo + connectors and fires from one or more **triggers** — scheduled (hourly / daily / weekdays / weekly), API call, or event. Runs execute on **Claude Code's web infrastructure**, not your machine. You create and manage them from three places: `claude.ai/code`, the Claude desktop app, and the CLI via the **`/schedule`** command. Usage is capped per plan: **Pro up to 5 routines/day, Max 15, Team & Enterprise 25**, each run counting as one use.

## Why it matters
This turns Claude Code from an interactive, laptop-bound tool into standing, unattended automation infrastructure — the same shift that took CI/CD from "run it on my box" to "run it on a server." Recurring engineering chores (triage new issues, summarize overnight PRs, run a dependency audit, prep a daily digest) become scheduled agents that run whether or not you are online. It is the operational counterpart to Managed Agents: Managed Agents is the API to build hosted agents; Routines is the productized "cron for Claude Code" for dev teams.

## Your point of view
- "Routines make Claude Code an always-on teammate, not just a session you drive — that's a genuine change in how you operate, not a new feature."
- "The per-day caps mean you pick your highest-value recurring jobs; it's not for spraying dozens of cheap crons."
- "Because runs are cloud-side, the connectors and repo access a routine holds are a real security surface — scope them like a service account."

## What to do
- Identify 1-3 recurring, well-scoped chores (issue triage, PR digest, scheduled report) and convert them to routines via `/schedule`.
- Give each routine only the repo and connectors it needs; review those grants as you would a CI credential.
- Track it against your plan's daily routine cap and prune ones that stop earning their slot.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [dev surfaces](../../../dev-surfaces/)
- [production architecture](../../../production-ops/production-architecture.md)
