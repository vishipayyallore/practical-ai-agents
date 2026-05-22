---
name: churn-project
description: Context and standards for the Customer Churn Prediction ML project — scope, workflow, dataset, models, and evaluation standards.
---

# Customer Churn Prediction ML

**Scope:** Swamy PKV's personal Advanced Apex Project. See `README.md` and `.cursor/rules/swamy_personal_learning_only.mdc`.

## Project Overview

End-to-end ML pipeline to predict customer churn using the IBM Telco Customer Churn Dataset.

## ML Workflow (Notebook Sequence)

| Notebook | Purpose |
|----------|---------|
| `01_data_understanding.ipynb` | Dataset exploration and EDA |
| `02_data_preprocessing.ipynb` | Cleaning and preprocessing |
| `03_feature_engineering.ipynb` | Feature creation and transformation |
| `04_model_building.ipynb` | Baseline and comparative models |
| `05_model_evaluation.ipynb` | Metrics, comparison, business interpretation |

## Models

- Baseline: Logistic Regression
- Comparative: Decision Tree, Random Forest

## Evaluation Priority

Recall is the primary metric — missing a churner is more costly than a false alarm.

## Related

- **CI commands:** `.github/skills/ci-checks/SKILL.md`
- **Workspace review:** `.github/skills/workspace-review/SKILL.md`
- **Subagent:** `.cursor/agents/ml-ci-verify.md`
