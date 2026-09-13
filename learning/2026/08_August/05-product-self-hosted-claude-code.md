# Self-hosted environments for Claude Code (public beta)

- **Category:** ① Product release
- **Date:** 2026-08-06  ·  **What it affects:** where Claude Code sessions execute — your own compute instead of Anthropic-hosted infra; Team & Enterprise plans
- **Sources:** https://claude.com/blog/run-claude-code-sessions-on-your-own-compute · https://www.unite.ai/claude-code-sessions-can-now-run-on-infrastructure-your-team-controls/ · https://dev.classmethod.jp/en/articles/claude-code-self-hosted-runner/

## In one line
Claude Code sessions can now run inside your own network on machines you control, so code, secrets, and build artifacts never leave your infrastructure.

## What actually changed
Public beta opened Aug 6, 2026 (Claude Code v2.1.224, Aug 7, added the feature). The model mirrors self-hosted CI runners: an **environment** is a named destination created in admin settings that groups a set of **runners** — long-lived processes deployed on hosts inside your network that pick up sessions. A single command, `claude self-hosted-runner`, turns your machines or containers into that compute layer. Sessions can be launched from web, mobile, desktop, or a routine, and then execute next to your internal services, toolchains, and security controls. Repository checkouts, build artifacts, secrets, and any files a session creates or modifies stay on machines you provision. Available to Team and Enterprise customers in public beta.

## Why it matters
This removes the biggest blocker to Claude Code adoption in regulated and security-conscious orgs: "your proprietary code and secrets touch a vendor's cloud." With self-hosted runners, the agent's reasoning still uses Anthropic inference, but execution — checkout, build, file writes — happens on infrastructure the customer governs, next to existing network controls and compliance boundaries. It reframes Claude Code from a hosted tool into deployable infrastructure.

## Your point of view
- This is the compliance unlock: the answer to "we can't let code leave our network" is now "the runner is in your network."
- The CI-runner mental model is the right one — reason about it like GitHub self-hosted runners: capacity, isolation, and who can register a runner all become your responsibility.
- Inference still goes to Anthropic; self-hosting execution is not the same as self-hosting the model, so the data-flow story for prompts still matters.

## What to do
- If code-egress rules blocked Claude Code, pilot self-hosted environments: stand up a runner with `claude self-hosted-runner`, define an environment in admin settings, and route sensitive-repo sessions to it.
- Treat runners as privileged infra — scope network access, isolate them, and control who can register one.
- Confirm the inference data path separately; self-hosting execution doesn't change where prompts are processed.

## Connects to
- [agentic systems](../../../agents/agentic-systems.md)
- [production architecture](../../../production-ops/production-architecture.md)
- [AI security](../../../safety-trust/ai-security.md)
