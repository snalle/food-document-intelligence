# Evaluation

This directory contains the retrieval evaluation dataset used in the benchmark.

## Pilot Queries

The initial pilot contains approximately 20–30 manually constructed queries across the first 10 benchmark documents.

Queries are designed to cover:

- simple factual retrieval
- numeric specifications
- tables and structured values
- scanned/image-based content
- near-duplicate products

## Query Schema

Each record in `queries.jsonl` contains:

- `query_id`
- `query`
- `relevant_documents`
- `relevant_pages`
- `answer`
- `query_type`
- `difficulty`

## Example

```json
{
  "query_id": "q001",
  "query": "What is the maximum moisture content of dried basil?",
  "relevant_documents": ["doc_005"],
  "relevant_pages": [3],
  "answer": "8%",
  "query_type": "numeric_specification",
  "difficulty": "easy"
}