# Repository skills (Customer Churn Prediction ML)

This file is **local to `customer-churn-prediction-ml`**. It complements `.cursor/rules/*.mdc` and `.github/copilot-instructions.md` with concise guidance for assistants editing this repo.

**Strict scope:** Swamy PKV's personal project only — see `README.md` and `.cursor/rules/swamy_personal_learning_only.mdc`.

**Bundled agent skills:** `.github/skills/` is canonical; `.cursor/skills/` is a **byte-identical mirror** (see `.github/skills/README.md`). Bundles: **`churn-project`**, **`churn-workflow`**, **`ci-checks`**, **`docs-verification`**, **`workspace-review`**, **`e2e-testing`**. Pushes under skills paths run **`.github/workflows/ci-skills-parity.yml`**; agent-facing path changes also run **`.github/workflows/ci-agent-docs-guard.yml`**.

**Governance integrity (primary):** Commit or stash before another tool touches copilot, rules, skills, agents, or `CLAUDE.md`; keep `.github/skills` ↔ `.cursor/skills` and agent mirrors in one change; prefer small diffs. **Secondary (restore only if damaged):** **`docs/agent-governance-recovery.md`**.

**Project subagents:** **`churn-ci-verify`** (CI-aligned checks), **`churn-workflow-review`** (notebook step audit), **`churn-analysis-review`** (analysis quality pass).

---

## Project structure

```text
data/raw/          — immutable source datasets (read-only)
data/processed/    — cleaned and transformed outputs
notebooks/         — numbered workflow notebooks (01–05)
src/               — reusable Python modules (data_preprocessing, feature_engineering, modeling, evaluation)
reports/figures/   — exported charts and report outputs
docs/              — project documentation
```

See `docs/01-repository-structure.md`.

---

## CI expectations

- **Python:** `uv sync`, isort / black / flake8, notebook JSON — `ci-python.yml`.
- **Docs:** Markdown lint and Lychee — `ci-documentation.yml`.
- **Parity / guard:** `.github/skills/` ↔ `.cursor/skills/`; **`.github/agents/` ↔ `.cursor/agents/`**; **`ci-agent-docs-guard.yml`** when `.cursor/`, `.github/` skills or agents, or `CLAUDE.md` change.

Use the **`ci-checks`** skill for exact local commands.
