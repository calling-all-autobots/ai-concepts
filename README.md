# AI Concepts — Interview Study Book

A structured, read-it-like-a-book study set for an AI-heavy product manager interview. Depth target: **conceptual clarity — explain it, defend the choice, know the failure mode.** Assumes no ML background; every prerequisite term is explained inline.

Lessons are ordered so you can read top-to-bottom without meeting a term before it's taught.

New to the vocabulary? Start with the [ML vocabulary primer](primers/ml-vocabulary.md). Every term the book defines is listed in the [Keyword index](KEYWORDS.md).

**Where things stand:** see the [Tracker](TRACKER.md) (change registry — what's done, what's left).

---

## Table of Contents

### 1. Foundations — how models work
1. [Tokenization and tokens](foundations/tokenization.md)
2. [Embeddings](foundations/embeddings.md)
3. [Attention](foundations/attention.md)
4. [Transformers](foundations/transformers.md)
5. [Context windows](foundations/context-windows.md)
6. [Pretraining vs. post-training](foundations/pretraining-vs-posttraining.md)

### 2. Model behavior and training
1. [Fine-tuning](model-behavior-training/fine-tuning.md)
2. [PEFT](model-behavior-training/peft.md)
3. [LoRA](model-behavior-training/lora.md)
4. [Instruction tuning](model-behavior-training/instruction-tuning.md)
5. [RLHF](model-behavior-training/rlhf.md)
6. [DPO](model-behavior-training/dpo.md)
7. [Distillation](model-behavior-training/distillation.md)
8. [Quantization](model-behavior-training/quantization.md)
9. [Mixture of Experts](model-behavior-training/mixture-of-experts.md)

### 3. Reasoning and generation
1. [Sampling and decoding](reasoning-generation/sampling-decoding.md)
2. [Chain-of-thought and extended thinking](reasoning-generation/chain-of-thought.md)
3. [Reasoning models and test-time compute](reasoning-generation/reasoning-models.md)
4. [Hallucination](reasoning-generation/hallucination.md)
5. [Structured outputs](reasoning-generation/structured-outputs.md)

### 4. Retrieval and knowledge (RAG stack)
1. [RAG](retrieval-knowledge/rag.md)
2. [Chunking](retrieval-knowledge/chunking.md)
3. [Vector databases](retrieval-knowledge/vector-databases.md)
4. [Retrieval](retrieval-knowledge/retrieval.md)
5. [Hybrid search](retrieval-knowledge/hybrid-search.md)
6. [Reranking](retrieval-knowledge/reranking.md)
7. [Grounding and citations](retrieval-knowledge/grounding-citations.md)

### 5. Prompting
1. [Prompt engineering](prompting/prompt-engineering.md)
2. [Few-shot and in-context learning](prompting/few-shot-icl.md)
3. [KV caching](prompting/kv-caching.md)
4. [Prompt caching](prompting/prompt-caching.md)

### 6. Agents
1. [Tool calling / function calling](agents/tool-calling.md)
2. [MCP (Model Context Protocol)](agents/mcp.md)
3. [Agentic systems](agents/agentic-systems.md)
4. [Agent memory](agents/agent-memory.md)
5. [Planning and orchestration](agents/planning-orchestration.md)
6. [Multi-agent architectures](agents/multi-agent.md)

### 7. Multimodal
1. [Vision-language models](multimodal/vision-language.md)
2. [Audio and speech](multimodal/audio-speech.md)
3. [Multimodal product surfaces](multimodal/multimodal-products.md)

### 8. Safety and trust
1. [Guardrails](safety-trust/guardrails.md)
2. [AI security](safety-trust/ai-security.md)
3. [Privacy and PII](safety-trust/privacy-pii.md)
4. [Responsible AI](safety-trust/responsible-ai.md)

### 9. Evaluation
1. [Evaluation methods](evaluation/evaluation-methods.md)
2. [Benchmarks and their limits](evaluation/benchmarks.md)
3. [Regression testing for prompts and models](evaluation/regression-testing.md)

### 10. Production and operations
1. [Production LLM architecture](production-ops/production-architecture.md)
2. [Inference optimization](production-ops/inference-optimization.md)
3. [LLM observability](production-ops/observability.md)
4. [Cost and unit economics](production-ops/cost-unit-economics.md)

### 11. Product and strategy
1. [AI product metrics](product-strategy/ai-product-metrics.md)
2. [Build vs. buy](product-strategy/build-vs-buy.md)
3. [Data moats and feedback loops](product-strategy/data-moats.md)
4. [The iron triangle](product-strategy/iron-triangle.md)

### 12. Agent engineering — how you wield the model
1. [Tool design](agent-engineering/tool-design.md)
2. Harness engineering *(coming)*
3. Loop engineering *(coming)*
4. Memory architecture *(coming)*

---

## Appendix — Dev surfaces (usage tier)

Operational, platform-facing vocabulary — the surfaces and mechanics of *building with* an LLM, kept separate from the concept syllabus. See the [Dev surfaces index](dev-surfaces/README.md) and the practical [usage keyword index](USAGE-KEYWORDS.md).

- [Workbench / Playground](dev-surfaces/workbench-playground.md)
- [Console / dashboard](dev-surfaces/console-dashboard.md)
- [SDK](dev-surfaces/sdk.md)
- [API endpoint](dev-surfaces/api-endpoint.md)
- [API key](dev-surfaces/api-key.md)
- [Rate limits (TPM / RPM)](dev-surfaces/rate-limits.md)
- [Model ID / snapshot / version](dev-surfaces/model-id-versioning.md)
