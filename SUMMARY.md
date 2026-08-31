# Titanic Survival Analysis — Summary

## Project Overview

This project started with an exploratory analysis of the Titanic passenger data and has now moved into the machine learning stage. The EDA work is complete, and the ML notebook covers feature engineering, leakage-free preprocessing, model comparison, hyperparameter tuning, and a calibration check.

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

The comparison uses 5-fold stratified cross-validation and looks at accuracy, ROC-AUC, and F1 score. The mean scores across the five folds are used for the baseline comparison.

### Hyperparameter Tuning

After the baseline comparison, GridSearchCV is used to test a small set of parameter combinations for each model.

The tuning is done on the training data using 5-fold cross-validation. The preprocessing remains inside each pipeline during the search, so the imputation and encoding are not fitted on the validation data.

The best version of each model is then checked on the held-out validation set using accuracy, ROC-AUC, and F1.

### Final Model and Calibration

The final model is selected by looking at the three validation metrics together rather than choosing the model from accuracy alone.

A calibration check is then run on the selected model. The notebook reports accuracy, ROC-AUC, F1, and Brier score and also includes a calibration plot.

This gives a final check of both the model's classification performance and its predicted probabilities.

## Next Steps

The next part of the ML work will focus on understanding the final model. This will include permutation importance and SHAP analysis, followed by a short model card and the final model artifact.

## Output

The EDA stage produces:

```text
data/titanic_cleaned.csv
```

The ML notebook now produces baseline model results, tuned model results, final model selection results, and a calibration check.

The actual scores are generated when the notebook is run.
