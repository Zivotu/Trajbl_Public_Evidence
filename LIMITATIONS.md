# Limitations and Disclosures

This document details the boundary conditions, evaluation caveats, and known
limitations of the Trajbl evidence-packing pipeline.

---

## 1. Research and Publication Status

- **Not Peer-Reviewed:** The methodologies and results described in this repository
  have not been independently peer-reviewed by an academic or industry committee.
- **Staged Disclosure:** This v0.1 repository is a public evidence summary and does
  not constitute a full reproducibility package.
  Code, scoring boundaries, and coefficients are omitted.

---

## 2. Proprietary Boundaries

- **Source Code Closed:** The source code and implementation heuristics of Trajbl
  are proprietary.
- **Review Protocol:** Technical validation of code files and configuration
  parameters is restricted to formal partner review channels under a
  Non-Disclosure Agreement (NDA).

---

## 3. Methodological and Algorithmic Limitations

- **Extractive Nature:** Trajbl is strictly an extractive compressor.
  It cannot rewrite sentences or synthesize text.
  If a critical piece of evidence is split across a sentence boundary in a poorly
  formatted document, extractive selection may lose contextual links.
- **Semantic Retrieval Gap vs. Model-Based Compressors:**
  Evaluation against pre-trained model-based compressors (such as Provence)
  indicates that model-based systems retain a semantic relevance advantage on
  generic query categories.
  Trajbl is preferred where CPU-only inference, strict determinism, and full
  sentence auditability are required.

---

## 4. Evaluation Caveats

- **LLM-Judge Subjectivity:** The Croatian single-document and cross-document
  benchmarks rely on LLM-judge evaluations (Gemini Pro).
  While correlation checks were performed, judge evaluations carry inherent bias.
- **Small Sample Size:** The Croatian cross-document evaluation is limited to a
  small sample size (n=16) and should be interpreted as an initial validation of
  multi-document balancing rather than a generalized production proof.
- **Controlled Demo Limitations:** The public web demo is a demonstration tool.
  It does not reflect a controlled benchmark harness and is not suited for scoring
  quantitative performance.
