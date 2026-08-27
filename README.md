# Titanic Survival Analysis

> Exploring the factors behind passenger survival using Python.

## About the Project

This project looks at the Titanic passenger dataset using Python. The goal is to understand the data, clean it, and create useful features that can be used to explore patterns in passenger survival.

The analysis covers data profiling, data cleaning, feature engineering, exploratory data analysis, and basic statistical analysis.

## Current Progress

So far, the project includes:

- Loading the Titanic training and test datasets
- Checking the shape and columns of both datasets
- Reviewing data types and basic dataset information
- Checking summary statistics
- Checking categorical variables
- Checking missing values and their percentages
- Checking for duplicate rows
- Looking at the survival distribution
- Reviewing basic statistics for `Age`, `Fare`, `SibSp`, and `Parch`
- Filling missing `Age` values with the median
- Creating a `CabinKnown` flag for missing cabin information
- Filling missing `Embarked` values with the mode
- Checking data types after cleaning
- Checking for duplicate rows again
- Performing a final missing-value check
- Extracting passenger `Title` from the `Name` column
- Creating `FamilySize` from `SibSp` and `Parch`
- Creating an `IsAlone` indicator from `FamilySize`
- Checking the new features and their data types

More analysis will be added as the project progresses.

## Data Cleaning

The dataset was checked for missing values, duplicate records, and data types.

The following steps were taken:

- Missing `Age` values were filled using the median age.
- Missing `Embarked` values were filled using the most common value.
- A `CabinKnown` column was created to show whether cabin information was available.
- The original `Cabin` column was kept because the missing values were not replaced with made-up cabin information.
- Duplicate rows were checked and no complete duplicate records were found.
- Data types were checked after cleaning to make sure they were suitable for the analysis.

## Feature Engineering

Three new features have been created so far.

### Title

The passenger title was extracted from the `Name` column.

Examples include:

- `Mr`
- `Mrs`
- `Miss`
- `Master`
- Other less common titles

The `Title` feature can be used later to compare survival patterns between different passenger groups.

### FamilySize

`FamilySize` was created using:

```python
FamilySize = SibSp + Parch + 1
```

The `+1` represents the passenger themselves.

### IsAlone

`IsAlone` was created from `FamilySize`.

```text
1 = Passenger was travelling alone
0 = Passenger was travelling with family
```

These features will be used later during the exploratory analysis.

## Dataset

The project uses the Kaggle Titanic dataset, which is split into two files:

- `train.csv` — Contains passenger information and the `Survived` target variable.
- `test.csv` — Contains passenger information but does not include the `Survived` variable.

The datasets are stored in the `data` folder.

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/francisparwez/titanic-survival-analysis.git
cd titanic-survival-analysis
```

### 2. Install the required libraries

Make sure Python is installed, then run:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

Open `Titanic_EDA.ipynb` and run the cells from top to bottom.

## Tech Stack

- **Python** — Main programming language
- **Pandas** — Data cleaning and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Jupyter Notebook** — Analysis and documentation
- **Git & GitHub** — Version control

## Project Structure

```text
Titanic-Survival-Analysis/
│
├── data/
│   ├── train.csv
│   └── test.csv
│
├── Titanic_EDA.ipynb
│
└── README.md
```

## Project Preview

A screenshot of the final analysis will be added here once the visualizations are completed.

<!-- Screenshot will be added here later -->

## Results

The final results and key findings will be added after the exploratory analysis and visualizations are completed.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
