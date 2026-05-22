---
name: ai-implementation-standards
description: >-
  Implementation workflow and quality standards for Practical AI Agents — code structure,
  patterns, quality checklist, and definition of done. Use when adding or reviewing implementations.
---

# Implementation Standards — Practical AI Agents

**Applies to**: `practical-ai-agents` **only**.
**Canonical governance**: `.github/copilot-instructions.md`.

## Module Structure (`src/`)

Each `src/` subfolder represents a domain:

| Folder | Purpose |
|---|---|
| `fundamentals/` | Prompts, embeddings, RAG, vector stores, tool basics |
| `agents/` | Single-agent and multi-agent implementations |
| `frameworks/` | Framework-specific examples and comparisons |
| `protocols/` | MCP, A2A, function-calling integrations |
| `orchestration/` | Workflow, state machine, event-driven, durable execution |
| `observability/` | Tracing, evaluations, telemetry, prompt testing |
| `security/` | Guardrails, sandboxing, prompt injection defense |
| `architecture/` | Patterns, anti-patterns, scalability, distributed agents |
| `projects/` | Complete end-to-end agent projects |

## Standards (per module)

- [ ] Docstring on the module explaining its purpose and usage.
- [ ] Type hints on all public functions and methods.
- [ ] No hardcoded credentials — environment variables only.
- [ ] Meaningful error messages for LLM failures and tool errors.
- [ ] Agent tool functions have accurate descriptions.

## Standards (per notebook)

- [ ] Markdown concept cell before each major section.
- [ ] `Kernel → Restart & Run All` passes without error.
- [ ] References `src/` modules for reusable logic.
- [ ] Clear, descriptive cell outputs.

## Definition of done (per implementation)

- [ ] Passes CI notebook JSON parse (for notebooks).
- [ ] Passes Python linting (for `src/` modules).
- [ ] No broken internal links.
- [ ] Security checklist passed (no hardcoded credentials).

## Related

- **Subagent:** `.cursor/agents/ai-agents-implementation-review.md` (one module/notebook pass)
- **CI commands:** `.github/skills/ci-checks/SKILL.md`
