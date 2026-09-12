# How we contain Claude — containment via environmental boundaries

- **Category:** ② New best practice
- **Date:** 2026-05-25  ·  **What it affects:** agent security architecture; Claude Code / Cowork / claude.ai builders
- **Sources:** https://www.anthropic.com/engineering/how-we-contain-claude

## In one line
Anthropic's argument that you contain a capable agent by bounding its *environment* (sandboxes, VMs, egress) — deterministic controls that cap maximum damage — not by trusting model-layer behavior, which is probabilistic and will eventually fail.

## What actually changed
This is a guidance post, not a product, but it reframes how to build agents. Its core formula: **risk = likelihood of failure x potential damage ("blast radius")**. As capability grows you can't drive likelihood to zero, so you cap *damage* with the environment. Three overlapping layers, in priority order:
1. **Environment (primary):** process sandbox, VM, filesystem boundaries, egress/output controls — hard limits independent of intent.
2. **Model (secondary):** system prompts, classifiers, probes, training — shaping, but probabilistic.
3. **External content (tertiary):** MCP servers, plugins, web tools — injection surface to restrict and audit.

It ties isolation strength to audience: **claude.ai** uses ephemeral gVisor containers; **Claude Code** uses human-in-the-loop + OS sandbox (and notes approval fatigue); **Cowork** uses VMs with mounted workspaces so non-technical users aren't approving every action. Real failures disclosed: `.claude/settings.json` hooks executing *before* the trust prompt on repo clone; a phishing prompt exfiltrating AWS credentials **24 of 25 times**; an approved domain (Files API) abused with attacker keys despite an egress allowlist; VM isolation blinding endpoint-detection tooling. The stated lesson: **"the weakest layer is the one you built yourself"** — standard hypervisors and syscall filters beat homegrown proxies and classifiers.

## Why it matters
As agents get autonomous enough to run migrations and control machines, "the model refused" stops being a security control. This post is Anthropic conceding that model-layer defenses are a shaping mechanism, and that the deterministic guarantees come from the sandbox. It also reframes allowlists: each permitted domain is a **capability grant** exposing every function reachable there, not merely a destination filter.

## Your point of view
- "Behavioral safety is probabilistic; environmental containment is deterministic. Design for the day the model *does* comply with the attacker."
- "Treat local input — project config, mounted files, `settings.json` — as hostile network input; pre-trust validation is mandatory."
- "Match blast-radius controls to who's driving: developers can tolerate approvals, non-technical users need stronger defaults."

## What to do
- Audit your agents for pre-trust code execution (config/hooks loaded before consent) and gate them.
- Replace custom proxies/classifiers as your *primary* boundary with hypervisor/syscall-level isolation; keep model-layer defenses as defense-in-depth.
- Re-scope egress allowlists as capability grants; assume any reachable API on an allowed domain is exploitable.

## Connects to
- [AI security](../../../08-safety-trust/42-ai-security.md) · [guardrails](../../../08-safety-trust/41-guardrails.md) · [agentic systems](../../../06-agents/34-agentic-systems.md) · [MCP](../../../06-agents/33-mcp.md)
