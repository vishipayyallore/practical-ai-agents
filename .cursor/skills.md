# Repository skills (Practical AI Agents)

This file is **local to `practical-ai-agents`**. It complements `.cursor/rules/*.mdc` and
`.github/copilot-instructions.md` with concise guidance for assistants editing this repo.

**Strict scope:** Swamy PKV's personal project only — see `README.md` and
`.cursor/rules/swamy_personal_learning_only.mdc`.

**Bundled agent skills:** `.github/skills/` is canonical; `.cursor/skills/` is a
**byte-identical mirror** (see `.github/skills/README.md`). Bundles: **`ai-agents-project`**,
**`ai-implementation-standards`**, **`ci-checks`**, **`docs-verification`**, **`workspace-review`**,
**`e2e-testing`**. Pushes under skills paths run **`.github/workflows/ci-skills-parity.yml`**;
agent-facing path changes also run **`.github/workflows/ci-agent-docs-guard.yml`**.

**Governance integrity (primary):** Commit or stash before another tool touches copilot, rules,
skills, agents, or `CLAUDE.md`; keep `.github/skills` ↔ `.cursor/skills` and agent mirrors in
one change; prefer small diffs. **Secondary (restore only if damaged):** **`docs/agent-governance-recovery.md`**.

**Project subagents:** **`ai-agents-ci-verify`** (CI-aligned checks), **`ai-agents-implementation-review`**
(module/notebook audit), **`ai-agents-code-review`** (code quality pass).

---

## Project structure

```text
src/               — reusable Python modules (fundamentals, agents, frameworks, protocols,
                     orchestration, observability, security, architecture, projects)
notebooks/         — Jupyter notebooks for exploration and learning
docs/              — project documentation (ADRs, diagrams, learnings, references)
tests/             — test suites
scripts/           — utility scripts
references/        — read-only learning materials
```

See `README.md`.

---

## CI expectations

- **Python:** `uv sync`, isort / black / flake8, notebook JSON — `ci-python.yml`.
- **Docs:** Markdown lint and Lychee — `ci-documentation.yml`.
- **Parity / guard:** `.github/skills/` ↔ `.cursor/skills/`; **`.github/agents/` ↔ `.cursor/agents/`**;
  **`ci-agent-docs-guard.yml`** when `.cursor/`, `.github/` skills or agents, or `CLAUDE.md` change.

Use the **`ci-checks`** skill for exact local commands.
