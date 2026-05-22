# S.M.A.R.T. Prompt Framework for GitHub Copilot Coding Agents

**Practical AI Agents Edition** — Framework for creating high-quality coding agent instructions
aligned with AI agent implementation best practices and engineering standards.

---

## The S.M.A.R.T. Framework

Use this framework to create highly effective coding agent instructions:

```text
S - Specific Role Definition (AI Engineer, Agent Architect, Framework Specialist, etc.)
M - Mission-Critical Requirements (What must be accomplished with measurable outcomes)
A - Audience-Aware Communication (Team expertise level, domain context, framework familiarity)
R - Response Format Control (Code structure, agent patterns, documentation style)
T - Task-Oriented Constraints (Technology stack, implementation patterns, forbidden actions)
```

---

## AI Agent System Alignment

When creating prompts, consider:

- **Agent Type**: Is this a single-agent, multi-agent, or orchestrated workflow?
- **Framework Context**: Which framework is in scope (LangChain, LangGraph, AutoGen, CrewAI, etc.)?
- **Pattern**: ReAct, Planner-Executor, Reflection, Tool-Calling, Memory-augmented?
- **Template Reusability**: Can this prompt be templated for reuse across similar agent implementations?

## Advanced Problem Statement Template

Use this enhanced template for coding agent tasks:

```markdown
## ROLE DEFINITION

You are a [Specific Role] specializing in [Technology Stack] with expertise in [Domain Areas]

## MISSION

[Clear, specific objective with measurable outcomes]

## CONTEXT

[Brief overview of current situation and progress made]

## CURRENT STATUS

- **Progress Made**: [Specific achievements and metrics]
- **Main Issue**: [Root cause analysis]
- **Files Affected**: [List specific files]

## REMAINING WORK

### 1. [Priority Task Name] (Priority N)

- **Problem**: [Specific technical issue]
- **Current Error**: [Exact error messages]
- **Solution Approach**: [Concrete implementation steps]
- **Files to Modify**: [Specific file paths]

## TECHNICAL CONSTRAINTS

- **CRITICAL**: [Non-negotiable requirements]
- **Framework**: [Technology stack requirements]
- **Dependencies**: [Package/version constraints]

## RESPONSE FORMAT REQUIREMENTS

- [Specific code structure expectations]
- [Documentation requirements]
- [Testing requirements]
- [Security requirements]

## WHAT NOT TO DO

- [Explicit forbidden actions with reasoning]

## WHAT TO DO

- [Explicit required actions with priority]

## SUCCESS CRITERIA

[Measurable outcomes with acceptance criteria]

## QUALITY STANDARDS

- [Code quality requirements]
- [Security expectations]
- [Performance considerations]
```

## Role-Based Specialization Examples

### For AI Agent Implementation

```markdown
ROLE: You are an AI Engineer specializing in building production-grade AI agents,
tool orchestration, and agentic workflow design

EXPERTISE FOCUS: Agent patterns (ReAct, Reflection, Planner-Executor), tool definition,
LLM orchestration, error handling, observability

OUTPUT REQUIREMENTS: Clean Python code with type hints, docstrings, clear tool descriptions,
error handling, and logging

MANDATORY VALIDATION:
- Tool functions have accurate, descriptive docstrings
- Agent logic is separated from tool definitions
- No hardcoded credentials (environment variables only)
- LLM calls have error handling and retry logic
```

### For LangGraph Workflow Implementation

```markdown
ROLE: You are a LangGraph specialist building stateful multi-actor agent workflows

EXPERTISE FOCUS: State graphs, conditional edges, human-in-the-loop, streaming, checkpointing

OUTPUT REQUIREMENTS: Well-typed state schemas, clear node functions, conditional routing logic

MANDATORY VALIDATION:
- State schema uses TypedDict or Pydantic models
- All edges are explicitly defined
- Graph compiles without errors
- Nodes are single-responsibility functions
```

### For MCP Integration

```markdown
ROLE: You are an MCP (Model Context Protocol) integration specialist

EXPERTISE FOCUS: MCP server/client patterns, tool schemas, resource definitions, prompts

OUTPUT REQUIREMENTS: Standards-compliant MCP server or client implementation

MANDATORY VALIDATION:
- Tool schemas match MCP specification
- Error handling follows MCP error codes
- Server starts and responds to initialize handshake
- Tool execution returns correct content types
```

