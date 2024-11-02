# Predictive Modeling of Birth Weight

Welcome to the **Predictive Modeling of Birth Weight** repository! This project is an in-depth analysis of the factors affecting infant birth weight to demonstrate proficiency in statistical modeling, data transformation, and evaluation of predictive models.

## Table of Contents

- [Project Overview](#project-overview)
- [Motivation](#motivation)
- [Data Description](#data-description)
- [Methodology](#methodology)
  - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
  - [Preliminary Transformations](#preliminary-transformations)
  - [Model Construction](#model-construction)
  - [Model Comparison](#model-comparison)
- [Key Findings](#key-findings)
- [Results](#results)
- [Limitations and Future Work](#limitations-and-future-work)
- [Installation and Setup](#installation-and-setup)
- [How to Run the Analysis](#how-to-run-the-analysis)
- [Contact Information](#contact-information)
- [License](#license)

## Project Overview

This project examines the significance of eight variables as predictors of birth weight using multiple regression models. We utilized data collected from Baystate Medical Centre, MA, in 1986, containing 189 observations. The analysis compares the performance of models trained on the original dataset with those trained on a version where categorical factor levels with few observations were merged to mitigate overfitting.

## Motivation

Low birth weight is a critical public health issue associated with increased risks of infant mortality and long-term health complications. Despite its importance, predictors of low birth weight are not extensively studied. This project aims to identify the most significant predictors of birth weight and improve model generalizability to inform better healthcare decisions.

## Data Description

The **birthwt** dataset, sourced from the MASS package, consists of 10 variables, including the dependent variable (birth weight) and several categorical and numerical independent variables. The variables were transformed and renamed for clarity, focusing on four numerical and four categorical predictors.

### Data Summary

- **Dependent Variable**: Birth weight (grams)
- **Predictors**: 
  - Categorical: Race, Smoking Status, Hypertension, Uterine Irritation, etc.
  - Numerical: Weight at Last Menstruation, Number of Premature Labors, Number of First Trimester Physician Visits

For a detailed tabular summary, refer to the appendix in the report.

## Methodology

### Exploratory Data Analysis (EDA)

Initial data exploration revealed several variables that did not satisfy linearity assumptions with the dependent variable. The discrete nature of some predictors necessitated transformations to improve model fit.

### Preliminary Transformations

- **Factorization**: Variables like the number of premature labors and first trimester physician visits were transformed into categorical variables.
- **Log Transformation**: Applied to weight at last menstruation to improve linearity and homoscedasticity.

### Model Construction

Two versions of the dataset were prepared:
1. **Original Dataset**: All factor levels retained.
2. **Merged Levels Dataset**: Levels with few observations were combined to reduce overfitting risk.

Linear regression models were built for both datasets, and stepwise selection was used to identify the most significant predictors. Model assumptions (independence, normality, linearity, and homoscedasticity) were thoroughly checked.

### Model Comparison

- **R² and AIC**: Used to compare in-sample and out-of-sample performance.
- **Cross-Validation**: Performed 10-fold cross-validation with 1,000 repetitions to evaluate model generalizability.

## Key Findings

- **Significant Predictors**: Variables such as race, smoking status, hypertension, and uterine irritation were found to be significant. Mother's age and the number of physician visits were dropped for being non-informative.
- **Merged Levels**: Merging factor levels improved out-of-sample performance, reducing overfitting while slightly lowering R².

## Results

The refined model with merged factor levels demonstrated better generalizability, with significant reductions in Root Mean Squared Error and Mean Absolute Error. Despite a minor decrease in R², the trade-off for improved out-of-sample performance was justified.

### Final Model

The final regression equation is:
  
\[
\hat{\text{Birth weight}} = 610.22 + 132.66(\text{RaceOther}) + 460.01(\text{RaceWhite}) 
- 316.87(\text{SmokeYes}) - 211.68(\text{PTL} \geq 1) - 562.41(\text{HTYes}) 
- 483.45(\text{UIYes}) + 572.37(\log(\text{LMW}))
\]

This model highlights the positive impact of race (Other and White) and the negative impact of smoking, premature labors, hypertension, and uterine irritation on birth weight.

## Limitations and Future Work

- **Sample Bias**: The data is from a single medical center, limiting generalizability. Expanding the sample size and diversity would improve model robustness.
- **Loss of Information**: Merging factor levels simplified the model but may have introduced bias. Future research should explore more nuanced approaches to handling sparse data.

## Installation and Setup

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/birthweight-analysis.git
   ```

2. **Navigate to the Project Directory**:

   ```bash
   cd birthweight-analysis
   ```

3. **Install Dependencies**:

   Make sure you have R installed, along with the necessary packages:

   ```R
   install.packages(c("MASS", "tidyverse", "caret"))
   ```

## How to Run the Analysis

1. Open the **R Project** file in your preferred IDE (e.g., RStudio).
2. Load the dataset and run the scripts to perform EDA, model construction, and evaluation.
3. Review the plots and results generated to understand the model performance.


Thank you for reviewing this analysis! Your feedback and suggestions for future improvements are greatly appreciated.
