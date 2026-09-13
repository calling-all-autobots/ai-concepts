# Keyword Index

Every key term the book covers, grouped by lesson in reading order. A term links to the lesson that defines it **once that lesson is written** — so links appear progressively. Written lessons are marked ✅.

Foundational jargon (model, weights, training, inference, GPU) lives in the [ML vocabulary primer](primers/ml-vocabulary.md).

---

## 1. Foundations

**1. [Tokenization](foundations/tokenization.md) ✅** — token, subword, byte-pair encoding (BPE), vocabulary, token count, token tax

**2. [Embeddings](foundations/embeddings.md) ✅** — embedding, vector, semantic similarity, cosine similarity, embedding model, vector space, multimodal embedding

**3. [Attention](foundations/attention.md) ✅** — self-attention, query / key / value, attention weights, multi-head attention, softmax, long-range dependency, lost in the middle

**4. [Transformers](foundations/transformers.md) ✅** — transformer, feed-forward network (FFN), encoder / decoder / encoder-decoder, positional encoding, next-token prediction, quadratic cost

**5. [Context windows](foundations/context-windows.md) ✅** — context window, token budget, working memory, lost in the middle, long context, window-vs-retrieval

**6. [Pretraining vs. post-training](foundations/pretraining-vs-posttraining.md) ✅** — pretraining, post-training, base model, instruct / chat model, knowledge cutoff, next-token prediction

## 2. Model behavior and training

**7. [Fine-tuning](model-behavior-training/fine-tuning.md) ✅** — fine-tuning, supervised fine-tuning (SFT), catastrophic forgetting, domain adaptation

**8. [PEFT](model-behavior-training/peft.md) ✅** — PEFT (parameter-efficient fine-tuning), adapters, prefix tuning, prompt tuning

**9. [LoRA](model-behavior-training/lora.md) ✅** — LoRA (low-rank adaptation), adapter, low-rank update, frozen weights

**10. [Instruction tuning](model-behavior-training/instruction-tuning.md) ✅** — instruction tuning, instruction dataset, instruction following, chat template

**11. [RLHF](model-behavior-training/rlhf.md) ✅** — RLHF (reinforcement learning from human feedback), reward model, preference data, alignment

**12. [DPO](model-behavior-training/dpo.md) ✅** — DPO (direct preference optimization), preference pairs, reward-model-free

**13. [Distillation](model-behavior-training/distillation.md) ✅** — distillation, teacher model, student model, knowledge transfer

**14. [Quantization](model-behavior-training/quantization.md) ✅** — quantization, precision (FP16 / INT8 / INT4), model compression, accuracy tradeoff

**15. [Mixture of Experts](model-behavior-training/mixture-of-experts.md) ✅** — mixture of experts (MoE), expert, router, sparse activation, active parameters

## 3. Reasoning and generation

**16. [Sampling and decoding](reasoning-generation/sampling-decoding.md) ✅** — temperature, top-p (nucleus), top-k, greedy decoding, determinism

**17. [Chain-of-thought and extended thinking](reasoning-generation/chain-of-thought.md) ✅** — chain-of-thought (CoT), step-by-step, extended thinking, scratchpad

**18. [Reasoning models and test-time compute](reasoning-generation/reasoning-models.md) ✅** — reasoning model, test-time compute, inference-time scaling, thinking tokens

**19. [Hallucination](reasoning-generation/hallucination.md) ✅** — hallucination, confabulation, grounding, factuality

**20. [Structured outputs](reasoning-generation/structured-outputs.md) ✅** — structured output, JSON mode, function schema, constrained decoding

## 4. Retrieval and knowledge (RAG stack)

**21. [RAG](retrieval-knowledge/rag.md) ✅** — retrieval-augmented generation (RAG), retriever, generator, grounding, knowledge base

**22. [Chunking](retrieval-knowledge/chunking.md) ✅** — chunking, chunk size, overlap, splitting strategy

**23. [Vector databases](retrieval-knowledge/vector-databases.md) ✅** — vector database, index, approximate nearest neighbor (ANN), similarity search

**24. [Retrieval](retrieval-knowledge/retrieval.md) ✅** — retrieval, top-k retrieval, recall, relevance

