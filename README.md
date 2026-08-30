# Titanic Survival Analysis

> Exploring passenger survival with Python and machine learning.

## About the Project

This project uses the Titanic passenger dataset to understand the data and build a machine learning model to predict survival.

The work is split into two parts:

- Exploratory Data Analysis
- Machine Learning

## Current Progress

### Exploratory Data Analysis

The EDA phase includes:

- Data profiling
- Missing-value checks
- Data cleaning
- Duplicate checks
- Feature engineering
- Outlier analysis
- 10 visualizations
- Group-by analysis
- Correlation analysis
- Key findings

The cleaned EDA dataset is saved as `data/titanic_cleaned.csv`.

### Machine Learning

The ML phase currently covers the first two parts of the workflow.

Feature engineering was completed using the original `train.csv` and `test.csv` data. The notebook creates:

- `Title`
- `FamilySize`
- `IsAlone`
- `AgeBin`
- `FareBin`
- `Deck`
- `CabinKnown`

A leakage-free preprocessing setup has also been added.

The preprocessing uses:

- `Pipeline`
- `ColumnTransformer`
- Median imputation for numerical columns
- Most-frequent imputation for categorical columns
- `StandardScaler` for numerical columns
- `OneHotEncoder` for categorical columns

The preprocessing is fitted as part of the model pipeline using the training data. The validation data is only transformed after the preprocessing has been fitted.

The pipeline was also checked with stratified cross-validation. Because the preprocessing is inside the pipeline, each fold fits its own imputer, scaler, and encoder using that fold's training portion only.

A Logistic Regression pipeline has been used as the first check that the preprocessing and model work together.

The remaining ML work will cover model comparison, tuning, calibration, and model interpretation.

## Dataset

The project uses the Kaggle Titanic dataset:

- `train.csv` — contains passenger information and the `Survived` target
- `test.csv` — contains passenger information without the `Survived` target
- `titanic_cleaned.csv` — cleaned training data produced during the EDA phase

The files are stored in the `data` folder.

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

This notebook focuses on understanding and cleaning the data, followed by exploratory and statistical analysis.

### Titanic_ML.ipynb

This notebook focuses on feature engineering, leakage-free preprocessing, and the rest of the machine learning workflow.

## Getting Started

Install the main libraries with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then run the notebooks from top to bottom.

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

The EDA found clear differences in survival by sex and passenger class. Fare and travelling alone also showed useful relationships with survival, while age had a much weaker linear relationship.

The ML model results will be added as the remaining model comparison and evaluation steps are completed.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
