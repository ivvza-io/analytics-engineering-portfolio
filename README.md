# SQL & Analytics Engineering Portfolio  
**From Reproducible Data Models to Engineering Design Tools**

---

## Overview

This repository presents a curated portfolio of analytics and modeling study cases built on real industrial metallurgy data.

The focus is not on isolated machine learning experiments, but on **end-to-end analytical reasoning**:
from reproducible data modeling, through conservative predictive analysis, to **engineering-ready decision tools**.

All study cases originate from a real manufacturing problem and are organized as a **coherent analytical roadmap**, not as standalone demos.

---

## Real-World Motivation

This work originated in a flat-rolled aluminum manufacturing environment facing recurring quality issues and external customer claims.

Despite meeting industry standards (AA specifications), materials exhibited:
- unstable mechanical performance,
- excessive variability,
- downstream processing issues,
- and inconsistent customer outcomes.

Root cause analysis revealed a structural gap:
- no internal chemistry design standards,
- no internal mechanical targets,
- and decisions driven solely by specification compliance rather than performance robustness.

Physical trial campaigns to define better standards were impractical due to cost and operational risk.

The objective of this portfolio is therefore:

> **To show how industrial data can be used to define internal design ranges and decision tools that reduce risk, without relying on extensive physical experimentation.**

---

## What This Portfolio Demonstrates

- Designing **reproducible SQL-based semantic layers** for industrial analytics
- Treating data modeling as an analytical discipline
- Evaluating predictive signal **before increasing model complexity**
- Quantifying uncertainty and tail risk
- Translating models into **engineering decision tools**
- Prioritizing **interpretability, robustness, and decision value** over metric optimization

---

## Portfolio Roadmap

Each study case answers a specific question raised by the previous one.

| Study Case | Focus |
|-----------|-------|
| **SC1** | From spreadsheets to a reproducible SQL analytics foundation |
| **SC2** | Chemistry-only baseline predictive modeling |
| **SC3** | Generalization across alloy systems |
| **SC4** | Screening which additional variables are worth measuring |
| **SC5** | Uncertainty-aware chemistry design maps for engineering decisions |

The cases are intended to be read **in order**, but each one is self-contained.

---

## Technologies & Stack

- **PostgreSQL** — data modeling and semantic layer  
- **SQL** — staging, cleaning, analytics-ready views  
- **Python** — analysis, modeling, uncertainty quantification  
- **Git** — versioned, reproducible workflows  

---

## Guiding Principles

**Data before models**  
Trustworthy analysis starts with a clearly defined data grain and stable semantics.

**Signal before complexity**  
Simple models are explored first to understand predictive limits and uncertainty sources.

**Uncertainty is part of the answer**  
Engineering decisions require calibrated uncertainty, not just point predictions.

**Engineering value over peak performance**  
Models are evaluated by robustness, interpretability, and decision usefulness, not by chasing metric performance.

---

## Intended Audience

This portfolio is relevant for:
- Data scientists working with **industrial or physical systems**
- Analytics engineers bridging SQL, modeling, and decision-making
- Process, product, or materials engineers interested in analytics
- Hiring managers evaluating **end-to-end analytical maturity**

---

## What This Portfolio Is Not

This is intentionally **not**:
- a benchmark-focused ML portfolio,
- a collection of advanced algorithms,
- or a demonstration of model complexity for its own sake.

It is a demonstration of how analytics can:
- build trust in data,
- define predictive limits,
- justify complexity incrementally,
- and support real engineering decisions.

---

## Status

> This repository is under active development.  
> Study cases will be added and refined following the roadmap above.
