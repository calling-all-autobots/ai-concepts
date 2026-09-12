---
name: radar-sweep
description: One-off historical backfill of the Anthropic learning radar over a date range (e.g. Nov 2025 – Aug 2026). Uses a two-phase orchestrator-worker design — discover once, then fan out the authoring — to avoid re-fetching the same source pages. Reuses the anthropic-radar nugget standard. Use when the user wants to sweep/backfill past Anthropic changes over a span of months, not the ongoing weekly digest (that's anthropic-radar).
---

# Radar Sweep — historical backfill (two-phase)

For catching up on a **range** of past months at once. The ongoing weekly job is
[`anthropic-radar`](../anthropic-radar/SKILL.md); this skill is the one-off
catch-up. It shares that skill's **impact filter, categories, and
self-contained-nugget quality bar** — read that skill's §4 and §5 and apply them
verbatim. This file only adds the *orchestration*.

## Numbering rule (always)

Every numbered nugget file starts at **`01`** and counts up. **Never use `00`** —
for any file, ever. Cross-cutting reference docs (e.g. the model-deprecation
timeline) live in `learning/reference/` with descriptive names — not `00-`.

## The core efficiency principle

**Fan out on the unit of real, non-overlapping work — never on time-slices or
categories.** Anthropic's sources are chronological feeds; fetching them
per-month or per-category just re-reads the same pages. Impactful items are
sparse (~2–5/month). So:

- **Discovery fetches each source ~once** for the whole window.
- **Categories are labels assigned after reading — never a separate search.**
- **Parallelism is spent only on authoring** (each impactful item is independent
  work with its own confirmation fetch).

## Inputs

- **Window:** start date … end date (inclusive). Walk months **backward** from
  the end (most recent first) so output arrives newest-first.
- **Output layout:** `learning/<year>/<MM_Month>/` — one folder per month, with the
  nuggets directly inside (historical months have no weekly sub-folders). Cross-
  cutting reference docs go in `learning/reference/`.

---

## Phase 1 — Discovery (fetch once, filter, categorize)

Run a small set of **discovery agents in parallel — one per source group**, not
per month. Source groups:

1. **Release feeds** — https://docs.claude.com/en/release-notes/overview (API,
   Claude Apps, Claude Code, System Prompts) + https://releasebot.io/updates/anthropic
   (and /claude, /claude-code, /claude-developer-platform) as a dated cross-check.
2. **Announcements** — https://www.anthropic.com/news
3. **Engineering / practices** — https://www.anthropic.com/engineering

Each discovery agent returns a **dated candidate list** for the window:
`{date, title, one-line description, canonical URL, first-guess category}`.
Tell them to skip obvious noise (patch bumps, wording/UI tweaks) but **not** to
over-filter — final filtering is central.

**Central merge (orchestrator does this):**
- Combine all candidates; de-dup by canonical URL / title / date (a launch shows
  up in several feeds — keep one).
- Apply the **anthropic-radar impact filter** strictly (impactful only).
- Assign each kept item **exactly one category** and **exactly one month**
  (by publication date) so nothing is written twice.
- Produce the **master kept list**, grouped by month, newest month first.

**Checkpoint:** show the master list to the user before Phase 2 — authoring is the
expensive part, and the list is the cheapest place to correct an impact call.

## Phase 2 — Authoring (fan out here)

Fan out **writer agents, one per month that has kept items** (skip empty months).
Each writer:
- receives *only its month's kept list* (title + date + URL + category),
- **confirms each item against its official source** (one fetch per item),
- writes one nugget per item to `learning/<year>/<MM_Month>/NN-<category>-<slug>.md`
  using the anthropic-radar §5 format and bar (In one line / What actually
  changed / Why it matters / Your point of view / What to do / Connects to).
  A backfill month nugget is THREE levels below the repo root, so lesson links use
  `../../../` (e.g. `../../../06-agents/33-mcp.md`),
- writes that month's `monthly-summary.md` — the living monthly newsletter:
  `# <Month Year> — Monthly Summary`, a `_last updated dd/mm/yyyy_` line, a
  `**This month:**` one-line narrative, then the ①②③ sections linking its nuggets
  with one-line hooks,
- returns a one-line-per-nugget summary.

Keep writer agents independent — no shared files between them except their own
month folder. This is what makes the fan-out safe and parallel.

## Phase 3 — Aggregation (orchestrator, single writer)

After all writers finish:
- Write the cross-cutting reference nugget(s) yourself (e.g. the model-deprecation
  timeline) into `learning/reference/` — a doc there is TWO levels below the repo
  root, so its lesson links use `../../`.
- Write/refresh the year index `learning/<year>/README.md` (months newest-first)
  and the top-level `learning/README.md`.
- Record the swept window in `learning/.radar-state.json` (`swept_ranges`) and merge
  notable items into `seen` so the weekly job never re-reports them. This is the
  **only** place state is written — writers never touch it.
- Commit locally to a branch `radar/sweep-<start>_<end>`. **Do not push** unless
  the user asks. Report the totals (months covered, nuggets by category,
  excluded count).

## Guardrails

- Confirm impactful items against the official source before writing — no
  aggregator-only claims in a nugget.
- Honest zeros: a month with nothing impactful gets a one-line note, not filler.
- If a source is unreachable, note it and proceed with the rest.
- Respect the workflow-size guideline: prefer ≤ ~15 agents total. Group thin
  months into one writer if needed rather than spawning near-empty agents.
