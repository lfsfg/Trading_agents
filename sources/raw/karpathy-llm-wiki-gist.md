# Source: LLM Wiki Gist — Andrej Karpathy

URL: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
Captured: 2026-05-08

---

A pattern for building personal knowledge bases using LLMs.
Three-layer architecture: Raw Sources (immutable) → Wiki (LLM-maintained markdown) → Schema (CLAUDE.md rules).

Core operations: INGEST, QUERY, LINT, UPDATE.
Navigation via index.md (catalog) and log.md (append-only history).
Key insight: wiki compounds knowledge session-to-session rather than re-deriving it through RAG each time.
Optional tools: Obsidian Web Clipper, local BM25/vector search, Marp for slides.
