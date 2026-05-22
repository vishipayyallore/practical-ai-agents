# GitHub Copilot Instructions for Customer Churn Prediction ML

**Version**: 1.0
**Last Updated**: May 21, 2026
**Repository**: `customer-churn-prediction-ml`
**Context**: M.Sc. Data Science & AI — Advanced Apex Project (Trimester 2)

**Environment**: Windows, PowerShell, Python 3.12+, Jupyter Notebooks
**Note**: All commands and scripts should use PowerShell syntax.

---

## Strict scope (non-negotiable)

This repository is **Swamy PKV's personal project work only**. It is **not** for anyone else as courseware, templates, tutorials, or a reference corpus. Do **not** frame content for a general audience. Public visibility is **not** an invitation to use this repo for third-party purposes.

---

## Repository Purpose

**Customer Churn Prediction** is an end-to-end machine learning project to predict customer churn using the IBM Telco Customer Churn Dataset. Built as Swamy's Advanced Apex Project for the M.Sc. DSAI program (Trimester 2).

### Project Objectives

- Identify customers likely to churn using historical customer data and behavioural patterns.
- Evaluate ML models: Logistic Regression (baseline), Decision Tree, Random Forest.
- Provide business-oriented interpretation of results (customer retention, revenue impact).

---

## Repository Structure

**Quick Reference:**
- `data/raw/` — original, immutable datasets (never modify).
- `data/processed/` — cleaned and transformed datasets.
- `notebooks/` — numbered Jupyter Notebooks following the ML workflow steps.
- `src/data_preprocessing/` — reusable preprocessing modules.
- `src/feature_engineering/` — feature creation and transformation.
- `src/modeling/` — model training and inference.
- `src/evaluation/` — metrics, validation, and model comparison.
- `reports/figures/` — exported charts and report-ready visuals.
- `docs/` — project documentation (`01-repository-structure.md`).
- `README.md` — project overview.

**Single Source of Truth for Structure:** `docs/01-repository-structure.md`.

---

## Development Guidelines

### Data Governance

- **`data/raw/` is read-only.** Never modify, overwrite, or delete original dataset files.
- Cleaning and transformation outputs go to `data/processed/`.
- Do not commit large binary data files to Git — use `.gitignore`.

### Notebook Workflow

Notebooks are numbered to reflect the ML pipeline sequence:

| # | Notebook | Purpose |
|---|----------|---------|
| 01 | `01_data_understanding.ipynb` | Dataset exploration and EDA |
| 02 | `02_data_preprocessing.ipynb` | Cleaning and preprocessing |
| 03 | `03_feature_engineering.ipynb` | Feature creation and transformation |
| 04 | `04_model_building.ipynb` | Baseline and comparative models |
| 05 | `05_model_evaluation.ipynb` | Metrics, comparison, and business interpretation |

**Notebook standards:**

- **Kernel Restart & Run All** must pass without errors.
- Logical flow per notebook: Import → Load → Process → Visualize/Evaluate → Save.
- Markdown cells must explain each major section before the code.
- Visualizations require titles, axis labels, and legends.
- Fixed random seeds: `random_state=42` or `np.random.seed(42)`.
- No hidden state: avoid variables defined only in deleted cells.
- Save report figures to `reports/figures/`.

### Source Module Standards

Reusable logic is factored into `src/` modules. Each subfolder (`data_preprocessing/`, `feature_engineering/`, `modeling/`, `evaluation/`) should contain focused, documented Python modules.

- Follow PEP 8 style guide.
- Use type hints for function arguments and return types.
- Use meaningful variable names (`customer_id`, `monthly_charges_scaled`, `churn_label`).
- No hardcoded paths — use `pathlib` or relative paths.
- Write docstrings for all public functions and classes.

### Code Comments Philosophy

Comment the **why**, not the **what**:

- Explain preprocessing choices (e.g., "Imputing with median to avoid sensitivity to outliers in TotalCharges").
- Explain feature engineering decisions (e.g., "Grouping tenure into buckets to capture non-linear churn behaviour").
- Explain model choices (e.g., "Using class_weight='balanced' to handle class imbalance in churn labels").

### Evaluation Standards

- **Prioritize Recall** — missing a churner (false negative) costs more than a false alarm.
- Report all standard metrics: Accuracy, Precision, Recall, F1-Score, ROC-AUC, Confusion Matrix.
- Include business interpretation: what does the metric mean for customer retention?

### Visualization

- Use Matplotlib and Seaborn.
- Always include titles, axis labels, and legends.
- Key plots: churn distribution, feature distributions, correlation heatmap, ROC curves, confusion matrices, feature importance.
- Save all report figures to `reports/figures/`.

---

## Running the Code

**Python Environment:**

```powershell
# Optional: suppress cross-drive hardlink warnings
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

- Name the specific notebook or module (e.g., `notebooks/02_data_preprocessing.ipynb`, `src/feature_engineering/churn_features.py`).
- Specify the task clearly (e.g., "handle missing values in TotalCharges", "encode categorical variables").
- Ask for evaluation metrics relevant to churn (Recall, F1, ROC-AUC, confusion matrix).
- Request business interpretation alongside technical metrics.
- Specify reproducibility: `random_state=42`.

---

## Protecting assistant governance (primary)

These files must stay **uncorrupted**: `.cursor/rules/`, mirrored **`.github/skills` ↔ `.cursor/skills`**, mirrored **`.github/agents` ↔ `.cursor/agents`**, `CLAUDE.md`, and this `copilot-instructions.md`. Before another AI tool or mass refactor touches them: **commit or stash**; edit **both** sides of each mirror in one change; prefer **small scoped diffs**; rely on **`ci-skills-parity.yml`** and **`ci-agent-docs-guard.yml`** on push.

**Secondary (only if damage already happened):** restore from Git — **`docs/agent-governance-recovery.md`**.
