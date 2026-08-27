# Titanic Survival Analysis

> Exploring the factors behind passenger survival using Python.

## About the Project

This project looks at the Titanic passenger dataset using Python. The goal is to understand the data, clean it, create useful features, and explore patterns related to passenger survival.

The project covers data profiling, data cleaning, feature engineering, exploratory data analysis, outlier analysis, and data visualization.

## Current Progress

So far, the project includes:

- Loading the Titanic training and test datasets
- Checking the shape and columns of both datasets
- Reviewing data types and basic dataset information
- Checking summary statistics
- Checking categorical variables
- Checking missing values and their percentages
- Checking for duplicate rows
- Reviewing the survival distribution
- Reviewing basic statistics for `Age`, `Fare`, `SibSp`, and `Parch`
- Filling missing `Age` values with the median
- Creating a `CabinKnown` flag for missing cabin information
- Filling missing `Embarked` values with the mode
- Checking data types after cleaning
- Checking duplicate rows again
- Performing a final missing-value check
- Extracting passenger `Title` from the `Name` column
- Creating `FamilySize` from `SibSp` and `Parch`
- Creating an `IsAlone` indicator from `FamilySize`
- Checking the new features
- Exploring the distributions of `Age`, `Fare`, and `Pclass`
- Checking possible outliers in `Age` and `Fare`
- Using the IQR method to flag possible outliers
- Comparing survival rates by sex, passenger class, and family size
- Creating a correlation heatmap
- Comparing survival by both sex and passenger class
- Creating and saving 10 visualizations as PNG files

## Data Cleaning

The dataset was checked for missing values, duplicate records, and data types.

The following steps were taken:

- Missing `Age` values were filled using the median age.
- Missing `Embarked` values were filled using the most common value.
- A `CabinKnown` column was created to show whether cabin information was available.
- The original `Cabin` column was kept instead of filling missing cabin values with made-up information.
- Duplicate rows were checked in both datasets.
- Data types were checked after cleaning.

## Feature Engineering

Three new features were created from the existing passenger information.

### Title

The passenger title was extracted from the `Name` column and stored in a new `Title` column.

Examples include:

- `Mr`
- `Mrs`
- `Miss`
- `Master`
- Other less common titles

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

## Exploratory Data Analysis

The EDA is divided into four parts.

### Univariate Analysis

The following variables were explored individually:

- `Age`
- `Fare`
- `Pclass`

### Outlier Analysis

Possible outliers were checked for `Age` and `Fare` using boxplots and the IQR method.

The possible outliers were flagged but not removed because unusual values can still represent real passengers and are not necessarily data errors.

### Bivariate Analysis

Survival rates were compared by:

- Sex
- Passenger class
- Family size

### Multivariate Analysis

A correlation heatmap was created to look at relationships between numerical variables.

Another visualization compares survival by both sex and passenger class.

## Visualizations

The notebook contains **10 visualizations**, which is above the required minimum of 8.

Each chart is saved as a PNG file in the `images` folder.

### 1. Age Distribution

![Age Distribution](images/01_age_distribution.png)

### 2. Fare Distribution

![Fare Distribution](images/02_fare_distribution.png)

### 3. Passengers by Class

![Passengers by Class](images/03_passengers_by_class.png)

### 4. Age Boxplot

![Age Boxplot](images/04_age_boxplot.png)

### 5. Fare Boxplot

![Fare Boxplot](images/05_fare_boxplot.png)

### 6. Survival Rate by Sex

![Survival Rate by Sex](images/06_survival_by_sex.png)

### 7. Survival Rate by Passenger Class

![Survival Rate by Passenger Class](images/07_survival_by_class.png)

### 8. Survival Rate by Family Size

![Survival Rate by Family Size](images/08_survival_by_family_size.png)

### 9. Correlation Heatmap

![Correlation Heatmap](images/09_correlation_heatmap.png)

### 10. Survival Rate by Sex and Class

![Survival Rate by Sex and Class](images/10_survival_by_sex_and_class.png)

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

The notebook creates the `images` folder and saves the visualizations as PNG files when the visualization cells are run.

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
├── images/
│   ├── 01_age_distribution.png
│   ├── 02_fare_distribution.png
│   ├── 03_passengers_by_class.png
│   ├── 04_age_boxplot.png
│   ├── 05_fare_boxplot.png
│   ├── 06_survival_by_sex.png
│   ├── 07_survival_by_class.png
│   ├── 08_survival_by_family_size.png
│   ├── 09_correlation_heatmap.png
│   └── 10_survival_by_sex_and_class.png
│
├── Titanic_EDA.ipynb
│
└── README.md
```

## Results

The data cleaning, feature engineering, exploratory analysis, outlier checks, and visualizations are now in place.

The final data-driven insights and statistical conclusions will be added after the remaining analysis is completed.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
