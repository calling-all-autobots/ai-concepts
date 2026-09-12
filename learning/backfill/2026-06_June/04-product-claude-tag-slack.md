# Claude Tag — one shared @Claude teammate inside Slack

- **Category:** ① Product release
- **Date:** 2026-06-23  ·  **What it affects:** new product surface (Claude in Slack for Enterprise & Team)
- **Sources:** https://techcrunch.com/2026/06/23/anthropics-claude-tag-is-learning-your-company-one-slack-message-at-a-time/ · https://fortune.com/2026/06/23/anthropic-claude-tag-virtual-employee-tool-slack/

## In one line
Claude Tag puts a single shared @Claude inside a Slack channel that the whole team can hand tasks to and steer together — replacing the old per-user "Claude in Slack" chatbot with a persistent, multiplayer teammate.

## What actually changed
- Launched in **public beta on June 23, 2026** for **Claude Enterprise and Team** customers.
- You **tag @Claude in a channel**, assign a task, and it works through it **in stages** while you do other things; teammates can pick up mid-task, redirect, or delegate in parallel.
- Runs on **Claude Opus 4.8**, using **approved context** from conversations, connected tools, data, and codebases.
- It **replaces the old per-user Claude in Slack app** (the Dec 2025 research preview) with one shared, persistent agent per channel.
- Ships with enterprise controls: **access controls, activity logs, and spending limits**.
- Anthropic says an internal version already **writes 65% of their product team's code**, including much of Claude Tag itself.

## Why it matters
The design shift is from a private assistant to a *shared* teammate: state and task ownership live in the channel, not in one person's DM thread. That changes the collaboration model — work is visible, hand-offable, and parallelizable — but it also raises the governance questions the enterprise controls are meant to answer (who can invoke it, what it can see, how much it can spend). The "65% of our code" claim is the marketing hook, but the real story is agents becoming a first-class participant in team workflows rather than a solo tool.

## Your point of view
- "Claude Tag moves the agent from 'my copilot' to 'the team's teammate' — the unit of work is the channel, not the individual."
- "The interesting part isn't the model (it's Opus 4.8), it's the multiplayer, staged-execution UX plus the enterprise guardrails."
- "Treat activity logs and spend limits as mandatory config, not nice-to-haves — a shared agent with codebase access is a real blast-radius question."

## What to do
1. If on Enterprise/Team, pilot Claude Tag in one channel with scoped context and a spend limit before broad rollout.
2. Migrate off the old per-user Claude in Slack app and set access controls up front.

## Connects to
- [agentic systems](../../../06-agents/34-agentic-systems.md)
- [multi-agent](../../../06-agents/37-multi-agent.md)
- [agent memory](../../../06-agents/35-agent-memory.md)
- [AI security](../../../08-safety-trust/42-ai-security.md)
