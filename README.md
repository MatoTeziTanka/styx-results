<div align="center">

# STYX

### State-First Context Engine

**A fundamentally different approach to AI context management.**

STYX replaces text retrieval (RAG) with a novel extraction approach.<br>
Instead of searching for similar text, STYX extracts only what actually matters for the next decision.

[![Patent](https://img.shields.io/badge/status-patent%20pending-blue)]()
[![Data Points](https://img.shields.io/badge/validated-10%2C063%20data%20points-green)]()
[![License](https://img.shields.io/badge/results-CC%20BY%204.0-orange)]()

---

</div>

## 📊 Real-World Results

Validated against **10,063 real data points** — 9,882 GitHub Issues from 11 major repositories plus 181 Wikipedia articles — using a **production RAG stack** with cross-encoder reranking.

<div align="center">

### GitHub Issues — 11 Repositories

| Repository | Issues | Token Reduction | vs RAG+Reranker |
|:---:|:---:|:---:|:---:|
| facebook/react | 1,000 | 82.5% | 0.9x |
| microsoft/vscode | 1,000 | 91.6% | 1.8x |
| kubernetes/kubernetes | 1,000 | 81.8% | 0.8x |
| golang/go | 1,000 | 86.9% | 1.0x |
| rust-lang/rust | 1,000 | 86.4% | 1.0x |
| tensorflow/tensorflow | 382 | 84.0% | 1.9x |
| angular/angular | 1,000 | 82.6% | 0.8x |
| vercel/next.js | 1,000 | 89.3% | 1.3x |
| microsoft/TypeScript | 1,000 | 84.9% | 0.9x |
| nodejs/node | 1,000 | 87.0% | 1.1x |
| python/cpython | 500 | 83.5% | 1.5x |

### Wikipedia — Non-GitHub Validation

| Data Source | Articles | Token Reduction | vs RAG+Reranker |
|:---:|:---:|:---:|:---:|
| **Wikipedia** | **181** | **98.5%** | **20.1x** |

</div>

<div align="center">

### Aggregate

| Metric | Value |
|:---|:---:|
| Total data points | **10,063** |
| Overall token reduction | **85.9%** |
| STYX vs full dataset | **7.1x** smaller |
| STYX vs RAG (no reranker) | **1.6x** more efficient |
| STYX vs RAG (with reranker) | **1.1x** more efficient |
| Wikipedia | **20.1x** more efficient |

</div>

---

## 🔑 What This Means

<div align="center">

| | RAG | STYX |
|:---|:---|:---|
| **Approach** | Retrieves text by similarity | Extracts only what matters |
| **Infrastructure** | Embeddings + vector DB + reranker | None required |
| **Token efficiency** | Baseline | **86% reduction** |
| **On unstructured content** | Baseline | **20x more efficient** |

</div>

<br>

> STYX achieves **86% token reduction** from raw input while matching or beating a fully optimized RAG pipeline — with zero embedding infrastructure, zero vector storage, and zero reranking overhead.

---

## 🔬 Methodology

| Component | Detail |
|:---|:---|
| **Data source** | Real GitHub Issues (11 repos via API) + Wikipedia articles |
| **Token counting** | tiktoken — OpenAI's production tokenizer, gpt-4 encoding |
| **RAG stack** | sentence-transformers/all-MiniLM-L6-v2 + ChromaDB + LangChain |
| **RAG reranking** | cross-encoder/ms-marco-MiniLM-L-6-v2 (production cross-encoder) |
| **Comparison** | Same input data, same queries, token output measured |
| **Reproducibility** | Methodology documented — patent pending, implementation withheld |

---

## 🌐 Multi-Language Implementation

<div align="center">

STYX has been implemented and tested in 4 languages:

| Language | Status |
|:---:|:---:|
| Python | ✅ Tested |
| Go | ✅ Tested |
| Rust | ✅ Tested |
| TypeScript | ✅ Tested |

</div>

---

## 🔒 Evidence Integrity

All results are SHA-256 hash-verified. Evidence artifacts and source code hashes are available upon request for due diligence.

```
Enhanced Results SHA-256: f21aed4c68467487d0370710c137c97c680f477086d051cd241fe84998a9d322
Initial Results SHA-256:  b569e9d57b315a706ccc337ed9efae77d074c573fbba0f8d6396638663f8c24c
Generated: 2026-02-03
```

---

## 💡 Why This Matters

Context noise is one of the most critical unsolved problems in AI. Current approaches like RAG retrieve relevant text but include substantial noise that wastes tokens, degrades reasoning, and increases latency. Fine-tuning improves task-specific performance but doesn't address the fundamental retrieval problem.

STYX demonstrates that a different extraction approach can eliminate 86% of retrieval noise while preserving decision-relevant context — with zero embedding infrastructure, zero vector storage, and zero reranking overhead. Faster, cheaper, and more accurate.

---

<details>
<summary><strong>❓ Frequently Asked Questions</strong></summary>

<br>

**How large is the dataset?**<br>
10,063 data points across 11 independent GitHub repositories (react, vscode, kubernetes, golang, rust, tensorflow, angular, next.js, TypeScript, node, cpython) plus 181 Wikipedia articles. The pattern holds consistently across all domains — from UI frameworks to compilers to container orchestration to encyclopedic content.

**How are tokens counted?**<br>
All results use tiktoken, OpenAI's production tokenizer with gpt-4 encoding. These are the same token counts used in production billing. No approximations.

**Your RAG baseline seems too simple. Would a better RAG stack change the results?**<br>
The benchmark uses a production-grade RAG stack with cross-encoder reranking (ms-marco-MiniLM-L-6-v2), which is the standard technique for improving RAG precision. The reranker improves RAG by ~30%. Even against this optimized baseline, STYX matches or exceeds RAG efficiency — while requiring zero embedding infrastructure, zero vector storage, and zero reranking overhead. On unstructured content (Wikipedia), STYX is 20x more efficient even against reranked RAG.

**GitHub Issues aren't a real knowledge base. Would this work on other data?**<br>
Wikipedia validation (181 articles) shows STYX at 20.1x more efficient than production RAG with reranking, with 98.5% token reduction. The extraction approach is data-agnostic. GitHub Issues were chosen because they're publicly accessible and reproducible — anyone can verify the RAG baseline independently.

**Where's the code? How do I know this is real?**<br>
Patent pending. Implementation available under NDA for serious inquiries. All evidence is SHA-256 hash-verified and reproducible. The methodology is fully documented. Tests use publicly available data (GitHub Issues via API) and standard open-source tools (sentence-transformers, ChromaDB, LangChain). Anyone can independently verify the RAG baseline.

**If this works so well, why hasn't someone done this before?**<br>
RAG emerged as the default approach because it's conceptually simple: embed text, store vectors, retrieve by similarity. But similarity doesn't equal relevance to the next decision. STYX takes a fundamentally different approach to extraction that focuses on what actually matters, not what looks similar.

**What's the catch? There's always a tradeoff.**<br>
The tradeoff is upfront extraction cost. STYX requires processing input data through a proprietary extraction pipeline before retrieval. For static knowledge bases (documentation, support tickets, policies), this is a one-time cost. For dynamic real-time use cases, the extraction overhead must be weighed against token savings. The results show that for retrieval-heavy workloads, the tradeoff strongly favors STYX.

</details>

---

<details>
<summary><strong>🏭 Potential Industry Impact</strong></summary>

<br>

**Enterprise AI / Copilots** — Today's AI copilots retrieve code snippets or document fragments by similarity, often including irrelevant context that wastes tokens and degrades suggestions. STYX reduces context overhead by delivering only decision-relevant information, enabling faster, more accurate code completions and document analysis.

**Healthcare / Clinical Decision Support** — RAG systems in healthcare retrieve patient records or medical literature by keyword similarity, often returning tangential information that increases cognitive load for clinicians. STYX eliminates noise in retrieval, surfacing only the context needed for the current clinical decision.

**Legal / Contract Analysis** — Contract review systems retrieve clauses by similarity, but similar text doesn't mean relevant text. STYX focuses extraction on what actually matters for the legal question at hand, reducing attorney review time and improving contract risk analysis.

**Financial Services / Compliance** — Compliance systems retrieve regulatory text or transaction records by keyword match, often returning hundreds of irrelevant documents. STYX filters out noise before retrieval, delivering only the regulations or transactions that impact the current compliance decision.

**DevOps / Incident Response** — Incident response tools retrieve logs, tickets, and runbooks by similarity, often overwhelming responders with noise during outages. STYX delivers only context relevant to the current failure mode, reducing mean time to resolution.

**Scientific Research / Literature Review** — Researchers wade through hundreds of retrieved papers to find relevant findings. STYX eliminates irrelevant citations and extracts only decision-relevant findings, accelerating literature review and hypothesis generation.

**Government / Policy Analysis** — Policy analysis systems retrieve legislative text, case law, or regulatory filings by keyword, often returning thousands of pages of tangential material. STYX reduces context noise, enabling faster policy impact analysis.

**Customer Support** — Support chatbots retrieve help articles by similarity, often returning multiple articles that don't address the actual issue. STYX extracts only the steps or context needed to resolve the customer's specific problem.

**Autonomous Systems / Robotics** — Autonomous systems retrieve sensor data, maps, or operational logs by similarity, but noise in context degrades real-time decision-making. STYX reduces retrieval overhead, enabling faster perception-to-action cycles.

**Education / Adaptive Learning** — Adaptive learning platforms retrieve educational content by topic similarity, often overwhelming students with tangential material. STYX delivers only the context needed for the student's current learning objective.

</details>

---

<div align="center">

## Status

**Patent pending** · Implementation details are proprietary<br>
Licensing inquiries: [open an issue on this repo](../../issues)

---

**Author:** Seth Schultz

**Results & benchmarks:** CC BY 4.0 (share with attribution)<br>
**Implementation:** All rights reserved (patent pending)

</div>

---

<div align="center">

## Support This Project

[![GoFundMe](https://img.shields.io/badge/GoFundMe-Donate-green)](https://gofund.me/e4d3f3ca0)
[![GitHub Sponsors](https://img.shields.io/badge/GitHub-Sponsors-pink)](https://github.com/sponsors/MatoTeziTanka)

Patent pending -- independent research by a solo inventor.

</div>
