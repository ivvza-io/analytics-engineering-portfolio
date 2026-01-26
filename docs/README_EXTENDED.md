# Analytics Engineering Portfolio — Internal Notes
**Analytical Rationale, Design Decisions, and Modeling Philosophy**

---

## 1. Purpose of This Document

This document captures the internal analytical rationale behind the portfolio.

It is not intended as a public overview or marketing material.
Its purpose is to document:

- analytical intent
- design decisions 
- trade-offs
- constraints 
- exit criteria (at the portfolio level)

In short: **how and why decisions were made**, not just what was built.

---

## 2. Industrial Motivation

This work originated from a real quality problem in a flat-rolled aluminum operation.

Despite operating within Aluminum Association (AA) specification limits, the organization experienced recurring quality issues and customer claims related to mechanical performance variability—materials perceived as too hard, too soft, or unstable in downstream forming.

Root cause analysis revealed a structural gap:
- No internal chemistry standards
- No internal mechanical property targets  
- Release decisions driven by compliance rather than design intent

**The core problem:** External specifications define **allowable ranges**, not **operational targets**. Without internal standards, the organization could not distinguish between chemistries that were merely acceptable versus chemistries that were operationally robust.

Physical trial campaigns to define internal standards were economically and operationally constrained. This portfolio explores whether **data-driven modeling** could serve as a complementary design tool to define conservative, defensible internal standards under uncertainty.

**Note on public vs. internal outcomes:**  
Operational impact is described qualitatively in this public portfolio. Quantitative metrics and proprietary implementation details remain internal.

---

## 3. Central Question of the Portfolio

> *How can industrial data be transformed into analytical models that engineers can trust and actually use to define design standards and reduce risk?*

This portfolio treats data engineering, analytics, and modeling as a **single system**, not isolated steps.

**The answer demonstrated here:**
1. Build reproducible data foundations first (SC01)
2. Validate signal exists before adding complexity (SC02-SC04)
3. Make uncertainty explicit in decision tools (SC05)
4. Enforce consistency through shared conventions (this document + toolkit)

---

## 4. Portfolio as a System - Architecture-Level View

This portfolio is structured as a pipeline of analytical capability:

1. **Reproducible data foundation**   
Industrial data is transformed into stable, traceable analytical entities with explicit grain.

2. **Semantic layer as the analytical interface**   
SQL-based semantic views are treated as **first-class analytical artifacts**—the “API” that analysis and modeling consume.

3. **Modeling as disciplined experimentation**   
Modeling is used to validate signal, characterize uncertainty, and understand what is explainable under real constraints.

4. **Decision tools as the end product**  
The highest-value outputs are not model objects or coefficients, but **decision-ready artifacts** (standards, robust regions, conservative maps).

---

## 5. Core Analytical Principles

### 5.1 Reproducibility before modeling

No modeling work is performed without:
- a clearly defined data grain
- stable semantics
- traceability back to raw data

SQL-based semantic layers are treated as **first-class analytical artifacts**.

---

### 5.2 Signal before sophistication

The portfolio intentionally starts with:
- simple baselines
- limited feature sets
- conservative modeling choices

The objective is to understand:
- what is explainable,
- where uncertainty originates,
- and what the natural limits of prediction are.

Complexity is introduced only when it clearly earns its place.

---

### 5.3 Uncertainty is part of the answer

Point predictions are insufficient for engineering decisions.

Throughout the portfolio:
- calibration,
- out-of-fold error,
- and stability across operating regimes

are treated as **core analytical outputs**, not optional add-ons.

---

### 5.4 Engineering value over metric optimization

Model performance is evaluated through:
- robustness,
- interpretability,
- and consistency under real constraints.

Marginal metric improvements are not prioritized unless they translate into meaningful reductions in risk or variability.

---

## 6. Portfolio-Wide Method Conventions

This section defines shared conventions used across study cases to ensure comparability and to prevent “moving goalposts” across analyses.

### 6.1 Grain policy - analytical unit

- The default analytical unit is **heat-level grain** unless explicitly stated otherwise.
- Any transformation that changes grain must be declared and justified (e.g., lab-session → heat aggregation, pivoting).
- Grain is treated as a contract: *one row per unit* in analysis-ready datasets.

### 6.2 Validation policy - leakage prevention

- Validation is **group-aware** where appropriate, using heat identifiers as grouping variables.
- This prevents leakage from near-duplicate observations that share production context.

### 6.3 Evaluation policy - OOF-first discipline

- All reported performance is based on **out-of-fold (OOF)** predictions.
- In-sample performance is not used for conclusions or decision artifacts.

### 6.4 Metric policy - risk-aware reporting

Model evaluation prioritizes:
- **MAE** for central error tendency
- **P95 absolute error** (or comparable tail metric) for worst-case risk

Rationale:
- Engineering decisions are dominated by tail behavior and rare failures, not average performance.

### 6.5 Uncertainty policy - conservative by design

Uncertainty is treated as an explicit modeling output.
When uncertainty margins are used to create decision artifacts (e.g., design maps), the portfolio favors:

- conservative margins derived from OOF residual behavior
- interpretability over locally adaptive complexity
- explicit guardrails for domain validity

Formal uncertainty methods may be discussed when relevant, but decisions are justified primarily through *empirical OOF behavior* and engineering defensibility.

---

## 7. Documentation Policy

This portfolio intentionally separates narrative layers to reduce duplication and maintain clarity.

### 7.1 What belongs in each artifact

