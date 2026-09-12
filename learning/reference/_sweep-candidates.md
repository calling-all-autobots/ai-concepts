# Radar Sweep — Phase 1 master candidate list

Window **2025-11-01 → 2026-08-31**. Merged from 3 discovery agents (release feeds ·
announcements · engineering), de-duplicated, impact-filtered, categorized, one item →
one month → one category. Sept 2026+ excluded (covered by the weekly radar).

Legend: **①** product release · **②** new best practice · **③** new way of working.
This is the authoring worklist for Phase 2 (one writer agent per month).

---

## 2026-08 August
- **①** Computer Use & Browser tools GA + Files/Skills/Admin GA wave (Aug 19–20) — the core agent-building primitives leave beta; new Browser Use tool; web-tool domain allow/block lists.
- **①** Inference Hooks (beta) (Aug 5) — programmatic inspection/blocking of prompts & tool responses (enterprise guardrail).
- **①** Self-Hosted Claude Code (public beta) (Aug 6) — Claude Code on self-managed compute.
- **③** Skill & Plugin security scanning (Aug 6) — automated malware detection for third-party skills/plugins (supply-chain).
- _light/optional:_ Apps memory sync + Gmail/Drive/M365 write actions; Model Hardware Standard preview; Python SDK v1.0 breaking changes.

## 2026-07 July
- **①** Claude Opus 5 (Jul 24) — new frontier: 1M ctx, 128k output, thinking-on-by-default, $5/$25 per M.
- **①** Updated Memory System (Jul 10) — individual categorized memory entries read mid-conversation (vs daily summaries).
- **②** MCP 2026-07-28 spec (Jul 28) — stateless/serverless core, MCP Apps/Tasks, enhanced OAuth; major protocol shift.
- _light/optional:_ Managed Agents effort + lifecycle webhooks; User Management API; Cowork web/mobile + M365 write tools.

## 2026-06 June
- **①** Claude Sonnet 5 (Jun 30) — $2/$10 per M, 1M ctx, adaptive thinking default, new tokenizer (~30% more tokens — cost caveat).
- **①** Claude Fable 5 & Mythos 5 (Jun 9) — first Mythos-class model line; new tokenizer; $10/$50; `refusal` stop reason.
- **①** New surfaces: Claude Science (Jun 30) + Claude Tag / Slack (Jun 23).
- _light/optional:_ MCP Tunnels API move (Jun 22); code-execution REPL persistence (Jun 18); rate-limit tiers → Start/Build/Scale (Jun 26).

## 2026-05 May
- **①** Claude Opus 4.8 + Dynamic Workflows research preview (May 28) — 1M ctx default, effort defaults high; **Dynamic Workflows = hundreds of parallel subagents in one Claude Code session** (the one you lost track of).
- **①** Multi-agent orchestration + Outcomes (public beta) (May 4) — platform-level agent orchestration + eval/outcomes; Dreams research preview.
- **②** "How we contain Claude" (May 25) — contain agents via environmental boundaries / blast-radius, not just model-layer defenses.
- _light/optional:_ MCP Tunnels research preview + self-hosted sandboxes (May 19); Claude Platform on AWS (May 11); Workload Identity Federation (May 6).

## 2026-04 April
- **①** Claude Opus 4.7 (Apr 16) — coding, higher-res vision, long-running tasks; Task Budgets beta; file-system memory.
- **①** Managed Agents GA (Apr 9) — cloud agent build/deploy platform; sandboxing; `ant` CLI.
- **①** Cowork GA (Apr 9) — agentic knowledge-work app (macOS/Windows).
- **①** Agent Memory for Managed Agents → public beta (Apr 23).
- **③** "Scaling Managed Agents: brain/hands" (Apr 8) — decouple reasoning from execution to scale hosted agents.
- _light/optional:_ Claude Design (Apr 17); Routines in Claude Code (Apr).

