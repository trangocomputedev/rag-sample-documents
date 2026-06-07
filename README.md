# RAG Sample Documents

Sample documents for testing RAG (Retrieval-Augmented Generation) pipelines — chunking strategies, embedding quality, and retrieval evaluation.

## Contents

### Size-tiered excerpts (chunking benchmarks)

Each file is an excerpt of the same academic text (*The Role of Semantic Web Technologies in Smart Environments*, a PhD thesis by Faisal Razzak, Politecnico di Torino, 2013), truncated at different sizes to exercise chunking behaviour at scale.

| File | Approx. size |
|------|-------------|
| `sample_50k.md` | 50 KB |
| `sample_100k.md` | 100 KB |
| `sample_250k.md` | 250 KB |
| `sample_500k.md` | 500 KB |

### Full academic papers (semantic richness benchmarks)

Complete peer-reviewed papers converted from PDF to Markdown, with all sections, tables, algorithms, and references preserved.

| File | Source | Description |
|------|--------|-------------|
| `intelligent_energy_optimization_smart_home.md` | IEEE Trans. Smart Grid, Vol. 3, No. 4, Dec. 2012 | Energy optimization for smart homes using Domotic Effects and Boolean SAT; includes 3 data tables and 2 algorithms |
| `spamming_internet_of_things.md` | Procedia Computer Science, Vol. 10, 2012 | IoT spam via QR code spoofing and ECDSA-based countermeasures; includes 2 experimental results tables |

## Use cases

- **Chunking benchmarks** — compare fixed-size, sentence, paragraph, and semantic chunking on real prose
- **RAG pipeline smoke tests** — load a known document and assert expected retrieval results
- **Embedding model evaluation** — measure retrieval quality across different embedding models and chunk sizes
- **Latency / throughput profiling** — stress-test indexing and query latency against realistic document sizes

## License

The original thesis is publicly available. These excerpts are provided for non-commercial research and tooling purposes only.
