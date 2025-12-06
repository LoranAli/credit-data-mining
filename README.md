# Credit Card Data Balance – Regression and Prediction Analysis

This project investigates how demographic and financial variables relate to customers’ average credit card balances.  
Using the **Credit** dataset from the ISLR2 package (400 observations), the analysis focuses on identifying significant predictors and building predictive models.

The project combines data cleaning, exploratory visualization, multiple regression, and regularized regression techniques (Ridge and LASSO).

---

## Dataset

- **Source:** ISLR2 – *Credit* dataset  
- **Observations:** 400 customers  
- **Key variables:**
  - `Balance` — average monthly credit card balance (USD)  
  - `Income` — annual income (USD thousands)  
  - `Limit` — credit limit  
  - `Rating` — credit score  
  - `Cards` — number of credit cards  
  - `Age`, `Education`, `Region`  
  - `Student`, `Own`, `Married` (categorical indicators)

---

## Objectives & Research Questions

### **Main objective**
Identify which customer attributes are significantly associated with credit card balance and evaluate predictive performance of different regression models.

### **Guiding questions**
- Which variables best explain variation in credit card balances?  
- Does log-transforming income improve model behavior?  
- Which model predicts unseen customer balances most accurately:  
  **OLS**, **Ridge**, or **LASSO**?

---

## Methods & Workflow

### **1. Exploratory Visualization**
- Scatterplots of Balance vs. Income  
- Histograms of Income and log(Income)  
- Comparisons of balances for **students vs. non-students**  
- Detected skewness and outliers → motivated use of log transformations

### **2. Data Processing**
- Removed observations with `Balance = 0` to focus on active credit users  
- Created `Income_log` variable  
- Converted categorical variables to factors

### **3. Regression Analysis**
- Estimated multiple linear regression models  
- Initial model: all predictors  
- Final model: only statistically significant variables (based on p-values)

### **4. Predictive Modeling**
Compared three models:

| Model | Method | Purpose |  
|-------|--------|----------|  
| **OLS** | Standard regression | Baseline predictor |  
| **Ridge** | L2 regularization | Stabilize coefficients |  
| **LASSO** | L1 regularization | Variable selection |  

Evaluation metric:
- **Out-of-sample rMSPE (root Mean Squared Percentage Error)**

---

## Key Results

### **Significant predictors of Balance**
- **Income_log** (negative coefficient)  
- **Limit** (positive)  
- **Cards** (positive)  
- **Age** (negative)  
- **Student** (positive and large effect)

### **Interpretation**
- Higher income → lower credit card balances  
- Students hold significantly higher balances  
- More credit cards → higher balances  
- Older customers → lower balances  

### **Model Performance**
- **Final OLS model:** explains ~91.7% of variation  
- **LASSO:** lowest rMSPE (~129.33)  
- Differences across methods small → OLS already performs well  

---

## Conclusions

- Demographic and financial characteristics strongly correlate with credit card balance.  
- Income, limit, number of cards, age, and student status are the most important drivers.  
- LASSO offers slightly better predictive performance, but practical improvements are minor.  
- Results can inform credit risk assessment and customer segmentation strategies.

---
