---
name: ai-agents-project
description: >-
  Context and standards for the Practical AI Agents project — scope, architecture, frameworks,
  workflow, and implementation standards.
---

# Practical AI Agents — Project Context

**Scope:** Swamy PKV's personal learning and engineering workspace. See `README.md` and
`.cursor/rules/swamy_personal_learning_only.mdc`.

## Project Overview

Hands-on learning and engineering workspace for building AI Agents, Agentic AI systems, MCP
integrations, RAG pipelines, orchestration workflows, multi-agent systems, and production-grade
AI architectures.

## Architecture Progression

| Phase | Focus |
|---|---|
| Phase 1 | Foundations: prompts, embeddings, RAG, tool calling, memory |
| Phase 2 | AI Agents: ReAct, reflection, planning, tool orchestration, autonomous loops |
| Phase 3 | Multi-Agent Systems: delegation, coordination, routing, shared context |
| Phase 4 | Production Systems: observability, evaluations, security, governance |
| Phase 5 | Advanced Architectures: distributed agents, MCP ecosystems, durable execution |

## Frameworks

- **LangChain** — foundational AI application framework
- **LangGraph** — stateful multi-actor applications with graphs
- **Semantic Kernel** — enterprise AI orchestration (.NET and Python)
- **AutoGen** — multi-agent conversation framework
- **CrewAI** — collaborative AI agent teams
- **OpenAI Agents SDK** — production-grade agent building

## Implementation Standards

- Separation of concerns: agent definition, tool registration, execution loop.
- Tool functions require accurate descriptions for LLM routing decisions.
- Use environment variables for all credentials and API keys.
- Log agent actions and LLM calls for observability.

## Related

- **CI commands:** `.github/skills/ci-checks/SKILL.md`
- **Workspace review:** `.github/skills/workspace-review/SKILL.md`
- **Subagent:** `.cursor/agents/ai-agents-ci-verify.md`
