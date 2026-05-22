# Practical AI Agents — Workspace Verification and Content Review

## Context

You are working with **Practical AI Agents**, a hands-on learning and engineering workspace for
building AI Agents, Agentic AI systems, MCP integrations, RAG pipelines, orchestration workflows,
multi-agent systems, and production-grade AI architectures.

**Repository Structure:**

- `src/fundamentals/` — prompts, embeddings, RAG, vector stores, tool basics
- `src/agents/` — single-agent, multi-agent, ReAct, reflection, memory
- `src/frameworks/` — LangChain, LangGraph, Semantic Kernel, AutoGen, CrewAI, OpenAI Agents SDK
- `src/protocols/` — MCP, A2A, function-calling integrations
- `src/orchestration/` — workflows, state machines, event-driven, durable execution
- `src/observability/` — tracing, evaluations, telemetry, prompt testing
- `src/security/` — prompt injection defense, guardrails, sandboxing, secrets
- `src/architecture/` — patterns, anti-patterns, scalability, distributed agents
- `src/projects/` — complete end-to-end agent projects
- `notebooks/` — Jupyter notebooks for exploration and learning
- `docs/` — project documentation (ADRs, diagrams, learnings, references)
- `tests/` — test suites

**Primary Objective:**

Perform a COMPREHENSIVE review of the repository using Practical AI Agents standards and quality
criteria. Verify file contents, run structured checks, and produce actionable reports with
suggestions and fixes.

---

## Verification Checks

### A. File Content Inspection

- Open and verify every file (no file skipped)
- Ensure markdown formatting compliance
- Check for completeness and consistency with project objectives
- Verify no hardcoded credentials or secrets

### B. Agent Implementation Alignment

- Verify agent implementations use clear separation of concerns (definition, tools, execution)
- Validate tool function descriptions are accurate and informative for LLM routing
- Check proper use of framework-idiomatic patterns
- Ensure agent implementations follow architectural patterns documented in `docs/`

### C. Content Accuracy and Quality

- Verify technical correctness and alignment with AI agent best practices
- Ensure completeness for stated objectives
- Check alignment with framework documentation and standards
- Validate code examples are correct and runnable
- Verify Python type hints and docstrings are present and accurate

### D. Project Metadata Requirements

Check for presence of:

- Domain designation (fundamentals, agents, frameworks, protocols, etc.)
- Learning objective or implementation purpose
- Clear objectives with runnable examples
- References to related modules and cross-references

### E. Naming Convention Compliance

- Use snake_case for Python files: `react_agent.py`
- Use descriptive names for classes: `ReactAgent`, `MCPClient`
- Verify folder structure follows repository standards
- Check proper organization by domain

### F. Broken Links and References

- Verify all internal cross-references work correctly
- Check README files and navigation structure
- Ensure module navigation links are accurate

### G. Content Quality Standards

- Spellcheck and grammar verification
- Character encoding validation (UTF-8 only)
- Markdown formatting compliance (markdownlint standards)
- Code example correctness and completeness
- Proper code fence language specification

### H. Security Review

- No API keys, tokens, or credentials committed
- `.env` files listed in `.gitignore`
- No prompt injection vectors from untrusted inputs to LLMs
- External tool calls validated before execution

### I. Repository Structure Clarity

- Verify folder organization is intuitive and follows README
- Check navigability and discoverability
- Validate table of contents accuracy
- Ensure README files guide through content

---

## Output Requirements

### 1. SUMMARY (Top-level)

```json
{
  "repo_name": "practical-ai-agents",
  "total_files_checked": 0,
  "total_issues_found": 0,
  "system_compliance_percentage": 0.0,
  "high_severity_count": 0,
  "medium_severity_count": 0,
  "low_severity_count": 0,
  "suggested_next_steps": ["step1", "step2", "step3"]
}
```

### 2. DETAILED_REPORT (array of file reports)

For each file:

```json
{
  "file_path": "string",
  "domain": "string (e.g., fundamentals, agents, frameworks, protocols)",
  "language_category": "string (e.g., python, notebook, documentation)",
  "checks_passed": ["list of check keys, e.g., A,B,C,F,G"],
  "content_quality_score": "0-100",
  "issues": [
    {
      "id": "string (unique, e.g., PAA-001)",
      "severity": "high|medium|low",
      "line_start": 0,
      "line_end": 0,
      "description": "string",
      "suggested_fix": "string",
      "fix_type": "replace|delete|add|rename|format|link-fix|security-fix",
      "violation_type": "string (e.g., missing-docstring, hardcoded-credential, broken-link)"
    }
  ],
  "overall_status": "compliant|needs_updates|remove"
}
```

---

## Behavioral Expectations

- **Agent Focus**: Prioritize agent implementation quality, architecture patterns, and correctness
- **Security**: Flag any hardcoded credentials, prompt injection risks, or unsafe tool patterns
- **Architecture Integrity**: Ensure agents follow documented patterns from `docs/adr/`
- **Practical Relevance**: Verify content provides actionable AI agent implementation guidance
- **Code Quality**: Validate examples are well-documented, runnable, and follow best practices

---

## Start Now

Open every file in the repository tree, run Practical AI Agents-specific checks, and produce the
structured report. Focus on agent implementation correctness, security, architecture alignment,
and code quality.
