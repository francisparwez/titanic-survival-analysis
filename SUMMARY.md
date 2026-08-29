# Titanic Survival Analysis — Summary

## Project Overview

This project uses the Titanic passenger dataset to understand the data and build a machine learning workflow for survival prediction.

The project currently covers the completed EDA work and the first part of the machine learning work.

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

The ML notebook is now in the feature-engineering stage.

The following features have been created from the original `train.csv` and `test.csv`:

- `Title`
- `FamilySize`
- `IsAlone`
- `AgeBin`
- `FareBin`
- `Deck`
- `CabinKnown`

Missing values have not been manually filled in the ML notebook at this stage. They will be handled later inside the preprocessing pipeline so that the preprocessing can be fitted only on the appropriate training data.

## Next ML Steps

The remaining ML workflow will cover:

1. Train-test split
2. Leakage-free preprocessing
3. Baseline models
4. Stratified cross-validation
5. Model comparison
6. Hyperparameter tuning
7. Final model selection
8. Calibration
9. Permutation importance
10. SHAP analysis
11. Model card
12. Final model artifact

## Output

The EDA phase exports:

`data/titanic_cleaned.csv`

The ML phase will add its model outputs after training and evaluation are complete.

## Note

The EDA findings describe associations in the dataset. They should not be treated as proof that one variable directly caused survival.
