# CLAUDE.md — Claude Code entry point

## Repository

**Practical AI Agents** — Swamy PKV's personal learning and engineering workspace for AI Agents,
Agentic AI, MCP, RAG, orchestration, multi-agent systems, and production-grade AI architectures.
**Not** a public tutorial collection or enterprise production system.

## Non-negotiable: Swamy only

This repository is **Swamy PKV's personal project work**. It is **not** maintained for other
learners, employers, or the public. Do **not** reword `README.md` or docs to imply a general
audience unless Swamy explicitly asks.

## Project layout

```text
practical-ai-agents/
├── src/
│   ├── fundamentals/      — prompts, embeddings, RAG, vector stores, tools
│   ├── agents/            — single-agent, multi-agent, ReAct, reflection, memory
│   ├── frameworks/        — LangChain, LangGraph, Semantic Kernel, AutoGen, CrewAI, OpenAI Agents SDK
│   ├── protocols/         — MCP, A2A, function-calling
│   ├── orchestration/     — workflows, state machines, event-driven, durable execution
│   ├── observability/     — tracing, evaluations, telemetry, prompt testing
│   ├── security/          — prompt injection, guardrails, sandboxing, secrets
│   ├── architecture/      — patterns, anti-patterns, scalability, distributed agents
│   └── projects/          — complete end-to-end agent projects
├── notebooks/             — Jupyter notebooks for exploration and learning
├── docs/                  — project documentation (ADRs, diagrams, learnings, references)
├── tests/                 — test suites
├── scripts/               — utility scripts
├── assets/                — static assets
└── references/            — learning materials, books, papers, external refs
```

## Agent skills (`SKILL.md`)

Bundled on-demand procedures live under `.github/skills/` (mirrored at `.cursor/skills/`). They
use YAML frontmatter plus a Markdown body so agents can match tasks without loading everything
up front. How this fits `CLAUDE.md`, rules, and MCP: **`docs/agent-skills.md`**.

## Agent subagents (Cursor)

**Custom subagents** live under **`.cursor/agents/`** (YAML frontmatter + instructions). Cursor
uses them for delegated tasks with a fresh context. The same files are **mirrored** at
**`.github/agents/`** for visibility in Git; keep both trees identical when editing.

- **Index and how this fits `CLAUDE.md`:** **`docs/agent-subagents.md`**
- **Invocation:** natural language ("use the ai-agents-ci-verify subagent") or
  `/ai-agents-ci-verify` when supported.

**Claude Code** reads this **`CLAUDE.md`** as the project entry point.

## Context layering: global contract vs playbooks

| Layer | In this repository | Holds |
|---|---|---|
| **Global contract** | **`CLAUDE.md` (this file)** | What this repo *is*, scope, layout pointer, governance and CI pointers. |
| **Playbooks** | **`.github/skills/`** (mirrored **`.cursor/skills/`**), **`.cursor/agents/`** (mirrored **`.github/agents/`**) | How to run CI, review implementations, etc. |
| **Rules** | **`.cursor/rules/`** | Always-applied agent constraints. |

**Rule of thumb:** universal behaviour → **`.github/copilot-instructions.md`** +
**`.cursor/rules/`**. Repeatable procedure → **`SKILL.md`** or a **subagent**.
**`CLAUDE.md`** → **links and summaries** only.

## Governance integrity (primary)

Assistant behaviour is defined under `.github/copilot-instructions.md`, `.cursor/rules/`,
mirrored **`.github/skills` ↔ `.cursor/skills`**, mirrored **`.github/agents` ↔ `.cursor/agents`**,
and **`CLAUDE.md`**. **Do not corrupt these:** commit or stash before another tool bulk-edits
them; change both skill/agent mirrors in the same commit; prefer small scoped diffs; rely on
`ci-skills-parity` / `ci-agent-docs-guard` to catch drift.

**Secondary (only if damage already happened):** restore from Git using
**`docs/agent-governance-recovery.md`**.

## Key rules (summary)

- **Project scope**: AI Agents, Agentic AI, MCP, RAG, orchestration, multi-agent systems.
  See `.cursor/rules/05_primary-directives.mdc`.
- **Repository structure**: Follow `README.md` and `.cursor/rules/02_repository-structure.mdc`.
- **Scope**: See `.cursor/rules/swamy_personal_learning_only.mdc`.
- **Reference materials**: `references/` is read-only. See `.cursor/rules/06_source_material_rules.mdc`.
- **Code and notebook quality**: See `.cursor/rules/01_educational-content-rules.mdc`.

## Environment

```powershell
$Env:UV_LINK_MODE = "copy"
uv sync
jupyter notebook
```

## CI checks (run locally)

Aligned with `.github/workflows/ci-python.yml` and `.github/workflows/ci-documentation.yml`.
Full detail: `.github/skills/ci-checks/SKILL.md`.

```bash
uv sync
uv run isort --check-only --diff src/
uv run black --check --line-length 127 --target-version py312 src/
uv run flake8 src/ --count --select=E9,F63,F7,F82 --show-source --statistics
uv run flake8 src/ --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics
uv run python -c "import json,glob; [json.load(open(p,encoding='utf-8')) for p in glob.glob('notebooks/**/*.ipynb', recursive=True)]"
npx --yes markdownlint-cli2 "README.md" "docs/**/*.md"
```

## Key files

| Path | Purpose |
|---|---|
| `README.md` | Project overview |
| `docs/agent-skills.md` | SKILL.md pattern and skills mirror |
| `docs/agent-subagents.md` | Subagent index |
| `docs/agent-governance-recovery.md` | Governance integrity; Git restore bundle |
| `.github/copilot-instructions.md` | Canonical Copilot / agent instructions |
| `.cursor/skills.md` | Bundled skills pointer |
| `.github/skills/` | Canonical agent skills; mirrored at `.cursor/skills/` |
| `.cursor/agents/` | Cursor custom subagents; mirrored at `.github/agents/` |
| `.cursor/rules/swamy_personal_learning_only.mdc` | Swamy-only scope (always apply) |
| `.cursor/rules/01_educational-content-rules.mdc` | Code and notebook quality standards |
| `.cursor/rules/02_repository-structure.mdc` | Repository layout |
| `.cursor/rules/03_quality-assurance.mdc` | QA checklists for `src/` and notebooks |
| `.cursor/rules/04_markdown-standards.mdc` | Markdown structure for `.md` files |
| `.cursor/rules/05_primary-directives.mdc` | Primary project directives |
| `.cursor/rules/06_source_material_rules.mdc` | `references/` — read-only reference materials |
| `.cursor/rules/07_file-naming-conventions.mdc` | File and folder naming conventions |
| `.cursor/rules/08_copilot-instructions-extract.mdc` | Condensed Copilot guardrails |
| `.github/workflows/ci-skills-parity.yml` | Skills mirror parity on GitHub Actions |
| `.github/workflows/ci-agent-docs-guard.yml` | Validates rules, `CLAUDE.md` references, skills and agents mirrors |
