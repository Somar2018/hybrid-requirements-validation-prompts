RESEARCH ARTIFACT DOCUMENTATION
Hybrid Framework for Validating Natural Language Software Requirements
1. Overview & Framework Architecture
This repository serves as the official research artifact documentation accompanying the scientific publication:
"A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic"
The engineering suite implements a five-stage verification pipeline designed to minimize classical large language model shortcomings—such as unpredictable hallucinations, domain blindness, or logical inconsistency—by balancing semantic analysis against formal constraint solvers.
2. Multi-Stage Pipeline Specification
Stage 1: Retrieval and Re-ranking Engine
Leverages Agentic Retrieval-Augmented Generation to search compliance contexts, engineering rulesets (ISO 29148, ISO 25010, INCOSE, Volere), and domain repositories. It filters noise and scores incoming knowledge contexts based on direct validation utility rather than shallow semantic similarity.
Stage 2: Semantic Quality Validation
Executes high-precision text analysis to discover classic requirements engineering flaws. Monitored criteria span Ambiguity, Completeness, Consistency, Verifiability, Feasibility, Necessity, Traceability, Correctness, Atomicity, and Uniqueness.
Stage 3: Logical Formalization Mapping
Extracts key requirement constructs (Actors, Actions, Objects, Conditions, Purposes, and Obligation Levels) and transforms raw text structures directly into First-Order Logic (FOL) predicates, AULIA formal variables, and JSON structures.
Stage 4: Automated Z3 SMT Verification
Compiles formal logical models into assertive constraint code blocks executed directly by the Microsoft Z3 SMT Theorem Prover backend. This stage tests mathematical satisfiability (SAT / UNSAT), maps dependencies, isolates conflicts, and identifies cross-requirement policy contradictions automatically.
Stage 5: Interpretation & Reporting Engine
Aggregates semantic finding dimensions, solver models, traceability signatures, and confidence parameters into a comprehensive, human-in-the-loop review report.
3. Pipeline Code Blocks & Examples
Example Stage 1 Context Selection Output Schema
{
  "document_id": "DOC-001",
  "semantic_similarity": 9.1,
  "domain_relevance": 8.7,
  "compliance_relevance": 9.4,
  "overall_score": 9.0,
  "selection_status": "selected"
}

Example Stage 4 Solver Verification Matrix
Requirement A: Users shall authenticate before accessing reports.
Requirement B: Users may access reports without authentication.
// Generated Solver Contradiction Verification Map
AccessReport(User) -> Authenticated(User)
AccessReport(User) -> ¬Authenticated(User)

Z3 Solver Output: UNSAT
Status: Logical Contradiction Detected (Revision Required)

4. Repository Tree Structure
hybrid-requirements-validation-prompts/
├── README.md
├── LICENSE
├── CITATION.cff
├── prompts/
│   ├── retrieval_reranking_prompt.md
│   ├── semantic_validation_prompt.md
│   ├── formalization_prompt.md
│   ├── z3_verification_prompt.md
│   └── reporting_prompt.md
├── datasets/
│   ├── benchmark_requirements.csv
│   └── validation_results.csv
├── Manual Document
├── Hybrid AI Framework for Software Requirement Validation.json


6. Technical Metadata & Citation
Investigators and Supervisory Team:
Principal Investigator: Antonio Soares Martins, ORCID: [https://orcid.org/0009-0006-9958-2136]
Supervisor: Pedro Salgueiro, ORCID: [https://orcid.org/0000-0001-7614-2951]
Supervisor: Vítor Nogueira, ORCID: [https://orcid.org/0000-0002-0793-0003]

Research Domains:
Requirements Engineering, Formal Verification Methods, Large Language Models, Agentic RAG Frameworks, SMT Logic Solver Architectures.  

Consolidated BibTeX (2026): @misc{martins2026hybridrequirementsvalidation,
  title={A Hybrid Framework for Validating Natural Language Software Requirements Using RAG, LLMs, and Formal Logic},
  author={Martins, Antonio Soares and Salgueiro, Pedro and Nogueira, Vítor},
  year={2026},
  publisher={GitHub},
  repository={Hybrid Requirements Validation Prompts}
}
