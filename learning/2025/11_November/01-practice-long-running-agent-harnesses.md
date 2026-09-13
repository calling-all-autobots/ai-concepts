# Effective harnesses for long-running agents

- **Category:** ② New best practice
- **Date:** 2025-11-26  ·  **What it affects:** agent scaffolding / long-horizon coding agents (the harness around the model, not the model)
- **Sources:** https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents

## In one line
For an agent that has to work for hours or days, the durable state lives *outside* the context window — in a feature-list JSON, a `claude-progress.txt` log, and git — so any fresh session can pick up exactly where the last one left off.

## What actually changed
Anthropic published its playbook for building agents that survive far longer than one context window. The pattern splits work across two roles: an **initializer agent** (first session) that scaffolds the project, and a **coding agent** (every session after) that makes incremental progress. The state that lets a context-less session resume:

- **A feature list as structured JSON** — hundreds of entries (the demo, a claude.ai clone, had "over 200 features"), each like `{"category":"functional","description":"New chat button creates a fresh conversation","steps":[...],"passes":false}`. Agents may edit only the `passes` field; descriptions and tests are frozen. The prompt is explicit: *"It is unacceptable to remove or edit tests because this could lead to missing or buggy functionality."*
- **`claude-progress.txt`** — a running human-readable log of what happened between sessions.
- **Git** — descriptive commits after every change, so a bad step can be reverted to a known-good state; each session runs `git log --oneline -20` to reorient.

Each fresh session follows a fixed recovery protocol: run `pwd`, read git log + progress file, pick the highest-priority incomplete feature, run `init.sh` to start the dev server, run end-to-end tests before writing anything new, and only mark a feature `passing` after verifying it end-to-end with browser automation (e.g. Puppeteer MCP) as a human would.

## Why it matters
The context window is the wrong place to store long-horizon memory — it gets compacted, truncated, or simply ends. This post reframes reliability as an **externalized-state problem**: the model is stateless and disposable; the harness (files + git + tests) is what persists. That is why the "one feature per session, leave the repo clean and mergeable" discipline matters — every session boundary is a potential crash, so the environment must always be recoverable.

## Your point of view
- The moat for long-running agents isn't a smarter model — it's the harness. Durable state in files/git beats bigger context windows.
- Frozen tests are the safety rail: the agent grades itself against criteria it cannot rewrite, which prevents "declaring victory" by deleting the failing check.
- Treat every agent session as recoverable-from-scratch. If a new session with zero memory can't resume from your repo, your harness is incomplete.

## What to do
- For any multi-hour agent build, scaffold three artifacts before coding: a feature-list JSON with a boolean `passes` per item, a `claude-progress.txt`, and a git repo with an `init.sh` bootstrap.
- Write a session-start prompt that forces the recovery sequence (orient via git log + progress, pick one feature, verify end-to-end, commit).
- Make the agent verify through the real UI (browser automation), not by asserting success in prose.

## Connects to
- [agent memory](../../../agents/agent-memory.md)
- [agentic systems](../../../agents/agentic-systems.md)
- [planning & orchestration](../../../agents/planning-orchestration.md)
