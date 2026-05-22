---
name: e2e-testing
description: Smoke verification for Customer Churn Prediction ML (environment, notebook JSON, optional manual notebook run). Use when smoke-testing the workspace end-to-end.
---

# Smoke / E2E-style verification — Customer Churn Prediction ML

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
   uv run python -c "import numpy, pandas, sklearn, matplotlib, seaborn; print('ok')"
   ```

3. **Notebook JSON** (same as CI):

   ```powershell
   uv run python -c "import json,glob; paths=sorted(glob.glob('notebooks/**/*.ipynb',recursive=True)); [json.load(open(p,encoding='utf-8')) for p in paths]"
   ```

4. **Manual (optional)** — open `notebooks/01_data_understanding.ipynb`, run all cells, verify it completes cleanly.

## Summary

Report each step **PASS** / **FAIL** / **SKIPPED**.
