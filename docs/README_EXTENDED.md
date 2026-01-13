# Analytics Engineering Portfolio — Internal Notes  
**Analytical Rationale, Design Decisions, and Modeling Philosophy**

---

## Purpose of This Document

This document captures the internal analytical rationale behind the portfolio.

It is not intended as a public overview or marketing material.
Its purpose is to document:

- analytical intent
- design decisions
- trade-offs
- constraints
- exit criteria

In short: **how and why decisions were made**, not just what was built.

---

## Industrial Motivation

This work originated from a real quality problem in a flat-rolled aluminum operation.

Despite operating within AA specification limits, the organization experienced recurring quality issues and customer claims related to mechanical performance variability (materials perceived as too hard, too soft, or unstable in downstream forming).

Root cause analysis revealed a structural gap:
- no internal chemistry standards,
- no internal mechanical performance targets,
- and release decisions driven by compliance rather than design intent.

Physical trial campaigns to define internal standards were economically and operationally constrained. This portfolio explores whether data-driven modeling could serve as a complementary design tool to define conservative, defensible design ranges under uncertainty.

---

## Central Question of the Portfolio

> *How can industrial data be transformed into analytical models that engineers can trust and actually use to define design standards and reduce risk?*

This portfolio treats data engineering, analytics, and modeling as a **single system**, not isolated steps.

---

## Core Analytical Principles

### Reproducibility before modeling

No modeling work is performed without:
- a clearly defined data grain
- stable semantics
- traceability back to raw data

SQL-based semantic layers are treated as **first-class analytical artifacts**.

---

### Signal before sophistication

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

### Uncertainty is part of the answer

Point predictions are insufficient for engineering decisions.

Throughout the portfolio:
- calibration,
- out-of-fold error,
- and stability across operating regimes

are treated as **core analytical outputs**, not optional add-ons.

---

### Engineering value over metric optimization

Model performance is evaluated through:
- robustness,
- interpretability,
- and consistency under real constraints.

Marginal metric improvements are not prioritized unless they translate into **meaningful reductions in risk or variability**.

---

## Industrial Outcome

The analytical framework developed in this portfolio was applied to define internal chemistry standards for selected alloy systems.

These standards replaced specification-only release criteria and contributed to a significant reduction in quality claims.  
More importantly, they enabled a shift toward **process stability–driven improvement**, providing a structured basis for subsequent optimization efforts.

---

## Narrative Flow Between Study Cases

Each study case exists to answer a question raised by the previous one.

---

## Study Case 1 — Reproducible Data Foundation

### Question  
**Can industrial analytics be made reproducible, trustworthy, and decision-ready?**

### Context  
Initial analytics relied on spreadsheets and ad-hoc data extracts, with:
- unclear data grain,
- inconsistent joins,
- manual wrangling,
- limited traceability.

This made downstream modeling fragile and difficult to defend.

### Key Decisions
- Replace spreadsheet workflows with a SQL-based semantic layer.
- Treat data modeling as an analytical task.
- Explicitly define heat-level grain.
- Encode domain assumptions directly in SQL views.

### Exit Condition  
Analytics outputs can be reproduced deterministically from raw data without manual intervention.

---

## Study Case 2 — Chemistry-Only Predictive Signal

### Question  
**Does chemistry alone contain usable and calibratable predictive signal for UTS?**

### Context  
Before defining internal standards, it was necessary to verify that chemistry provided a meaningful and quantifiable link to mechanical performance.

### Key Decisions
- Use chemistry-only features.
- Select UTS as a representative target.
- Favor simple, interpretable models (ridge and polynomial).
- Use group-aware validation and out-of-fold error.

### Exit Condition  
Chemistry-only models demonstrate consistent, calibratable predictive signal suitable for conservative interpretation.

---

## Study Case 3 — Generalization Across Alloy Systems

### Question  
**Does the chemistry-only approach generalize across alloy systems?**

### Context  
A single-alloy model is insufficient for defining internal standards.

### Key Decisions
- Reuse the exact SC2 pipeline.
- Avoid new modeling techniques.
- Compare systems, not architectures.
- Focus on functional behavior, not just metrics.

### Exit Condition  
Chemistry-only modeling generalizes in principle, while revealing system-dependent functional behavior.

---

## Study Case 4 — Variable Influence Screening

### Question  
**Which additional variables are worth measuring beyond chemistry?**

### Context  
Before building a full process-aware model, it was necessary to evaluate whether added complexity would meaningfully reduce uncertainty.

### Key Decisions
- Restrict to a single alloy system.
- Freeze the chemistry-only baseline.
- Incrementally add variables based on process knowledge.
- Evaluate both average error and tail risk (P95 absolute error).

### Exit Condition  
Clear identification of variables that do **not** justify additional complexity under conservative evaluation.

---

## Study Case 5 — Uncertainty-Aware Engineering Design Tools

### Question  
**How can validated models be translated into tools engineers can actually use?**

### Context  
The goal was never point prediction, but the definition of **conservative chemistry design ranges** to replace specification-only release criteria.

Mathematical model equations are not practical decision interfaces for engineering teams.

### Key Decisions
- Treat models as constraint generators, not predictors.
- Layer uncertainty using out-of-fold residuals.
- Translate models into 2D chemistry design maps.
- Favor ridge regression for smooth, stable design surfaces.
- Define robust regions relative to target UTS.

### Exit Condition  
Model outputs support concrete engineering decisions and were used to define internal chemistry standards, contributing to a measurable reduction in customer claims and enabling process-stability-driven improvement.

---

## Assumptions and Scope Boundaries

- Industrial data reflects inherent variability and partial observability.
- Not all physical mechanisms are measured.
- Data quality reflects real production conditions.
- Models support decisions; they do not replace engineering judgment.

---

## What This Portfolio Intentionally Avoids

This portfolio does **not** aim to:
- chase state-of-the-art benchmarks,
- maximize model complexity,
- demonstrate exotic algorithms,
- optimize metrics without interpretability.

These choices are deliberate.

---

## Final Notes

> **Complexity is not a goal. Insight, trust, and decision value are.**

> This portfolio is designed to demonstrate system-level thinking, disciplined model design, and the ability to translate uncertainty-aware analytics into real engineering decisions.