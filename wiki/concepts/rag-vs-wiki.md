---
title: "RAG vs Wiki Pattern"
type: concept
tags: [rag, knowledge-management, llm, retrieval]
created: 2026-05-08
updated: 2026-05-08
related: [../concepts/llm-wiki-pattern.md, ../sources/2026-05-08-karpathy-llm-wiki-gist.md]
---

Two competing approaches to giving LLMs access to a personal knowledge base.

## Comparison

| Dimension | RAG | LLM Wiki |
|-----------|-----|----------|
| Knowledge location | Vector DB / chunk store | Structured markdown pages |
| Cross-references | Reconstructed at query time | Pre-built at ingest time |
| Synthesis | Ephemeral (per query) | Persistent (written to wiki) |
| Session continuity | Re-embed everything | index.md + log.md |
| Scales to | Millions of docs | ~Hundreds of rich pages |
| Best for | Large corpora, exact retrieval | Personal KB, compounding insight |

## When to Use RAG Instead

- Source corpus is too large to summarize per-document.
- Need exact text retrieval (legal, medical verbatim).
- Sources change faster than ingest cadence.

## References

- [llm-wiki-pattern.md](../concepts/llm-wiki-pattern.md)
- [2026-05-08-karpathy-llm-wiki-gist.md](../sources/2026-05-08-karpathy-llm-wiki-gist.md)