### For Multi-Agent Systems

```markdown
ROLE: You are a multi-agent systems architect specializing in agent coordination and delegation

EXPERTISE FOCUS:
- Agent coordination patterns (supervisor, swarm, hierarchical)
- Task delegation and routing
- Shared memory and state management
- Inter-agent communication protocols

OUTPUT REQUIREMENTS:
- Clear agent role definitions
- Explicit delegation and handoff logic
- Shared state schema
- Termination conditions

MANDATORY VALIDATION:
- Agents have distinct, non-overlapping responsibilities
- Handoff conditions are explicitly coded
- Infinite loop prevention is implemented
- Results are aggregated correctly
```

## Critical Constraint Guidelines

### Framework/Package Versions

```markdown
- CRITICAL: Use Python 3.12+ ONLY — DO NOT downgrade
- CRITICAL: Use framework latest stable versions — DO NOT downgrade
- DO NOT mix incompatible framework versions
- DO NOT modify pyproject.toml to downgrade packages
```

### Security Constraints

```markdown
- CRITICAL: No hardcoded API keys, tokens, or credentials
- CRITICAL: Load all credentials from environment variables
- DO NOT pass raw user input to LLMs without sanitization
- DO NOT execute tool outputs as code without validation
```

### File Modification Boundaries

```markdown
- DO NOT modify [specific files]
- ONLY modify [allowed areas]
```

## Effective Instruction Patterns

### DO — Be Specific and Explicit

- "Implement a ReAct agent using LangGraph with web search and code execution tools"
- "Create an MCP server exposing a database query tool with proper schema validation"
- "Fix the tool routing logic in react_agent.py — verify tool descriptions match LLM expectations"

### DON'T — Be Vague

- "Fix the agent"
- "Make it work"
- "Update the code"

## Constraint Language Examples

### Strong Constraint Language That Works

```markdown
ABSOLUTELY DO NOT hardcode API keys or credentials in any file.

The following packages MUST remain at their current versions:
- langchain: current pinned version
- langgraph: current pinned version

CRITICAL: All tool functions must have accurate docstrings that describe what the
tool does, its parameters, and what it returns — the LLM uses these for routing.
```

### Weak Language That Doesn't Work

```markdown
Please try to maintain Python 3.12+ compatibility
Prefer keeping current package versions
```

## Advanced Prompt Design Patterns

### Multi-Layered Prompt Architecture

```markdown
SYSTEM LAYER:
You are a [Specialist Role] with expertise in [Technology Stack] and [Domain Expertise].

CONTEXT LAYER:
[Project context, current situation, what has been implemented]

TASK LAYER:
[Specific implementation task with clear deliverables]

SPECIFICATION LAYER:
[Detailed technical requirements, constraints, and acceptance criteria]
```

## Success Indicators

### Agent is working correctly when

- It acknowledges security constraints explicitly
- It asks clarifying questions about tool descriptions and agent scope
- It maintains clean separation of agent, tool, and execution concerns
- It focuses on correctness and architecture, not just functionality
- It provides detailed progress updates
- It includes proper error handling and logging

### Agent needs restart when

- It hardcodes credentials
- It ignores security requirements
- It ignores explicit constraints
- It duplicates logic between `src/` and notebooks
- It takes overly broad approach to simple problems

## Agent Restart Protocol

### When to restart the coding agent

- Agent hardcodes credentials or secrets
- Agent breaks architectural separation of concerns
- Agent modifies forbidden files
- Agent ignores explicit constraints
- Agent creates security vulnerabilities

### How to restart

1. Close current pull request
2. Create new pull request with more explicit constraints
3. Include specific examples of what went wrong
4. Add stronger constraint language

## AI Agent Implementation Patterns

### Pattern: Clean Agent Architecture

```markdown
IMPLEMENTATION PATTERN: Layered Agent Architecture

REQUIREMENTS:
- Agent definition (model, tools, system prompt) in one place
- Tool functions as separate, focused functions with accurate docstrings
- Execution loop separated from configuration
- Error handling at each layer

QUALITY GATES:
- Tool descriptions are accurate and informative
- No hardcoded credentials
- Agent actions are logged
- Error handling covers LLM timeouts and tool failures
```

### Pattern: Tool Definition

