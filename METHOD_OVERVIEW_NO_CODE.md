# Method Overview (No Source Code)

Trajbl acts as a deterministic, rule-based filter that operates on sentences
retrieved during a RAG lookup.
It does not perform deep neural model inference at the compression step, but
instead analyzes the structure of retrieved context to make structural pruning
decisions.

---

## Core Operational Mechanics

The algorithm follows a three-stage sequence focusing on whole-sentence
preservation, deterministic evidence packing, and auditability and citation
preservation:

### 1. Document Segmentation

Retrieval results (chunky raw contexts) are segmented into complete sentences.
Because sentence boundaries contain complete semantic ideas, this guarantees that
individual words are never truncated or fragmented, preserving grammatical
readability for the generation model.

### 2. Question-Aware Evidence Selection

Each sentence is evaluated according to structural features to identify alignment
with the query.
This step prioritizes sentences that directly support the queried subjects, respect
contextual assertions, and target value-oriented fact patterns without fragmenting
the underlying sentences.

### 3. Source-Balance Strategy

To prevent a single document from dominating the compressed packet, Trajbl groups
sentences by their source document.
It applies a source-balance strategy to distribute the selection across multiple
files.
This ensures that minority sources are preserved in the final packed context under
tight context budgets.
