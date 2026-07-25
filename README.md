# Hybrid Requirements Validation Prompts

[ttps://img.shields.io/badge/Research-Artifact-blue]()
[![Prompt Engineering](https://img.-Engineering-green]()
https://img.shields.io/badge/RAG-Enabled-purple]()
[![Formal Logic](https://img.shields.io/badgeOL%20%26%20AULIA-orange]()
[![Z3 Verification](https://img.shields.io/badge/Z-red]()
[![License](https://img.adge/License-MIT-yellow]()

# Hybrid Requirements Validation Prompts

A research artifact repository accompanying the paper:

> **A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic**

This repository contains the prompt engineering framework, validation workflows, datasets, examples, and formal verification artifacts used to validate software requirements written in natural language.

The framework integrates:

- Retrieval-Augmented Generation (RAG)
- Agentic RAG
- Large Language Models (LLMs)
- First-Order Logic (FOL)
- AULIA Formal Representations
- Z3 SMT Solver
- Human-in-the-Loop Validation

to support evidence-based, explainable, and formally verified software requirements validation.

---

# Motivation

Natural language remains the dominant medium for specifying software requirements. However, such requirements frequently suffer from quality defects that negatively affect software development, testing, maintenance, and verification.

Common defects include:

- Ambiguity
- Incompleteness
- Inconsistency
- Vagueness
- Non-Verifiability
- Unrealistic Constraints
- Missing Traceability
- Contradictory Statements

Although Large Language Models (LLMs) have shown promising capabilities for requirement analysis and defect detection, relying solely on LLM reasoning may introduce:

- Hallucinations
- Unsupported conclusions
- Domain misunderstandings
- Inconsistent validation decisions

To address these limitations, this repository proposes a hybrid validation framework that combines contextual retrieval, semantic reasoning, and formal verification.

---

# Framework Overview

The framework follows a multi-stage validation pipeline.

```text
Natural Language Requirement
           │
           ▼
┌───────────────────────────────┐
│ Retrieval & Re-ranking        │
│ (RAG / Agentic RAG)           │
└───────────────────────────────┘
           │
           ▼
┌───────────────────────────────┐
│ Semantic Validation           │
│ (ISO/IEC/IEEE 29148)          │
└───────────────────────────────┘
           │
           ▼
┌───────────────────────────────┐
│ Formalization                 │
│ JSON + FOL + AULIA            │
└───────────────────────────────┘
           │
           ▼
┌───────────────────────────────┐
│ Z3 SMT Verification           │
│ Consistency Checking          │
│ Satisfiability Analysis       │
└───────────────────────────────┘
           │
           ▼
┌───────────────────────────────┐
│ Interpretation & Reporting    │
└───────────────────────────────┘
           │
           ▼
      Validation Report
```

---

# Validation Criteria

The semantic validation stage evaluates requirements using principles inspired by ISO/IEC/IEEE 29148.

## Quality Attributes

- Ambiguity
- Completeness
- Consistency
- Verifiability
- Feasibility
- Necessity
- Traceability
- Correctness
- Atomicity
- Uniqueness

Each criterion is evaluated independently and then aggregated into an overall quality assessment.

---

# Prompt Engineering Pipeline

## Stage 1 – Retrieval and Re-ranking Prompt

The first prompt retrieves and evaluates relevant contextual evidence.

### Objectives

- Retrieve domain knowledge
- Evaluate semantic similarity
- Measure compliance relevance
- Score validation usefulness
- Eliminate noisy contexts
- Rank supporting evidence

### Output

```json
{
  "document_id": "DOC-001",
  "semantic_similarity": 9.1,
  "domain_relevance": 8.7,
  "compliance_relevance": 9.4,
  "overall_score": 9.0,
  "selection_status": "selected"
}
```

---

## Stage 2 – Semantic Validation Prompt

The second prompt performs requirement quality analysis.

### Defects Detected

- Ambiguity
- Vagueness
- Incompleteness
- Inconsistency
- Non-verifiability
- Feasibility concerns
- Missing traceability

### Example Output

```json
{
  "criterion": "Verifiability",
  "status": "Fail",
  "issue": "Performance requirement is not measurable",
  "recommendation": "Specify quantitative thresholds"
}
```

---

## Stage 3 – Formalization Prompt

Validated requirements are translated into structured representations.

### Extracted Elements

- Actors
- Entities
- Actions
- Constraints
- Conditions
- Events
- Permissions
- Obligations
- Dependencies

### Example

```json
{
  "actors": ["Customer"],
  "actions": ["Submit Order"],
  "conditions": ["User Authenticated"],
  "constraints": ["Maximum 5 Orders Per Minute"]
}
```

### Generated Formal Models

- JSON Representation
- First-Order Logic (FOL)
- AULIA Expressions

Example:

```text
∀u (SubmitOrder(u) → Authenticated(u))
```

---

# Stage 4 – Z3 SMT Verification

After formalization, the generated logical representations are automatically translated into SMT constraints and submitted to the Microsoft Z3 Solver.

The objective is to verify whether the requirement specification is logically valid and internally consistent.

## Verification Activities

### Consistency Checking

Detect logical contradictions among requirements.

### Satisfiability Checking

Verify whether all constraints can simultaneously hold.

### Dependency Verification

Validate dependencies between requirements.

### Conflict Detection

Detect incompatible obligations, permissions, and restrictions.

### Rule Compliance Validation

Check whether constraints satisfy defined business rules.

---

## Example

### Requirement

```text
The system shall allow access to financial reports only after successful authentication.
```

### FOL Representation

```text
∀u (AccessReport(u) → Authenticated(u))
```

### Z3 Result

```text
SAT
```

### Interpretation

```text
No contradiction detected.
Requirement is logically satisfiable.
```

---

## Contradiction Example

Requirement A:

```text
Users shall authenticate before accessing reports.
```

Requirement B:

```text
Users may access reports without authentication.
```

Generated Constraints:

```text
AccessReport(User)
→ Authenticated(User)

AccessReport(User)
→ ¬Authenticated(User)
```

Z3 Output:

```text
UNSAT
```

Interpretation:

```text
Logical contradiction detected.
Requirements must be revised.
```

---

# Stage 5 – Interpretation and Reporting

The final prompt consolidates:

- Semantic Validation Results
- RAG Evidence
- Formal Verification Results
- Z3 Analysis
- Confidence Assessments

### Example Output

```json
{
  "validation_status": "Needs Revision",
  "semantic_quality_score": 84,
  "logical_consistency_score": 97,
  "overall_confidence": 90,
  "identified_defects": [
    "Ambiguity",
    "Missing performance threshold"
  ]
}
```

---

# Repository Structure

```text
hybrid-requirements-validation-prompts/
│
├── README.md
├── LICENSE
├── CITATION.cff
│
├── prompts/
│   ├── retrieval_reranking_prompt.md
│   ├── semantic_validation_prompt.md
│   ├── formalization_prompt.md
│   ├── z3_verification_prompt.md
│   ├── reporting_prompt.md
│   └── orchestration_prompt.md
│
├── datasets/
│   ├── benchmark_requirements.csv
│   ├── requirements_dataset.csv
│   └── validation_results.csv
│
├── examples/
│   ├── example_01.md
│   ├── example_02.md
│   └── example_03.md
│
├── formal_models/
│   ├── json/
│   ├── fol/
│   ├── aulia/
│   └── smt/
│
├── z3_scripts/
│   ├── constraint_generator.py
│   ├── requirements_checker.py
│   └── contradiction_detector.py
│
├── outputs/
│   ├── gpt_results.csv
│   ├── claude_results.csv
│   ├── gemini_results.csv
│   └── perplexity_results.csv
│
├── figures/
│   ├── framework_architecture.png
│   └── validation_pipeline.png
│
└── docs/
    ├── methodology.md
    ├── evaluation_protocol.md
    └── replication_guide.md
```

---

# Research Contributions

This repository contributes:

- A hybrid prompt engineering framework for requirements validation.
- Agentic RAG-based contextual grounding.
- Semantic quality assessment aligned with Requirements Engineering principles.
- Transformation from natural language to formal representations.
- Automated verification using Z3 SMT solving.
- Explainable validation reports.
- Reproducible research artifacts for replication and benchmarking.

---

# Intended Audience

This repository is useful for:

- Requirements Engineering Researchers
- Software Engineers
- Quality Assurance Specialists
- AI Researchers
- Formal Methods Researchers
- Graduate Students
- Practitioners applying LLMs to Software Engineering

---

# Citation

```bibtex
@misc{martins2026hybridrequirementsvalidation,
  title={A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic},
  author={Antonio Soares Martins},
  year={2026},
  publisher={GitHub},
  repository={Hybrid Requirements Validation Prompts}
}
```

---

# License

This project is released under the MIT License.

---

# Author

**Antonio Soares Martins**

Research Interests:

- Requirements Engineering
- Software Quality Assurance
- Artificial Intelligence
- Large Language Models
- Retrieval-Augmented Generation
- Formal Methods
- Automated Software Validation

---

# Acknowledgments

This repository was developed to advance reproducible research on intelligent software requirements validation by combining the complementary strengths of Retrieval-Augmented Generation, Large Language Models, Formal Logic, and SMT-based verification through Microsoft Z3.
