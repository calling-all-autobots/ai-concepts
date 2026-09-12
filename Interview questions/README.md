# Interview questions

Mock-interview study documents produced by the **`interview-candidate`** skill.

In each session, Claude plays an exceptionally sharp candidate (~200 IQ, first-principles thinker) and you play the interviewer. When the session ends, the whole exchange is written here as one FAQ document you can revise from.

## How to run it

| Say this | What happens |
|---|---|
| **`start interview`** | Claude enters candidate mode and answers everything in persona — first-principles, mental model first, analogy + example every time, no meta-questions. |
| *(ask your questions)* | Claude answers in-flow. Feed in constraints mid-session ("requirements change", "tokens aren't cheap") and it recalibrates. |
| **`done`** | Claude leaves the persona and **automatically writes this session to a `.md` file here** — no prompting, no "should I save this?". |

## What each file contains

One document per interview arc (not one per question):

- The candidate persona + role lens + any scenario constraints you supplied
- Each Q&A, polished into readable FAQ prose (summarized, not verbatim)
- Diagrams where they help — diagnostic questions get recalibrating elimination trees; design/tradeoff questions get a mental-model diagram
- A **Summary — the through-line** at the end distilling the reusable principles

## Role lens

Defaults to an **AI-native forward-deployed engineer, as a product & design person** (no code/architecture deep-dives). Set a different role at the start of a session to override it, e.g. *"start interview — this is for a senior PM role."*

## Files

- `interview-sim-token-costs.md` — diagnosing rising AI token costs (elimination-tree method)
- `interview-sim-workflows-vs-skills.md` — autonomous workflows vs. skills for ideation → groomed user stories
