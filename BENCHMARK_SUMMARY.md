# Benchmark Summary

This document details the evaluation settings, baselines, and aggregate results for the three benchmark slices validated during Phase 29.

---

## 1. Croatian Single-Document Benchmark (Phase 29)

* **Dataset:** Croatian medical and business documents.

* **Sample Size:** 109 questions.

* **Task Type:** Factoid and extractive question answering on long contexts.

* **Baseline:** Raw full-context RAG (RAG prior to compression) and LLMLingua-2.

* **Metric:** LLM-Judge Quality Score (0.0 to 1.0, evaluated via Gemini Pro). Context sizes are evaluated using word count as a proxy for the context budget.

### Results

| Compression Mode | Quality Score (Mean) | Input Context Size (Words) |
| :--- | :---: | :---: |
| **RAG (Full Context)** | 0.661 | 3183 |
| **Trajbl (`trajbl_pool12`)** | **0.628** | **1160** |
| LLMLingua-2 (Question-Aware) | 0.438 | 1331 |
| LLMLingua-2 (Question-Blind) | 0.420 | 1290 |
| Naive Truncation | 0.445 | 1029 |

* **Caveat:** The evaluation quality depends on the LLM-Judge rubric and the Croatian linguistic patterns of the tested corpus.

---

## 2. Croatian Cross-Document Benchmark (Phase 29)

* **Dataset:** Mixed Croatian documents requiring multi-source synthesis.

* **Sample Size:** 16 questions.

* **Task Type:** Multi-hop cross-document synthesis (comparison, contradiction, or complementation).

* **Baseline:** LLMLingua-2.

* **Metric:** LLM-Judge Quality Score (0.0 to 1.0, evaluated via Gemini Pro). Context sizes are evaluated using word count as a proxy for the context budget.

### Results

| Compression Mode | Quality Score (Mean) | Input Context Size (Words) |
| :--- | :---: | :---: |
| **RAG (Full Context)** | 0.625 | 7456 |
| **Trajbl (`trajbl_crossdoc`)** | **0.609** | **1308** |
| LLMLingua-2 (Question-Aware) | 0.313 | 1350 |

* **Caveat:** The sample size (n=16) is small and serves as an early validation of the document-balanced selection strategy rather than a generalized production proof.

---

## 3. English LongBench-E Slice Benchmark (Phase 29)

* **Dataset:** English LongBench-E subset.

* **Sample Size:** 100 questions.

* **Task Type:** English multi-hop QA.

* **Baseline:** LLMLingua-2.

* **Metric:** SQuAD F1 score. Context sizes are evaluated using word count as a proxy for the context budget.

### Results

| Compression Mode | SQuAD F1 (Mean) | Input Context Size (Words) |
| :--- | :---: | :---: |
| **RAG (Full Context)** | 0.587 | 10593 |
| **Trajbl** | **0.400** | **1313** |
| LLMLingua-2 (Question-Aware) | 0.233 | 1405 |

* **Caveat:** This slice evaluation compares performance within the reported compressed-budget setup, but does not capture performance differences on open-ended creative tasks.
