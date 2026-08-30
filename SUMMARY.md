# Titanic Survival Analysis — Summary

## Project Overview

This project uses the Titanic passenger dataset to understand the data and build a machine learning workflow for survival prediction.

The EDA work is complete, and the ML workflow is now moving through feature engineering and preprocessing.

## EDA Summary

### Data Cleaning

- `Age` had **177 missing values**, about **19.87%** of the training data. The median was used for the EDA cleaning step because it is less affected by unusually high or low values.
- `Cabin` had **687 missing values**, about **77.10%** of the training data. Instead of guessing missing cabin numbers, a `CabinKnown` flag was created.
- `Embarked` had **2 missing values**, about **0.22%** of the training data. The mode, `S`, was used for the EDA cleaning step.
- No duplicate rows were found in the training data.

## EDA Feature Engineering

The EDA created:

- `Title` — extracted from `Name`
- `FamilySize` — calculated as `SibSp + Parch + 1`
- `IsAlone` — identifies passengers travelling alone
- `FamilyGroup` — groups passengers by family size
- `TitleGroup` — groups less common titles as `Rare`

## Key Findings

### 1. Survival differed strongly by sex

Female passengers had a survival rate of about **74.20%**, compared with **18.89%** for male passengers.

### 2. Survival differed by passenger class

Survival rates were:

- First class: **62.96%**
- Second class: **47.28%**
- Third class: **24.24%**

### 3. Fare had a positive relationship with survival

`Fare` had a correlation of about **0.257** with `Survived`.

This shows an association, not causation.

### 4. Travelling alone was associated with lower survival

`IsAlone` had a correlation of about **-0.203** with `Survived`.

### 5. Age had a weak linear relationship with survival

`Age` had a correlation of about **-0.065** with `Survived`.

## Visualizations

The EDA notebook contains **10 visualizations** covering:

1. Age distribution
2. Fare distribution
3. Passengers by class
4. Age boxplot
5. Fare boxplot
6. Survival rate by sex
7. Survival rate by passenger class
8. Survival rate by family group
9. Correlation heatmap
10. Survival rate by sex and passenger class

## Outlier Analysis

Potential outliers in `Age` and `Fare` were checked using the IQR method.

They were not automatically removed because an unusual value is not necessarily a data error.

## Machine Learning Progress

### Feature Engineering

The ML notebook creates the following features from the original training and test data:

- `Title`
- `FamilySize`
- `IsAlone`
- `AgeBin`
- `FareBin`
- `Deck`
- `CabinKnown`

### Leakage-Free Preprocessing

The ML notebook now uses a scikit-learn `Pipeline` and `ColumnTransformer`.

Numerical columns are processed with:

- Median imputation
- Standard scaling

Categorical columns are processed with:

- Most-frequent imputation
- One-hot encoding

The preprocessing is kept inside the model pipeline. It is fitted using the training data and then used to transform validation data.

This means the validation data does not provide the values used to calculate the imputation statistics, scaling parameters, or category encoding.

The pipeline was also checked with stratified cross-validation. Each fold fits the preprocessing on its own training portion before transforming that fold's validation portion.

A Logistic Regression pipeline has also been fitted as the first check of the preprocessing workflow.

## Next ML Steps

The remaining ML workflow will cover:

1. Baseline model comparison
2. Stratified cross-validation
3. Model comparison using accuracy, ROC-AUC, and F1
4. Hyperparameter tuning
5. Final model selection
6. Calibration check
7. Permutation importance
8. SHAP analysis
9. Model card
10. Final model artifact

## Output

The EDA phase exports:

`data/titanic_cleaned.csv`

The ML model outputs will be added after the remaining training and evaluation steps are complete.

## Note

The EDA findings describe associations in the dataset. They should not be treated as proof that one variable directly caused survival.
