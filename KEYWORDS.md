# Keyword Index

Every key term the book covers, grouped by lesson in reading order. A term links to the lesson that defines it **once that lesson is written** — so links appear progressively. Written lessons are marked ✅.

Foundational jargon (model, weights, training, inference, GPU) lives in the [ML vocabulary primer](primers/ml-vocabulary.md).

---

## 1. Foundations

**1. [Tokenization](01-foundations/01-tokenization.md) ✅** — token, subword, byte-pair encoding (BPE), vocabulary, token count, token tax

**2. [Embeddings](01-foundations/02-embeddings.md) ✅** — embedding, vector, semantic similarity, cosine similarity, embedding model, vector space, multimodal embedding

**3. [Attention](01-foundations/03-attention.md) ✅** — self-attention, query / key / value, attention weights, multi-head attention, softmax, long-range dependency, lost in the middle

**4. [Transformers](01-foundations/04-transformers.md) ✅** — transformer, feed-forward network (FFN), encoder / decoder / encoder-decoder, positional encoding, next-token prediction, quadratic cost

**5. [Context windows](01-foundations/05-context-windows.md) ✅** — context window, token budget, working memory, lost in the middle, long context, window-vs-retrieval

**6. [Pretraining vs. post-training](01-foundations/06-pretraining-vs-posttraining.md) ✅** — pretraining, post-training, base model, instruct / chat model, knowledge cutoff, next-token prediction

## 2. Model behavior and training

**7. [Fine-tuning](02-model-behavior-training/07-fine-tuning.md) ✅** — fine-tuning, supervised fine-tuning (SFT), catastrophic forgetting, domain adaptation

**8. [PEFT](02-model-behavior-training/08-peft.md) ✅** — PEFT (parameter-efficient fine-tuning), adapters, prefix tuning, prompt tuning

**9. [LoRA](02-model-behavior-training/09-lora.md) ✅** — LoRA (low-rank adaptation), adapter, low-rank update, frozen weights

**10. [Instruction tuning](02-model-behavior-training/10-instruction-tuning.md) ✅** — instruction tuning, instruction dataset, instruction following, chat template

**11. [RLHF](02-model-behavior-training/11-rlhf.md) ✅** — RLHF (reinforcement learning from human feedback), reward model, preference data, alignment

**12. [DPO](02-model-behavior-training/12-dpo.md) ✅** — DPO (direct preference optimization), preference pairs, reward-model-free

**13. [Distillation](02-model-behavior-training/13-distillation.md) ✅** — distillation, teacher model, student model, knowledge transfer

**14. [Quantization](02-model-behavior-training/14-quantization.md) ✅** — quantization, precision (FP16 / INT8 / INT4), model compression, accuracy tradeoff

**15. [Mixture of Experts](02-model-behavior-training/15-mixture-of-experts.md) ✅** — mixture of experts (MoE), expert, router, sparse activation, active parameters

## 3. Reasoning and generation

**16. [Sampling and decoding](03-reasoning-generation/16-sampling-decoding.md) ✅** — temperature, top-p (nucleus), top-k, greedy decoding, determinism

**17. [Chain-of-thought and extended thinking](03-reasoning-generation/17-chain-of-thought.md) ✅** — chain-of-thought (CoT), step-by-step, extended thinking, scratchpad

**18. [Reasoning models and test-time compute](03-reasoning-generation/18-reasoning-models.md) ✅** — reasoning model, test-time compute, inference-time scaling, thinking tokens

**19. [Hallucination](03-reasoning-generation/19-hallucination.md) ✅** — hallucination, confabulation, grounding, factuality

**20. [Structured outputs](03-reasoning-generation/20-structured-outputs.md) ✅** — structured output, JSON mode, function schema, constrained decoding

## 4. Retrieval and knowledge (RAG stack)

**21. [RAG](04-retrieval-knowledge/21-rag.md) ✅** — retrieval-augmented generation (RAG), retriever, generator, grounding, knowledge base

**22. [Chunking](04-retrieval-knowledge/22-chunking.md) ✅** — chunking, chunk size, overlap, splitting strategy

**23. [Vector databases](04-retrieval-knowledge/23-vector-databases.md) ✅** — vector database, index, approximate nearest neighbor (ANN), similarity search

**24. [Retrieval](04-retrieval-knowledge/24-retrieval.md) ✅** — retrieval, top-k retrieval, recall, relevance

