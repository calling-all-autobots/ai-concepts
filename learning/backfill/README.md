# Anthropic Radar — Historical Backfill (Nov 2025 → Aug 2026)

A one-off catch-up sweep, produced by the [`radar-sweep`](../../.claude/skills/radar-sweep/SKILL.md)
skill (two-phase: discover once → fan out authoring by month). **57 nuggets across
10 months**, each a self-contained knowledge document (what changed · why it matters
· a point of view · what to do), confirmed against official Anthropic sources.

Category legend: **①** product release · **②** new best practice · **③** new way of working.
The vetted source worklist is in [`_candidates.md`](_candidates.md).

## Cross-cutting
- **①** [Model deprecation & retirement timeline](01-cross-cutting-model-deprecations.md) — the whole Claude 3/4 sunset wave in one table + the version-pinning lesson.

## Months (newest first)

| Month | Nuggets | Headlines |
|---|:---:|---|
| [August 2026](2026-08_August/README.md) | 7 | Computer/Browser tools + Files/Skills/Admin **GA wave**; Inference Hooks; self-hosted Claude Code; skill/plugin malware scanning; Python SDK v1.0 |
| [July 2026](2026-07_July/README.md) | 6 | **Claude Opus 5** (~96% SWE-bench, $5/$25); **MCP 2026-07-28** stateless spec; updated memory system; Cowork web/mobile |
| [June 2026](2026-06_June/README.md) | 7 | **Claude Sonnet 5** ($2/$10, tokenizer caveat); **Fable 5 & Mythos 5** + `refusal` stop reason; Claude Science; Claude Tag/Slack |
| [May 2026](2026-05_May/README.md) | 6 | **Opus 4.8 + Dynamic Workflows**; multi-agent orchestration + Outcomes + Dreaming; "How we contain Claude"; MCP tunnels; Claude on AWS |
| [April 2026](2026-04_April/README.md) | 7 | **Opus 4.7** (92.3% SWE-bench, `xhigh`); **Managed Agents** beta + `ant` CLI; **Cowork GA**; Claude Design; Routines in Claude Code |
| [March 2026](2026-03_March/README.md) | 6 | Claude Code **auto mode**; long-running-app harness design; computer use in Claude apps; 1M-context GA; eval-awareness/BrowseComp |
| [February 2026](2026-02_February/README.md) | 6 | **Opus 4.6 & Sonnet 4.6**; **automatic prompt caching**; Claude Code Remote Control; parallel-Claudes C-compiler; infra-noise-in-evals |
| [January 2026](2026-01_January/README.md) | 4 | **Structured Outputs GA**; agent-evals practice pair; **Cowork** research preview; Anthropic Labs |
| [December 2025](2025-12_December/README.md) | 2 | **Agent Skills open standard**; Claude Code in Slack |
| [November 2025](2025-11_November/README.md) | 5 | **Opus 4.5** (80.9% SWE-bench, `effort`); Structured Outputs beta; long-running-agent harnesses; Tool Search Tool; code-execution-with-MCP |

## The through-lines (what to actually take away)
- **Models got cheaper and more agentic fast:** Opus 4.5 → 4.6 → 4.7 → 4.8 → **Opus 5**, plus Sonnet 5 and the Fable/Mythos 5 line — SWE-bench Verified climbed from ~81% to ~96%, and per-token thinking/effort controls became standard.
- **The platform became an agent platform:** Managed Agents, multi-agent orchestration, **Dynamic Workflows**, memory systems, MCP (code-execution, tunnels, the 2026-07 stateless spec), Computer/Browser use, Skills-as-open-standard.
- **"How to build well" hardened into doctrine:** eval design (and eval-gaming), long-running-agent harnesses, environmental containment, tool-search to fight context bloat.
- **Lifecycle is now a first-class risk:** a steady drumbeat of deprecations — see the cross-cutting timeline.

## Sourcing caveats (flagged honestly)
A handful of items had official pages that 404'd or weren't directly fetchable, so they rest on corroborated secondary sources; each such nugget says so inline. Notable: Inference Hooks (Aug), the infra-noise & Remote Control writeups (Feb), Cowork GA page (Apr). Several date conflicts between the aggregator and official pages were resolved to the official date and noted in-nugget (Structured Outputs GA, Anthropic Labs, Workload Identity Federation, Managed Agents beta-vs-GA).
