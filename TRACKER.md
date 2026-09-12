# Tracker — Change Registry

Work status for the [study book](README.md). This is for managing the work; the [README](README.md) is for reading it.

**Progress: 28 / 55 written and passed the eval gate.** (Categories 1–2 complete and fully to standard: dependency-clean order, Mermaid diagrams, per-answer rationales, and the "one analogy to remember" section in every lesson. On disk: 1–19, 21, 22, 23, 29, 30, 31, 32, 33, 34. Category 3 needs only 20 (structured outputs); concurrent sessions also advancing categories 4/6.)

Legend: ☐ not started · ◧ drafting · ☑ written + passed `lesson-eval`

| # | Topic | Status | Passed eval | Notes |
|---|-------|:------:|:-----------:|-------|
| 1 | Tokenization and tokens | ☑ | ✅ | LEGO analogy |
| 2 | Embeddings | ☑ | ✅ | city-map analogy |
| 3 | Attention | ☑ | ✅ | cocktail-party analogy |
| 4 | Transformers | ☑ | ✅ | reworked as capstone; editorial-team analogy |
| 5 | Context windows | ☑ | ✅ | whiteboard analogy |
| 6 | Pretraining vs. post-training | ☑ | ✅ | library-then-manners analogy |
| 7 | Fine-tuning | ☑ | ✅ | journalist house-style analogy |
| 8 | PEFT | ☑ | ✅ | glasses + clip-on analogy |
| 9 | LoRA | ☑ | ✅ | blueprint + tracing-paper analogy |
| 10 | Instruction tuning | ☑ | ✅ | new-hire + binder analogy |
| 11 | RLHF | ☑ | ✅ | chef taste-test analogy |
| 12 | DPO | ☑ | ✅ | editor's-folder analogy |
| 13 | Distillation | ☑ | ✅ | sommelier analogy |
| 14 | Quantization | ☑ | ✅ | price-list rounding analogy |
| 15 | Mixture of Experts | ☑ | ✅ | hospital-triage analogy |
| 16 | Sampling and decoding | ☑ | ✅ | weighted-dice analogy |
| 17 | Chain-of-thought and extended thinking | ☑ | ✅ | scratchpad / show-your-working analogy |
| 18 | Reasoning models and test-time compute | ☑ | ✅ | chess study-vs-clock analogy |
| 19 | Hallucination | ☑ | ✅ | never-says-"I-don't-know" trivia-friend analogy |
| 20 | Structured outputs | ☐ | | |
| 21 | RAG | ☑ | ✅ | open-book consultant analogy; category-4 opener |
| 22 | Chunking | ☑ | ✅ | textbook-to-flashcards analogy |
| 23 | Vector databases | ☑ | ✅ | coffee-shop map-app / ANN analogy |
| 24 | Retrieval | ☑ | ✅ | recruiter/résumé analogy; similarity≠relevance |
| 25 | Hybrid search | ☐ | | (swapped with reranking) |
| 26 | Reranking | ☐ | | (swapped with hybrid search) |
| 27 | Grounding and citations | ☐ | | |
| 28 | Prompt engineering | ☐ | | |
| 29 | Few-shot and in-context learning | ☑ | ✅ | temp-worker-with-sample-forms analogy |
| 30 | KV caching | ☑ | ✅ | corkboard-of-index-cards analogy |
| 31 | Prompt caching | ☑ | ✅ | prep-kitchen base-steps analogy |
| 32 | Tool calling / function calling | ☑ | ✅ | consultant + request-slip analogy; category 6 opener |
| 33 | MCP (Model Context Protocol) | ☑ | ✅ | USB-C-for-AI-tools analogy |
| 34 | Agentic systems | ☑ | ✅ | intern-with-a-goal vs. checklist analogy |
| 35 | Agent memory | ☑ | ✅ | Memento amnesiac + desk + filing-cabinet analogy |
| 36 | Planning and orchestration | ☐ | | |
| 37 | Multi-agent architectures | ☐ | | |
| 38 | Vision-language models | ☐ | | |
| 39 | Audio and speech | ☐ | | |
| 40 | Multimodal product surfaces | ☐ | | |
| 41 | Guardrails | ☐ | | |
| 42 | AI security | ☐ | | |
| 43 | Privacy and PII | ☐ | | |
| 44 | Responsible AI | ☐ | | |
| 45 | Evaluation methods | ☐ | | |
| 46 | Benchmarks and their limits | ☐ | | |
| 47 | Regression testing | ☐ | | |
| 48 | Production LLM architecture | ☐ | | |
| 49 | Inference optimization | ☐ | | |
| 50 | LLM observability | ☐ | | |
| 51 | Cost and unit economics | ☐ | | |
| 52 | AI product metrics | ☐ | | |
| 53 | Build vs. buy | ☐ | | |
| 54 | Data moats and feedback loops | ☐ | | |
| 55 | The iron triangle | ☐ | | |

