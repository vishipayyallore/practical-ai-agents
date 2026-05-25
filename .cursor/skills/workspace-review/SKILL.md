---
name: workspace-review
description: >-
  Comprehensive workspace review for Practical AI Agents — structure, CI, code quality,
  notebook quality, security, and src module standards.
---

# Workspace Review — Practical AI Agents

## Protocol

1. Read `.github/copilot-instructions.md` (code standards, notebook quality, security).
2. Compare the tree to `README.md` for structural accuracy.
3. Python: `uv sync` at repo root; `uv run …` per `pyproject.toml` / CI.
4. **Reference materials:** `references/` is read-only — no modifications allowed.
5. **Code quality:** `src/` modules have type hints, docstrings, and PEP 8 compliance.
6. **Security:** No hardcoded credentials; `.env` in `.gitignore`; no prompt injection risks.
7. **Notebook quality:** Markdown concept cells before code; clean `Kernel → Restart & Run All`.
8. Run the **ci-checks** skill (Python + notebook JSON + markdownlint + optional Lychee).
9. Optionally run **docs-verification**.
10. **Skills parity:** `.github/skills/**` ↔ `.cursor/skills/**` byte-identical.
11. **Agents parity:** `.github/agents/**` ↔ `.cursor/agents/**` byte-identical.

## Output

Critical / Major / Minor findings; CI summary; doc accuracy notes.

**Governance integrity (primary):** do not bulk-edit copilot, rules, skills, or agents without
commits and mirror-safe diffs.
