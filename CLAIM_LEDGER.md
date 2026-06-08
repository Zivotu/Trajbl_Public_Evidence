# Claim Ledger

This ledger lists the validated empirical claims for Trajbl, mapping them to their
target datasets, metrics, and caveats to ensure strict compliance with our
intellectual property boundaries.

---

## Validated Claims List

---

### 1. Context Budget Reduction

- **Claim:** Trajbl reduces the context budget (using word count as a proxy) by
  64% to 88% compared to raw RAG contexts.
- **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
- **Dataset:** Croatian Single-Doc, Croatian Cross-Doc, and English LongBench-E slices.
- **Sample Size:** 109 questions (HR single-doc), 16 questions (HR cross-doc),
  100 questions (EN LongBench-E).
- **Baseline:** Raw full-context RAG (RAG prior to compression).
- **Metric:** Word-count proxy compared to raw context.
- **Result:** 64% reduction (HR single-doc), 82% reduction (HR cross-doc),
  88% reduction (EN LongBench-E).
- **Confidence:** HIGH
- **Caveat:** Specific to the context sizes of the tested multi-document and
  single-document tasks.
- **Safe Public Wording:** "64% to 88% fewer input words across the reported
  Phase 29 HR single-doc, HR cross-doc, and EN LongBench slices."
- **README Headline Allowed:** YES

---

### 2. Quality Retention (Croatian Benchmarks)

- **Claim:** Trajbl retains 95%+ of the quality of full-context RAG on Croatian
  benchmarks.
- **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
- **Dataset:** Croatian Single-Doc & Croatian Cross-Doc.
- **Sample Size:** 109 questions (single-doc), 16 questions (cross-doc).
- **Baseline:** Raw full-context RAG (RAG prior to compression).
- **Metric:** LLM-Judge (Gemini Pro/Flash) evaluation quality score.
- **Result:** Single-doc: 95.0% retention (0.628 vs 0.661);
  Cross-doc: 97.4% retention (0.609 vs 0.625).
- **Confidence:** HIGH
- **Caveat:** Quality retention is tested on Croatian-language medical/business
  slices and may vary in other domains or languages.
- **Safe Public Wording:** "95%+ of full-context RAG quality retained on the
  reported Croatian Phase 29 single-doc and cross-doc benchmarks."
- **README Headline Allowed:** NO — only allowed if accompanied by the full
  dataset/language scope caveat.

---

### 3. LLMLingua-2 Comparison

- **Claim:** Trajbl outperforms LLMLingua-2 under comparable compressed-context
  budgets.
- **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
- **Dataset:** Croatian QA and English LongBench-E slices.
- **Sample Size:** 109 questions (HR single), 16 questions (HR cross),
  100 questions (EN).
- **Baseline:** LLMLingua-2 (Question-Aware).
- **Metric:** LLM-Judge quality score (HR), SQuAD F1 (EN).
- **Result:** HR Single-Doc: +0.190; HR Cross-Doc: +0.297;
  EN LongBench: +0.167 SQuAD F1.
- **Confidence:** HIGH
- **Caveat:** Does not represent a global evaluation of all LLMLingua variants
  (e.g., LongLLMLingua without VRAM context caps).
- **Safe Public Wording:** "Outperformed LLMLingua-2 on the reported Croatian QA
  and English LongBench-E slices within the reported compressed-budget setup."
- **README Headline Allowed:** YES — when specifying LLMLingua-2 and the specific
  evaluation setup.

---

### 4. Cross-Document Grounding

- **Claim:** Trajbl balances evidence across multiple documents to avoid dominant
  source crowding.
- **Phase / Source Artifact:** Phase 29 (`STO_JE_TRAJBL.md`)
- **Dataset:** Croatian Cross-Doc.
- **Sample Size:** 16 questions.
- **Baseline:** LLMLingua-2 (Question-Aware).
- **Metric:** LLM-Judge Quality Score.
- **Result:** Trajbl Cross-Doc: 0.609 vs LLMLingua-2: 0.313.
- **Confidence:** MEDIUM
- **Caveat:** Tested on a small sample size (n=16) of multi-document Croatian
  questions.
- **Safe Public Wording:** "Promising cross-document evidence balancing on n=16
  Croatian cross-doc questions."
- **README Headline Allowed:** NO

---

### 5. Provence Comparison

