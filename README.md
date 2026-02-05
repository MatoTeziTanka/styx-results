# STYX Benchmark Results

**Selective Token Yield eXtraction** - Context compression for LLMs

[![Patent Pending](https://img.shields.io/badge/Patent-Pending%20%2363%2F975%2C190-blue)](https://lightspeedup.com)
[![Validated](https://img.shields.io/badge/Validated-60%2C900%20Documents-green)](https://github.com/lightspeedup/styx-results)

## Results Summary

STYX achieves **90-98% token reduction** across diverse document types and scales.

| Benchmark | Documents | Full Tokens | STYX Tokens | Reduction | Ratio |
|-----------|-----------|-------------|-------------|-----------|-------|
| Single Project (React) | 300 | 150,720 | 9,141 | 93.9% | 16.5x |
| Multi-Language (R) | 300 | 92,563 | 3,243 | 96.5% | 28.5x |
| Multi-Language (Julia) | 300 | 139,216 | 3,307 | 97.6% | 42.1x |
| GitHub (30 Repos) | 6,000 | 1,761,612 | 85,528 | 95.1% | 20.6x |
| **Enterprise Scale** | **50,000** | **11,208,701** | **194,221** | **98.27%** | **57.7x** |

**Total validated:** 60,900 documents, 14.2M tokens processed

## What is STYX?

STYX extracts **binding state** from unstructured text:
- **Decisions** - What was decided
- **Constraints** - What limits options
- **Tensions** - What remains unresolved
- **Anti-patterns** - What to avoid

Everything else is discarded as narrative content.

## Key Findings

1. **Scales well** - Compression ratio *improves* with document count (93% → 98%)
2. **Language agnostic** - Same algorithm works in Python, R, Julia
3. **Content agnostic** - Works on GitHub issues, Stack Overflow, documentation
4. **Composable** - 88% additional reduction on top of GraphRAG

## Repositories Tested

- **Frontend:** React, Vue, Angular, Svelte, Next.js, Remix
- **Backend:** Node.js, Django, Flask, FastAPI
- **DevOps:** Kubernetes, Docker, Terraform, Ansible
- **AI/ML:** PyTorch, TensorFlow, Transformers
- **Languages:** Rust, Go, Python (CPython)
- **Databases:** Redis, PostgreSQL
- **Tools:** VSCode, Neovim, Deno, Bun, Tailwind, Storybook, Jest, Prettier

## Enterprise Impact

At enterprise scale (10K queries/day):
- **Daily token savings:** 2,210,000 tokens
- **Annual token savings:** 806,650,000 tokens
- **Annual cost savings:** $24,000+ (GPT-4 pricing)

## Benchmark Files

- [`benchmark_python.json`](./benchmark_python.json) - Python implementation results
- [`benchmark_r.json`](./benchmark_r.json) - R implementation results
- [`benchmark_julia.json`](./benchmark_julia.json) - Julia implementation results
- [`benchmark_github_30repos.json`](./benchmark_github_30repos.json) - Multi-repo results
- [`benchmark_enterprise.json`](./benchmark_enterprise.json) - Enterprise scale results

## How to Use These Results

These benchmarks validate the compression approach. To reproduce:

1. Fetch documents from the same sources (GitHub API, HuggingFace datasets)
2. Build full context as concatenated documents
3. Apply binding state extraction
4. Compare token counts

Detailed methodology in each benchmark file.

## RAG Comparison

STYX works **on top of** existing RAG systems:

| Method | Tokens | vs Full |
|--------|--------|---------|
| Full Context | 150,720 | - |
| Basic RAG | 9,510 | 93.7% reduction |
| STYX on RAG | 1,312 | 99.1% reduction |
| GraphRAG | 16,731 | 88.9% reduction |
| STYX on GraphRAG | 2,002 | 98.7% reduction |

## License

Benchmark results and methodology: MIT License

Core algorithm: Patent Pending #63/975,190

## Contact

- Website: [lightspeedup.com](https://lightspeedup.com)
- Twitter: [@lightspeedup](https://twitter.com/lightspeedup)
- Email: contact@lightspeedup.com

---

*STYX: Less noise. More signal. 98% smaller.*
