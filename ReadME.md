# Hybrid Requirements Validation Framework: Research Artifact Documentation

[![Research-Artifact](https://img.shields.io/badge/Research-Artifact-blue.svg)](#)
[![Prompt Engineering](https://img.shields.io/badge/Prompt-Engineering-green.svg)](#)
[![RAG-Enabled](https://img.shields.io/badge/RAG-Enabled-purple.svg)](#)
[![Formal-Logic](https://img.shields.io/badge/Formal_Logic-FOL_%26_AULIA-orange.svg)](#)
[![Z3-Verification](https://img.shields.io/badge/Z3_Verification-SMT_Solver-red.svg)](#)
[![License-MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#)

This repository serves as the official research artifact documentation accompanying the scientific publication:

> 📝 **"A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic"**

The engineering suite implements a robust, five-stage verification pipeline engineered to overcome classical large language model shortcomings—such as unpredictable hallucinations, domain blindness, or logical inconsistency—by balancing contextual semantic analysis against rigid formal constraint solvers.

---

## 1. Multi-Stage Pipeline Specification

```
   Natural Language Requirement
                 │
                 ▼
┌─────────────────────────────────┐
│  Stage 1: Retrieval & Reranking │  ◄── Context Grounding (Agentic RAG)
└─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│   Stage 2: Semantic Validation  │  ◄── Pattern & Quality Flaw Identification
└─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│     Stage 3: Formalization      │  ◄── Translates Text to FOL & AULIA
└─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│   Stage 4: Z3 SMT Verification  │  ◄── Mathematical Consistency Checking
└─────────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│  Stage 5: Reporting & Insights  │  ◄── Human-in-the-Loop Orchestration
└─────────────────────────────────┘
                 │
                 ▼
       Unified Validation Report
```

### 🔍 Stage 1: Retrieval and Re-ranking Engine
Leverages Agentic Retrieval-Augmented Generation to scan compliance contexts, engineering rulesets (ISO 29148, ISO 25010, INCOSE, Volere), and domain repositories. It heavily filters background noise and scores incoming knowledge contexts based on direct validation utility rather than shallow semantic similarity.

### 🛠️ Stage 2: Semantic Quality Validation
Executes high-precision structural text analysis to discover classic requirements engineering flaws. Monitored criteria span:
*   **Ambiguity & Vagueness**
*   **Completeness & Necessity**
*   **Consistency & Singularity (Atomicity)**
*   **Verifiability & Feasibility**
*   **Traceability & Uniqueness**

### 📐 Stage 3: Logical Formalization Mapping
Extracts key mathematical requirement constructs—**Actors**, **Actions**, **Objects**, **Conditions**, **Purposes**, and **Obligation Levels**—and transforms raw natural text structures directly into First-Order Logic (FOL) predicates, AULIA formal variables, and clean JSON structural models.

### ⚡ Stage 4: Automated Z3 SMT Verification
Compiles formal logical representations into assertive constraint code blocks executed directly by the Microsoft Z3 SMT Theorem Prover backend. This stage mathematically assesses satisfiability (SAT / UNSAT), automatically maps hidden dependencies, isolates structural conflicts, and flags cross-requirement policy contradictions.

### 📊 Stage 5: Interpretation & Reporting Engine
Aggregates multidimensional semantic findings, solver model variables, traceability signatures, and automated confidence indicators into a comprehensive, human-in-the-loop engineering review report.

---

## 2. Pipeline Execution Examples

### Example 1: Stage 1 Context Selection Output Schema
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

### Example 2: Stage 4 Solver Verification Matrix
*   **Requirement A:** *"Users shall authenticate before accessing reports."*
*   **Requirement B:** *"Users may access reports without authentication."*

```text
// Generated Solver Contradiction Verification Map
AccessReport(User) -> Authenticated(User)
AccessReport(User) -> ¬Authenticated(User)

Z3 Solver Output: UNSAT
Status: Logical Contradiction Detected (Revision Required)
```

---

## 3. Repository Tree Structure

```text
hybrid-requirements-validation-prompts/
├── README.md
├── LICENSE
├── CITATION.cff
├── Manual Document
├── Hybrid AI Framework for Software Requirement Validation.json
│
├── prompts/
│   ├── retrieval_reranking_prompt.md
│   ├── semantic_validation_prompt.md
│   ├── formalization_prompt.md
│   ├── z3_verification_prompt.md
│   └── reporting_prompt.md
│
├── datasets/
│   ├── benchmark_requirements.csv
│   └── validation_results.csv
```

---

## 4. Technical Metadata & Project Citation

### 👥 Investigators and Supervisory Team
*   **Principal Investigator:** Antonio Soares Martins
    *   **ORCID:** [0009-0006-9958-2136](https://orcid.org/0009-0006-9958-2136)
*   **Supervisor:** Pedro Salgueiro
    *   **ORCID:** [0000-0001-7614-2951](https://orcid.org/0000-0001-7614-2951)
*   **Supervisor:** Vítor Nogueira
    *   **ORCID:** [0000-0002-0793-0003](https://orcid.org/0000-0002-0793-0003)

### 🔬 Research Domains
Requirements Engineering, Formal Verification Methods, Large Language Models, Agentic RAG Frameworks, SMT Logic Solver Architectures.

### 📚 Consolidated BibTeX (2026)
```bibtex
@misc{martins2026hybridrequirementsvalidation,
  title={A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic},
  author={Martins, Antonio Soares and Salgueiro, Pedro and Nogueira, Vítor},
  year={2026},
  publisher={GitHub},
  repository={Hybrid Requirements Validation Prompts}
}
```