**Public README — decision layer**
- problem framing and decision objective
- minimal, decision-relevant evidence 
- operational guidance (how to use / when not to use, where relevant)
- explicit limitations and guardrails

**Technical Notes (per Study Case) — audit layer**
- data contracts and filters
- detailed diagnostics (fold stability, sensitivity checks)
- extended tables and methodology details
- failure modes and mitigations

**Notebooks — evidence layer**
- full analysis code and exploration
- complete figure set
- experiment variants and intermediate outputs

---

## 8. Study Case Map

Each study case answers a question raised by the previous one and extends the portfolio system.

- **SC01 — Reproducible Data Foundation**   
Builds the SQL semantic layer and establishes traceable, deterministic analytical consumption.

- **SC02 — Chemistry-Only Predictive Signal**
Validates that chemistry contains usable signa   l for UTS and establishes OOF-driven evaluation and risk-aware error reporting.

- **SC03 — Generalization Across Alloy Systems**   
Demonstrates that the framework generalizes structurally across systems, while functional behavior remains system-dependent.

- **SC04 — Variable Influence Screening**   
Evaluates whether commonly measured, metallurgically motivated process variables provide incremental predictive signal beyond chemistry.

- **SC05 — Uncertainty-Aware Engineering Design Tools**   
Translates validated models into conservative design maps and robust decision regions by making uncertainty explicit.

---

## 9. Assumptions and Scope Boundaries

- Industrial data reflects inherent variability and partial observability.
- Not all physical mechanisms are measured.
- Data quality reflects real production conditions.
- Models support decisions; they do not replace engineering judgment.
- Outputs are valid only within supported operating domains unless explicitly revalidated.

---

## 10. What This Portfolio Prioritizes

This portfolio **prioritizes** trust, interpretability, and operational deployment over:

- **State-of-the-art benchmarks**  
  Benchmarks are designed for different objectives (public datasets, standardized splits, metric optimization). Industrial decision support requires different trade-offs.

- **Model complexity**  
  Complex models reduce transparency and complicate maintenance. For engineering decision tools, interpretability is a requirement, not a nice-to-have.

- **Exotic algorithms**  
  Novel algorithms are valuable in research contexts, but production systems benefit from well-understood, robust approaches that engineers can trust.

- **Metric optimization without context**  
  Improving MAE by 0.5 MPa means nothing if it doesn't reduce tail risk or improve decision quality. Metrics must translate to engineering value.

These are **intentional trade-offs** appropriate for industrial decision support systems where:
- Decisions have real consequences (quality claims, production disruptions)
- Stakeholders must understand and trust the tools
- Models must remain maintainable over years, not months

---

## 11. Analytical Architecture and Reuse Strategy

### 11.1 Portfolio Structure

This portfolio is structured as a set of independent but methodologically aligned study cases.

To keep notebooks focused on analysis, interpretation, and decisions — rather than repeated boilerplate — a **shared analytics toolkit** is used across study cases.

## 11. Analytical Architecture and Reuse Strategy

### 11.1 Portfolio Structure

This portfolio is structured as a set of independent but methodologically aligned study cases.

To keep notebooks focused on analysis, interpretation, and decisions — rather than repeated boilerplate — a **shared analytics toolkit** is used across study cases.

### 11.2 The Portfolio Analytics Toolkit

**Repository:** [`portfolio-analytics-toolkit`](https://github.com/ivvza-io/portfolio-analytics-toolkit)

This toolkit:
- encapsulates reusable analytical primitives (OOF generation, metrics, grids, uncertainty margins, plotting),
- enforces consistent validation and evaluation patterns across study cases,
- improves auditability by reducing copy-pasted logic,
- and enables notebooks to focus on **what** was analyzed, not **how** boilerplate was implemented.

The toolkit is intentionally:
- **lightweight** — minimal dependencies, focused scope
- **notebook-first** — designed for interactive analysis, not production deployment
- **portfolio-scoped** — not a general-purpose library

**What it is not:**
- Not a general-purpose ML library
- Not a deployment framework
- Not meant for standalone use outside this portfolio

### 11.3 Dataset Loading Convention

Public datasets follow a standardized layout:
```
data/public/
  <dataset_id>/
    dataset.parquet  # or dataset.csv
```

Example: `data/public/sc02/dataset.parquet`

This convention enables:
- Notebooks to be executed from `notebooks/` without path resolution issues
- Consistent data loading: `load_public_dataset("sc02")`
- Clear separation between public (shareable) and internal (proprietary) data

### 11.4 Study Case Independence

Each study case:
- defines its own execution environment (`requirements.txt`)
- documents its own reproducibility instructions (`HOW_TO_RUN.md`)
- consumes only the toolkit utilities required for that specific analysis

This separation preserves:
- **methodological consistency** at the portfolio level,
- while keeping each study case **self-contained and reproducible**.

### 11.5 Versioning and Reproducibility

The toolkit uses **semantic versioning** aligned with study case releases.

Each study case pins its toolkit version in `requirements.txt`:
```txt
portfolio-analytics-toolkit @ git+https://github.com/ivvza-io/portfolio-analytics-toolkit.git@v1.0.0
```

This ensures:
- Running SC02 notebooks today uses the same toolkit version as when published
- Toolkit updates don't break previously published study cases
- Clear traceability between study cases and toolkit versions

**Current mapping:**
- `v1.0.0` — SC01-SC05 baseline release

---

## 12. Final Notes

> **Complexity is not a goal. Insight, trust, and decision value are.**

This portfolio is designed to demonstrate system-level thinking, disciplined model design, and the ability to translate uncertainty-aware analytics into real engineering decisions.