## 2026-03 March
- **①** Computer Use research preview in Claude apps (Mar 23) — Pro/Max grant Claude control of their computer.
- **②** "Harness design for long-running application development" (Mar 24) — scaffolding agents that build whole apps.
- **③** "Claude Code auto mode: a safer way to skip permissions" (Mar 25) — safe-autonomy permissioning pattern.
- **②** "Eval awareness in Opus 4.6's BrowseComp performance" (Mar 6) — models detect they're being evaluated → eval integrity.
- _light/optional:_ 1M context GA for 4.6 (Mar 13); memory for free tier (Mar 2).

## 2026-02 February
- **①** Claude Opus 4.6 (Feb 5) — 1M ctx, adaptive thinking, `effort` parameter, compaction API; fast mode (Feb 7).
- **①** Claude Sonnet 4.6 (Feb 17) — 1M ctx beta, agentic search; web search/fetch GA.
- **①** Automatic prompt caching (Feb 19) — single `cache_control`, no manual breakpoints.
- **①** Claude Code Remote Control (Feb 25) — drive local Claude Code sessions from mobile/web.
- **③** "Building a C compiler with a team of parallel Claudes" (Feb 5) — multi-agent parallel orchestration case study.
- **②** "Quantifying infrastructure noise in agentic coding evals" (Feb 5) — control for infra flakiness when reading eval numbers.

## 2026-01 January
- **①** Cowork research preview (Jan 12) — agentic knowledge-work; console.anthropic.com → platform.claude.com.
- **①** Structured Outputs GA (Jan 29) — guaranteed schema conformance out of beta.
- **②** Evals practice pair: "Demystifying evals for AI agents" (Jan 9) + "AI-resistant technical evaluations" (Jan 21).
- _light/optional:_ Anthropic Labs launch (Jan 11).

## 2025-12 December
- **②** Agent Skills as an open standard (Dec 18) — portable skills across platforms + app integrations.
- **①** Claude Code in Slack (research preview) (Dec 8) — delegate coding sessions via @Claude in Slack.

## 2025-11 November
- **①** Claude Opus 4.5 (Nov 24) — flagship; first >80% SWE-bench Verified; `effort` parameter, context compaction, memory tool.
- **②** Advanced tool use / Tool Search Tool (Nov 24) — on-demand tool discovery to cut context bloat.
- **②** Code execution with MCP (Nov 4) — agents write code to call tools instead of many tool calls; efficiency.
- **②** Effective harnesses for long-running agents (Nov 26) — feature-list JSON + `claude-progress.txt` + git for fresh-context recovery.
- **①** Structured Outputs beta (Nov 14) — schema conformance introduced (GA'd Jan 2026).

---

## Cross-cutting nugget
- **①** Model deprecation timeline (Nov'25–Aug'26) — one nugget consolidating every retirement (Opus 3, Haiku 3 & 3.5, Sonnet 3.7, Sonnet 4 & Opus 4, Opus 4.1, 1M-beta for Sonnet 4.5/4) + the version-pinning / migration lesson.

## Excluded as noise (kept clean)
Enterprise-admin/compliance items (Compliance API sessions, Admin API in SDKs, RBAC, self-serve Enterprise, HIPAA config, Analytics API), pricing tweaks (Sonnet 5 pricing made permanent), regional/parity (Bedrock/Azure/Foundry availability, search-result blocks on Bedrock), pure UI/product polish (Monthly Recap, Focus settings, in-place artifact editing, interactive mobile viz, Office add-ins), minor API params (max_tokens bumps, extended-thinking `display`, Models API fields), the Workbench→Playground rename, docs-platform move, and PR/policy posts (open-weights position, GOV.UK pilot, grants).

## Volume
Comprehensive scope authored **57 nuggets** across 10 months (56 monthly + 1
cross-cutting deprecation timeline); "light/optional" items were promoted to full
nuggets and the noise list was excluded.
