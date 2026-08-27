# Titanic Survival Analysis

> **Exploring the factors behind passenger survival using Python.**

## About the Project

This project is an end-to-end exploratory data analysis of the Titanic passenger dataset. The goal is to clean and understand the data, identify patterns in passenger survival, and explore how factors such as age, sex, passenger class, fare, and family size were associated with survival.

The analysis covers the full EDA process, from initial data profiling and cleaning to feature engineering, visualization, and statistical analysis.

## Key Features

- Initial data profiling and quality checks
- Handling missing values and duplicate records
- Data type corrections and basic data cleaning
- Feature engineering, including:
  - Passenger titles
  - Family size
  - IsAlone indicator

- Univariate analysis of key variables
- Bivariate analysis of survival patterns
- Multivariate analysis and correlation analysis
- Statistical summaries and group-by analysis
- 8+ visualizations using Matplotlib and Seaborn
- Data-driven findings and conclusions

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

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the Titanic analysis notebook and run the cells from top to bottom.

### 4. Dataset

The project uses the Kaggle Titanic dataset, which is provided as two separate files:

- `train.csv` — Contains passenger information along with the `Survived` target variable.
- `test.csv` — Contains passenger information without the `Survived` variable.

Both datasets are included in the `data` folder, so no additional download is required to reproduce the analysis.

## Tech Stack

- **Python** — Main programming language
- **Pandas** — Data cleaning, manipulation, and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Jupyter Notebook** — Analysis and documentation
- **Git & GitHub** — Version control and project sharing

## Project Structure

```text
Titanic-Survival-Analysis/
│
├── data/
│   ├── test.csv
│   └── train.csv
│
├── README.md
│
└── ...
```

## Results

The final analysis will highlight the main factors associated with passenger survival and present the findings through statistical summaries and visualizations.

More detailed findings will be added here once the analysis is complete.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
