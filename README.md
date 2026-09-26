# titanic-preprocessing
Data cleaning, preprocessing, and exploratory data analysis of the Titanic dataset using R. Includes missing value imputation, outlier detection (IQR), categorical encoding, normalization, visualizations (ggplot2), correlation analysis, and a complete report with R code.
# Titanic Data Analysis in R

Data cleaning, preprocessing, and exploratory data analysis of the Titanic dataset using R.

![R](https://img.shields.io/badge/R-4.6.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-completed-brightgreen)

---

## 📊 Dataset Overview

- **Source:** [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic/data)
- **Size:** 891 observations × 12 variables
- **Type:** Mix of numerical and categorical features
- **Missing Values:** Age (177), Cabin (687), Embarked (2)

### Variables

| Variable | Type | Description |
|----------|------|-------------|
| PassengerId | Integer | Unique identifier |
| Survived | Integer | Survival status (0 = No, 1 = Yes) |
| Pclass | Integer | Passenger class (1, 2, 3) |
| Name | Character | Full name |
| Sex | Character | Gender (male/female) |
| Age | Numeric | Age in years |
| SibSp | Integer | Siblings/spouses aboard |
| Parch | Integer | Parents/children aboard |
| Ticket | Character | Ticket number |
| Fare | Numeric | Passenger fare |
| Cabin | Character | Cabin number |
| Embarked | Character | Port (C, Q, S) |

---

## 🎯 Project Objectives

- Handle missing values using appropriate imputation strategies
- Detect and analyze outliers using the IQR method
- Encode categorical variables for modeling
- Normalize numerical features
- Perform exploratory data analysis with visualizations
- Generate actionable insights from the data

---

## 🛠️ Tools & Technologies

- **Language:** R 4.6.1
- **IDE:** Visual Studio Code with R Extension
- **Libraries:**
  - `tidyverse` — Data manipulation & visualization
  - `skimr` — Summary statistics
  - `naniar` — Missing value visualization
  - `mice` — Multivariate imputation
  - `corrplot` — Correlation heatmaps
  - `janitor` — Data cleaning utilities

---

## 🧹 Data Cleaning Methodology

### 1. Missing Value Handling

| Variable | Missing % | Strategy | Reasoning |
|----------|-----------|----------|-----------|
| Age | 19.87% | Median imputation | Robust to outliers |
| Embarked | 0.22% | Mode imputation | Minimal missingness |
| Cabin | 77.10% | Binary encoding | Too many missing |

### 2. Outlier Detection

Applied IQR method (Q1 - 1.5×IQR, Q3 + 1.5×IQR):
- **Fare:** 116 outliers detected (retained as legitimate high-value tickets)
- **Age, SibSp, Parch:** 0 outliers

### 3. Categorical Encoding

- **Sex:** male → 0, female → 1
- **Embarked:** C → 1, Q → 2, S → 3
- **Pclass:** Converted to factor

### 4. Normalization

Min-Max scaling applied to Age and Fare (0-1 range).

---

## 📈 Key Insights

| Insight | Value |
|---------|-------|
| Overall survival rate | **38.4%** |
| Female survival rate | **74%** |
| Male survival rate | **19%** |
| 1st class survival | **~63%** |
| 3rd class survival | **~24%** |
| Strongest correlation | **Pclass ↔ Fare (-0.55)** |
| Family correlation | **SibSp ↔ Parch (+0.41)** |

### Top 5 Correlations

1. `Pclass ↔ Fare`: **-0.55** — Higher class number = lower fare
2. `SibSp ↔ Parch`: **+0.41** — Families traveled together
3. `Pclass ↔ Survived`: **-0.34** — Lower class = higher survival
4. `Age ↔ Pclass`: **-0.34** — Younger passengers in 3rd class
5. `Fare ↔ Survived`: **+0.26** — Higher fare = higher survival

---

## 📊 Visualizations

### Age Distribution
Histogram showing most passengers were between 20-40 years old.

### Survival by Gender
Bar chart showing females had significantly higher survival rates.

### Fare by Passenger Class
Boxplot showing fare distribution across 1st, 2nd, and 3rd class.

### Correlation Heatmap
Matrix visualization of relationships between numeric variables.

---

## 📁 Repository Structure
titanic-data-analysis-r/
│
├── data/
│ └── train.csv # Raw dataset
│
├── scripts/
│ └── analysis.R # Complete R script
│
├── outputs/
│ ├── age_hist.png # Age distribution
│ ├── survival_sex.png # Survival by gender
│ ├── fare_pclass.png # Fare by class
│ ├── missing_values.png # Missing values plot
│ └── correlation.png # Correlation heatmap
│
├── report/
│ ├── Report.doc # Final report
│ └── screenshots/ # All screenshots
│
├── README.md
└── .gitignore

---

## 🚀 How to Run

### Prerequisites
- R 4.6.1 or higher
- RStudio or VS Code with R extension

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/titanic-data-analysis-r.git
   cd titanic-data-analysis-r

  Install required packages:

install.packages(c( "tidyverse", "skimr", "naniar", "mice", "corrplot", "janitor" ))
  # Run the analysis:

source("scripts/analysis.R")
# View outputs:

 1. Plots will be saved in outputs/
 2. Report available in report/Report.doc
# R Code Snippet
# Load libraries
library(tidyverse)
library(naniar)

# Load data
df <- read.csv("data/train.csv")

# Handle missing values
df$Age[is.na(df$Age)] <- median(df$Age, na.rm = TRUE)
df$HasCabin <- ifelse(is.na(df$Cabin), 0, 1)
df$Cabin <- NULL

# Visualization
ggplot(df, aes(x = Age)) +
  geom_histogram(bins = 30, fill = "steelblue") +
  labs(title = "Age Distribution")
# License
This project is licensed under the MIT License — see the LICENSE file for details.
# Author
Naman Tiwari
GitHub: @namantiwari222/namantiwari222
Email: naman701758@gmail.com

