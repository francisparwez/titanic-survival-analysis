# Titanic Survival Analysis — Summary

## Project Overview

This project started with an exploratory analysis of the Titanic passenger data and then moved into the machine learning stage. The EDA work is complete, and the ML notebook now covers feature engineering, leakage-free preprocessing, model comparison, hyperparameter tuning, calibration, permutation importance, SHAP analysis, and saving the final model.

## EDA Summary

The initial cleaning focused mainly on missing values. `Age` had 177 missing values, around 19.87% of the training data, so the median was used during the EDA cleaning step. `Cabin` had 687 missing values, around 77.10%, so a `CabinKnown` feature was created instead of trying to guess the missing cabin values. `Embarked` had 2 missing values, around 0.22%, which were filled using the mode, `S`. No duplicate rows were found.

The EDA also created `Title`, `FamilySize`, `IsAlone`, `FamilyGroup`, and `TitleGroup` to make the analysis easier.

## Main Findings

Female passengers had a survival rate of about 74.20%, compared with 18.89% for male passengers.

Survival also differed by passenger class. The rates were 62.96% for first class, 47.28% for second class, and 24.24% for third class.

`Fare` had a correlation of about 0.257 with survival, while `IsAlone` had a correlation of about -0.203. `Age` had a much weaker correlation of around -0.065.

The EDA notebook contains 10 visualizations covering the main distributions, passenger groups, survival patterns, outliers, and correlations.

## Machine Learning Progress

The ML notebook creates `Title`, `FamilySize`, `IsAlone`, `AgeBin`, `FareBin`, `Deck`, and `CabinKnown`.

The preprocessing uses a scikit-learn `Pipeline` and `ColumnTransformer`. Numerical columns use median imputation and standard scaling. Categorical columns use most-frequent imputation followed by one-hot encoding.

The preprocessing stays inside the pipeline. During cross-validation, each fold fits its imputer, scaler, and encoder using only that fold's training data.

### Model Comparison

Three models are compared using the same preprocessing setup:

1. Logistic Regression
2. Random Forest
3. Gradient Boosting

The comparison uses 5-fold stratified cross-validation and looks at accuracy, ROC-AUC, and F1 score.

### Hyperparameter Tuning

GridSearchCV is used to test parameter combinations for each model. The search keeps preprocessing inside each pipeline during the cross-validation folds.

The tuned models are then checked on the held-out validation set using accuracy, ROC-AUC, and F1.

### Final Model and Calibration

Logistic Regression was selected as the final model based on the overall validation results.

The validation results were:

- Accuracy: 0.8156
- ROC-AUC: 0.8625
- F1: 0.7519

The calibrated version produced a Brier Score of 0.1365, and the calibration plot was saved in the `images` folder.

### Model Interpretation

The selected model was interpreted using permutation importance and SHAP.

Permutation importance was calculated on the validation set and showed the largest ROC-AUC impact from `Sex`, `Title`, `Pclass`, and `Age`.

SHAP was applied to the selected Logistic Regression model after preprocessing. The strongest transformed features in the SHAP results included `Title_Mr`, `Pclass`, `Sex_female`, `Sex_male`, `CabinKnown`, and `Age`.

The interpretation plots are saved in the `images` folder.

### Model Card and Reproducibility

A short model card is included in the final section of the ML notebook. It records the model, objective, features, preprocessing, expected performance, assumptions, and limitations.

The final calibrated pipeline is saved as:

```text
artifacts/titanic_survival_model.joblib
```

The saved file contains the preprocessing and model together so the same pipeline can be loaded and reused.

## Final Model

Logistic Regression was selected as the final model after comparing the tuned models using accuracy, ROC-AUC, and F1.

The held-out validation results before calibration were:

- Accuracy: 0.8156
- ROC-AUC: 0.8625
- F1: 0.7519

After calibration, the Brier Score was 0.1365 and ROC-AUC was 0.8622.

## Output

The EDA stage produces:

```text
data/titanic_cleaned.csv
```

The ML stage now produces model comparison results, tuned model results, calibration and interpretation plots, a model card, and a saved model artifact.

The final model is saved as:

```text
artifacts/titanic_survival_model.joblib
```
