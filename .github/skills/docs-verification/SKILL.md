---
name: docs-verification
description: Verify markdown structure and documentation quality for Customer Churn Prediction ML. Use when auditing docs, broken links, or README accuracy.
---

# Documentation Verification — Customer Churn Prediction ML

## Verification matrix

| Concern | Source of truth | Common errors |
|--------|-----------------|---------------|
| Layout | `docs/01-repository-structure.md`, `README.md` | Missing folders; README not matching actual structure |
| README | `README.md` | Outdated status; missing sections; incorrect tech stack |
| Docs | `docs/**/*.md` | Broken relative links; stale paths |
| Notebooks | `notebooks/` | Not numbered; wrong naming convention; dirty kernel state |
| src modules | `src/` | Wrong subfolder placement; missing type hints or docstrings |
| Data lifecycle | `data/raw/` vs `data/processed/` | Raw data modified; processed data in wrong folder |
| Reports | `reports/figures/` | Figures missing from expected location |

## Output format

Use a table: **File | Status | Issues**. Concrete paths only; offer fixes when requested.
