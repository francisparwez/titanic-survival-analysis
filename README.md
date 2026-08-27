# Titanic Survival Analysis

> Exploring the factors behind passenger survival using Python.

## About the Project

This project looks at the Titanic passenger dataset using Python. The goal is to understand the data, clean it, create useful features, and explore patterns related to passenger survival.

The project covers data profiling, data cleaning, feature engineering, exploratory data analysis, outlier analysis, visualization, basic statistical analysis, and final data-driven findings.

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
- Creating and saving 10 visualizations as PNG files
- Creating summary statistics with `describe()`
- Calculating the overall survival rate
- Creating group-by summary tables for sex, passenger class, and family size
- Creating a correlation matrix
- Checking correlations with `Survived`
- Writing data-driven findings based on the analysis

## Data Cleaning

The dataset was checked for missing values, duplicate records, and data types.

The following steps were taken:

- Missing `Age` values were filled using the median age.
- Missing `Embarked` values were filled using the most common value.
- A `CabinKnown` column was created to show whether cabin information was available.
- The original `Cabin` column was kept instead of filling missing cabin values with made-up information.
- Duplicate rows were checked in both datasets.
- Data types were checked after cleaning.
- A final missing-value check was performed after the cleaning steps.

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

The EDA is divided into univariate, outlier, bivariate, and multivariate analysis.

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

## Basic Statistical Analysis

The analysis also includes basic statistics to support the patterns shown in the visualizations.

### Summary Statistics

`describe()` was used to review the main numerical variables, including:

- `Age`
- `Fare`
- `Pclass`
- `SibSp`
- `Parch`
- `Survived`

### Overall Survival Rate

The overall survival rate in the training dataset is **38.38%**.

### Survival by Sex

A group-by table was used to compare passengers and survivors by sex.

- Female passengers: 314 passengers, with a survival rate of about **74.20%**
- Male passengers: 577 passengers, with a survival rate of about **18.89%**

### Survival by Passenger Class

Survival was also compared across passenger classes.

- First class: **62.96%**
- Second class: **47.28%**
- Third class: **24.24%**

### Survival by Family Size

The `FamilySize` feature was used to compare survival rates across different family sizes.

The results show that survival rates were not the same across all family sizes. Smaller family groups showed different survival patterns from passengers travelling alone or in larger groups.

Some larger family-size groups have very small numbers of passengers, so their survival rates should be interpreted carefully.

### Correlation Analysis

A correlation matrix was created for the main numerical variables.

The correlations with `Survived` were also sorted to make the relationships easier to compare.

The strongest numerical relationships with survival in this analysis were:

- `Pclass`: **-0.338**
- `Fare`: **0.257**
- `IsAlone`: **-0.203**
- `Age`: **-0.065**

Correlation shows how variables are related to each other. It does not mean that one variable directly caused another.

## Key Findings

Based on the analysis, several clear patterns can be seen in passenger survival.

### 1. Sex was strongly related to survival

Female passengers had a much higher survival rate than male passengers.

The survival rate for females was about **74.20%**, compared with about **18.89%** for males.

### 2. Passenger class was related to survival

Passengers in higher classes generally had higher survival rates.

The survival rate was about **62.96%** for first-class passengers, **47.28%** for second-class passengers, and **24.24%** for third-class passengers.

### 3. Fare had a positive relationship with survival

`Fare` had a positive correlation with `Survived` of about **0.257**.

Passengers who paid higher fares tended to have higher survival rates. This is also related to passenger class, since higher-class passengers generally paid higher fares.

This does not mean that paying a higher fare directly caused a passenger to survive.

### 4. Travelling alone was associated with lower survival

`IsAlone` had a negative correlation with `Survived` of about **-0.203**.

This suggests that passengers travelling alone generally had lower survival compared with passengers travelling with family.

### 5. Age had a weak relationship with survival

`Age` had a correlation of about **-0.065** with `Survived`.

This is a relatively weak relationship, so age alone did not show a strong linear relationship with survival in this analysis.

### 6. Family size showed different survival patterns

Survival rates were not the same across all family sizes.

Passengers travelling with smaller family groups showed different survival patterns from passengers travelling alone or in larger groups.

Some larger family-size groups contained very few passengers, so their survival rates should be interpreted carefully.

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

The project now covers the main data cleaning, feature engineering, EDA, visualization, statistical analysis, and data-driven findings required for the first stage of the internship task.

The analysis shows that sex and passenger class had some of the clearest relationships with survival, while fare, travelling alone, and family size also showed useful patterns. Age had a much weaker relationship with survival in this analysis.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
