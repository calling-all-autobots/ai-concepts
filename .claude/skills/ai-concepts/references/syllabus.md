# AI Concepts Syllabus — 55 topics, 11 categories

Each line: global number, topic, and its lesson file path under `E:\ai-concepts`. **Ordering is dependency-clean** — within every category, a lesson only relies on earlier ones, so a newcomer never meets a term before it's taught. Write them in order by default; jump on request. Link related lessons across categories.

## 01-foundations
1. Tokenization and tokens — `01-foundations/01-tokenization.md`
2. Embeddings — `01-foundations/02-embeddings.md`
3. Attention — `01-foundations/03-attention.md`
4. Transformers — `01-foundations/04-transformers.md`
5. Context windows — `01-foundations/05-context-windows.md`
6. Pretraining vs. post-training — `01-foundations/06-pretraining-vs-posttraining.md`

## 02-model-behavior-training
7. Fine-tuning — `02-model-behavior-training/07-fine-tuning.md`
8. PEFT — `02-model-behavior-training/08-peft.md`
9. LoRA — `02-model-behavior-training/09-lora.md`
10. Instruction tuning — `02-model-behavior-training/10-instruction-tuning.md`
11. RLHF — `02-model-behavior-training/11-rlhf.md`
12. DPO — `02-model-behavior-training/12-dpo.md`
13. Distillation — `02-model-behavior-training/13-distillation.md`
14. Quantization — `02-model-behavior-training/14-quantization.md`
15. Mixture of Experts — `02-model-behavior-training/15-mixture-of-experts.md`

## 03-reasoning-generation
16. Sampling and decoding — `03-reasoning-generation/16-sampling-decoding.md`
17. Chain-of-thought and extended thinking — `03-reasoning-generation/17-chain-of-thought.md`
18. Reasoning models and test-time compute — `03-reasoning-generation/18-reasoning-models.md`
19. Hallucination — `03-reasoning-generation/19-hallucination.md`
20. Structured outputs — `03-reasoning-generation/20-structured-outputs.md`

## 04-retrieval-knowledge
21. RAG — `04-retrieval-knowledge/21-rag.md`
22. Chunking — `04-retrieval-knowledge/22-chunking.md`
23. Vector databases — `04-retrieval-knowledge/23-vector-databases.md`
24. Retrieval — `04-retrieval-knowledge/24-retrieval.md`
25. Hybrid search — `04-retrieval-knowledge/25-hybrid-search.md`
26. Reranking — `04-retrieval-knowledge/26-reranking.md`
27. Grounding and citations — `04-retrieval-knowledge/27-grounding-citations.md`

## 05-prompting
28. Prompt engineering — `05-prompting/28-prompt-engineering.md`
29. Few-shot and in-context learning — `05-prompting/29-few-shot-icl.md`
30. KV caching — `05-prompting/30-kv-caching.md`
31. Prompt caching — `05-prompting/31-prompt-caching.md`

## 06-agents
32. Tool calling / function calling — `06-agents/32-tool-calling.md`
33. MCP (Model Context Protocol) — `06-agents/33-mcp.md`
34. Agentic systems — `06-agents/34-agentic-systems.md`
35. Agent memory — `06-agents/35-agent-memory.md`
36. Planning and orchestration — `06-agents/36-planning-orchestration.md`
37. Multi-agent architectures — `06-agents/37-multi-agent.md`

## 07-multimodal
38. Vision-language models — `07-multimodal/38-vision-language.md`
39. Audio and speech — `07-multimodal/39-audio-speech.md`
40. Multimodal product surfaces — `07-multimodal/40-multimodal-products.md`

## 08-safety-trust
41. Guardrails — `08-safety-trust/41-guardrails.md`
42. AI security — `08-safety-trust/42-ai-security.md`
43. Privacy and PII — `08-safety-trust/43-privacy-pii.md`
44. Responsible AI — `08-safety-trust/44-responsible-ai.md`

## 09-evaluation
45. Evaluation methods — `09-evaluation/45-evaluation-methods.md`
46. Benchmarks and their limits — `09-evaluation/46-benchmarks.md`
47. Regression testing for prompts and models — `09-evaluation/47-regression-testing.md`

## 10-production-ops
48. Production LLM architecture — `10-production-ops/48-production-architecture.md`
49. Inference optimization — `10-production-ops/49-inference-optimization.md`
50. LLM observability — `10-production-ops/50-observability.md`
51. Cost and unit economics — `10-production-ops/51-cost-unit-economics.md`

## 11-product-strategy
52. AI product metrics — `11-product-strategy/52-ai-product-metrics.md`
53. Build vs. buy — `11-product-strategy/53-build-vs-buy.md`
54. Data moats and feedback loops — `11-product-strategy/54-data-moats.md`
55. The iron triangle (cost / latency / quality) — `11-product-strategy/55-iron-triangle.md`

## What changed vs. the original order (dependency-clean reorder)
- **Foundations:** tokens → embeddings → attention → transformers → context windows → pretraining (was transformers-first, which forward-referenced tokens/embeddings).
- **Model behavior:** fine-tuning → PEFT → LoRA (family before the flagship method), then instruction tuning → RLHF → DPO (alignment, simplest first), then distillation → quantization → MoE (efficiency).
- **Reasoning/generation:** sampling/decoding first (the generation mechanism), then chain-of-thought, then reasoning models (built on CoT + test-time compute), then hallucination, then structured outputs.
- **Retrieval:** RAG overview first, then the pipeline in order — chunking → vector databases → retrieval → hybrid search → reranking → grounding (was vector-DB before chunking; hybrid placed before reranking so "how to get candidates" precedes "how to reorder them").
- **Prompting:** prompt engineering → few-shot → KV caching (mechanism) → prompt caching (the productized feature built on it).
- **Agents:** tool calling → MCP → agentic systems → agent memory → planning → multi-agent (primitive → standard → loop → state → planning → many agents).
- Categories 7–11 were already dependency-clean; order unchanged.
