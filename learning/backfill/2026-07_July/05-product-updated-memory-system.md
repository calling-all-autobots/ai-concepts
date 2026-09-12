# Claude's memory becomes individual, categorized entries read mid-conversation

- **Category:** ① Product release
- **Date:** 2026-07-10  ·  **What it affects:** Claude apps memory (Free / Pro / Max), Settings > Memory
- **Sources:** https://support.claude.com/en/articles/12138966-release-notes

## In one line
Claude's memory shifted from a once-a-day rolled-up summary to a set of individual, categorized entries that Claude reads and updates *during* your conversations.

## What actually changed
Per Anthropic's release notes for 2026-07-10: "Memory on Claude now works as a set of individual, categorized entries that Claude reads and updates during your conversations, replacing the previous daily memory summary." The practical differences:
- **Specific facts persist as specific facts.** A stated preference (e.g. "concise answers, no preamble") becomes its own categorized entry rather than being blended into a daily average and competing for space with everything else from that day.
- **Read/updated mid-conversation**, not batched into a nightly summary — so newly learned facts are available and editable within the same session.
- **Granular management.** Entries are listed under Topics in Settings > Memory, where you can edit or delete any single item without wiping everything Claude knows about you.
- A companion feature, **Reflect** (Settings > Reflect, launched 2026-07-09, beta on Free/Pro/Max, web + desktop, requires memory on), surfaces the topics you spent time on, your most active day and peak hour, and observations about how you work.

## Why it matters
A daily summary is lossy and hard to correct: individual facts get averaged out, and you can't fix one thing without touching the whole blob. Discrete, categorized entries make memory *inspectable, correctable, and surgically deletable* — which is both a quality win (Claude retains the right specifics) and a trust/privacy win (you can see and remove exactly what it knows). Reading mid-conversation also tightens the loop between "you told Claude something" and "Claude acts on it."

## Your point of view
- The shift from summary to entries is really about *controllability* — memory you can audit item-by-item is far more trustworthy than an opaque summary.
- This is the consumer-app analog of how agent memory should work: structured, categorized, individually addressable records beat a single rolling context blob.
- Editable/deletable per-entry memory is a privacy feature as much as a quality one — worth calling out when people worry about what Claude "remembers."

## What to do
- Open Settings > Memory and review your Topics; delete stale or wrong entries directly rather than resetting all memory.
- When you want a preference to stick, state it explicitly so it lands as its own entry.
- If you build memory features, treat this as a design pattern: prefer categorized, individually editable entries over a single summarized context.

## Connects to
- [Agent memory](../../../06-agents/35-agent-memory.md)
- [Privacy & PII](../../../08-safety-trust/43-privacy-pii.md)
