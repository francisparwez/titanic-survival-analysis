# Titanic Survival Analysis

> Exploring passenger survival with Python and machine learning.

## About the Project

This project uses the Titanic passenger dataset to understand the data, find patterns in survival, and build a machine learning model to predict survival.

The project is being completed in two main parts:

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

The machine learning phase has started.

So far, the notebook includes:

- Loading the original training and test data
- Initial data checks
- Extracting `Title` from `Name`
- Creating `FamilySize`
- Creating `IsAlone`
- Creating `AgeBin`
- Creating `FareBin`
- Extracting `Deck` from `Cabin`
- Creating `CabinKnown`

The next part of the ML work will cover preprocessing, model training, cross-validation, tuning, evaluation, calibration, and model interpretation.

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

This notebook focuses on turning the passenger data into useful features and building the machine learning workflow.

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

The machine learning results will be added after model training and evaluation are complete.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
