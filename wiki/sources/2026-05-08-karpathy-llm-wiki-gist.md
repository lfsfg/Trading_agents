---
title: "LLM Wiki Pattern — Andrej Karpathy Gist"
type: source
tags: [knowledge-management, llm, second-brain, wiki]
created: 2026-05-08
updated: 2026-05-08
related: [../concepts/rag-vs-wiki.md, ../entities/andrej-karpathy.md, ../concepts/llm-wiki-pattern.md]
---

Karpathy's gist describing a pattern for LLM-maintained personal knowledge bases.
The core idea: use LLMs as disciplined wiki editors rather than one-shot Q&A engines,
so knowledge compounds across sessions.

## Key Claims

- Three layers: raw sources (immutable), wiki (LLM-written markdown), schema (CLAUDE.md).
- Single source ingest may touch 10–15 wiki pages.
- Index + log provide session continuity without re-reading everything.
- Superior to RAG for personal knowledge because cross-references are pre-built and synthesis is persistent.

## Entities Touched

- [andrej-karpathy.md](../entities/andrej-karpathy.md)

## Concepts Touched

- [llm-wiki-pattern.md](../concepts/llm-wiki-pattern.md)
- [rag-vs-wiki.md](../concepts/rag-vs-wiki.md)

## References

- Raw source: `sources/raw/karpathy-llm-wiki-gist.md`
- Original URL: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
