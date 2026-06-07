# Public Demo Guide

This document describes how to use and verify the behavior of the Trajbl evidence-packing layer using the online public demonstration interface.

---

## 1. Demo URL & Access

The demo is publicly hosted at:
**[https://neurobiz.me/demo/](https://neurobiz.me/demo/)**

To use the demo, follow the on-screen access request instructions to log in.

---

## 2. Interactive Operational Modes

Once logged in, the demo offers two testing layouts:

### Paste-Your-Own-Context Mode

This mode allows you to paste arbitrary raw text blocks and write a custom query.

* The system returns token/context-budget metrics for the selected evidence packet.
* Trajbl will segment your text and perform sentence-level evidence selection.
* The packed context output displays the selected evidence packet, token/context-budget metrics, and a verification prompt.

### Prepared English Demo Corpus Mode

This mode uses pre-loaded documents from our test sets to demonstrate cross-document balancing.

* Choose from selected multi-document questions.
* Observe how Trajbl uses a source-aware selection strategy to avoid one source dominating the compressed packet.

---

## 3. Verifying Results (LLM Evaluation)

The interface contains a button labeled **"Copy full verification prompt"**.

* Clicking this button copies a standardized prompt containing the query, the raw context, the Trajbl-selected context, and evaluation rubrics.
* You can paste this prompt directly into external LLMs (e.g., GPT-4, Gemini Pro, Claude Opus) to verify the quality of generation using the packed context.

---

## 4. Benchmark Disclosure

The public demo is intended for interactive verification of the selection behavior. It is **not a scored benchmark environment**. Performance metrics and error rates should be referenced in `BENCHMARK_SUMMARY.md` rather than derived from individual demo queries.
