#  DA5401 Assignment 6 — *Imputation via Regression*

###  Course
**DA5401 — Data Analytics Laboratory**  
Indian Institute of Technology Madras (IITM)  
Author: Omkar Chaudhari - NA22B059

---

##  Overview

This notebook implements and compares four different missing-data handling strategies on the **UCI Credit Card Default dataset**.  
The assignment explores how various imputation techniques affect the performance of a downstream **Logistic Regression** classifier under a **Missing At Random (MAR)** setting.

---

##  Objectives

1. Simulate **MAR missingness** in selected numeric variables.
2. Implement and evaluate the following imputation strategies:
   - **A)** Median Imputation (baseline)  
   - **B)** Linear Regression Imputation (single feature)  
   - **C)** Non-linear Regression Imputation (Random Forest)  
   - **D)** Listwise Deletion (rows with missing values dropped)
3. Compare downstream **classification performance** using:
   - Accuracy  
   - ROC–AUC  
   - Confusion Matrix & ROC Curve visualization
4. Discuss the statistical and practical implications of each strategy.

---

##  Dataset

- **Source:** [UCI Machine Learning Repository — Default of Credit Card Clients Dataset](https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients)
- **Records:** 30,000 clients  
- **Features:** 23 predictors + 1 target  
- **Target:** `default.payment.next.month` (binary; 1 = default)

Injected MAR missingness:
- Columns affected: `AGE`, `BILL_AMT1`, `PAY_AMT1`  
- Driver column: `PAY_0` (defines probability of missingness)

---

##  Implementation Summary

| **Strategy** | **Method** | **Rows Used** | **Accuracy** | **ROC–AUC** |
|---------------|-------------|----------------|---------------|--------------|
| A) Median | Train-median imputation | 30,000 | 0.679 | 0.707 |
| B) Linear | Linear regression impute `BILL_AMT1` | 30,000 | 0.679 | 0.707 |
| C) Non-linear | Random Forest impute `BILL_AMT1` | 30,000 | 0.679 | 0.707 |
| D) Listwise | Drop rows with missing values | 24,245 | 0.665 | 0.696 |

 Median imputation performed as well as the regression-based methods.  
 Listwise deletion degraded performance due to data loss (~19%).

---

##  Folder Structure

