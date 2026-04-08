# LLM Wiki — Schema

Based on Karpathy's LLM Wiki pattern. This is a persistent, LLM-maintained knowledge base.

## Architecture

```
sources/     → Raw immutable documents (articles, papers, notes)
wiki/        → LLM-generated markdown pages (summaries, entities, cross-references)
wiki/index.md → Content catalog organized by category
wiki/log.md  → Append-only chronological record of ingests and queries
```

## Operations

### Ingest
When given a new source document:
1. Read the source completely
2. Create/update 10-15 wiki pages based on the content
3. Update index.md with new pages
4. Append to log.md with timestamp and summary
5. Cross-reference with existing wiki pages

### Query
When asked a question:
1. Search relevant wiki pages
2. Synthesize an answer from wiki content
3. If the answer is valuable, save it as a new wiki page
4. Append query and result to log.md

### Lint
Periodically check for:
- Contradictions between pages
- Orphan pages (not in index.md)
- Missing cross-references
- Outdated information

## Page Format

Each wiki page should follow:
```markdown
# Title

Brief summary (2-3 sentences)

## Key Points
- Point 1
- Point 2

## Details
Extended content...

## Cross-References
- [[Related Page 1]]
- [[Related Page 2]]

## Sources
- source_filename.md
```

## Rules
- Never modify files in sources/ — they are immutable
- Always update index.md when creating new pages
- Always append to log.md for every operation
- Use [[double brackets]] for internal wiki links
- Keep pages focused — one concept per page
- Prefer updating existing pages over creating duplicates
