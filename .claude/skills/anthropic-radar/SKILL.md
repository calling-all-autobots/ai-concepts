---
name: anthropic-radar
description: Weekly "learning radar" that scans Anthropic's official sources for what changed, keeps only impactful items (new models, major capabilities, new products, meaningful best-practice or ways-of-working shifts — never minor patch notes), writes short categorized learning nuggets into a week-scoped folder under learning/, and commits them to a dated branch. Use whenever the user wants their Anthropic weekly digest / learning radar run or set up, or invokes /anthropic-radar.
---

# Anthropic Radar — weekly learning digest

Keep the user current on Anthropic **without manual effort**. Every run produces a
short, categorized set of "learning nuggets" for the current Mon–Sun week and
commits them to a dated branch for review.

The user is a product manager studying AI concepts (see the study book in this
repo). Nuggets are written for that audience: what changed, why it matters to a
PM, and what to do about it — not raw changelog text.

## Non-negotiables (the whole point of this skill)

1. **Only impactful items.** The user explicitly wants this kept clean. When in
   doubt, **exclude** and log it in the digest's "Excluded this scan" list.
2. **Only what's new since the last run.** Use the state file to diff. Never
   re-report something already covered in a previous week.
3. **Every kept item gets a category** (§4) and follows the nugget format (§5).
4. **Push to a dated branch, never to `main`.** The user reviews and merges.

---

## 1. Load state

Read `learning/.radar-state.json`. It records what has already been reported:

```json
{
  "last_run": "YYYY-MM-DD",
  "seen": {
    "<stable-id-or-url>": { "date": "YYYY-MM-DD", "week": "YYYY-Www", "title": "..." }
  }
}
```

- If the file is missing, treat this as the first run: create it, and only look
  back ~4 weeks so the first digest isn't a firehose.
- `seen` keys should be stable: a canonical URL, a release-notes anchor, a model
  ID, or `source|title|date` if nothing better exists.

## 2. Compute the current week

- Week = Monday → Sunday. Get today's date, find that week's Monday and Sunday.
- Folder name: `learning/<ISO-year>-W<ISO-week>_<MonDD>-<MonDD>/`
  e.g. `learning/2026-W37_Sep07-Sep13/`.
- Keep a `dd/mm/yyyy` string of "today" for the commit/branch (user's format).

## 3. Scan the sources

Fetch each source (WebSearch to find, WebFetch to read). Collect **candidate**
items with a title, date, one-line description, and canonical URL. Don't filter
yet — just gather everything dated since `last_run`.

**Primary — monitor for changes (highest signal):**
- Release notes hub — https://docs.claude.com/en/release-notes/overview
  (has separate API, Claude Apps, Claude Code, System Prompts streams)
- Anthropic News — https://www.anthropic.com/news
- Anthropic Engineering — https://www.anthropic.com/engineering
- Models overview + deprecations — https://docs.claude.com/en/docs/about-claude/models/overview
- Claude Code docs/changelog — https://docs.claude.com/en/docs/claude-code/overview

**Aggregator (fast cross-check of what shipped):**
- https://releasebot.io/updates/anthropic (and its /claude, /claude-code,
  /claude-developer-platform sub-pages). Useful for a dated list; always confirm
  impactful items against the official source before writing a nugget.

**Learn-from (deeper reading, cite when relevant):**
- Anthropic Academy — https://www.anthropic.com/learn · Courses — https://github.com/anthropics/courses
- Cookbooks — https://github.com/anthropics/claude-cookbooks
- Prompt engineering — https://docs.claude.com/en/docs/build-with-claude/prompt-engineering/overview

URLs migrated from `docs.anthropic.com` → `docs.claude.com`; if one redirects,
follow it and update this list.

## 4. Filter for impact, then categorize

Apply the filter to every candidate. **This is the core value — be strict.**

**INCLUDE (impactful):**
- New model, or a model update that changes capability/price/limits
  (context window, output limit, thinking, tool use, vision, pricing tier)
- A genuinely new product or product surface (a new agent product, a new API
  capability, a new Claude Code capability class — e.g. plugins, skills, MCP)
- A **deprecation / breaking change / sunset** the user must act on
- A **materially new recommended practice** (an Anthropic engineering post or
  docs guidance that changes how you'd build — e.g. context engineering,
  effective agents, evals guidance)
- A **new way of working** (a workflow/tooling shift — e.g. as-code deployment,
  long-running-agent harnesses, orchestration/dynamic-workflow patterns)

