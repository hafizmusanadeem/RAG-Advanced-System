# PROJECT RULES

Version: 1.0

---

# Core Philosophy

This project follows a systems-first approach.

The LLM is not the source of truth.

Retrieved evidence is the source of truth.

Every repeated failure must be converted into:

Problem
→ Rule
→ Check
→ Documentation

The goal is not to make the LLM smarter.

The goal is to make mistakes impossible through architecture.

---

# Retrieval Rules

- Never generate an answer without retrieval.
- Never rely on model parametric knowledge.
- Retrieved chunks are the only source of truth.
- If retrieval fails, the system must refuse to answer.
- Every answer must be grounded in retrieved evidence.

---

# Citation Rules

- Every factual claim must have a citation.
- Every citation must point to a retrieved chunk.
- Missing citation = failed response.
- Unsupported claim = failed response.

---

# Hallucination Prevention Rules

- If evidence is insufficient, answer:
  "I could not find supporting evidence."

- The system must prefer refusal over hallucination.

- Confidence must never be fabricated.

---

# Retrieval Quality Rules

Required Retrieval Pipeline:

1. BM25 Retrieval
2. Dense Vector Retrieval
3. Result Fusion
4. Cross Encoder Re-Ranking
5. Context Selection

No milestone may bypass this architecture once introduced.

---

# Prompt Rules

- Prompts are system assets.
- Prompts must be version controlled.
- Prompts must live in configs/prompts.
- No prompts inside Python code.
- Prompt changes require evaluation.

---

# Evaluation Rules

Every retrieval or prompt change must be measurable.

Every major change must run:

- Retrieval Evaluation
- Citation Evaluation
- Faithfulness Evaluation

No quality regression is allowed.

---

# Engineering Rules

- Strict typing required.
- Logging required.
- Tests required.
- Documentation required.
- No hardcoded configuration values.
- No business logic inside notebooks.
- Configuration must live in config files.

---

# AI Agent Rules

Before implementing any milestone:

1. Explain architecture.
2. Explain tradeoffs.
3. Show folder structure.
4. Show files to modify.

After implementing any milestone:

1. Run tests.
2. Verify build.
3. Update documentation.
4. Update architecture docs.
5. Update failures log if needed.

---

# Failure Learning Rules

Every discovered issue must be recorded.

docs/FAILURES.md

Format:

Problem
Root Cause
Impact
Fix
Prevention

Recurring failures must become:

- validation checks
- tests
- quality gates
- CI checks

Never solve the same problem twice.

---

# Quality Gate Rules

The system must fail if:

- Retrieval returns zero results
- Citation validation fails
- Faithfulness threshold fails
- Evaluation threshold fails
- Tests fail
- Type checking fails

No exception.