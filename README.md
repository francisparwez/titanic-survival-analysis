# Titanic Survival Analysis

> Exploring passenger survival with Python and machine learning.

## About the Project

This project explores the Titanic passenger data and builds a machine learning workflow to predict survival.

The work is divided into two main parts: exploratory data analysis and machine learning. The EDA focuses on understanding and cleaning the data, while the ML stage uses the cleaned understanding of the data to build and compare prediction models.

## Current Progress

### Exploratory Data Analysis

The EDA covers data profiling, missing-value checks, cleaning, duplicate checks, feature engineering, outlier analysis, group-by analysis, correlation analysis, and the main findings from the data. It also includes 10 visualizations covering different aspects of the dataset.

The cleaned dataset from the EDA stage is saved as:

```text
data/titanic_cleaned.csv
```

### Machine Learning

The ML stage currently covers feature engineering, leakage-free preprocessing, and comparison of three classification models.

The following features were created from the original `train.csv` and `test.csv` files:

```text
Title
FamilySize
IsAlone
AgeBin
FareBin
Deck
CabinKnown
```

The preprocessing is handled using `Pipeline` and `ColumnTransformer`. Numerical columns go through median imputation and standard scaling, while categorical columns use most-frequent imputation followed by one-hot encoding.

Keeping these steps inside the pipeline means that, during cross-validation, the preprocessing is fitted separately using only the training portion of each fold.

### Model Comparison

Three models are currently being compared using the same preprocessing setup:

- Logistic Regression
- Random Forest
- Gradient Boosting

The comparison uses 5-fold stratified cross-validation with accuracy, ROC-AUC, and F1 score. The mean result across the five folds is used when comparing the models.

## Dataset

The project uses the Kaggle Titanic dataset. The `data` folder contains the original training and test files along with the cleaned dataset from the EDA stage.

```text
train.csv
test.csv
titanic_cleaned.csv
```

`train.csv` contains the `Survived` target, while `test.csv` does not. The cleaned file was produced during the EDA stage.

## Project Structure

```text
titanic-survival-analysis/
│
├── data/
│   ├── train.csv
│   ├── test.csv
│   └── titanic_cleaned.csv
│
├── images/
│   └── EDA visualizations
│
├── Titanic_EDA.ipynb
├── Titanic_ML.ipynb
├── SUMMARY.md
└── README.md
```

## Notebooks

### Titanic_EDA.ipynb

The EDA notebook covers the initial data checks, cleaning, feature engineering, visualizations, and analysis of the main survival patterns.

### Titanic_ML.ipynb

The ML notebook continues with feature engineering, preprocessing, cross-validation, and comparison of the three models.

## Getting Started

The project uses Python and the following libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Jupyter Notebook can then be started with:

```bash
jupyter notebook
```

The notebooks should be run from top to bottom.

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
- Git & GitHub

## Results

The EDA shows clear differences in survival by sex and passenger class. Fare and travelling alone also show useful relationships with survival, while age has a much weaker linear relationship.

The ML stage currently provides a baseline comparison of Logistic Regression, Random Forest, and Gradient Boosting using 5-fold stratified cross-validation. The detailed scores are available in the notebook.

The next stage is hyperparameter tuning and final model selection.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