- **Claim:** Trajbl provides a CPU-only, deterministic alternative to model-based compressors with superior extraction robustness, higher Exact Match precision in localized languages, and significant performance boosts on binary and relational queries.
- **Phase / Source Artifact:** `K5_final_apples_to_apples.md`, `K2b_real_winner_vs_provence_hr.md`, `K8_pure_trajbl_yesno_bridge_answer_probe.md`, and `K8_pure_trajbl_relation_bridge_answer_probe.md`
- **Dataset:** Mixed Croatian and English validation slices.
- **Sample Size:** 248 questions.
- **Baseline:** Provence.
- **Metric:** SQuAD F1, Exact Match (EM), and extraction success rate.
- **Result:** 
  - F1 Quality: Provence 0.4914 (EN) / 0.4388 (HR); Trajbl 0.4532 (EN) / 0.4047 (HR).
  - Exact Match (HR): Trajbl **0.10** vs Provence **0.06**.
  - Robustness (HR): Trajbl **100% extraction rate** (0 empty outputs) vs Provence **87.5% extraction rate** (6 empty outputs / failures).
  - Yes/No Queries (n=19): Trajbl Yes/No Bridge (Plan A) SQuAD F1: **0.7895** vs Provence baseline SQuAD F1: **0.1579** (+0.6316 delta).
  - Relation-Based Queries (n=21): Trajbl Relation Bridge (Plan A) SQuAD F1: **0.4450** vs Provence SQuAD F1: **0.3310** (+0.1140 delta).
- **Confidence:** HIGH
- **Caveat:** Provence maintains a minor average semantic relevance F1 advantage on generic queries.
- **Safe Public Wording:** "Provence retains a minor semantic F1 advantage on generic QA slices, while Trajbl outperforms it on Croatian Exact Match (0.10 vs 0.06), binary Yes/No queries (0.7895 vs 0.1579 F1 on specialized bridge tasks), relational multi-hop queries (0.4450 vs 0.3310 F1 on relation tasks), and offers 100% extraction robustness."
- **README Headline Allowed:** YES (when specifying EM, binary/relational query, and robustness advantages)

---

### 6. Dynamic Confidence Gate Routing

- **Claim:** Trajbl dynamically routes queries through a query-only router, achieving quality improvements with zero regressions on fresh evaluations.
- **Phase / Source Artifact:** Phase 56 (`phase56_confidence_gate_v1f_full_selected_fresh_report.md`)
- **Dataset:** Croatian Single-Doc.
- **Sample Size:** 109 questions.
- **Baseline:** Canonical `trajbl_pool12` (winner baseline).
- **Metric:** LLM-Judge Quality Score (0.0 to 1.0, evaluated via Gemini Pro).
- **Result:** Winner quality: 0.7041, Selected v1f quality: 0.7225 (+0.0184 delta). Head-to-head W/L/T: 2W/0L/107T.
- **Confidence:** HIGH
- **Caveat:** Routing logic relies on query classification and requires validation across a wider array of domains.
- **Safe Public Wording:** "Selective Map-Surface context routing via a Confidence Gate achieved a +0.0184 quality score increase with zero regressions (2W/0L/107T) compared to the standard sentence-selection winner."
- **README Headline Allowed:** YES

---

### 7. Numeric / Value-Point Repair Research

- **Claim:** Value-point repair recovers exact numeric and value-heavy misses in context packaging.
- **Phase / Source Artifact:** Phase 66 (`phase66_value_point_repair_decision_note.md`)
- **Dataset:** Value/marker slice of Croatian Single-Doc.
- **Sample Size:** 47 questions.
- **Baseline:** Canonical `trajbl_pool12` slice baseline (0.7606).
- **Metric:** LLM-Judge Quality Score (0.0 to 1.0, evaluated via Gemini Pro).
- **Result:** Baseline winner slice: 0.7606, Selected V3 postfilter: 0.7979 (+0.0372 delta).
- **Confidence:** MEDIUM (Research/Protected candidate)
- **Caveat:** Not currently integrated into runtime production due to mixed performance on fresh replication slices outside the value-marker domain.
- **Safe Public Wording:** "Value-point repair shows promise as a research-level candidate, yielding a +0.0372 quality improvement on value-heavy queries, but remains non-defaulted at runtime."
- **README Headline Allowed:** NO — only allowed in technical research sections.