```markdown
TOOL PATTERN: Well-Defined Tool Function

CHARACTERISTICS:
- Accurate, descriptive docstring (LLM uses this for routing)
- Clear parameter types with type hints
- Explicit return type
- Error handling with informative error messages
- No side effects beyond intended action

QUALITY GATES:
- Tool name is descriptive and unambiguous
- Parameters are validated before execution
- Errors return informative messages to the agent
- Tool is focused on a single responsibility
```

## Universal PR Success Template

Include this template in EVERY coding agent PR for consistent validation:

```markdown
## MANDATORY SUCCESS CRITERIA (NON-NEGOTIABLE)

### Security Requirements

- No hardcoded credentials in any file
- All API keys loaded from environment variables
- `.env` file listed in `.gitignore`

### Code Quality Requirements

```powershell
# MUST PASS: Python linting
uv run isort --check-only --diff src/
uv run black --check --line-length 127 --target-version py312 src/
uv run flake8 src/ --count --select=E9,F63,F7,F82 --show-source --statistics
```

### Agent Implementation Requirements

- Tool functions have accurate docstrings
- Agent definition, tools, and execution are separated
- LLM calls have error handling

## FINAL CHECKLIST

Before marking this PR ready for review:

- [ ] No hardcoded credentials
- [ ] Python linting passes
- [ ] Type hints and docstrings in src/ modules
- [ ] Tool descriptions are accurate
- [ ] Error handling is present
- [ ] Agent actions are logged

CRITICAL: Do not mark this PR as ready for review until ALL validations pass.
```

## Practical AI Agents S.M.A.R.T. Example

```markdown
ROLE: You are an AI Engineer specializing in building production-grade AI agents using
LangGraph, with expertise in stateful workflows, tool orchestration, and observability

MISSION: Implement a ReAct agent in src/agents/react_agent.py that uses web search and
code execution tools, with proper state management and logging

AUDIENCE: Swamy's personal learning workspace — production-quality patterns with
clear documentation and architectural separation

RESPONSE FORMAT:
- Clean Python code with type hints and docstrings
- Clear separation: agent definition, tool registration, execution
- Logging of all agent actions and LLM calls
- Environment variables for all credentials

TASK CONSTRAINTS:
- CRITICAL: No hardcoded API keys — use environment variables
- CRITICAL: Tool functions must have accurate docstrings
- Architecture: Tools → Agent Definition → Execution Loop
- Quality Standards: PEP 8, type hints, error handling, logging
- Technology Stack: Python 3.12+, LangGraph, LangChain
```

## Best Practices Summary

1. **Be Specific**: Define exact roles, technologies, and constraints
2. **Set Clear Boundaries**: Use strong constraint language, especially for security
3. **Define Success**: Include measurable outcomes and validation steps
4. **Control Output**: Specify exactly what format and quality you expect
5. **Plan for Failure**: Include restart protocols and troubleshooting
6. **Validate Everything**: Always include build and security requirements
7. **Document Thoroughly**: Ensure all decisions and constraints are recorded
8. **Architecture First**: Reference patterns from `docs/adr/` and project standards
9. **Security Always**: Include credential and injection constraints in every prompt
10. **Progressive Complexity**: Scale scope to learning objectives

---

## Quick Reference Checklist

Use this checklist before submitting any coding agent task:

### Role Definition

- [ ] Specific role/expertise clearly stated
- [ ] Technology stack and frameworks identified
- [ ] Agent pattern or workflow type specified
- [ ] Domain context provided

### Task Clarity

- [ ] Mission and objectives clearly defined
- [ ] Success criteria are measurable
- [ ] Scope is appropriately sized
- [ ] Priority and sequencing defined

### Technical Requirements

- [ ] Framework and version constraints specified
- [ ] Agent patterns identified
- [ ] Dependencies listed explicitly
- [ ] Security requirements stated

### Constraints and Boundaries

- [ ] Forbidden actions explicitly listed (no hardcoded credentials, etc.)
- [ ] Required actions explicitly listed
- [ ] File modification boundaries defined
- [ ] Security decision constraints included

### Quality and Validation

- [ ] Code quality standards specified (PEP 8, type hints, docstrings)
- [ ] Build/test requirements included
- [ ] Security validation requirements defined
- [ ] Observability requirements addressed

### Output Expectations

- [ ] Code format and style specified
- [ ] Documentation requirements defined
- [ ] Testing approach specified
- [ ] Security review included
