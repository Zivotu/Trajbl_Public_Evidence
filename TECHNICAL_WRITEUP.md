# Technical Write-up

This document outlines the architecture, pipeline placement, and core design
philosophy of Trajbl.

---

## 1. The Core Problem Trajbl Addresses

In standard Retrieval-Augmented Generation (RAG) pipelines, the retriever fetches
multiple long documents or context chunks to answer a query.
Passing this raw context directly to the Large Language Model (LLM) introduces
three primary issues:

- **High Inference Costs:** Processing large context windows scales LLM prompt
  costs linearly.
- **Context Dilution:** LLMs can miss critical evidence when it is buried in long
  text inputs (the "lost in the middle" phenomenon).
- **Information Fragmentation:** Existing compression techniques often prune text
  at the word or sub-word token level, which breaks sentence syntax, interrupts
  grammatical structure, and increases the risk of semantic distortions or
  hallucinations.

---

## 2. Pipeline Integration

Trajbl acts as a post-retrieval, pre-generation filter.
It is positioned between the RAG retrieval engine and the LLM generation model:

```
[ User Query ]
    │
    ▼
[ Retrieval (RAG) ]
    │
    ▼
[ Trajbl Context Packer ]   ← sentence-level evidence & source balancing
    │
    ▼
[ LLM Generation ]
```

By extracting and ordering context at this stage, Trajbl delivers a compact,
high-density evidence packet to the generator.

---

## 3. The Case for Sentence-Level Evidence Packing

Traditional token-pruning models classify individual words for deletion, which
frequently leads to broken sentences and missing verbs or negative modifiers.
Trajbl maintains sentence boundaries intact:

- **Auditability and Citation:** Retaining whole, un-fragmented sentences allows
  the generation model to generate clean citations and enables users to verify the
  exact source sentence in the original document.
- **Semantic Preservation:** Preserving sentence structure prevents the loss of
  negative modifiers or boundary conditions, ensuring that assertions in the source
  text are not accidentally reversed or distorted during compression.

---

## 4. Distinctions from Token Pruning

| Feature            | Token-Pruning Systems (e.g., LLMLingua-2)                         | Trajbl Context Packer                            |
| :----------------- | :----------------------------------------------------------------- | :----------------------------------------------- |
| **Extraction Unit** | Individual sub-word tokens or words                               | Whole, contiguous sentences                      |
| **Text Output**    | Segmented, often grammatically incomplete text fragments           | Fully grammatical sentences                      |
| **Logic**          | Statistical probabilities of token importance                      | Deterministic, question-aware selection rules    |
| **Hardware**       | Frequently requires GPU inference for sequence classification      | CPU-only processing with zero model overhead     |
| **Auditability**   | Difficult to map broken phrases back to source files              | Direct click-to-source sentence alignment        |

---

## 5. How to Interpret the Public Evidence

The evaluations presented in this repository focus on QA performance (accuracy and
SQuAD F1) when comparing LLM outputs using Trajbl-selected contexts against raw
contexts and alternative compression baselines.

- **Evidence Retention:** The data illustrates that high quality can be maintained
  in the reported benchmark slices, reducing the input context by up to 88% using
  word count as a context-budget proxy.
- **Evaluation Scope:** All benchmarks reflect performance on fact-based, extractive
  queries. The results do not evaluate generative creativity or open-ended reasoning
  tasks.
