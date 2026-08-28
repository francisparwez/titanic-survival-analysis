# Titanic Survival Analysis

> Exploring the factors behind passenger survival using Python.

## About the Project

This project uses the Titanic passenger dataset to understand the data, clean it, create useful features, and explore patterns related to passenger survival.

The analysis covers:

- Data profiling
- Data cleaning
- Feature engineering
- Exploratory data analysis
- Outlier analysis
- Data visualization
- Basic statistical analysis
- Data-driven findings

## What I Did

The notebook includes:

- Initial checks of the training and test datasets
- Data types and summary statistics
- Missing-value analysis
- Duplicate checks
- Survival distribution
- Cleaning of missing `Age` and `Embarked` values
- A `CabinKnown` feature for missing cabin information
- Feature engineering with `Title`, `FamilySize`, and `IsAlone`
- Grouped analysis using `FamilyGroup` and `TitleGroup`
- IQR-based checks for potential outliers
- 10 visualizations
- Group-by survival analysis
- Correlation analysis
- A final cleaned dataset export

## Data Cleaning

### Age

There are **177 missing Age values**, about **19.87%** of the training dataset.

The mean age is about **29.70 years** and the median is **28 years**. The median was used for imputation because it is less affected by unusually high or low ages.

### Cabin

There are **687 missing Cabin values out of 891 passengers**, or about **77.10%**.

Instead of filling in unknown cabin numbers, the notebook creates `CabinKnown`:

```text
1 = Cabin information is available
0 = Cabin information is missing
```

The original `Cabin` column is kept.

### Embarked

Only **2 `Embarked` values** are missing, or about **0.22%** of the dataset.

The most common value is **S**, with **644 passengers**, so the missing values were filled with the mode.

### Duplicates

No duplicate rows were found in the training dataset.

## Feature Engineering

### Title

The passenger title is extracted from `Name` and stored in `Title`.

Examples include:

- `Mr`
- `Mrs`
- `Miss`
- `Master`
- Other less common titles

A `TitleGroup` column is also used to group titles with fewer than 10 observations as `Rare`.

### FamilySize

```python
FamilySize = SibSp + Parch + 1
```

The `+1` represents the passenger.

### IsAlone

```text
1 = Passenger was travelling alone
0 = Passenger was travelling with family
```

### FamilyGroup

For easier comparison, family sizes are also grouped into:

```text
Alone
Small Family
Large Family
```

## Exploratory Data Analysis

### Univariate Analysis

The notebook explores:

- `Age`
- `Fare`
- `Pclass`

### Outlier Analysis

Potential outliers in `Age` and `Fare` were checked using boxplots and the IQR method.

The potential outliers were flagged but not automatically removed because an unusual value is not necessarily a data error.

### Bivariate Analysis

Survival rates are compared by:

- Sex
- Passenger class
- Family group
- Title group

### Multivariate Analysis

The notebook includes:

- A correlation heatmap
- Survival by sex and passenger class
- A group-by table for sex and passenger class

## Key Findings

### Survival by Sex

- Female passengers: **74.20%**
- Male passengers: **18.89%**

### Survival by Passenger Class

- First class: **62.96%**
- Second class: **47.28%**
- Third class: **24.24%**

### Correlation with Survival

- `Pclass`: **-0.338**
- `Fare`: **0.257**
- `IsAlone`: **-0.203**
- `Age`: **-0.065**

`Fare` and `Pclass` are also related, so the positive relationship between fare and survival should not be treated as an independent effect.

Correlation shows association and does not prove causation.

## Visualizations

The notebook contains **10 visualizations**, saved as PNG files in the `images` folder.

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

### 8. Survival Rate by Family Group

![Survival Rate by Family Group](images/08_survival_by_family_size.png)

### 9. Correlation Heatmap

![Correlation Heatmap](images/09_correlation_heatmap.png)

### 10. Survival Rate by Sex and Class

![Survival Rate by Sex and Class](images/10_survival_by_sex_and_class.png)

## Dataset

The project uses the Kaggle Titanic dataset:

- `train.csv` — contains passenger information and the `Survived` target
- `test.csv` — contains passenger information without the `Survived` target
- `titanic_cleaned.csv` — cleaned training dataset exported by the notebook

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
├── SUMMARY.md
└── README.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/francisparwez/titanic-survival-analysis.git
cd titanic-survival-analysis
```

### 2. Install the libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

Open `Titanic_EDA.ipynb` and run the cells from top to bottom.

The notebook creates the `images` folder and exports the cleaned dataset to `data/titanic_cleaned.csv`.

## Tech Stack

- **Python** — Main programming language
- **Pandas** — Data cleaning and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical visualization
- **Jupyter Notebook** — Analysis and documentation
- **Git & GitHub** — Version control

## Results

The analysis shows clear differences in survival by sex and passenger class. Fare and travelling alone also show useful relationships with survival, while age has a much weaker linear relationship.

The project focuses on describing these patterns from the dataset rather than treating them as proof of causation.

## Author

**Francis Parwez**

This project was completed as part of a Data Science & Analytics internship.
