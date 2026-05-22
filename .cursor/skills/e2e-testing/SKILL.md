---
name: e2e-testing
description: >-
  Smoke verification for Practical AI Agents (environment, notebook JSON, optional manual
  notebook run). Use when smoke-testing the workspace end-to-end.
---

# Smoke / E2E-style verification — Practical AI Agents

No deployed application. "End-to-end" means **environment + parse + optional notebook execution**.

## Prerequisites

- Python 3.12+ with **`uv`** at repo root
- Optional: Jupyter — **Kernel → Restart & Run All**

## Suggested sequence

1. **Dependencies**

   ```powershell
   $Env:UV_LINK_MODE = "copy"
   uv sync
   ```

2. **Import smoke**

   ```powershell
   uv run python -c "import pathlib; print('Python OK')"
   ```

3. **Notebook JSON** (same as CI):

   ```powershell
   uv run python -c "import json,glob; paths=sorted(glob.glob('notebooks/**/*.ipynb',recursive=True)); [json.load(open(p,encoding='utf-8')) for p in paths]; print('Notebooks OK')"
   ```

4. **Manual (optional)** — open a notebook in `notebooks/`, run all cells, verify it completes cleanly.

## Summary

Report each step **PASS** / **FAIL** / **SKIPPED**.
