# Titanic Survival Analysis — Summary

## Project Overview

This project uses the Titanic passenger dataset to explore factors associated with passenger survival.

The analysis covers data profiling, cleaning, feature engineering, exploratory data analysis, outlier checks, visualization, and basic statistical analysis.

## Data Cleaning

### Age

There are **177 missing Age values**, which is about **19.87%** of the training dataset.

The mean age is about **29.70 years**, while the median is **28 years**. I used the median to fill the missing values because it is less affected by unusually high or low ages.

### Cabin

There are **687 missing Cabin values out of 891 passengers**, or about **77.10%** of the dataset.

Instead of guessing missing cabin numbers, I created `CabinKnown`:

- `1` = cabin information is available
- `0` = cabin information is missing

The original `Cabin` column is kept.

### Embarked

Only **2 values** are missing from `Embarked`, which is about **0.22%** of the dataset.

The most common value is **S**, with **644 passengers**, so the missing values were filled with the mode.

### Duplicates

No duplicate rows were found in the training dataset.

## Feature Engineering

Three main features were created:

- `Title` — extracted from the passenger's `Name`
- `FamilySize` — calculated as `SibSp + Parch + 1`
- `IsAlone` — identifies passengers travelling without family members

Two additional grouping features are used for analysis:

- `FamilyGroup` — Alone, Small Family, or Large Family
- `TitleGroup` — keeps common titles and groups titles with fewer than 10 observations as `Rare`

## Key Findings

### 1. Sex showed one of the largest differences in survival

Female passengers had a survival rate of about **74.20%**, compared with **18.89%** for male passengers.

This is one of the clearest differences in the dataset.

### 2. Passenger class was strongly associated with survival

Survival rates were:

- First class: **62.96%**
- Second class: **47.28%**
- Third class: **24.24%**

The results show a clear difference in survival across passenger classes.

### 3. Fare had a positive relationship with survival

`Fare` had a correlation of about **0.257** with `Survived`.

Higher fares were generally associated with higher survival rates. However, fare is also related to passenger class, so this should not be interpreted as fare itself causing survival.

### 4. Travelling alone was associated with lower survival

`IsAlone` had a correlation of about **-0.203** with `Survived`.

Passengers travelling alone generally had lower survival rates than passengers travelling with family.

### 5. Age had a weak relationship with survival

`Age` had a correlation of about **-0.065** with `Survived`.

This is a weak linear relationship, so age alone did not show a strong association with survival in this analysis.

### 6. Family size showed different survival patterns

Survival rates varied across family sizes, but some raw family-size groups contained very few passengers.

For this reason, the notebook also compares `FamilyGroup` categories rather than relying only on very small individual groups.

## Visualization Summary

The notebook contains **10 visualizations**:

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

The survival-rate charts use percentage-formatted axes and data labels to make the comparisons easier to read.

## Outlier Analysis

Potential outliers in `Age` and `Fare` were identified using the IQR method.

The potential outliers were **not removed automatically** because an unusual value is not necessarily an error. These observations may represent real passengers and may contain useful information.

## Statistical Notes

The strongest numerical relationships with `Survived` in the analysis were:

- `Pclass`: **-0.338**
- `Fare`: **0.257**
- `IsAlone`: **-0.203**
- `Age`: **-0.065**

Correlation describes association and does not prove causation.

## Output

The cleaned dataset is exported as:

`data/titanic_cleaned.csv`

The notebook also saves the 10 visualization images in the `images` folder.
