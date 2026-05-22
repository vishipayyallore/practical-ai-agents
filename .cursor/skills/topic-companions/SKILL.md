---
name: churn-workflow
description: >-
  Workflow notebook standards for Customer Churn Prediction ML — notebook sequence, naming,
  quality checklist, and definition of done. Use when adding or reviewing a notebook.
---

# Workflow Notebook Standards — Customer Churn Prediction ML

**Applies to**: `customer-churn-prediction-ml` **only**.
**Canonical governance**: `.github/copilot-instructions.md` and `docs/01-repository-structure.md`.

## Notebook Sequence

| # | Notebook | Purpose |
|---|----------|---------|
| 01 | `01_data_understanding.ipynb` | EDA — churn distribution, feature distributions, correlations |
| 02 | `02_data_preprocessing.ipynb` | Missing value handling, encoding, scaling |
| 03 | `03_feature_engineering.ipynb` | Tenure groups, service aggregations, risk indicators |
| 04 | `04_model_building.ipynb` | Logistic Regression, Decision Tree, Random Forest |
| 05 | `05_model_evaluation.ipynb` | Metrics, comparison, business interpretation |

## Standards (per notebook)

- [ ] Markdown concept cell before each major section.
- [ ] Fixed seed: `random_state=42` or `np.random.seed(42)`.
- [ ] `Kernel → Restart & Run All` passes without error.
- [ ] Visualizations have titles, axis labels, legends.
- [ ] Evaluation notebooks report Accuracy, Precision, Recall, F1, ROC-AUC, Confusion Matrix.
- [ ] Business interpretation accompanies technical results.

## Definition of done (per notebook)

- [ ] Named correctly: `XX_descriptive_name.ipynb`.
- [ ] Passes CI notebook JSON parse.
- [ ] No broken internal links.
- [ ] Clean kernel run verified.

## Related

- **Subagent:** `.cursor/agents/ml-topic-bundle-review.md` (one notebook pass)
- **CI commands:** `.github/skills/ci-checks/SKILL.md`
