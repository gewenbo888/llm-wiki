# LLM Wiki — AI-Maintained Knowledge Base

[![Live Demo](https://img.shields.io/badge/Live-llm--wiki.vercel.app-f0b040)](https://llm-wiki.vercel.app)

A persistent, LLM-maintained knowledge base based on [Karpathy's LLM Wiki pattern](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f). Instead of RAG (re-deriving answers every query), the LLM builds and maintains a structured wiki that compounds knowledge over time.

## How It Works

```
sources/     → Raw immutable documents
wiki/        → LLM-generated pages (summaries, entities, cross-references)
CLAUDE.md    → Schema defining structure and operations
```

Three operations:
1. **Ingest** — feed a source, LLM creates 10-15 wiki pages
2. **Query** — ask questions, answers come from structured wiki
3. **Lint** — health check for contradictions and orphans

## Quick Start

```bash
git clone https://github.com/gewenbo888/llm-wiki.git && cd llm-wiki
cp ~/my-article.md sources/
claude "Ingest sources/my-article.md into the wiki"
claude "What does the wiki say about [topic]?"
```

## Why Wiki > RAG

- RAG re-derives answers every time — work is thrown away
- Wiki compounds — each ingest enriches existing pages
- LLMs never get bored maintaining it — humans do
- Answers improve over time as the wiki grows

## Links

- **Live**: https://llm-wiki.vercel.app
- **Original concept**: [Karpathy's gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
