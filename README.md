# AI Reasoning — Reasoning Under Governance

Governance-first · auditable · reproducible · human-accountable  
Built for **MBA / Master of Finance cohorts** and **professional finance / corporate finance / trading / research practitioners** who need mechanism clarity under constraint.

---

## What this repository is

This repository is the governed home of **AI Reasoning**: a Colab-first laboratory for designing and reviewing **reasoning systems** as **controlled inference mechanisms**—not “smart chat.”

The objective is not “better outputs.”  
The objective is **reviewable reasoning**: a pipeline that behaves like a contract—explicit state, explicit routing, explicit constraints, explicit termination, explicit artifacts—so an independent reviewer can answer:

- what inputs were used (and what was excluded)
- what the system inferred (and what it refused to infer)
- what is **fact vs assumption vs open item**
- what steps were taken and why
- where the system stopped and what triggered escalation
- whether acceptance gates were met (or why they failed)

This repo is intentionally explicit about limits:

- it does **not** claim production readiness by default
- it does **not** claim correctness of external facts
- it does **not** treat generated narratives as evidence
- it does **not** promise performance, alpha, or deployability

**Core premise:**  
**Capability ↑ ⇒ Risk ↑ ⇒ Controls ↑**

---

## Repository structure (as in this repo)

- **/book/**  
  The book source. The book is the governing spec: definitions, mechanisms, failure modes, acceptance gates.

- **/notebooks/**  
  The governed laboratories that operationalize the book with deterministic setups, diagnostics, and mandatory artifacts.

---

## The book (PDF)

- **AI REASONING BOOK (PDF):**  
  https://github.com/alexdibol/ai-reasoning/blob/main/book/AI%20REASONING%20BOOK.pdf

---

## The notebooks (URL structure)

Each chapter notebook lives at:

- https://github.com/alexdibol/ai-reasoning/blob/main/notebooks/CHAPTER%201.ipynb  
- https://github.com/alexdibol/ai-reasoning/blob/main/notebooks/CHAPTER%202.ipynb  
- …and so on.

---

## The book structure (5 chapters)

This repository is organized to match the book exactly.  
Each chapter has corresponding governed notebooks.

### Chapter 1 — Why Reasoning Needs Governance
Reasoning systems feel authoritative because they “explain.” In professional settings, that is precisely why they require governance: persuasive chains can hide unsupported leaps, “clean” narratives can bury uncertainty, and confident structure can mask missing evidence.

Chapter 1 formalizes:
- reasoning as **controlled inference**, not storytelling
- “generation ≠ verification” as a non-negotiable discipline
- facts vs assumptions vs open items as a first-class requirement
- baseline failure modes: invented premises, silent assumption creep, scope drift, irreproducible runs

Deliverable expectation:
- a reviewer can reconstruct decisions from artifacts, not from persuasion

### Chapter 2 — Chains: Stepwise Reasoning as a Contract
Chains are the simplest reasoning shape: a bounded sequence of steps with explicit intermediate state. They are also the easiest to fake—unless governance forces every step to bind to declared inputs and constraints.

Chapter 2 operationalizes:
- explicit step structure (what each step is allowed to do)
- stateful logging of intermediate claims and dependencies
- “stop-if” conditions for missing evidence
- structured outputs that preserve uncertainty rather than smoothing it away

Deliverable expectation:
- each step is inspectable; leaps are forbidden by design

### Chapter 3 — Trees: Branching Scenarios and Decision Topologies
Professional decisions are rarely linear. Trees express competing hypotheses, scenarios, and paths. Governance ensures branching expands clarity—not confusion—and preserves the reasons paths were explored or pruned.

Chapter 3 operationalizes:
- branching rules (when to branch, how many branches, how to prune)
- scenario hygiene (distinct assumptions per branch, no cross-contamination)
- explicit comparison criteria (what “wins,” what fails, why)
- artifacted decision topology (so reviewers can see the explored space)

Deliverable expectation:
- the system can explain *why* it branched, *why* it pruned, and *why* it selected

### Chapter 4 — Loops: Iterative Refinement With Convergence Discipline
Loops allow refinement, but also invite infinite “try again” cycles and narrative polishing that hides uncertainty. Governance turns loops into controlled convergence: bounded iterations, explicit improvement targets, and hard stops.

Chapter 4 operationalizes:
- bounded iteration counts and termination reasons
- deltas between iterations (what changed, why it changed)
- escalation triggers when the loop cannot close open items
- stability checks across controlled perturbations

Deliverable expectation:
- iteration produces measurable improvement or safe termination—never endless churn

### Chapter 5 — Committees: Multi-Perspective Deliberation With Dissent Preservation
Committees introduce structured disagreement: different roles evaluate the same case with distinct risk lenses. Governance requires that dissent is preserved (not averaged away) and that final decisions show what was accepted, rejected, and escalated.

Chapter 5 operationalizes:
- role definitions (mandates, allowed claims, refusal posture)
- explicit vote/decision schema (including dissent)
- evidence discipline per role (no “committee hallucination”)
- board-facing synthesis that cites artifacts and open items

Deliverable expectation:
- the final output is a governed synthesis with preserved dissent and explicit escalation logic

---

## Notebooks (how they map to the chapters)

The notebooks are not “examples.” They are the operational proof of the book.

- **Chapter 1 notebooks** focus on:
  - scope discipline and evidence posture
  - fact/assumption/open separation
  - deterministic setup and artifact hygiene
  - early termination and escalation posture

- **Chapter 2 notebooks (Chains)** focus on:
  - explicit stepwise state
  - dependency tracking
  - safe stopping and refusal behavior
  - structured intermediate artifacts

- **Chapter 3 notebooks (Trees)** focus on:
  - branching/pruning controllers
  - scenario separation and comparison gates
  - exportable decision topology artifacts

- **Chapter 4 notebooks (Loops)** focus on:
  - bounded iterative refinement
  - convergence targets and delta logs
  - escalation when open items cannot be closed

- **Chapter 5 notebooks (Committees)** focus on:
  - multi-role deliberation with mandates
  - dissent preservation
  - board-facing synthesis with traceable rationale

(Notebook names and exact numbering live in **/notebooks/** and are the lab companion to the corresponding book chapter.)

---

## What every notebook enforces (non-negotiable)

Every notebook must be **reviewable by artifact inspection**. At minimum, each run must produce:

- deterministic behavior under seed where applicable
- explicit **state** (TypedDict or equivalent)
- bounded loops (no unbounded retries)
- explicit termination reasons (stop is a feature)
- explicit separation of:
  - **facts_provided** (supported by available inputs)
  - **assumptions** (declared and justified)
  - **open_items / open_questions** (what must be verified by humans)
- mandatory exported artifacts, including at minimum:
  - `run_manifest.json` (seed, versions, config hash, environment fingerprint)
  - `final_state.json` (what the system believed at the end)
  - `decision.json` (advance / revise / reject + reasons)
  - `risk_log.json` (risks triggered + controls applied)
  - `artifacts/` directory for generated deliverables (reports, tables, exhibits)

This is not extra process.  
This is what makes reasoning **auditable**.

---

## How to use this repository

Recommended posture:

1) Read the relevant **chapter** in **/book/** (mechanism + acceptance rules).  
2) Run the corresponding **notebook(s)** in **/notebooks/** as-is (no edits).  
3) Inspect artifacts: termination reason, open items, scope boundaries, refusal logic.  
4) Stress structurally: reduce evidence, introduce ambiguity, perturb inputs, tighten constraints.  
5) Record failures as artifacts (don’t hand-wave them away).  
6) Modify **one mechanism at a time**, then re-run and compare artifacts.

Operating rule:  
If the system “works” only when you ignore gates, constraints, termination logic, or evidence rules, then it does not work.

---

## Shared governance spine (applies across this repo)

- **Generation ≠ verification**  
  Outputs are **Not verified** until qualified humans validate them.

- **Facts vs assumptions discipline**  
  Facts provided, assumptions made, and open questions are separated explicitly.

- **Scope and boundary control**  
  Clear stop-if rules, escalation paths, and refusal posture where required.

- **Auditability by design**  
  Artifacts enable reconstruction, supervision, and review.

- **Human accountability**  
  Responsibility never leaves the human professional.

---

## IMPORTANT DISCLAIMERS (read before use)

### Educational / Non-Reliance
All materials are provided **for educational and research purposes only**.  
Nothing in this repository constitutes investment, trading, legal, tax, accounting, audit, or compliance advice.

### Not verified
Unless explicitly stated otherwise in a specific artifact, treat all outputs, claims, calculations, citations, and conclusions as **Not verified**.

### Confidentiality and data hygiene
Do not paste confidential, proprietary, regulated, or personally identifying information into external systems.  
Use anonymization/redaction and **minimum-necessary** inputs by default.

### No fabricated sources or claims
Zero tolerance for invented citations, performance claims, fees, terms, or consequences.  
When evidence is missing, the correct output is a **verification task list**, not persuasive narrative.

---

## License (MIT)

This project is released under the **MIT License**.

**Copyright (c) 2026 Alejandro Reynoso**

---

## Contact

Alejandro Reynoso  
Email: areynoso@yahoo.com  
GitHub: https://github.com/alexdibol
