# AI Concepts Syllabus — 59 topics, 12 categories

Each line: topic and its lesson file path under `E:\ai-concepts`. **Lessons and folders carry no number** — reading order lives here and in the README ToC, and lessons are referred to **by title**. **Ordering is dependency-clean** — within every category, a lesson only relies on earlier ones, so a newcomer never meets a term before it's taught. Write them in order by default; jump on request. Link related lessons across categories.

## Foundations
1. Tokenization and tokens — `foundations/tokenization.md`
2. Embeddings — `foundations/embeddings.md`
3. Attention — `foundations/attention.md`
4. Transformers — `foundations/transformers.md`
5. Context windows — `foundations/context-windows.md`
6. Pretraining vs. post-training — `foundations/pretraining-vs-posttraining.md`

## Model behavior and training
1. Fine-tuning — `model-behavior-training/fine-tuning.md`
2. PEFT — `model-behavior-training/peft.md`
3. LoRA — `model-behavior-training/lora.md`
4. Instruction tuning — `model-behavior-training/instruction-tuning.md`
5. RLHF — `model-behavior-training/rlhf.md`
6. DPO — `model-behavior-training/dpo.md`
7. Distillation — `model-behavior-training/distillation.md`
8. Quantization — `model-behavior-training/quantization.md`
9. Mixture of Experts — `model-behavior-training/mixture-of-experts.md`

## Reasoning and generation
1. Sampling and decoding — `reasoning-generation/sampling-decoding.md`
2. Chain-of-thought and extended thinking — `reasoning-generation/chain-of-thought.md`
3. Reasoning models and test-time compute — `reasoning-generation/reasoning-models.md`
4. Hallucination — `reasoning-generation/hallucination.md`
5. Structured outputs — `reasoning-generation/structured-outputs.md`

## Retrieval and knowledge (RAG stack)
1. RAG — `retrieval-knowledge/rag.md`
2. Chunking — `retrieval-knowledge/chunking.md`
3. Vector databases — `retrieval-knowledge/vector-databases.md`
4. Retrieval — `retrieval-knowledge/retrieval.md`
5. Hybrid search — `retrieval-knowledge/hybrid-search.md`
6. Reranking — `retrieval-knowledge/reranking.md`
7. Grounding and citations — `retrieval-knowledge/grounding-citations.md`

## Prompting
1. Prompt engineering — `prompting/prompt-engineering.md`
2. Few-shot and in-context learning — `prompting/few-shot-icl.md`
3. KV caching — `prompting/kv-caching.md`
4. Prompt caching — `prompting/prompt-caching.md`

## Agents
1. Tool calling / function calling — `agents/tool-calling.md`
2. MCP (Model Context Protocol) — `agents/mcp.md`
3. Agentic systems — `agents/agentic-systems.md`
4. Agent memory — `agents/agent-memory.md`
5. Planning and orchestration — `agents/planning-orchestration.md`
6. Multi-agent architectures — `agents/multi-agent.md`

## Multimodal
1. Vision-language models — `multimodal/vision-language.md`
2. Audio and speech — `multimodal/audio-speech.md`
3. Multimodal product surfaces — `multimodal/multimodal-products.md`

## Safety and trust
1. Guardrails — `safety-trust/guardrails.md`
2. AI security — `safety-trust/ai-security.md`
3. Privacy and PII — `safety-trust/privacy-pii.md`
4. Responsible AI — `safety-trust/responsible-ai.md`

## Evaluation
1. Evaluation methods — `evaluation/evaluation-methods.md`
2. Benchmarks and their limits — `evaluation/benchmarks.md`
3. Regression testing for prompts and models — `evaluation/regression-testing.md`

## Production and operations
1. Production LLM architecture — `production-ops/production-architecture.md`
2. Inference optimization — `production-ops/inference-optimization.md`
3. LLM observability — `production-ops/observability.md`
4. Cost and unit economics — `production-ops/cost-unit-economics.md`

## Product and strategy
1. AI product metrics — `product-strategy/ai-product-metrics.md`
2. Build vs. buy — `product-strategy/build-vs-buy.md`
3. Data moats and feedback loops — `product-strategy/data-moats.md`
4. The iron triangle (cost / latency / quality) — `product-strategy/iron-triangle.md`

## Agent engineering
1. Tool design — `agent-engineering/tool-design.md`
2. Harness engineering — `agent-engineering/harness-engineering.md`
3. Loop engineering — `agent-engineering/loop-engineering.md`
4. Memory architecture — `agent-engineering/memory-architecture.md`

## What changed vs. the original order (dependency-clean reorder)
- **Foundations:** tokens → embeddings → attention → transformers → context windows → pretraining (was transformers-first, which forward-referenced tokens/embeddings).
- **Model behavior:** fine-tuning → PEFT → LoRA (family before the flagship method), then instruction tuning → RLHF → DPO (alignment, simplest first), then distillation → quantization → MoE (efficiency).
- **Reasoning/generation:** sampling/decoding first (the generation mechanism), then chain-of-thought, then reasoning models (built on CoT + test-time compute), then hallucination, then structured outputs.
- **Retrieval:** RAG overview first, then the pipeline in order — chunking → vector databases → retrieval → hybrid search → reranking → grounding (was vector-DB before chunking; hybrid placed before reranking so "how to get candidates" precedes "how to reorder them").
- **Prompting:** prompt engineering → few-shot → KV caching (mechanism) → prompt caching (the productized feature built on it).
- **Agents:** tool calling → MCP → agentic systems → agent memory → planning → multi-agent (primitive → standard → loop → state → planning → many agents).
- Categories 7–11 were already dependency-clean; order unchanged.
- **Agent engineering (new, 12th category):** the "how you wield the model" cluster — tool design (craft on top of tool calling) → harness engineering (the scaffolding that runs the agent) → loop engineering (control flow inside the harness) → memory architecture (systems-level state design, building on agent memory). Placed as its own category so the four are studied together rather than scattered through the agents category.
