# AI-Powered Retail Sales Prediction

## Project Overview

This machine learning project predicts retail store sales using the
Rossmann Store Sales dataset from Kaggle. It explores historical sales,
promotions, store characteristics, calendar patterns, and competition
information to understand and predict retail demand.

## Objectives

- Explore historical retail sales patterns.
- Study the relationship between promotions and sales.
- Prepare and combine sales and store information.
- Train and compare machine learning regression models.
- Evaluate predictions using MAE, RMSE, and R².
- Generate a CSV of predictions for the competition test dataset.

## Dataset

**Source:** [Rossmann Store Sales — Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/data)

The downloaded dataset contains:
- `train.csv` — historical sales records.
- `test.csv` — records requiring predictions.
- `store.csv` — store-level characteristics.
- `sample_submission.csv` — example submission structure.

The original dataset files are not included in this repository.
Download them from Kaggle and follow its access requirements.

## Tools and Technologies

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Google Colab
- Git and GitHub

## Workflow

1. Load and inspect the original dataset.
2. Check missing values and duplicate records.
3. Merge sales records with store information.
4. Explore daily sales, weekday patterns, and promotions.
5. Create calendar features.
6. Split the data chronologically into training and validation sets.
7. Train HistGradientBoostingRegressor and RandomForestRegressor.
8. Compare model performance.
9. Examine feature importance and prediction errors.
10. Generate predictions for the test dataset.

## Exploratory Data Analysis

### Average Daily Sales

The daily sales visualization shows recurring fluctuations, including
days with zero sales. Store closures contribute to these zero values.

### Sales by Day of the Week

Average sales differ by weekday. The analysis uses open-store records
to avoid mixing closed days into this comparison.

### Promotion Analysis

Observed average sales:
- No promotion: approximately 5,929
- Promotion: approximately 8,228

Sales were approximately 38.8% higher on promotion days in this
analysis of open stores. This is an association, not proof of causation.

## Model Evaluation

Validation used a chronological split, with earlier records used for
training and later records used for validation. The evaluated records
were restricted to open stores with positive sales.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| HistGradientBoostingRegressor | 1296.84 | 1786.98 | 0.6598 |
| RandomForestRegressor | 904.95 | 1330.35 | 0.8114 |

The Random Forest was trained on a reproducible sample of 150,000
training rows. On this validation setup, it achieved lower MAE and
RMSE and a higher R² than the first model.

These results are from the current experiment and are not Kaggle
leaderboard scores.

## Feature Importance

The Random Forest feature-importance analysis highlights variables
such as competition distance, promotions, store identity, competition
opening dates, and weekday information.

Feature importance describes predictive usefulness in this model;
it does not establish causal relationships.

## Project Files

- `submission.csv` — predictions in the competition's Id/Sales format.
- `feature_importance.png` — feature-importance visualization.
- `random_forest_actual_vs_predicted.png` — actual vs predicted plot.
- `random_forest_residuals.png` — prediction error distribution.
- `README.md` — project documentation.

## Limitations

- The Random Forest was trained on a sample rather than all eligible
  training rows.
- Validation included only open stores with positive sales, so the
  reported metrics do not describe closed-store predictions.
- Future customer counts were not used as model features.
- The model and feature set can be improved through additional tuning,
  temporal feature engineering, and more robust validation.
- The generated CSV is a prediction artifact; no leaderboard result
  is claimed.

## Future Improvements

- Tune model hyperparameters using time-aware validation.
- Compare with additional gradient-boosting models.
- Improve holiday and promotion features.
- Evaluate performance across stores and sales ranges.
- Track experiments and document reproducible results.

## Author

**Tanushri D**

Data Analytics | Machine Learning | Retail Technology
