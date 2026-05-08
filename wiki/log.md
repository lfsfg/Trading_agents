# Wiki Log

Append-only. Never edit past entries. Format: `## YYYY-MM-DD HH:MM [OP] title`

---

## 2026-05-08 00:01 [INGEST] karpathy-llm-wiki-gist

Ingested `sources/raw/karpathy-llm-wiki-gist.md` (Karpathy's LLM Wiki gist).
Pages created: `sources/2026-05-08-karpathy-llm-wiki-gist.md`, `entities/andrej-karpathy.md`,
`concepts/llm-wiki-pattern.md`, `concepts/rag-vs-wiki.md`.
Index updated with 4 new entries. Key finding: wiki pattern beats RAG for personal KB
because synthesis is persistent and cross-references are pre-built.

---

## 2026-05-08 00:00 [INIT] wiki bootstrapped

Wiki schema created via CLAUDE.md. Folder structure initialized:
`wiki/{entities,concepts,syntheses,sources}` and `sources/raw/`.
Index and log files created. No pages ingested yet.
Next step: ingest first source via `INGEST sources/raw/<file>`.
