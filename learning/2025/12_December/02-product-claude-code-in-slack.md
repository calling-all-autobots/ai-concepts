# Claude Code in Slack (research preview)

- **Category:** ① Product release
- **Date:** 2025-12-08  ·  **What it affects:** Claude Code (on the web), the Claude app for Slack, developer team workflows
- **Sources:** https://claude.com/blog/claude-code-and-slack  ·  https://www.salesforce.com/news/stories/claude-code-in-slack/

## In one line
You can now `@Claude` a bug report or feature request in Slack and it will spin up a full Claude Code session on the web, do the work, and hand you a link to review changes and open a pull request.

## What actually changed
Launched Dec 8, 2025 as a **research preview (beta)**, built on the existing Claude app for Slack. When you mention `@Claude` in a channel or thread, Claude first reviews the message to decide whether it's a coding task. If it is, it **gathers context from recent channel and thread messages** — stack traces, log fragments, prior discussion, screenshots converted to text — and uses that as the task description.

It then **automatically chooses which repository to work in**, based on the repos you've authenticated to Claude Code on the web, and starts a session at claude.com/code with file-operation and shell tools enabled. Inside that session Claude Code reads files, searches directories, runs tests and CLI tools, applies edits, and iterates. As it works it **posts status updates back to the Slack thread**, and on completion returns a link to the full session (to review changes) plus a direct link to **open a pull request**. Requirements: the Claude app installed from the Slack App Marketplace and access to Claude Code on the web.

## Why it matters
This moves agentic coding to where the bug is actually reported. The friction of "read the Slack thread → figure out the repo → open a terminal → set up context" collapses into a single mention. The context-gathering is the real unlock: the agent pulls the surrounding conversation automatically instead of you re-typing it. It also makes coding-agent work **visible to non-engineers** in the same channel — a PM can watch a fix progress and get the PR link.

## Your point of view
- "This turns Slack into a triage-to-PR pipe: report a bug, tag Claude, get a reviewable PR — no context-switch."
- "It's a research preview — expect rough repo-selection and treat every PR as needing human review, not auto-merge."
- "The strategic point is surface expansion: Claude Code now lives in terminal, IDE, web, and chat. Where your team already works is the new distribution channel."

## What to do
- Install the Claude app from the Slack App Marketplace and authenticate the repos you'd want it to touch on Claude Code on the web.
- Pilot it on low-risk tasks first (small bug fixes, code review, doc edits); keep human review on every generated PR.
- Set a team norm for which channels can invoke it and who approves the resulting PRs, since it can read channel history to build the task.

## Connects to
- [Agentic systems](../../../agents/agentic-systems.md) — a delegated, tool-using agent running an end-to-end task loop.
- [Tool calling](../../../agents/tool-calling.md) — the file/shell tools the Slack-triggered session runs on.
- [SDK / dev surfaces](../../../dev-surfaces/sdk.md) — another surface in Claude Code's expanding footprint (terminal, IDE, web, chat).