**25. [Hybrid search](retrieval-knowledge/hybrid-search.md) ✅** — hybrid search, keyword search (BM25), dense vs. sparse, fusion

**26. [Reranking](retrieval-knowledge/reranking.md) ✅** — reranking, cross-encoder, relevance score

**27. [Grounding and citations](retrieval-knowledge/grounding-citations.md) ✅** — grounding, citation, attribution, source passage

## 5. Prompting

**28. [Prompt engineering](prompting/prompt-engineering.md) ✅** — prompt, system prompt, instruction, prompt template, delimiters

**29. [Few-shot and in-context learning](prompting/few-shot-icl.md) ✅** — few-shot, zero-shot, in-context learning (ICL), exemplars

**30. [KV caching](prompting/kv-caching.md) ✅** — KV (key/value) cache, decoding speed, memory footprint

**31. [Prompt caching](prompting/prompt-caching.md) ✅** — prompt caching, cache hit, cached prefix

## 6. Agents

**32. [Tool calling / function calling](agents/tool-calling.md) ✅** — tool calling, function calling, tool schema, API call

**33. [MCP](agents/mcp.md) ✅** — Model Context Protocol (MCP), server, tool interoperability

**34. [Agentic systems](agents/agentic-systems.md) ✅** — agent, agentic loop, tool use, autonomy, environment

**35. [Agent memory](agents/agent-memory.md) ✅** — short-term memory, long-term memory, state, scratchpad

**36. [Planning and orchestration](agents/planning-orchestration.md) ✅** — planning, orchestration, task decomposition, workflow

**37. [Multi-agent architectures](agents/multi-agent.md) ✅** — multi-agent, orchestrator, sub-agent, handoff

## 7. Multimodal

**38. [Vision-language models](multimodal/vision-language.md) ✅** — vision-language model (VLM), multimodal, image encoder

**39. [Audio and speech](multimodal/audio-speech.md) ✅** — speech-to-text (STT), text-to-speech (TTS), automatic speech recognition (ASR)

**40. [Multimodal product surfaces](multimodal/multimodal-products.md) ✅** — modality, cross-modal, multimodal input / output

## 8. Safety and trust

**41. [Guardrails](safety-trust/guardrails.md) ✅** — guardrail, input / output filter, policy, moderation

**42. [AI security](safety-trust/ai-security.md) ✅** — prompt injection, jailbreak, data exfiltration, adversarial input

**43. [Privacy and PII](safety-trust/privacy-pii.md) ✅** — personally identifiable information (PII), redaction, data retention

**44. [Responsible AI](safety-trust/responsible-ai.md) ✅** — bias, fairness, transparency, regulation (EU AI Act)

## 9. Evaluation

**45. [Evaluation methods](evaluation/evaluation-methods.md) ✅** — eval, offline eval, human eval, LLM-as-judge

**46. [Benchmarks and their limits](evaluation/benchmarks.md) ✅** — benchmark, leaderboard, contamination, overfitting to the test

**47. [Regression testing](evaluation/regression-testing.md) ✅** — regression test, golden set, eval suite

## 10. Production and operations

**48. [Production LLM architecture](production-ops/production-architecture.md) ✅** — inference server, gateway / router, fallback, orchestration

**49. [Inference optimization](production-ops/inference-optimization.md) ✅** — latency, throughput, batching, streaming

**50. [LLM observability](production-ops/observability.md) ✅** — observability, tracing, logging, monitoring, drift

**51. [Cost and unit economics](production-ops/cost-unit-economics.md) ✅** — cost per query, tokens, gross margin, unit economics

## 11. Product and strategy

**52. [AI product metrics](product-strategy/ai-product-metrics.md) ✅** — deflection rate, acceptance / edit rate, containment, task completion

**53. [Build vs. buy](product-strategy/build-vs-buy.md) ✅** — build vs. buy, API vs. open-source, self-hosting

**54. [Data moats and feedback loops](product-strategy/data-moats.md) ✅** — data moat, feedback loop, proprietary data

**55. [The iron triangle](product-strategy/iron-triangle.md) ✅** — cost / latency / quality tradeoff, the iron triangle
