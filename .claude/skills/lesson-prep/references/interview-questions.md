# Interview Questions: The Stumper Transcript Format

## Rules
- **Stumpers only.** Never include the obvious "what is X?" for the lesson's own topic. If the lesson is on transformers, "what is a transformer?" is banned. Target the questions that expose whether someone actually understands the concept — the *why*, the *tradeoff*, the *failure mode*, the common misconception.
- **Write each as a transcript**, not a Q-with-a-tip. Real questions live inside a conversation with follow-ups. Show the exchange.
- **Every question ends with a rationale** — a `> [!TIP]` box explaining *why the answer is the strong move*. This is the most important part: it turns a memorized line into an understood one. Say what trap the answer avoids, what it signals to the interviewer, and the reasoning that lets the learner respond that way with confidence.
- **Some questions call for a clarify-back.** The strongest candidates don't answer a loaded question immediately — they ask one sharp clarifying question first, which signals seniority and situational awareness. Mark these and format them so the learner can lift each line at a glance. Their rationale box also covers *why clarifying was right*.
- Aim for as many questions as the topic genuinely warrants (typically 4–6). Don't pad.

## Format for a straightforward stumper

```markdown
**Q: "<the interviewer's question>"**

**Interviewer:** <the question, in their voice>
**You:** <the strong answer — lead with the sharp framing, then support it.>

> [!TIP]
> **Why this answer works:** <the reasoning that solidifies it — the trap the
> naive answer falls into, what this response signals, and why it's correct.
> This is what the learner internalizes, not just the words of the answer.>
```

## Format for a clarify-back stumper

Put each turn on its own labeled line, then the rationale box (covering both the clarify move and the answer).

```markdown
**Q (clarify-back): "<the loaded question>"**

**Interviewer:** <the loaded question that has no single right answer>

**You (clarify back):** <the one sharp question you ask before answering>

**Interviewer:** <their answer, which pins down the missing variable>

**You:** <your answer, now that the ambiguity is resolved — show how the
clarification changed the recommendation>

> [!TIP]
> **Why this works:** <why the question was ambiguous and clarifying was the
> right move, what it signals, and why the final answer follows once the
> variable is pinned down.>
```

## Worked example (clarify-back)

```markdown
**Q (clarify-back): "Would you use a bigger context window or retrieval for this?"**

**Interviewer:** We need the assistant to answer from our 400-page policy manual. Bigger context window, or retrieval?

**You (clarify back):** Before I pick — how often does that manual change, and what's my latency and cost budget per query?

**Interviewer:** It's updated most weeks, and responses need to feel snappy.

**You:** Then retrieval. A frequently-changing source means I'd be re-sending a huge static prompt on every call and paying the quadratic attention cost for content that's mostly irrelevant to any one question. Retrieval fetches just the few relevant passages — cheaper, faster, and it stays current when the manual changes without re-loading everything.

> [!TIP]
> **Why this works:** "Bigger window vs. retrieval" has no universal answer — it hinges on data volatility and cost/latency budget, so answering immediately would expose you as someone reciting a rule. Asking pins down the two variables that actually decide it and signals you've shipped this tradeoff before. Once "changes weekly" and "must be snappy" are on the table, retrieval follows directly.
```

## Worked example (straightforward)

```markdown
**Q: "Why were transformers a breakthrough?"**

**Interviewer:** In your own words — why were transformers such a big deal?
**You:** The trap answer is "because of attention." The real reason is what attention *enabled*: because every word is processed in parallel, the architecture fit GPUs, which made it scalable, and scale is what produced the emergent capabilities. So I'd frame it as a chain — architecture to scale to capability.

> [!TIP]
> **Why this answer works:** Most candidates name the mechanism ("attention") and stop, which sounds like they've read a headline. Naming the *causal chain* — parallelism → scale → capability — shows you understand why the mechanism mattered commercially, not just that it exists. It also sets you up to talk about cost and scaling laws if they probe further.
```