- **2026-09-12** — **Category 3 started. Lesson 16 (Sampling and decoding)** written and passed `lesson-eval` (14/14). Covers logits→softmax→decoding, greedy vs. sampling, temperature, top-k/top-p, beam search, repetition/stop controls, and the determinism/reproducibility product lens; weighted-dice analogy. 16/55.

- **2026-09-12** — **Category 3 continued: Chain-of-thought and extended thinking (17)** written and passed eval (14/14). Scoped as the CoT *behavior/technique* + the extended-thinking *feature*: why intermediate tokens help (more compute per token + autoregressive scratchpad + serialized decomposition), zero-shot → few-shot → trained reasoning spectrum, self-consistency (majority vote over sampled chains), and tradeoffs (latency/cost, not-always-better, faithfulness gap, hiding the raw chain). Reasoning models + test-time compute (18) linked not taught; few-shot (29), sampling (16), pretraining (06) linked. scratchpad/show-your-working analogy.

- **2026-09-12** — **Category 3 continued: Reasoning models and test-time compute (18)** written and passed eval (14/14). Scoped as the model *class* + the test-time-compute *scaling principle*: two axes of capability (train-time baked-in-once vs. test-time bought-per-query), reasoning models as same-architecture transformers post-trained (typically RL on verifiable math/code) to reason and use a budget, the forms of test-time compute (longer chains / parallel sampling+voting / search+verification), diminishing returns, when-not-to-reason, route-by-difficulty, and the cost shift to per-query inference. CoT/self-consistency/extended-thinking (17) linked not taught; RLHF contrast → (11); unit economics → (51). chess study-vs-clock analogy.

- **2026-09-12** — **Category 3 continued: Hallucination (19)** written and passed eval (14/14). Scoped as the *failure mode*, framed as intrinsic not a bug: four roots (objective is plausibility-not-truth, no internal knowledge boundary, training-data limits, alignment/RLHF rewarding confident answers→sycophancy cousin), the flavors (factual fabrication, fabricated citations, faithfulness failures with docs present, fluent-but-wrong reasoning), the manage-don't-cure toolkit (RAG grounding, citations, permit "I don't know," low temp for facts, task constraint, evals+human review), and product truths (can't be zeroed, confidence is uncalibrated, grounding changes the failure not removes it, why it's not "lying"). RAG (21), grounding/citations (27), RLHF (11), temperature (16), CoT (17), evals (45), pretraining (06) all linked, not taught. trivia-friend-who-can't-say-"I-don't-know" analogy.

