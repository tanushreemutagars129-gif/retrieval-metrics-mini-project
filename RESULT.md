# Retrieval Metrics Evaluation: MRR and Recall@10

## Evaluation Results Table

| Query | Keyword rank | Semantic rank |
|---|---|---|
| my redis cache keeps showing old data | 8 | 1 |
| how do I add semantic search to a table I already have | miss | 2 |
| redis or memcached for caching | 1 | 2 |
| why did my query get slower after I added an index | miss | 1 |
| what does ACID actually guarantee | 2 | 1 |
| how do I keep my postgres online while changing the schema | 6 | 3 |
| my background jobs stop after every deploy | miss | 2 |
| how do I let my database accept more writes per second | 4 | 1 |
| sql or nosql for a new product | 1 | 3 |
| why does my redis memory keep climbing | miss | 2 |
| **Summary** | **MRR 0.30 · Recall@10 0.60** | **MRR 0.67 · Recall@10 1.00** |

## Findings and Interpretation

Overall, semantic search is clearly the superior system across both metrics, achieving an MRR of 0.67 compared to keyword's 0.30, and a perfect Recall@10 of 1.00 compared to keyword's 0.60 (always finding the correct post in the top 3 results without a single miss). Keyword search only won on two specific queries—edis or memcached for caching (rank 1 vs 2) and sql or nosql for a new product (rank 1 vs 3)—which both consist of concise, exact technology keywords and direct comparative phrases where literal token matching works best. In contrast, semantic search dominated on symptom-based, paraphrased, and troubleshooting queries like my redis cache keeps showing old data and why did my query get slower after I added an index, capturing the underlying conceptual intent where exact keywords fail. An engineering team would still keep the keyword search system around because it reliably outperforms vector search on queries with rare, exact technical terms and identifiers, making a hybrid search (combining BM25 and vector embeddings via Reciprocal Rank Fusion) far more resilient than either system alone.