**25. [Hybrid search](04-retrieval-knowledge/25-hybrid-search.md) ✅** — hybrid search, keyword search (BM25), dense vs. sparse, fusion

**26. [Reranking](04-retrieval-knowledge/26-reranking.md) ✅** — reranking, cross-encoder, relevance score

**27. [Grounding and citations](04-retrieval-knowledge/27-grounding-citations.md) ✅** — grounding, citation, attribution, source passage

## 5. Prompting

**28. [Prompt engineering](05-prompting/28-prompt-engineering.md) ✅** — prompt, system prompt, instruction, prompt template, delimiters

**29. [Few-shot and in-context learning](05-prompting/29-few-shot-icl.md) ✅** — few-shot, zero-shot, in-context learning (ICL), exemplars

**30. [KV caching](05-prompting/30-kv-caching.md) ✅** — KV (key/value) cache, decoding speed, memory footprint

**31. [Prompt caching](05-prompting/31-prompt-caching.md) ✅** — prompt caching, cache hit, cached prefix

## 6. Agents

**32. [Tool calling / function calling](06-agents/32-tool-calling.md) ✅** — tool calling, function calling, tool schema, API call

**33. [MCP](06-agents/33-mcp.md) ✅** — Model Context Protocol (MCP), server, tool interoperability

**34. [Agentic systems](06-agents/34-agentic-systems.md) ✅** — agent, agentic loop, tool use, autonomy, environment

**35. [Agent memory](06-agents/35-agent-memory.md) ✅** — short-term memory, long-term memory, state, scratchpad

**36. [Planning and orchestration](06-agents/36-planning-orchestration.md) ✅** — planning, orchestration, task decomposition, workflow

**37. [Multi-agent architectures](06-agents/37-multi-agent.md) ✅** — multi-agent, orchestrator, sub-agent, handoff

## 7. Multimodal

**38. [Vision-language models](07-multimodal/38-vision-language.md) ✅** — vision-language model (VLM), multimodal, image encoder

**39. [Audio and speech](07-multimodal/39-audio-speech.md) ✅** — speech-to-text (STT), text-to-speech (TTS), automatic speech recognition (ASR)

**40. [Multimodal product surfaces](07-multimodal/40-multimodal-products.md) ✅** — modality, cross-modal, multimodal input / output

## 8. Safety and trust

**41. [Guardrails](08-safety-trust/41-guardrails.md) ✅** — guardrail, input / output filter, policy, moderation

**42. [AI security](08-safety-trust/42-ai-security.md) ✅** — prompt injection, jailbreak, data exfiltration, adversarial input

**43. [Privacy and PII](08-safety-trust/43-privacy-pii.md) ✅** — personally identifiable information (PII), redaction, data retention

**44. [Responsible AI](08-safety-trust/44-responsible-ai.md) ✅** — bias, fairness, transparency, regulation (EU AI Act)

## 9. Evaluation

**45. [Evaluation methods](09-evaluation/45-evaluation-methods.md) ✅** — eval, offline eval, human eval, LLM-as-judge

**46. [Benchmarks and their limits](09-evaluation/46-benchmarks.md) ✅** — benchmark, leaderboard, contamination, overfitting to the test

**47. [Regression testing](09-evaluation/47-regression-testing.md) ✅** — regression test, golden set, eval suite

## 10. Production and operations

**48. [Production LLM architecture](10-production-ops/48-production-architecture.md) ✅** — inference server, gateway / router, fallback, orchestration

**49. [Inference optimization](10-production-ops/49-inference-optimization.md) ✅** — latency, throughput, batching, streaming

**50. [LLM observability](10-production-ops/50-observability.md) ✅** — observability, tracing, logging, monitoring, drift

**51. [Cost and unit economics](10-production-ops/51-cost-unit-economics.md) ✅** — cost per query, tokens, gross margin, unit economics

## 11. Product and strategy

**52. [AI product metrics](11-product-strategy/52-ai-product-metrics.md) ✅** — deflection rate, acceptance / edit rate, containment, task completion

**53. [Build vs. buy](11-product-strategy/53-build-vs-buy.md) ✅** — build vs. buy, API vs. open-source, self-hosting

**54. [Data moats and feedback loops](11-product-strategy/54-data-moats.md) ✅** — data moat, feedback loop, proprietary data

**55. [The iron triangle](11-product-strategy/55-iron-triangle.md) ✅** — cost / latency / quality tradeoff, the iron triangle
