---
name: ci-checks
description: >-
  Run CI-aligned checks for Practical AI Agents (Python lint, recursive notebook JSON parse,
  markdown lint). Use when asked to run CI, lint, or verify code quality.
---

# CI Checks — Local Runner (Practical AI Agents)

Commands mirror `.github/workflows/ci-python.yml` and `.github/workflows/ci-documentation.yml`.

## Policy

- **Quality expectations:** `.cursor/rules/03_quality-assurance.mdc` and `.github/copilot-instructions.md`.

## Prerequisites

- **Python:** `uv` at repo root — `uv sync` (dev dependency group supplies black, isort, flake8).
- **Node.js:** **20.x** for `markdownlint-cli2` (match `ci-documentation.yml`).
- **Link checks:** **Docker** with `lycheeverse/lychee:latest` or local `lychee`.

### Windows / `uv run` troubleshooting

If `uv run` fails with **"Failed to canonicalize script path"** (some Windows setups), use the
project venv after `uv sync`:

```powershell
.\.venv\Scripts\python.exe -m isort --check-only --diff src/
.\.venv\Scripts\python.exe -m black --check --line-length 127 --target-version py312 src/
.\.venv\Scripts\python.exe -m flake8 src/ --count --select=E9,F63,F7,F82 --show-source --statistics
```

## Checks to run

Report each as PASS or FAIL with output.

### 1. isort

```powershell
uv run isort --check-only --diff src/
```

### 2. Black

```powershell
uv run black --check --line-length 127 --target-version py312 src/
```

### 3. flake8

```powershell
uv run flake8 src/ --count --select=E9,F63,F7,F82 --show-source --statistics
uv run flake8 src/ --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics
```

### 4. Notebook JSON parse

```powershell
uv run python -c "import json,glob; paths=sorted(glob.glob('notebooks/**/*.ipynb',recursive=True)); [json.load(open(p,encoding='utf-8')) for p in paths]"
```

### 5. markdownlint-cli2

```powershell
npx --yes markdownlint-cli2 "README.md" "docs/**/*.md"
```

### Optional — Lychee (Docker, recommended)

```powershell
docker run --rm `
  -v "${PWD}:/workspace" `
  -w /workspace `
  lycheeverse/lychee:latest `
  --config lychee.toml --cache --max-cache-age 1d '**/*.md'
```

## Execution strategy

Run 1–4 from repo root with `uv`; run 5 with Node.

## On failure

- **Black / isort:** suggest `uv run black src/` / `uv run isort src/` from repo root.
- **flake8 / markdownlint / JSON parse:** report file and line if applicable.

## Summary format

| # | Check | Status | Notes |
|---|---|---|---|
| 1 | isort | | |
| 2 | black | | |
| 3 | flake8 | | |
| 4 | notebooks JSON | | |
| 5 | markdownlint | | |
