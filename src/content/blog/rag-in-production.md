---
title: "RAG in production: what the tutorials don't tell you"
date: 2026-02-04
---

Retrieval-augmented generation is well understood at the prototype stage. You embed documents, store vectors, retrieve the top-k chunks, and pass them to a language model. It works in a notebook. It works in a demo.

Production is different.

## Retrieval quality degrades silently

In a prototype, your document set is small and curated. In production, documents accumulate, formats vary, and old content sits alongside new content without any indication of relative reliability. Your retrieval system will surface stale or contradictory chunks, and the model will use them confidently.

You need a strategy for document freshness — either a staleness threshold that removes or flags outdated content, or metadata that lets the model reason about recency. Neither is hard to implement, but both require deliberate design.

## Chunk boundaries matter more than chunk size

Most RAG tutorials recommend a chunk size and move on. In practice, the semantic coherence of your chunks has a bigger impact on retrieval quality than the size. A chunk that splits a definition from its context, or separates a table from its caption, will retrieve incorrectly even with a good embedding model.

Spend time on your chunking strategy. Sentence-boundary chunking, document-structure-aware chunking, and overlapping windows each have tradeoffs that depend on your content type.

## Evals are not optional

Without evals, you cannot measure whether a change to your retrieval pipeline improved or degraded output quality. This makes iteration nearly impossible — you're flying blind.

Build a small, representative eval set before you start tuning. It doesn't need to be large. Fifty to a hundred question-answer pairs, covering the range of queries your system will receive, is enough to detect regression and guide improvement.
