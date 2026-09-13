# Claude Code Remote Control — drive your local terminal session from phone or browser

- **Category:** ① Product release
- **Date:** 2026-02-25  ·  **What it affects:** Claude Code (CLI), Claude mobile app (iOS/Android), claude.ai/code web
- **Sources:** https://simonwillison.net/2026/Feb/25/claude-code-remote-control/ · https://docs.claude.com/en/docs/claude-code/overview

## In one line
Claude Code Remote Control lets you start a coding session on your laptop and then steer that same live session from your phone or a browser, while all the code and tools stay on the local machine.

## What actually changed
Anthropic shipped Remote Control as a research preview (Feb 24–25, 2026). You enable it with `claude remote-control`, the `--remote-control` flag, or `/remote-control` inside an existing session; the terminal prints a QR code you scan with the Claude mobile app, or a session URL you open at claude.ai/code. It is a synchronization layer, not a relocation: the session keeps running on your local machine the whole time, and files, MCP servers, environment variables, and project config all stay local. Only chat messages and tool results flow through an encrypted bridge. The conversation stays in sync across terminal, browser, and phone — you can type into any of them interchangeably. It rolled out to Max first, then Pro; Team and Enterprise were not covered at launch. Practical constraints: it depends on the local terminal staying alive, and it is single-user.

## Why it matters
The long-running-agent workflow has a babysitting problem: you kick off a multi-minute task, then you are chained to the desk to answer the next permission prompt or clarifying question. Remote Control breaks that tether without moving your secrets or code to the cloud — the security model (local files, encrypted bridge for chat/tool-results only) is the whole point, and it is what makes this safe to adopt where a fully cloud-hosted agent would not be. It turns "start it and wait" into "start it and check in from anywhere."

## Your point of view
- This is a workflow-ergonomics release, not a capability one: same model, same repo, new control surface. The value is reclaiming the dead time during long agent runs.
- The design choice that matters is "session stays local, only chat/tool-results bridged" — that is the answer to the obvious security objection, and worth saying out loud.
- Treat it as preview-grade: single-user and terminal-dependent, so it is for individual dev flow, not shared/team automation yet.

## What to do
- If you are on Max or Pro, try it on a real long-running task: start locally, `/remote-control`, scan the QR, and approve the next tool call from your phone.
- Don't design team processes around it yet (no Team/Enterprise support at launch, single-user).

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [planning & orchestration](../../../agents/planning-orchestration.md)
- [the SDK & dev surfaces](../../../dev-surfaces/sdk.md)
