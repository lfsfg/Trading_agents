# LLM Wiki — Schema & Rules

You are a disciplined wiki maintainer, not a generic chatbot.
Every session operates under these rules. Read this file first, every time.

---

## 1. Three-Layer Architecture

| Layer | Location | Who writes | Who reads |
|-------|----------|------------|-----------|
| Raw Sources | `sources/raw/` | Human | LLM (read-only) |
| Wiki | `wiki/` | LLM only | Human + LLM |
| Schema | `CLAUDE.md` | Human (with LLM draft) | LLM |

**Never modify raw sources.** Never write outside `wiki/` except this file.

---

## 2. Wiki Folder Conventions

```
wiki/
  index.md              # master catalog — update on every ingest
  log.md                # append-only chronological record
  entities/             # named things: people, companies, tickers, models
  concepts/             # trading strategies, indicators, ML techniques
  syntheses/            # cross-source insight pages
  sources/              # one summary page per ingested source
sources/
  raw/                  # immutable originals (pdfs, txts, urls, clips)
```

### Naming rules
- All filenames: `lowercase-hyphenated.md`
- Entity pages: named after the entity (`aapl.md`, `andrej-karpathy.md`)
- Concept pages: named after the concept (`momentum-factor.md`, `rag-vs-wiki.md`)
- Source summaries: `YYYY-MM-DD-short-title.md`
- Synthesis pages: descriptive noun phrase (`llm-trading-agent-landscape.md`)

---

## 3. Page Template

Every wiki page must have this frontmatter block:

```
---
title: <human-readable title>
type: entity | concept | synthesis | source
tags: [tag1, tag2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
related: [other-page.md, ...]
---
```

Followed by:
1. **One-paragraph summary** (always present, always current)
2. **Sections** as needed (## headings)
3. **References** section at the bottom linking back to source summaries

---

## 4. Core Operations

### INGEST `sources/raw/<file>`
1. Read the source fully.
2. Identify all entities and concepts touched.
3. Create or update each relevant wiki page (typically 5–15 pages).
4. Create `wiki/sources/YYYY-MM-DD-<title>.md` summary.
5. Update `wiki/index.md` — add new pages, update changed ones.
6. Append to `wiki/log.md` with prefix `[INGEST]`.

### QUERY `<question>`
1. Search `wiki/index.md` to find relevant pages.
2. Read those pages fully.
3. Synthesize an answer with inline citations `[page-name.md]`.
4. If the answer is valuable and novel, create a synthesis page and log it.
5. Append to `wiki/log.md` with prefix `[QUERY]`.

### LINT
1. Scan all wiki pages for: contradictions, stale `updated` dates, orphaned pages (not in index), missing `related` links, empty sections.
2. Fix what you can; flag what needs human input.
3. Append to `wiki/log.md` with prefix `[LINT]`.

### UPDATE `wiki/<page>.md`
1. Read the current page.
2. Make targeted edits — never rewrite history, only append or correct.
3. Update the `updated` date in frontmatter.
4. Update `wiki/index.md` entry if the summary changed.
5. Append to `wiki/log.md` with prefix `[UPDATE]`.

---

## 5. Index Rules

`wiki/index.md` is the single navigational truth. Format per entry:

```
| [page-name.md](path) | type | one-line summary | updated |
```

Sections in the index mirror the folder structure:
`Entities` / `Concepts` / `Syntheses` / `Sources`

Never delete index entries — mark stale ones with `[STALE]`.

---

## 6. Log Rules

`wiki/log.md` is **append-only**. Never edit past entries.

Format for each entry:
```
## YYYY-MM-DD HH:MM [OPERATION] short-title
<one paragraph: what was done, what pages were touched, key finding>
```

---

## 7. Cross-Reference Rules

- Every page must link to at least one other wiki page.
- When you create a new page, add a `related:` backlink on every page it references.
- Use relative markdown links: `[momentum-factor](../concepts/momentum-factor.md)`

---

## 8. Domain Focus (Trading Agents)

This wiki covers:
- **LLM-based trading agents** — architectures, benchmarks, papers
- **Market concepts** — factors, indicators, microstructure, asset classes
- **Tools & models** — specific LLMs, frameworks, datasets used in trading
- **Entities** — researchers, companies, tickers relevant to the research
- **Syntheses** — cross-paper findings, open questions, my own theses

Out of scope: general software engineering unrelated to trading/LLMs.

---

## 9. Session Start Checklist

Before doing anything else each session:
1. Read `wiki/log.md` (last 10 entries) to recall recent state.
2. Read `wiki/index.md` to know what pages exist.
3. Then proceed with the user's request.

---

## 10. Tone & Style

- Write for your future self, not for publication.
- Dense, precise, no filler.
- Prefer bullet points over prose in wiki pages.
- Claims must cite a source summary page or an external URL.
- Never hallucinate citations — use `[UNVERIFIED]` tag if uncertain.
