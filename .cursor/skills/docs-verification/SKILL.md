---
name: docs-verification
description: >-
  Verify markdown structure and documentation quality for Practical AI Agents.
  Use when auditing docs, broken links, or README accuracy.
---

# Documentation Verification — Practical AI Agents

## Verification matrix

| Concern | Source of truth | Common errors |
|---|---|---|
| Layout | `README.md` | Missing folders; README not matching actual structure |
| README | `README.md` | Outdated scope; missing sections; incorrect tech stack |
| Docs | `docs/**/*.md` | Broken relative links; stale paths |
| Notebooks | `notebooks/` | Wrong naming convention; dirty kernel state |
| src modules | `src/` | Wrong subfolder placement; missing type hints or docstrings |
| Reference materials | `references/` | References modified; wrong folder placement |
| ADRs | `docs/adr/` | Missing rationale; outdated decisions |

## Output format

Use a table: **File | Status | Issues**. Concrete paths only; offer fixes when requested.
