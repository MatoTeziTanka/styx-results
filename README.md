# STYX Benchmark Results

**Selective Token Yield eXtraction** - Context compression for LLMs

[![Patent Pending](https://img.shields.io/badge/Patent-Pending%20%2363%2F975%2C190-blue)](https://lightspeedup.com)
[![Validated](https://img.shields.io/badge/Validated-60%2C900%20Documents-green)](https://github.com/lightspeedup/styx-results)
[![Quality](https://img.shields.io/badge/Quality-Beats%20GraphRAG%2061%25-orange)](https://github.com/lightspeedup/styx-results)

## Key Results

- **98% compression** across 60,900+ documents (up to 57.7x ratio)
- **Quality parity** with full context (500 blind judgments, 5 models: 239-238)
- **Beats GraphRAG** on answer quality (500 blind judgments, 5 models: 305-179, 61% win rate)
- Cross-validated in Python, R, and Julia

## Compression Benchmarks

| Benchmark | Documents | Full Tokens | STYX Tokens | Reduction | Ratio |
|-----------|-----------|-------------|-------------|-----------|-------|
| Single Project (React) | 300 | 150,720 | 9,141 | 93.9% | 16.5x |
| Multi-Language (R) | 300 | 92,563 | 3,243 | 96.5% | 28.5x |
| Multi-Language (Julia) | 300 | 139,216 | 3,307 | 97.6% | 42.1x |
| GitHub (30 Repos) | 6,000 | 1,761,612 | 85,528 | 95.1% | 20.6x |
| **Enterprise Scale** | **50,000** | **11,208,701** | **194,221** | **98.27%** | **57.7x** |

**Total validated:** 60,900 documents, 14.2M tokens processed

## Quality Benchmarks

### STYX vs Full Context (Raw)

500 blind head-to-head LLM judgments. Each model saw the same question with STYX compressed context and full original context. Position randomized. Neither model nor evaluator knew which was which.

| Method | Wins | Rate |
|--------|------|------|
| STYX (compressed) | 239 | 47.8% |
| Raw (full context) | 238 | 47.6% |
| Tie | 23 | 4.6% |

**Verdict:** Statistical parity. Same answer quality. Up to 57x fewer tokens.

Models tested: Mistral 7B, LLaMA 3.2, DeepSeek Coder v2 16B, Phi-3 Mini, Qwen 2.5 Coder 7B (NVIDIA A100 GPU)

### STYX vs GraphRAG

Same blind methodology. 500 judgments across the same 5 models. Position randomized.

| Method | Wins | Rate |
|--------|------|------|
| **STYX** | **305** | **61.0%** |
| GraphRAG | 179 | 35.8% |
| Tie | 16 | 3.2% |

**Verdict:** STYX produces better answers than GraphRAG while compressing 88% further.

**Win rate by model (all favor STYX):**
Mistral 65% | LLaMA 3.2 60% | DeepSeek 57% | Phi-3 64% | Qwen 59%

**Win rate by document category:**
Architecture 70% | Documentation 64% | GitHub Issues 56% | Stack Overflow 54%

Zero errors across all 500 judgments.

## What is STYX?

STYX extracts **structural intelligence** from unstructured text:
- **Decisions** - What was decided
- **Constraints** - What limits options
- **Tensions** - What remains unresolved
- **Anti-patterns** - What to avoid

Everything else is discarded as narrative content.

## Key Findings

1. **Scales well** - Compression ratio *improves* with document count (93% to 98%)
2. **Language agnostic** - Same algorithm works in Python, R, Julia
3. **Content agnostic** - Works on GitHub issues, Stack Overflow, documentation
4. **Quality preserved** - Statistical parity with full context across 5 models
5. **Beats GraphRAG** - 61% win rate on answer quality, plus 88% additional compression
6. **Composable** - Works on top of existing RAG pipelines

## RAG Compression Comparison

STYX works **on top of** existing RAG systems:

| Method | Tokens | vs Full |
|--------|--------|---------|
| Full Context | 150,720 | - |
| Basic RAG | 9,510 | 93.7% reduction |
| STYX on RAG | 1,312 | 99.1% reduction |
| GraphRAG | 16,731 | 88.9% reduction |
| STYX on GraphRAG | 2,002 | 98.7% reduction |

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
- **Annual cost savings:** $1,400-$17,000+ depending on model tier

Current model pricing context (Feb 2026): GPT-5.2 $1.75/1M, GPT-5.2 Pro $21/1M, Claude Opus 4.6 $5/1M, Grok 3 $3/1M, Gemini 2.5 Pro $1.25/1M.

## Benchmark Files

### Compression
- [`benchmark_python.json`](./benchmark_python.json) - Python implementation results
- [`benchmark_r.json`](./benchmark_r.json) - R implementation results
- [`benchmark_julia.json`](./benchmark_julia.json) - Julia implementation results
- [`benchmark_github_30repos.json`](./benchmark_github_30repos.json) - Multi-repo results
- [`benchmark_enterprise.json`](./benchmark_enterprise.json) - Enterprise scale results
- [`benchmark_rag_comparison.json`](./benchmark_rag_comparison.json) - RAG pipeline comparison

### Quality
- [`benchmark_quality_styx_vs_raw.json`](./benchmark_quality_styx_vs_raw.json) - STYX vs full context quality
- [`benchmark_quality_styx_vs_graphrag.json`](./benchmark_quality_styx_vs_graphrag.json) - STYX vs GraphRAG quality

## Methodology

These benchmarks validate the compression and quality approach. The methodology is fully described in each benchmark file and is auditable by anyone.

**Compression:** Documents fetched from public sources (GitHub API, HuggingFace datasets). Full context built as concatenated documents. STYX compression applied. Token counts compared.

**Quality:** Blind A/B comparison with position randomization. Each of 5 LLM models judges 100 sample pairs. Models see two responses to the same question — one from STYX compressed context, one from full context (or GraphRAG context). Neither the judge model nor the evaluator knows which is which.

## License

Benchmark results and methodology: MIT License

Core algorithm: Patent Pending #63/975,190

## Contact

- Website: [lightspeedup.com](https://lightspeedup.com)
- Twitter: [@lightspeedup](https://twitter.com/lightspeedup)
- Email: contact@lightspeedup.com

---

*STYX: Less noise. More signal. Better answers. 98% smaller.*