**EXCLUDE (noise — log, don't nugget):**
- Point/patch releases and minor version bumps with no new capability
- Bug fixes, wording/docs tweaks, UI polish, telemetry/admin knob changes
- Regional availability, pricing-parity-across-clouds, small quota changes
- Anything you can't confirm against an official source
- Anything already in `seen`

**Category (exactly one per kept item):**
- **① Product release** — new/updated model, new product or product surface,
  major new API/Claude Code capability, deprecation.
- **② New best practice** — a recommended technique or guidance shift for
  building *better* with existing capabilities.
- **③ New way of working** — a workflow/tooling/process shift in *how* you build
  or operate (as-code, harnesses, orchestration, new dev surfaces).

If an item is impactful but fits none cleanly, prefer ① for capabilities and ③
for process. If unsure it's impactful at all → exclude.

Aim for **quality over volume**: a typical week is 0–5 nuggets. Zero is a valid,
honest result — write the digest saying "no impactful changes this week" and
still list what was excluded.

## 5. Write the nuggets — self-contained knowledge documents

**The bar (this is the whole point).** Each nugget must be a *self-contained
knowledge document*: after reading only this file, the user can hold and defend
a point of view on the topic in a conversation, without opening anything else.
That means:
- **Explain the "why," in full.** Never say "awareness item," "note this," or
  "confirm the details yourself." Do the confirming and the reasoning *for* them.
- **Be specific.** Real numbers, quoted specifics, model IDs, prices, benchmark
  deltas, exact command/field names. Vague = failed nugget.
- **Give a point of view.** Tell them what to think and what to say — the take
  they'd bring to a meeting — not just what happened.
- **Be actionable.** State the concrete change/action, not "keep an eye on it."

Before writing an impactful item, **confirm it against the official source**
(docs.claude.com, the announcement, the release notes) and gather the specifics
you need to write it fully. If you genuinely can't get enough to write a
self-contained doc, say so *inside the nugget* with what you do know and the
exact open question — don't hand the user homework.

Write each kept item to a file in the week folder:
`NN-<category-slug>-<short-slug>.md` (category-slug =
`product` | `practice` | `ways-of-working`). Format:

**Numbering rule (always):** `NN` starts at **01** and counts up — `01, 02, 03…`.
**Never use `00`**, for any file, ever — including cross-cutting or "special"
nuggets. If a file feels like it belongs "before" the rest, it's still `01`.

```markdown
# <Title>

- **Category:** ① Product release   <!-- ② New best practice / ③ New way of working -->
- **Date:** <YYYY-MM-DD>  ·  **What it affects:** <model ID / product / API surface>
- **Sources:** <official URL(s)>

## In one line
<A sentence you could say out loud to explain what this is.>

## What actually changed
<The specifics — numbers, prices, benchmark deltas, quoted behavior, command/
field names. Concrete enough to reason from.>

## Why it matters
<The reasoning: the implication, the tradeoff, what it unlocks or breaks, who it
affects. Enough that the user understands, not just knows.>

## Your point of view
<2–4 crisp take-away statements the user can bring to a conversation — the
opinion, the "so what," the nuance. Written as things they could say.>

## What to do
<Concrete action(s) / change(s). Real steps, not "be aware." If genuinely
nothing to do yet, say why and what would trigger action.>

## Connects to
<Relevant study-book lesson links, e.g. [prompt caching](../../05-prompting/31-prompt-caching.md).>
```

Target ~250–450 words per nugget — long enough to stand alone, tight enough to
read in two minutes. Depth and a clear POV beat brevity here.

## 6. Write the week digest — `learning/<week>/README.md`

```markdown
# Anthropic Radar — Week of <MonDD>–<MonDD>, <YYYY> (<ISO-week>)

_Scanned <dd/mm/yyyy>. Sources: release notes, Anthropic News, Engineering, docs._

**This week: N impactful item(s).**

## ① Product releases
- [<Title>](NN-product-<slug>.md) — one-line hook.

## ② New best practices
- [<Title>](NN-practice-<slug>.md) — one-line hook.

## ③ New ways of working
- [<Title>](NN-ways-of-working-<slug>.md) — one-line hook.

## Excluded this scan (kept clean)
- <item> — <why excluded, e.g. "Claude Code v2.1.269 patch — no new capability">
```

Also keep/update a top-level `learning/README.md` index that lists every week
folder newest-first (create it if missing).

## 7. Update state

Add every **kept** item to `seen` (and impactful items you deliberately deferred).
It's fine to also record notable excluded items so they don't resurface.
Set `last_run` to today. Write `learning/.radar-state.json`.

## 8. Commit to a dated branch

- Branch: `radar/<yyyy-mm-dd>` (ISO date sorts well).
- Stage only `learning/`.
- Commit message:
  ```
  Anthropic radar — <dd/mm/yyyy>

  <N> new nugget(s):
  - [①/②/③] <Title>
  - ...
  Excluded <M> minor item(s). Week <ISO-week> (<MonDD>–<MonDD>).
  ```
- Push the branch to `origin` (never `main`). Do **not** open a PR unless asked.
- Report back to the user: the branch name, the count by category, and the
  one-line hooks, so they can decide whether to merge.

## Running unattended (cloud routine)

This skill is invoked by a weekly Monday cloud routine as well as manually. When
unattended: complete all steps including the branch push, and make the final
message a self-contained summary (branch + nuggets + excluded count) since no one
is watching live. If a source is unreachable, note it in the digest and proceed
with the rest rather than aborting.
