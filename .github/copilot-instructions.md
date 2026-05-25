# GitHub Copilot Instructions for Practical AI Agents

**Version**: 1.0
**Last Updated**: May 22, 2026
**Repository**: `practical-ai-agents`
**Context**: Swamy PKV's personal learning and engineering workspace

**Environment**: Windows, PowerShell, Python 3.12+, Jupyter Notebooks
**Note**: All shell commands use PowerShell syntax unless otherwise stated.

---

## Strict scope (non-negotiable)

This repository is **Swamy PKV's personal project work only**. It is **not** for anyone else as
courseware, templates, tutorials, or a reference corpus. Do **not** frame content for a general
audience. Public visibility is **not** an invitation to use this repo for third-party purposes.

---

## Repository Purpose

**Practical AI Agents** is a hands-on learning and engineering workspace for building AI Agents,
Agentic AI systems, MCP integrations, RAG pipelines, orchestration workflows, multi-agent
systems, and production-grade AI architectures.

### Project Objectives

- Build progressively from foundational AI concepts to production-grade AI systems.
- Explore agent frameworks: LangChain, LangGraph, Semantic Kernel, AutoGen, CrewAI, OpenAI Agents SDK.
- Implement and compare orchestration patterns: ReAct, Planner-Executor, Reflection, Tool-Calling.
- Integrate protocols: Model Context Protocol (MCP), Agent-to-Agent (A2A), function calling.
- Apply production engineering: observability, evaluations, security, governance, cost optimization.

---

## Repository Structure

**Quick Reference:**

- `src/fundamentals/` — prompts, embeddings, RAG, vector stores, tool usage basics.
- `src/agents/` — single-agent, multi-agent, ReAct, planner-executor, reflection, memory.
- `src/frameworks/` — implementations using LangChain, LangGraph, Semantic Kernel, AutoGen, CrewAI, OpenAI Agents SDK.
- `src/protocols/` — MCP, A2A, and function-calling integrations.
- `src/orchestration/` — workflows, state machines, event-driven, durable execution.
- `src/observability/` — tracing, evaluations, telemetry, prompt testing.
- `src/security/` — prompt injection defense, guardrails, sandboxing, secrets management.
- `src/architecture/` — patterns, anti-patterns, scalability, distributed agents.
- `src/projects/` — complete end-to-end agent projects.
- `notebooks/` — Jupyter notebooks for exploration and learning.
- `docs/` — project documentation (ADRs, diagrams, learnings, references).
- `tests/` — test suites.
- `scripts/` — utility and automation scripts.
- `references/` — learning materials, books, papers, external references (read-only).
- `README.md` — project overview.

---

## Development Guidelines

### Code Organisation

- **`src/`** holds all reusable Python modules organized by domain (fundamentals, agents, frameworks, etc.).
- **`notebooks/`** holds Jupyter notebooks for exploration, experimentation, and demonstrations.
- **`tests/`** holds unit and integration tests for `src/` modules.
- Each `src/` subfolder should be a proper Python package (`__init__.py`) or module collection.

### Python Code Standards

- Follow PEP 8 style guide.
- Use type hints for function arguments and return types.
- Write docstrings for all public functions, classes, and modules.
- No hardcoded paths — use `pathlib` or relative paths.
- Use meaningful variable names (`agent_config`, `tool_registry`, `llm_response`).
- Comment the **why** of architectural or algorithmic decisions, not the what.

### Notebook Standards

- Notebooks are for exploration, learning, and demonstration — not production logic.
- Keep notebooks focused on a single concept or workflow.
- Markdown cells must explain each major section before code.
- Use clear, descriptive cell outputs.
- Prefer `Kernel → Restart & Run All` clean runs for shared notebooks.
- Reference modules from `src/` rather than duplicating logic in notebooks.

### Agent Implementation Standards

- Define tool functions with clear descriptions — agents rely on these for routing decisions.
- Separate agent definition, tool registration, and execution into distinct concerns.
- Use environment variables (`.env`) for API keys and secrets — never hardcode credentials.
- Log agent actions, tool calls, and LLM responses for observability.
- Include error handling for tool failures and LLM timeouts.

### Framework Usage

- Prefer framework-idiomatic patterns over generic Python.
- Document why a particular framework was chosen for each implementation.
- Include minimal, self-contained examples before adding complexity.

---

## Running the Code

**Python Environment:**

```powershell
# Optional: suppress cross-drive hardlink warnings on Windows
$Env:UV_LINK_MODE = "copy"
uv sync
```

**Jupyter:**

```powershell
jupyter notebook
```

---

## Prompt Engineering

When asking Copilot for help:

- Name the specific module or notebook (e.g., `src/agents/react_agent.py`, `notebooks/mcp_intro.ipynb`).
- Specify the framework context (e.g., "using LangGraph", "using OpenAI Agents SDK").
- Ask for architecture-aware implementations (separation of concerns, tool definitions, memory).
- Request docstrings and type hints for all public functions.
- Ask for error handling around LLM calls and tool execution.

---

## Protecting assistant governance (primary)

These files must stay **uncorrupted**: `.cursor/rules/`, mirrored **`.github/skills` ↔ `.cursor/skills`**,
mirrored **`.github/agents` ↔ `.cursor/agents`**, `CLAUDE.md`, and this `copilot-instructions.md`.
Before another AI tool or mass refactor touches them: **commit or stash**; edit **both** sides of
each mirror in one change; prefer **small scoped diffs**; rely on **`ci-skills-parity.yml`** and
**`ci-agent-docs-guard.yml`** on push.

**Secondary (only if damage already happened):** restore from Git — **`docs/agent-governance-recovery.md`**.
