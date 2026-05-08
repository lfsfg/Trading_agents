---
title: "LLM Wiki Pattern"
type: concept
tags: [knowledge-management, llm, architecture, second-brain]
created: 2026-05-08
updated: 2026-05-08
related: [../concepts/rag-vs-wiki.md, ../sources/2026-05-08-karpathy-llm-wiki-gist.md, ../entities/andrej-karpathy.md]
---

A system where an LLM acts as a disciplined wiki editor across sessions,
maintaining a structured markdown knowledge base rather than answering one-off questions.

## Architecture

```
Raw Sources (immutable)
    ↓ INGEST
Wiki (LLM-maintained markdown)
    ↑ governed by
Schema / CLAUDE.md
```

## Core Operations

| Op | Trigger | What happens |
|----|---------|--------------|
| INGEST | New source added | Read → update 5–15 pages → update index → log |
| QUERY | User question | Search index → read pages → synthesize + cite |
| LINT | Periodic | Check contradictions, orphans, stale dates |
| UPDATE | Targeted correction | Edit page → update index → log |

## Why Better Than RAG for Personal KB

- Cross-references pre-built at ingest time, not reconstructed per query.
- Synthesis is persistent — once written, no re-derivation needed.
- Log + index give session continuity with O(1) context overhead.
- Knowledge compounds: each ingest makes future queries richer.

## Weaknesses

- Requires LLM discipline (schema enforcement via CLAUDE.md).
- Scales to ~hundreds of pages before index becomes unwieldy (use search CLI then).
- Not suited for real-time or high-frequency updates.

## References

- [2026-05-08-karpathy-llm-wiki-gist.md](../sources/2026-05-08-karpathy-llm-wiki-gist.md)
