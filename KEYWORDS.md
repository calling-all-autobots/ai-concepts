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

**7. Fine-tuning** — fine-tuning, supervised fine-tuning (SFT), catastrophic forgetting, domain adaptation

**8. PEFT** — PEFT (parameter-efficient fine-tuning), adapters, prefix tuning, prompt tuning

**9. LoRA** — LoRA (low-rank adaptation), adapter, low-rank update, frozen weights

**10. Instruction tuning** — instruction tuning, instruction dataset, instruction following, chat template

**11. RLHF** — RLHF (reinforcement learning from human feedback), reward model, preference data, alignment

**12. DPO** — DPO (direct preference optimization), preference pairs, reward-model-free

**13. Distillation** — distillation, teacher model, student model, knowledge transfer

**14. Quantization** — quantization, precision (FP16 / INT8 / INT4), model compression, accuracy tradeoff

**15. Mixture of Experts** — mixture of experts (MoE), expert, router, sparse activation, active parameters

## 3. Reasoning and generation

**16. Sampling and decoding** — temperature, top-p (nucleus), top-k, greedy decoding, determinism

**17. Chain-of-thought and extended thinking** — chain-of-thought (CoT), step-by-step, extended thinking, scratchpad

**18. Reasoning models and test-time compute** — reasoning model, test-time compute, inference-time scaling, thinking tokens

**19. Hallucination** — hallucination, confabulation, grounding, factuality

**20. Structured outputs** — structured output, JSON mode, function schema, constrained decoding

## 4. Retrieval and knowledge (RAG stack)

**21. RAG** — retrieval-augmented generation (RAG), retriever, generator, grounding, knowledge base

**22. Chunking** — chunking, chunk size, overlap, splitting strategy

**23. Vector databases** — vector database, index, approximate nearest neighbor (ANN), similarity search

**24. Retrieval** — retrieval, top-k retrieval, recall, relevance

**25. Reranking** — reranking, cross-encoder, relevance score

**26. Hybrid search** — hybrid search, keyword search (BM25), dense vs. sparse, fusion

**27. Grounding and citations** — grounding, citation, attribution, source passage

## 5. Prompting

**28. Prompt engineering** — prompt, system prompt, instruction, prompt template, delimiters

**29. Few-shot and in-context learning** — few-shot, zero-shot, in-context learning (ICL), exemplars

**30. KV caching** — KV (key/value) cache, decoding speed, memory footprint

**31. Prompt caching** — prompt caching, cache hit, cached prefix

## 6. Agents

**32. Tool calling / function calling** — tool calling, function calling, tool schema, API call

**33. MCP** — Model Context Protocol (MCP), server, tool interoperability

**34. Agentic systems** — agent, agentic loop, tool use, autonomy, environment

**35. Agent memory** — short-term memory, long-term memory, state, scratchpad

**36. Planning and orchestration** — planning, orchestration, task decomposition, workflow

**37. Multi-agent architectures** — multi-agent, orchestrator, sub-agent, handoff

## 7. Multimodal

**38. Vision-language models** — vision-language model (VLM), multimodal, image encoder

**39. Audio and speech** — speech-to-text (STT), text-to-speech (TTS), automatic speech recognition (ASR)

**40. Multimodal product surfaces** — modality, cross-modal, multimodal input / output

## 8. Safety and trust

**41. Guardrails** — guardrail, input / output filter, policy, moderation

**42. AI security** — prompt injection, jailbreak, data exfiltration, adversarial input

**43. Privacy and PII** — personally identifiable information (PII), redaction, data retention

**44. Responsible AI** — bias, fairness, transparency, regulation (EU AI Act)

## 9. Evaluation

**45. Evaluation methods** — eval, offline eval, human eval, LLM-as-judge

**46. Benchmarks and their limits** — benchmark, leaderboard, contamination, overfitting to the test

**47. Regression testing** — regression test, golden set, eval suite

## 10. Production and operations

**48. Production LLM architecture** — inference server, gateway / router, fallback, orchestration

**49. Inference optimization** — latency, throughput, batching, streaming

**50. LLM observability** — observability, tracing, logging, monitoring, drift

**51. Cost and unit economics** — cost per query, tokens, gross margin, unit economics

## 11. Product and strategy

**52. AI product metrics** — deflection rate, acceptance / edit rate, containment, task completion

**53. Build vs. buy** — build vs. buy, API vs. open-source, self-hosting

**54. Data moats and feedback loops** — data moat, feedback loop, proprietary data

**55. The iron triangle** — cost / latency / quality tradeoff, the iron triangle
