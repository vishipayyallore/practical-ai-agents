---
name: workspace-review
description: Comprehensive workspace review for Customer Churn Prediction ML — structure, data governance, CI, notebook quality, and src module standards.
---

# Workspace Review — Customer Churn Prediction ML

## Protocol

1. Read `.github/copilot-instructions.md` (data governance, notebook standards, `data/raw/` read-only).
2. Compare the tree to `docs/01-repository-structure.md` and `README.md`.
3. Python: `uv sync` at repo root; `uv run …` per `pyproject.toml` / CI.
4. **Data governance:** `data/raw/` is read-only — no modifications allowed.
5. **Notebook quality:** numbered correctly (`01_` through `05_`); markdown concept cells before code; reproducible seeds; clean kernel runs.
6. **src modules:** each subfolder (`data_preprocessing/`, `feature_engineering/`, `modeling/`, `evaluation/`) contains focused, typed, documented Python modules.
7. Run the **ci-checks** skill (Python + notebook JSON + markdownlint + optional Lychee).
8. Optionally run **docs-verification**.
9. **Skills parity:** `.github/skills/**` ↔ `.cursor/skills/**` byte-identical.
10. **Agents parity:** `.github/agents/**` ↔ `.cursor/agents/**` byte-identical.

## Output

Critical / Major / Minor findings; CI summary; doc accuracy notes.

**Governance integrity (primary):** do not bulk-edit copilot, rules, skills, or agents without commits and mirror-safe diffs.
