# Credit Card Data Balance – Regression and Prediction Analysis

## Project Overview

This project explores correlations and predictive relationships between customer credit card balances and various demographic and banking factors. The analysis is designed to provide banks with insights that may inform decision-making regarding credit card customers.

The study uses the "Credit" dataset from ISLR2, which contains data for 400 customers.  
**Dependent variable:**  
- `Balance` (average credit card balance in dollars)

**Independent variables:**  
- `Income`, `Cards`, `Limit`, `Age`, `Rating`, `Education`, `Region`, `Student`, `Own`, `Married`  
(See variable definitions below.)

## Objectives & Research Questions

- **Objective:**  
  To investigate which factors have a significant correlation with customers’ average credit card balance, and to develop predictive models for future customers’ balances.
- **Main question:**  
  Which factors are significantly associated with credit card balance, and how strong are these associations?

## Methods and Visualization

- **Exploratory Visualization:**  
  Various plots were used to examine relationships and distributions (e.g., Balance vs. Income, histograms of Income/log Income, comparisons for students vs. non-students).
- **Data Processing:**  
  - Observations with `Balance = 0` were excluded for model relevance.
  - `Income` was log-transformed to reduce skewness and improve model behavior.
- **Regression Analysis:**  
  - Multiple regression models were estimated.
    - Initial models included all variables.
    - Final models included only those with statistically significant coefficients.
- **Prediction Models:**  
  - Compared Ordinary Least Squares (OLS), Ridge, and LASSO regression for predictive accuracy.
  - Used out-of-sample root mean squared percentage error (rMSPE) for model evaluation.

## Key Results

- **Significant predictors of credit card balance:**  
  - Log Income (`Income_log`), Limit, Cards, Age, and Student status
- **Model summary:**  
  - Final regression explained ~91.7% of variation in Balance.
  - Largest coefficients:  
    - `Income_log`: -365 (higher income → lower balance)
    - `Student`: 458 (students tend to have higher balances)
    - `Limit`: 0.27 (small positive effect)
    - `Cards`: 19.93 (more cards → higher balance)
    - `Age`: -1.41 (older age → lower balance)
- **Prediction models:**  
  - LASSO regression gave the lowest out-of-sample rMSPE (~129.33), but was only marginally better than OLS.

## Discussion

- **Interpretation:**  
  - Higher income is associated with lower credit card balances, possibly due to less need for borrowing.
  - Students tend to have higher balances, likely reflecting costs and financial needs associated with studying.
  - Older customers have lower balances, which may relate to risk tolerance.
  - More credit cards are associated with higher balances, consistent with greater credit usage.
- **Implications:**  
  The results can help banks predict and understand customer credit behavior. While causality is not established, the findings flag important correlates for future research and decision-making.

## Conclusions

- Several demographic and banking variables are strongly correlated with credit card balance.
- LASSO regression is recommended for prediction, but differences with OLS are minor.
- The project provides a foundation for further analysis and for banks considering new customers.

## How to Run

- Requires R and the ISLR2, tidyverse, ggplot2, and glmnet packages.
- Load the Credit dataset and follow the script in `analysis.R` (see Appendix for code).
- Data cleaning: remove observations with `Balance = 0`, log-transform `Income`.
- Run visualizations and regression/prediction code.

## Variable Definitions

- **Income:** Annual income (in $1,000s)
- **Limit:** Credit limit
- **Rating:** Credit score
- **Cards:** Number of credit cards
- **Age:** Age (years)
- **Education:** Years of education
- **Own:** Home ownership (1 = No, 2 = Yes)
- **Student:** Student status (1 = No, 2 = Yes)
- **Married:** Marital status (1 = No, 2 = Yes)
- **Region:** Geographic region (1 = East, 2 = South, 3 = West)
- **Balance:** Average credit card balance (dollars)

## Files

- `analysis.R`: Main R script for data cleaning, visualization, regression, and prediction.
- (Optional) `Credit.csv` or use the ISLR2 Credit dataset directly.

