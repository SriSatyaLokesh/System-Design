[🏠 Home (System-Design)](../README.md) > **AI Engineering**

# 🧠 AI Engineering & Applied LLM Systems

> Production patterns, foundation model lifecycle, RAG architectures, evaluation frameworks, and operational guardrails for building enterprise AI applications.

---

## 📌 Architectural Overview

AI Engineering bridges the gap between research machine learning models and robust software engineering. While ML engineering focuses on training and optimizing foundation models, **AI Engineering** focuses on building reliable, cost-effective, and scalable systems using foundation models, retrieval pipelines, and agentic workflows.

### Core Disciplines of AI Engineering

1. **Prompt Engineering & In-Context Learning:**
   - Systematic prompt evaluation, few-shot prompting, chain-of-thought (CoT), and structured JSON schema enforcement.
   - Managing context windows, token budgets, and prompt caching strategies.

2. **Retrieval-Augmented Generation (RAG):**
   - Ingestion pipelines: Chunking strategies, semantic chunking, and document parsing.
   - Vector databases & embeddings: Dense vector search, hybrid search (BM25 + vector), and re-ranking (cross-encoders).
   - Advanced RAG: Query rewriting, recursive retrieval, and metadata filtering.

3. **Evaluation & Guardrails (Evals):**
   - Automated evaluation suites: Faithfulness, answer relevance, context recall, and toxicity checks.
   - Production guardrails: Input sanitation, prompt injection defenses, output validation, and PII masking.

4. **Inference Optimization & Cost Management:**
   - Model routing (small models for classification, frontier models for complex reasoning).
   - Semantic caching of LLM responses to reduce latency and API expenditure.
   - Structured streaming and asynchronous queue workers for long-running generations.

---

## 📚 Included Reference Books

- **`AI Engineering.pdf`** — Definitive guide covering the full foundation model lifecycle, evaluation, fine-tuning, RAG architecture, and deploying reliable AI applications into production.

---

## 🔗 Related Resources

- [Agentic AI Learning Pathway](../Agentic%20AI/README.md)
- [Prompt Engineering Handbook](../Prompt-Engineering/prompt-engineering-beginner-to-pro-guide.md)
- [Distributed Caching Architecture](../Caching/README.md)
- [System Design Bibles](../System%20Design%20bibles/README.md)
