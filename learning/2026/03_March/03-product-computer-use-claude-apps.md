# Computer Use research preview in Claude apps

- **Category:** ① Product release
- **Date:** 2026-03-23  ·  **What it affects:** Claude Cowork and Claude Code in the Desktop app (macOS + Windows); Pro/Max plans
- **Sources:** https://claude.com/blog/dispatch-and-computer-use

## In one line
Pro and Max subscribers can now let Claude take over their actual computer — pointing, clicking and navigating the screen — inside Cowork and Claude Code, as a fallback when no direct integration exists.

## What actually changed
Computer use, previously an API-only capability for developers, arrived in the consumer Claude apps as a research preview on Mar 23, 2026. In Cowork and Claude Code within the Claude Desktop app, Claude can point, click, and navigate what is on your screen to finish a task — opening files, driving the browser, running dev tools — with no setup per task. It is a **fallback of last resort**: Claude first reaches for direct connectors (Slack, Google Calendar, etc.) and only drives the screen when it lacks the right tool, because screen control is slower and complex tasks sometimes need a second attempt. It runs on **macOS and Windows** (not just Mac), requires enabling in Desktop settings, and needs the app kept awake and running. It pairs with **Dispatch**, the mobile hand-off tool from the week prior: you assign a task from your phone and Claude executes it on your computer while you are away — e.g. build a morning briefing, make IDE changes and open a PR. Safeguards include automatic scanning of the model's internal activations to detect prompt-injection-style activity, explicit per-application permission grants, and a user stop control; Anthropic advises against giving it access to sensitive data during the preview.

## Why it matters
This is the general-purpose escape hatch for the long tail of software that has no API or MCP server. It turns "Claude can use tools we integrated" into "Claude can use anything on your screen," which massively widens what an agent can accomplish — and equally widens the attack surface, which is why the injection-detection and permission gating are front and center.

## Your point of view
- Computer use is the universal adapter for un-integrated software — but treat it as the slow, brittle fallback, not the default path; a real connector beats screen-driving every time.
- The security model is the whole story: an agent with mouse and keyboard plus a prompt-injection vector is a serious blast-radius problem — keep it away from credentials and sensitive files in preview.
- Dispatch + computer use is the "delegate from your phone" pattern maturing — watch it as the shape of consumer agents.

## What to do
Try it on low-stakes, API-less workflows in a throwaway or non-sensitive context. Keep secrets and financial/PII data off the screen while it runs. Prefer building or wiring an MCP/connector for anything you will automate repeatedly.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [tool calling](../../../agents/tool-calling.md)
- [MCP](../../../agents/mcp.md)
- [AI security](../../../safety-trust/ai-security.md)
