# Claim Ledger

This ledger lists the validated empirical claims for Trajbl, mapping them to their target datasets, metrics, and caveats to ensure strict compliance with our intellectual property boundaries.

---

## Validated Claims List

### 1. Context Budget Reduction
* **Claim:** Trajbl reduces the context budget (using word count as a proxy) by 64% to 88% compared to raw RAG contexts.
* **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
* **Dataset:** Croatian Single-Doc, Croatian Cross-Doc, and English LongBench-E slices.
* **Sample Size:** 109 questions (HR single-doc), 16 questions (HR cross-doc), 100 questions (EN LongBench-E).
* **Baseline:** Raw full-context RAG (RAG prior to compression).
* **Metric:** Word-count proxy compared to raw context.
* **Result:** 64% reduction (HR single-doc), 82% reduction (HR cross-doc), 88% reduction (EN LongBench-E).
* **Confidence:** HIGH
* **Caveat:** Specific to the context sizes of the tested multi-document and single-document tasks.
* **Safe Public Wording:** "64% to 88% fewer input words across the reported Phase 29 HR single-doc, HR cross-doc, and EN LongBench slices."
* **README Headline Allowed:** YES

### 2. Quality Retention (Croatian Benchmarks)
* **Claim:** Trajbl retains 95%+ of the quality of full-context RAG on Croatian benchmarks.
* **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
* **Dataset:** Croatian Single-Doc & Croatian Cross-Doc.
* **Sample Size:** 109 questions (single-doc), 16 questions (cross-doc).
* **Baseline:** Raw full-context RAG (RAG prior to compression).
* **Metric:** LLM-Judge (Gemini Pro/Flash) evaluation quality score.
* **Result:** Single-doc: 95.0% retention (0.628 vs 0.661); Cross-doc: 97.4% retention (0.609 vs 0.625).
* **Confidence:** HIGH
* **Caveat:** Quality retention is tested on Croatian-language medical/business slices and may vary in other domains or languages.
* **Safe Public Wording:** "95%+ of full-context RAG quality retained on the reported Croatian Phase29 single-doc and cross-doc benchmarks."
* **README Headline Allowed:** NO (Only allowed if accompanied by the full dataset/language scope caveat)

### 3. LLMLingua-2 Comparison
* **Claim:** Trajbl outperforms LLMLingua-2 under comparable compressed-context budgets.
* **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
* **Dataset:** Croatian QA and English LongBench-E slices.
* **Sample Size:** 109 questions (HR single), 16 questions (HR cross), 100 questions (EN).
* **Baseline:** LLMLingua-2 (Question-Aware).
* **Metric:** LLM-Judge quality score (HR), SQuAD F1 (EN).
* **Result:** HR Single-Doc: +0.190; HR Cross-Doc: +0.297; EN LongBench: +0.167 SQuAD F1.
* **Confidence:** HIGH
* **Caveat:** Does not represent a global evaluation of all LLMLingua variants (e.g., LongLLMLingua without VRAM context caps).
* **Safe Public Wording:** "Outperformed LLMLingua-2 on the reported Croatian QA and English LongBench-E slices within the reported compressed-budget setup."
* **README Headline Allowed:** YES (When specifying LLMLingua-2 and the specific evaluation setup)

### 4. Cross-Document Grounding
* **Claim:** Trajbl balances evidence across multiple documents to avoid dominant source crowding.
* **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md` / `run_phase29_trajbl_crossdoc_b2.py`)
* **Dataset:** Croatian Cross-Doc.
* **Sample Size:** 16 questions.
* **Baseline:** LLMLingua-2 (Question-Aware).
* **Metric:** LLM-Judge Quality Score.
* **Result:** Trajbl Cross-Doc: 0.609 vs LLMLingua-2: 0.313.
* **Confidence:** MEDIUM
* **Caveat:** Tested on a small sample size (n=16) of multi-document Croatian questions.
* **Safe Public Wording:** "Promising cross-document evidence balancing on n=16 Croatian cross-doc questions."
* **README Headline Allowed:** NO

### 5. Provence Comparison
* **Claim:** Trajbl provides a CPU-only, deterministic alternative to model-based compressors.
* **Phase / Source Artifact:** `K5_final_apples_to_apples.md`
* **Dataset:** Mixed Croatian and English validation slices.
* **Sample Size:** 248 questions.
* **Baseline:** Provence.
* **Metric:** SQuAD F1 and Word/Token budget.
* **Result:** Provence F1: 0.4914 (EN) / 0.4388 (HR) vs Trajbl F1: 0.4532 (EN) / 0.4047 (HR).
* **Confidence:** HIGH
* **Caveat:** Provence maintains a semantic relevance advantage on generic query categories.
* **Safe Public Wording:** "Provence retains a semantic relevance advantage on generic QA slices; Trajbl remains attractive where CPU-only, deterministic, sentence-level, auditable evidence packing is preferred."
* **README Headline Allowed:** NO
