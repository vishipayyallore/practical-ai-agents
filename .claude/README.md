# `.claude/` - optional Claude Code extras

This folder is for **Claude Code** (or similar) **runtime** add-ons you choose to keep
**beside** the repo's main agent layout.

## Canonical layout (do not duplicate here)

| Need | Use this (single source) |
|---|---|
| Always-on assistant rules | `.github/copilot-instructions.md`, `.cursor/rules/` |
| Repeatable procedures | `.github/skills/` <-> `.cursor/skills/` (`SKILL.md` files) |
| Delegated audits / fresh-context tasks | `.cursor/agents/` <-> `.github/agents/` |
| Reusable prompt skeletons | `.github/prompts/` (for example `task-prompt.md`, `smart-prompt-framework-guide.md`) |
| Entry + map | Root **`CLAUDE.md`** |

Keeping long policy **only** in copilot instructions + Cursor rules avoids **drift** between
`CLAUDE.md`, `.claude/`, and Cursor.

## What you *may* put under `.claude/`

Short, **task-local** files (for example one-off prompt fragments or Claude Code-specific hooks)
that are **not** mirrored elsewhere, **if** you use the Claude Code CLI and its conventions.

This repo does **not** require a `.claude/agents/` tree; custom subagents already live under
**`.cursor/agents/`** (mirrored to **`.github/agents/`**). If you need Claude-native agent paths,
copy from there rather than maintaining two divergent definitions.

## This learning workspace is not enterprise "clean architecture"

This repository is **Practical AI Agents** — Swamy's personal workspace for learning and
engineering AI Agents, MCP, RAG, orchestration, and multi-agent systems. Keep this folder
minimal and avoid duplicating governance content that already lives under
`.github/copilot-instructions.md`, `.cursor/rules/`, `.github/skills/`, and `.cursor/agents/`.
