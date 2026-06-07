# FAQ for Reviewers

This FAQ is compiled for technical reviewers and partnership teams from Microsoft, OpenAI, Anthropic, Cohere, Mistral, and academic research groups.

---

## 1. Algorithmic Architecture

### Q: Why use sentence-level compression instead of token-level pruning like LLMLingua?

**A:** Token-level pruning (such as LLMLingua-2) classifies individual words or sub-words for deletion. While highly efficient for context reduction, this frequently fragments sentences, breaks grammatical syntax, and introduces semantic distortions. For regulated domains (healthcare, legal, finance), maintaining whole sentences preserves the exact meaning and allows for direct, click-to-source citation mapping.

### Q: What are the hardware and GPU requirements for Trajbl?

**A:** Trajbl is CPU-only and has zero GPU requirements during selection. It is written as a deterministic, rule-based filter that processes text segmentations on the fly. This makes it highly predictable, fast, and inexpensive compared to model-based context summarizers.

---

## 2. Evaluation & Performance

### Q: How does Trajbl compare to Provence?

**A:** Provence is a pre-trained model-based compressor that excels at broad semantic matching. Trajbl, being rule-based and deterministic, excels on queries requiring strict structural, numeric, or multi-hop relationship matching. For generic QA tasks, Provence maintains a semantic quality advantage, whereas Trajbl is preferred where CPU-only deployment and full text auditability are required.

### Q: Are the reported quality improvements language-agnostic?

**A:** While the initial high-quality retention (95%+) was measured on Croatian medical/business data, tests on English LongBench-E datasets confirm a similar relative performance gain (+0.167 SQuAD F1) over baseline token-pruning solutions (LLMLingua-2), providing an early English-language validation signal.

---

## 3. Partnership & Integration

### Q: Can we evaluate Trajbl on our own internal dataset?

**A:** Yes. We can coordinate evaluations on custom, private datasets. Under a Non-Disclosure Agreement (NDA), we can provide sandboxed evaluation wrappers or run the evaluations on our side using your sanitized test slices.

### Q: How can we request access to the source code?

**A:** Please refer to `CONTACT.md` to initiate a formal partnership request. Source code access is granted only under NDA to qualified partners.
