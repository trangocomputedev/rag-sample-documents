# RAG Sample Documents

Sample documents for testing RAG (Retrieval-Augmented Generation) pipelines — chunking strategies, embedding quality, and retrieval evaluation.

## Contents

Each file is an excerpt of the same academic text (*The Role of Semantic Web Technologies in Smart Environments*, a PhD thesis by Faisal Razzak, Politecnico di Torino, 2013), truncated at different sizes to exercise chunking behaviour at scale.

| File | Approx. size |
|------|-------------|
| `sample_50k.md` | 50 KB |
| `sample_100k.md` | 100 KB |
| `sample_250k.md` | 250 KB |
| `sample_500k.md` | 500 KB |

## Use cases

- **Chunking benchmarks** — compare fixed-size, sentence, paragraph, and semantic chunking on real prose
- **RAG pipeline smoke tests** — load a known document and assert expected retrieval results
- **Embedding model evaluation** — measure retrieval quality across different embedding models and chunk sizes
- **Latency / throughput profiling** — stress-test indexing and query latency against realistic document sizes

## License

The original thesis is publicly available. These excerpts are provided for non-commercial research and tooling purposes only.
