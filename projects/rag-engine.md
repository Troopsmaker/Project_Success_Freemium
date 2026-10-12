# Showcase — Applied AI / RAG Engine

> **Signal:** production-grade Retrieval-Augmented Generation, self-hosted vectors — not a wrapper around a hosted vector DB. Hiring managers filter on this instantly.

## The one-liner
An ingestion-to-answer pipeline that turns a pile of PDFs into a typed question-answering API using **PostgreSQL + pgvector**, with **sub-200ms** semantic search.

## Why this project exists (the story)
Businesses have terabytes of PDF/doc data doing nothing. The goal: ingest → chunk → embed → store → let an internal employee query it in plain English and get a cited answer in milliseconds. This is the "Applied AI" proof that separates a resume bullet from a portfolio.

## What's shown (architecture — the depth lives in the paid curriculum)

```
[PDFs / S3] --ingest--> [Chunker] --embed--> [PostgreSQL + pgvector]
                                                  │
[User question] --> [Embedding] --> [HNSW nearest-neighbor search] --> [context]
                                                  │
                                   [LLM generates a cited answer]
```

- **Store:** PostgreSQL with the `pgvector` extension, **HNSW index** for fast approximate nearest-neighbor search.
- **Async pipeline:** heavy document parsing is decoupled from the HTTP request via a **distributed queue** (so the API never blocks on a 3-second embedding).
- **RAG strategy:** chunking + retrieval + context injection + hallucination controls.

## The metrics used to sell it
- Semantic search **< 200 ms** latency.
- Answers **cited to source chunks** (traceability).
- Runs on a cheap single Postgres instance — **no proprietary vector DB subscription**.

## The interview answer (why it's hard)
"OpenAI's API takes ~3 seconds. With 100 concurrent users, your server blocks. How did you fix it?" — the full, graded answer + architecture walkthrough are in the paid curriculum's project chapters.

> **Not public:** the source, the schema, the chunking strategy, the failure-mode analysis, and the deep-dive answers. These are inside the 180-day curriculum → **[UPGRADE.md](../UPGRADE.md)**.