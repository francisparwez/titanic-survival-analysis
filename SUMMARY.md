# Titanic Survival Analysis — Summary

## Project Overview

This project started with an exploratory analysis of the Titanic passenger data and has now moved into the machine learning stage. The EDA work is complete, and the ML notebook currently covers feature engineering, leakage-free preprocessing, and a comparison of three models.

## EDA Summary

The initial data cleaning focused mainly on missing values. `Age` had 177 missing values, around 19.87% of the training data, so the median was used during the EDA cleaning step. `Cabin` had 687 missing values, around 77.10%, so instead of trying to fill in the missing cabin information, a `CabinKnown` feature was created. `Embarked` had only 2 missing values, around 0.22%, which were filled using the mode, `S`. No duplicate rows were found.

A few additional features were created during the EDA. These included `Title`, extracted from `Name`, `FamilySize`, calculated from `SibSp + Parch + 1`, and `IsAlone`, which identifies passengers travelling without family. `FamilyGroup` and `TitleGroup` were also created to make some of the analysis easier.

## Main Findings

One of the clearest patterns was the difference in survival between male and female passengers. Female passengers had a survival rate of about 74.20%, compared with 18.89% for male passengers.

Passenger class also showed a clear difference. The survival rate was 62.96% for first class, 47.28% for second class, and 24.24% for third class.

Fare had a correlation of about 0.257 with survival, while `IsAlone` had a correlation of about -0.203. Age had a much weaker correlation with survival at around -0.065.

The EDA notebook contains 10 visualizations covering age and fare distributions, passenger class, outliers, survival by sex and class, family groups, and the overall feature correlations.

Potential outliers in `Age` and `Fare` were also checked using the IQR method. They were not automatically removed during the analysis.

## Machine Learning Progress

The ML notebook starts from the original training and test datasets and adds several features: `Title`, `FamilySize`, `IsAlone`, `AgeBin`, `FareBin`, `Deck`, and `CabinKnown`.

The preprocessing is handled with a scikit-learn `Pipeline` and `ColumnTransformer`. Numerical columns use median imputation and standard scaling, while categorical columns use most-frequent imputation followed by one-hot encoding.

The preprocessing stays inside the pipeline rather than being applied to the full dataset beforehand. During cross-validation, each fold fits its preprocessing using only the training portion of that fold.

Three models have been compared using the same preprocessing setup: Logistic Regression, Random Forest, and Gradient Boosting. The comparison uses 5-fold stratified cross-validation and looks at accuracy, ROC-AUC, and F1 score. The notebook reports the mean scores across the five folds.

## Next Steps

The next part of the ML work will focus on hyperparameter tuning and choosing the final model. After that, the workflow will move on to calibration, permutation importance, SHAP analysis, the model card, and the final model artifact.

## Output

The EDA stage produces:

```text
data/titanic_cleaned.csv
```

The ML notebook currently produces the cross-validation results for the three baseline models. Further outputs will be added as the remaining ML work is completed.
