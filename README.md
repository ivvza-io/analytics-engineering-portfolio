# Analytics Engineering Portfolio  
**From Industrial Data to Decision-Ready Standards Under Uncertainty**

---

## Executive Thesis

This portfolio documents how **industrial manufacturing data** can be transformed into:

- reproducible analytics foundations,
- conservative and interpretable analytical models,
- and **decision-ready engineering tools**,

used to define **internal standards** and reduce operational risk **under uncertainty**.

The work reflects system-level thinking at the intersection of **analytics engineering**, **applied data science**, and **industrial decision support**.

![Robust chemistry design map illustrating conservative decision regions](assets/sc5_design_map.png)

*Example of a human-readable, uncertainty-aware chemistry design map.
The surface represents a conservative estimate of mechanical performance, while the highlighted target line indicates compositions that meet the design criterion with an explicit safety margin. This map illustrates how analytical models are translated into practical decision tools rather than point predictions.*

>The work reflects system-level thinking at the intersection of **analytics engineering**, **applied data science**, and **industrial decision support**.
> In comparable industrial operations, this approach could deliver $250K-$800K annually through quality claim reduction, trial optimization, and faster standardization. Specific operational results remain proprietary.

---

## Industrial Problem Context

This portfolio originated from a real quality problem in a flat-rolled aluminum operation.

Despite operating within AA specification limits, the organization experienced recurring quality issues and customer claims driven by **mechanical performance variability materials** perceived as too hard, too soft, or unstable in downstream forming.

Root cause analysis revealed a structural gap:

- absence of internal chemistry standards,
- absence of internal mechanical performance targets,
- release decisions driven by compliance rather than design intent.

Physical trial campaigns to define internal standards were costly and operationally constrained.  
This portfolio explores whether **data-driven modeling** can act as a complementary design tool to define **conservative, defensible internal standards**.

---

## What This Portfolio Demonstrates

Rather than isolated projects, this portfolio demonstrates the ability to design and connect:

- **Reproducible data foundations**  
  Stable analytical semantics, explicit grain, and traceability.

- **Disciplined modeling pipelines**  
  Signal validation, leakage-aware evaluation, and conservative assumptions.

- **Uncertainty-aware decision tools**  
  Translating models into artifacts engineers can actually use.

The emphasis is not on algorithmic novelty, but on **trust, robustness, and decision value**, supporting standards definition, **risk reduction**, and **process stability**.

---

## Portfolio Structure (System View)

Each study case answers a question raised by the previous one. Together, they form a coherent analytical system:

### SC01 — Reproducible Analytics Foundation  
**From Excel-based analysis to a SQL semantic layer**

Designs a reproducible analytics foundation by replacing spreadsheet workflows with a SQL-based semantic layer that enforces grain, semantics, and traceability.   
[View Study Case →](https://github.com/ivvza-io/sc01-from-excel-to-sql-analytics)

→ Establishes the conditions required for trustworthy downstream analysis.

---

### SC02 — Chemistry-Only Predictive Signal  
**Can chemistry alone support conservative UTS standards?**

Validates that chemistry contains meaningful, calibratable signal for UTS using simple, interpretable models and group-aware, out-of-fold evaluation.   
[View Study Case →](https://github.com/ivvza-io/sc02-chemistry-only-mechanical-properties)

→ Demonstrates that internal standards can be grounded in data.

---


### SC03 — Generalization Across Alloy Systems  
**Does the framework generalize beyond a single system?**

Applies the same modeling pipeline across alloy systems to test generalization in principle, revealing system-dependent functional behavior.   
[View Study Case →](https://github.com/ivvza-io/sc03-chemistry-generalization-across-systems)

→ Establishes modeling approaches as transferable frameworks, not fixed formulas.

---

### SC04 — Variable Influence Screening  
**Does added complexity actually reduce uncertainty?**

Evaluates whether commonly measured, metallurgically motivated process variables provide incremental predictive value beyond chemistry.  
[View Study Case →](https://github.com/ivvza-io/sc04-variable-influence-screening)

→ Demonstrates disciplined restraint: complexity must earn its place.

---

### SC05 — Uncertainty-Aware Design Maps  
**Turning models into decision-ready engineering tools**

Transforms validated chemistry-only models into conservative design maps with explicit uncertainty margins and operational guardrails.   
[View Study Case →](https://github.com/ivvza-io/sc05-uncertainty-aware-design-maps)

→ Translates analytics into human-readable, uncertainty-aware standards and decision-support tools.

---

## How to Navigate the Portfolio

- **README (per Study Case)**  
  Executive-level, decision-oriented summaries with minimal but sufficient evidence.

- **Technical Notes (per Study Case)**  
  Detailed methodology, diagnostics, extended tables, and audit-level discussion.

- **Notebooks**  
  Full analytical evidence: code, experiments, and intermediate outputs.

- **README_EXTENDED — Analytical System and Design Philosophy**  
  Documents portfolio-wide analytical principles, validation conventions, and design rules.  
  [Read the extended documentation →](docs/README_EXTENDED.md)

- **[Analytics Toolkit](https://github.com/ivvza-io/portfolio-analytics-toolkit)** *(separate repository)*  
  Shared utilities used across notebooks to enforce consistent validation, metrics, and plotting patterns.

## Quick Start for Reviewers

> **Short on time?** Optimal reading paths:

- **5 min:** This overview + [Design Philosophy](#design-philosophy-summary) below
- **15 min:** Jump to [SC05](https://github.com/ivvza-io/sc05-uncertainty-aware-design-maps) — see final decision-ready design tools
- **30 min:** Read [SC02](https://github.com/ivvza-io/sc02-chemistry-only-mechanical-properties) + [SC01](https://github.com/ivvza-io/sc01-from-excel-to-sql-analytics) — analytical foundation
- **Full review:** [Portfolio Design Documentation](docs/README_EXTENDED.md) — methodology and conventions

---

## Design Philosophy

This portfolio is built on four principles:

1. **Reproducibility before modeling** — No analysis without stable data semantics and explicit grain
2. **Signal before sophistication** — Validate signal exists before adding complexity
3. **Uncertainty as a first-class output** — Point predictions are insufficient for engineering decisions
4. **Engineering value over metric optimization** — Models exist to support decisions, not optimize leaderboards

> Detailed methodology and analytical conventions: [Portfolio Design Documentation](docs/README_EXTENDED.md)

---

## What This Portfolio Is — and Is Not

### This portfolio *is*:
- Industrially grounded and decision-oriented
- Conservative by design
- Focused on trust, robustness, and interpretability
- Representative of senior-level analytical ownership

### This portfolio is *not*:
- A benchmark-chasing exercise
- A collection of exotic algorithms
- An academic modeling showcase
- Metric optimization without operational context

---

## Intended Audience

This work is most relevant for:

- Hiring managers evaluating **Senior Data Scientist / Analytics Engineer** profiles
- Industrial analytics and data platform teams
- Organizations operating under real variability, constraints, and risk

---

## Closing Statement

> **Complexity is not the goal.  
> Insight, trust, and decision value are.**

This portfolio demonstrates how disciplined analytics engineering and uncertainty-aware modeling can be used to define **defensible internal standards** and support real engineering decisions.

---

### Next Steps

Each study case can be explored independently, but the full value emerges when read as a system, from data foundations to decision tools.

Start with [**SC01**](https://github.com/ivvza-io/sc01-from-excel-to-sql-analytics.git) for context, or jump directly to [**SC05**](https://github.com/ivvza-io/sc05-uncertainty-aware-design-maps) to see the end-state.
