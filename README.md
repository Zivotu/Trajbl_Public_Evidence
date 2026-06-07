# Trajbl Public Evidence Repository (v0.1)

Trajbl is a proprietary evidence-packing layer for RAG/LLM pipelines. This public repository provides evidence summaries, aggregate benchmark results, limitations, and a link to a controlled demo. Source code is not included.

---

## What Trajbl Is

Trajbl is a question-aware evidence selection and packing layer that sits between the Retrieval (RAG) and Generation (LLM) stages of information retrieval pipelines. Unlike token-level pruning solutions that discard words and fragment sentences, Trajbl selects whole sentences as complete units of evidence based on their relevance to the query and context balance.

---

## What This Repository Contains

This repository serves as a public evidence package for research and partnership teams at Microsoft, OpenAI, Anthropic, Cohere, Mistral, and other organizations. It includes:
* **Evidence Ledger (`CLAIM_LEDGER.md`)**: A detailed map of all public claims, performance metrics, and evaluation boundaries.
* **Technical Write-up (`TECHNICAL_WRITEUP.md`)**: A conceptual, high-level description of sentence-level evidence packing and source-balance strategies.
* **Benchmark Summaries (`BENCHMARK_SUMMARY.md`)**: Empirical evaluation summaries from Croatian and English QA datasets.
* **Limitations (`LIMITATIONS.md`)**: Disclosures regarding the extractive nature of the method, evaluation scopes, and comparisons with model-based approaches.
* **Non-inclusion Statement (`WHAT_IS_NOT_INCLUDED.md`)**: Explicit description of proprietary assets omitted from this public repository.
* **Controlled Demo Guide (`PUBLIC_DEMO_GUIDE.md`)**: Instructions for accessing and testing the hosted demonstration.
* **Aggregate Performance Data (`RESULTS_TABLES/`)**: CSV files containing summarized metrics.

---

## What This Repository Does NOT Contain

This is an evidence-first, not code-first, repository. It **does not** contain:
* Proprietary source code, routing files, or segmenters.
* Scoring boundaries, tuning coefficients, or constant configurations.
* Cue listings, structured index maps, or LLM generation templates.
* Private evaluation datasets, reference answer sheets, or raw benchmark data.

---

## Key Performance Results (Stated with Scopes)

* **Context Budget Reduction:** 64% to 88% fewer input words (used as a proxy for context budget) across the reported Phase 29 HR single-doc, HR cross-doc, and EN LongBench slices.
* **Quality Retention:** 95%+ of full-context RAG quality retained on the reported Croatian Phase29 single-doc and cross-doc benchmarks.
* **Token-Compressor Baselines:** Outperformed LLMLingua-2 on the reported Croatian QA and English LongBench-E slices within the reported compressed-budget setup.

---

## Public Demo Link

The controlled demonstration of the Trajbl evidence-packing behavior is available at:
**[https://neurobiz.me/demo/](https://neurobiz.me/demo/)**

---

## Critical Notices
* **Peer-Review Status:** The results and methods presented in this repository have not been independently peer-reviewed.
* **Proprietary Notice:** The source code and implementation heuristics of Trajbl are proprietary. Review of the code and core architecture is available only under Non-Disclosure Agreement (NDA) or formal partnership processes.
