# Megaline Mobile Plan Recommendation

TripleTen classification coursework predicting the recorded Smart/Ultra mobile-plan label from monthly usage. The dataset contains **3,214 customer records**, with calls, minutes, messages, and mb_used as features and is_ultra as the target.

## Methods
Stratified 60/20/20 training/validation/test splitting with random_state=42; Random Forest, Decision Tree, and scaled Logistic Regression; five-fold cross-validation and GridSearchCV. The original Random Forest configuration was selected using validation and refit on train plus validation before test scoring.

## Saved results
- Random Forest test accuracy: **81.65%** (as displayed in the notebook).
- Majority-class test baseline: **69.36%**; approximately **12.29 percentage points** lower.
- Decision Tree test accuracy: **79.16%**.
- Logistic Regression test accuracy: **73.25%**.
- Original forest validation accuracy: **81.03%**; tuned forest: **80.72%**. Tuning did not improve this validation result.

The test split contains 643 records. Results are retained from the supplied notebook, not rerun during preparation.

## Run
Use Python 3.10 or newer in a virtual environment:

```bash
pip install -r requirements.txt
jupyter lab
```

Obtain users_behavior.csv through authorized course access and place it in data/users_behavior.csv, or set MEGALINE_DATA_PATH. Open megaline_plan_recommendation.ipynb and run in order. Data is excluded. The forest search tests 216 configurations with five-fold CV and can take substantial time; reduce the grid for experimentation while keeping original results clearly labeled.

## Limits
Later cells compare additional models on the same test split, so this is exploratory evaluation rather than a fully untouched final holdout. Accuracy alone can conceal weaker minority-class performance. Predicting an existing plan label does not determine an optimal plan or establish conversion, revenue, or savings improvements. No deployment or measured business outcome is claimed. Original dependency versions are unavailable; dependencies are unpinned. The portfolio copy corrects the narrative and makes data loading portable; no model metrics were changed or regenerated.
