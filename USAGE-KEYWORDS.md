# Essential Usage Keywords

The practical, operational vocabulary of *building with and talking about* LLM platforms — the terms you meet in a console, an API, or an engineering conversation. This is deliberately separate from the concept lessons and from [KEYWORDS.md](KEYWORDS.md) (which indexes the *what-it-is* topics). Some terms also have a concept lesson; here the entry is the hands-on usage angle. PM-level: enough to use the word correctly and know what it implies.

**Coverage key** (does a concept lesson teach this?):
- ✅ **written** — a finished lesson covers it
- 📋 **#NN** — a planned lesson will cover it
- 🅿️ **parked** — only covered if a proposed [parked addition](#) (Computer use / server-side tools) is added to the syllabus
- ❌ **gap** — not covered anywhere (see [Coverage gaps](#coverage-gaps) below)

## Dev surfaces

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **Workbench / Playground** | A web UI for writing prompts and testing model responses interactively, no code. | Anthropic Console Workbench; OpenAI Playground. | ❌ gap |
| **Console / dashboard** | The provider's web admin area — API keys, usage, billing, logs. | platform.claude.com. | ❌ gap |
| **SDK** | An official code library (Python, TypeScript) that wraps the API so you don't hand-build HTTP calls. | The `anthropic` Python SDK. | ❌ gap |
| **API endpoint** | The URL your code calls to run the model. | The Messages API endpoint. | ❌ gap |
| **API key** | A secret token that authenticates requests and ties usage to your account. | `sk-ant-…` (kept secret, never in client code). | ❌ gap |
| **Rate limits (TPM / RPM)** | Caps on usage — tokens-per-minute and requests-per-minute; exceed them and requests are throttled. | A `429 rate_limit` error that resets shortly. | ❌ gap |
| **Model ID / snapshot / version** | The exact string naming which model and version you call, so behaviour is pinned. | `claude-opus-4-8`. | ❌ gap |

## Request building blocks

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **System prompt / developer message** | Standing instructions setting the model's role and rules, separate from the user's message. | "You are a terse support agent; never discuss competitors." | 📋 #28 |
| **Roles (user / assistant)** | Turn labels in a conversation; the API takes a list of messages tagged by role. | user asks → assistant replies. | 📋 #28 (✅ #10) |
| **Generation params** | Knobs controlling how text is sampled: temperature (randomness), top-p / top-k (candidate pool), max tokens (length cap), stop sequences (cut-off). | temperature 0 for the most predictable output. | ✅ #16 |
| **Seed** | A fixed random seed for more reproducible sampling run-to-run (best-effort, not guaranteed). | Same seed + temperature 0 → near-identical output. | ✅ #16 |
| **Streaming (SSE)** | Delivering the answer token-by-token as it's generated, so the UI shows text appearing live. | The "typing" effect in a chat UI. | 📋 #49 |
| **Batch / async API** | Submitting many requests to run offline within a window, usually at a large discount, instead of real-time. | Overnight classification of 100k records at ~50% cost. | 📋 #51 |

## Tools & agents

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **Function / tool calling** | The model emits a structured request to call a tool you defined; your code runs it and feeds the result back. | Model asks to call `get_weather("Paris")`. | 📋 #32 |
| **Tool schema** | The JSON description of a tool's name, purpose, and parameters that you hand the model so it knows how to call it. | A schema for `search_orders(customer_id)`. | 📋 #32 |
| **MCP / connectors** | Model Context Protocol — an open standard for plugging tools and data sources into a model uniformly. | An MCP server exposing your internal database. | 📋 #33 |
| **Harness / agent runtime** | The scaffolding around the model that runs the loop — calls the model, executes tools, manages state and memory, retries — turning a single call into an agent. | The loop that lets an agent keep acting until a task is done. | 📋 #37 |
| **Orchestration loop** | The control flow deciding the sequence of model and tool steps. | Plan → call tool → observe → repeat. | 📋 #36 |
| **Sandbox / code execution** | An isolated environment where model-generated code runs safely. | A code-interpreter that runs Python on an uploaded CSV. | 🅿️ parked |
| **Computer use** | A capability where the model controls a computer via screenshots plus mouse/keyboard actions. | Filling a form in a desktop app. | 🅿️ parked |
| **Browser use** | The model driving a web browser to navigate and read pages. | Looking up a fact on a live site. | 🅿️ parked |
| **Web search / fetch tool** | Built-in tools letting the model search the web or fetch a URL at answer time. | Grounding an answer in a current article. | 🅿️ parked |

## Knowledge & caching

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **Embeddings endpoint** | An API that turns text into vectors for semantic search and retrieval. | Embedding a knowledge base for search. | ✅ #2 |
| **Vector store** | A database that stores embeddings and returns nearest matches. | Pinecone, pgvector, a managed vector DB. | 📋 #23 |
| **RAG** | Retrieval-augmented generation — fetch relevant passages and put them in the prompt so the model answers from them. | A support bot answering from your docs. | ✅ #21 |
| **Prompt caching / cached prefix** | Reusing the model's processing of an unchanged prompt prefix across calls to cut cost and latency. | Caching a long system prompt reused on every request. | 📋 #31 |
| **KV cache** | The model's internal cache of past tokens' key/value vectors during generation, so it doesn't recompute them each step. | Why generating token 500 doesn't re-read tokens 1–499. | 📋 #30 |

## Tuning & ops

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **Fine-tune job** | A managed training run that adapts a base model on your data, producing a custom model ID. | A model tuned to your ticket-reply style. | ✅ #7 |
| **Eval suite** | A repeatable set of test cases plus scoring to measure model or prompt quality. | 200 graded cases run on every prompt change. | 📋 #45 |
| **LLM-as-judge** | Using a model to grade another model's outputs against criteria. | Scoring answer helpfulness 1–5 automatically. | 📋 #45 |
| **Guardrails / moderation** | Filters and policies on inputs and outputs that block unsafe or off-policy content. | Blocking a jailbreak attempt before it reaches the model. | 📋 #41 |
| **Observability / tracing** | Logging each request, tool call, latency, and cost so you can debug and monitor production. | A trace showing why an agent looped 12 times. | 📋 #50 |
| **Latency / throughput / p95 / TTFT** | Speed metrics — time per request, requests-per-second, the 95th-percentile (tail) latency, and time-to-first-token. | "p95 latency 4s; TTFT 300ms." | 📋 #49 |

## Cost & reliability

| Term | What it means | Example | Coverage |
|------|---------------|---------|:--------:|
| **Cost per token (input vs output)** | You pay per token, usually with output priced higher than input. | Estimating a feature's per-request cost. | 📋 #51 |
| **Batch discount** | Reduced price for async batch processing. | ~50% off for non-real-time jobs. | 📋 #51 |
| **Retries / backoff** | Re-sending failed or throttled requests with increasing delays. | Exponential backoff after a 429. | ❌ gap |
| **Fallback model** | Automatically switching to another model when the primary fails or is slow. | Falling back to a cheaper model on timeout. | 📋 #48 |
| **Timeouts** | Cutting off a request that runs too long, including streaming idle timeouts. | Aborting a stuck generation at 30s. | ❌ gap |

---

## Coverage gaps

Terms **not** covered by any written or planned lesson. To resolve in the syllabus sweep.

### ❌ Uncovered — genuine gaps (no lesson, not parked)

**Dev-surface / API mechanics** — absent because the syllabus is concept-first, not platform-onboarding:
- Workbench / Playground
- Console / dashboard
- SDK
- API endpoint
- API key
- Rate limits (TPM / RPM)
- Model ID / snapshot / version

**Production plumbing** — borderline; could be folded into #48 Production architecture rather than taught:
- Retries / backoff
- Timeouts

### 🅿️ Parked — covered only if the proposed topic is added

Depend on adding the parked **"Computer use / server-side tools"** topic (see the `syllabus-2026-doc-review-additions` note):
- Sandbox / code execution
- Computer use
- Browser use
- Web search / fetch tool

### Suggested resolution (for the sweep)
1. Add the parked **Computer use / server-side tools** topic → clears all four 🅿️ items.
2. Decide on the **dev-surface / API mechanics** cluster: either a short "Working with the API" reference lesson, or accept it as out-of-scope for a concept book and let USAGE-KEYWORDS carry it.
3. Fold **retries / timeouts** into #48 and re-tag them here.