## Changelog
- **2026-09-12** — **Category 4: Retrieval (24) written and passed eval (14/14), + order swap 25↔26.** Retrieval scoped as query-time logic — embed-query/score/top-k/threshold, cosine-vs-dot-vs-Euclidean (direction not magnitude), top-k as the recall dial, query rewriting/expansion, Recall@k/Precision@k/MRR — anchored on the *similarity ≠ relevance* thesis (similar-but-not-relevant → reranking; relevant-but-not-similar → hybrid). Reranking/hybrid/vector-DB/chunking/embeddings all linked, not taught (removed a leaked "cross-encoder" ref → deferred to reranking). recruiter/résumé analogy. **Swap:** per user request, Hybrid search is now **25** and Reranking is now **26** (flow: get candidates → reorder them); applied to README, syllabus (+ "what changed" note), tracker rows, and all cross-links in lessons 21/23/24. Files 25/26 unwritten, so this was a plan renumber only.
- **2026-09-12** — **Category 6 continued: Agent memory (35) written and passed eval (14/14).** Scoped as state *around* the stateless model — memory is a system you build, not a model feature; short-term (=context window, ephemeral) vs. long-term (external store, persists); long-term memory ≈ RAG over the agent's own experience; the write/read cycle as designed policies; window management via summarization (lossy) or retrieval; episodic/semantic/procedural taxonomy kept light; tradeoffs (what-to-remember is curation, stale memory persists+poisons→needs invalidation, retrieval quality caps it, per-step token cost, persistence=PII decision). Agentic (34), context windows (05), RAG (21), vector DBs (23), prompt caching (31), PII (43) linked, not taught. Memento-amnesiac + desk + filing-cabinet analogy. Category 6 needs only 36, 37.
- **2026-09-12** — **Category 5 (reverse) continued: Few-shot and in-context learning (29) written and passed eval (14/14).** Scoped as ICL + the shot vocabulary — zero/one/few-shot spectrum; in-context learning as inference-time, weights-frozen, ephemeral pattern-completion (mechanism flagged as still-debated, not stated as fact); few-shot teaches *task/format, not facts*; few-shot-vs-fine-tuning decision on volume × stability; examples-are-the-spec sensitivity (quality, selection, order/majority-label bias, diminishing returns). Prompt engineering (28), fine-tuning (07), RAG (21), prompt caching (31), context windows (05), attention (03), pretraining (06) all linked, not taught. temp-worker-with-sample-forms analogy. Category 5 now needs only 28 (Prompt engineering).
- **2026-09-12** — **Category 6 continued: Agentic systems (34) written and passed eval (14/14).** Scoped as the loop itself — an LLM in a loop with tools + a goal, reason→act→observe→repeat; the defining property is *autonomy over control flow* (model decides steps + when to stop); workflow↔agent as a spectrum with the "least autonomy that works" rule; compounding error as the signature failure (0.95^10≈60%), plus unpredictability, multiplied cost/latency, runaway loops and execution-layer guardrails. Tool calling (32), CoT (17), memory (35), planning (36), multi-agent (37), prompt caching (31), AI-security (42) all linked, not taught. intern-with-a-goal vs. checklist analogy. On disk now 1–17, 21, 22, 30, 31, 32, 33, 34 = **23/55**.
- **2026-09-12** — **Category 5 (reverse) continued: KV caching (30) written and passed eval (14/14).** Scoped as the within-a-generation mechanism — the autoregressive recompute waste; cache K and V (not Q, which is consumed once); prefill (parallel, compute-bound, sets TTFT) vs. decode (sequential, memory-bandwidth-bound, sets tok/s); the KV cache as the *memory* bottleneck growing linearly with context length × batch → context-vs-throughput tradeoff; GQA/MQA/PagedAttention/sliding-window/KV-quant as cache-shrinking fixes (depth deferred to inference-optimization 49); lossless vs. lossy distinction. Attention Q/K/V (03), autoregressive loop (16), prompt caching (31), quantization (14) all linked, not taught. corkboard-of-index-cards analogy. On disk now 1–16, 21, 22, 30, 31, 32, 33 = **21/55**.
- **2026-09-12** — **Category 6 continued: MCP (33) written and passed eval (14/14).** Scoped as the standard *around* tool calling, not a model capability — the N×M→N+M integration problem; "USB-C for AI tools"; host/client + server + protocol roles; dynamic discovery as the new trick vs. hardcoded schemas; tools/resources/prompts at overview depth only; tradeoffs (security as active-code-with-access + injected resources, standardizes access not judgment, young standard, extra moving part). Tool calling (32), prompt injection/AI-security (42), context windows (05) linked, not taught. On disk now 1–16, 21, 31, 32, 33 = **20/55**.
- **2026-09-12** — **Category 5 started in reverse order: Prompt caching (31) written and passed eval (14/14).** Scoped as the productized, persisted form of the KV cache — same mechanism, wider scope (across requests vs. within one generation); the prefix rule and stable-to-variable ordering; three-price economics (write premium ~1.25–2×, read ~90% off) as a break-even bet on reuse; TTL/minimum-length/best-effort operational rules; latency (prefill-skip) win; agent-loop and long-chat as ideal workloads; cache-hit-rate as the metric. KV caching (30), few-shot (29), RAG (21), retrieval (24), tool calling (32), context windows (05), agents (34) all linked, not taught. prep-kitchen base-steps analogy. On disk now 1–16, 21, 31, 32 = **19/55**.
- **2026-09-12** — **Category 6 started: Tool calling / function calling (32) written and passed eval (14/14).** Scoped as the category opener — the model *requests*, your code *executes*; the tool-calling loop; learned-in-post-training tool selection driven by descriptions; failure modes (wrong tool / hallucinated args / silent non-call / multiplied latency+cost / security of untrusted tool calls); consultant-and-request-slip analogy. Agents/MCP/multi-agent/structured-outputs/hallucination/prompt-caching/AI-security all linked out, not taught inline. **Note:** written concurrently with other sessions; on-disk passed lessons are now 1–15, 16, 21, 32 = **18/55** (the per-lesson "16/55" stamps below are racy and predate this).
- **2026-09-11** — Scaffold created (README ToC, this tracker, 11 folders, ML vocabulary primer). Lesson 1 (Transformers) written and passed `lesson-eval`.
- **2026-09-11** — Category 1 written in parallel (5 Opus writer agents), independent reviewer pass (consistency + links verified).
- **2026-09-11** — Standard revised: ASCII → **Mermaid** diagrams; **every** interview Q&A carries a `[!TIP]` rationale; vocab primer reworked (Mermaid + grouped tables with Example column); added `KEYWORDS.md`. All 6 category-1 lessons retrofitted.
- **2026-09-11** — **Dependency-clean reorder of the whole syllabus** (see `syllabus.md`). Foundations renumbered tokens → embeddings → attention → transformers → context windows → pretraining; categories 2–6 resequenced; files renamed and all cross-links rewritten.
- **2026-09-11** — New standard: one memorable **analogy** per lesson (Picture → Mapping → **Why it holds** → Say it like this → Where it breaks). Added the analogy section to all 6 category-1 lessons and **reworked Transformers** into a capstone (assumes tokens/embeddings/attention; added the "why depth builds abstraction" section + editorial-team analogy).
- **2026-09-12** — **Category 4 started: RAG (21) written and passed eval.** User chose to jump to category 4 (retrieval) ahead of category 3 (reasoning, 16–20), which is deferred. RAG scoped as the category opener — retrieve-then-generate architecture, RAG-vs-fine-tuning decision, the "retrieval quality caps answer quality" iron law, and what RAG doesn't fix — with chunking/vector-DBs/retrieval/reranking/hybrid-search/grounding all linked out, not taught inline. 16/55.
- **2026-09-12** — **Category 2 complete (9 lessons, 7–15).** Written by two parallel Opus waves (fine-tuning, PEFT, LoRA, instruction tuning, RLHF; then DPO, distillation, quantization, MoE), each self-passing all 14 rubric items. Reviewer pass done in-session (the Opus reviewer agent hit the session limit): links verified, concept ownership confirmed (low-rank→LoRA, reward model→RLHF, DPO contrasts not re-teaches), nine analogies distinct. 15/55.
