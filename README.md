# Credit Risk Probability of Default (PD) Scorecard Pipeline

## Overview
This repository contains an end-to-end quantitative credit risk analytics and modeling pipeline developed in Python. The project implements a traditional credit risk scorecard to predict customer default risk, featuring rigorous data quality audits, stratified data partitioning, distribution-based feature binning, Weight of Evidence (WoE) transformations, and Logistic Regression modeling coupled with production-grade stability monitoring.

---

## Complete Pipeline Architecture

### 1. Dataset Overview & Characteristics
* **Dataset Shape**: Processes a structured credit portfolio containing 100 customer records and 34 variables[cite: 1].
* **Feature Composition**: Integrates numerical predictors (Age, Income, Loan Amount, Savings Balance, Employment Years) with categorical attributes (`Marital_Status`, `Education_Level`, `Pay_History`)[cite: 1].
* **Target Variable**: Evaluates the binary default indicator (`Default_y`), establishing an overall portfolio default rate of $30.0\%$[cite: 1].
* **Demographic Risk Segmentation**: Analyzes default risk variations across education levels (e.g., PhD holders at $41.67\%$, Postgraduates at $10.00\%$), marital statuses, and historical payment behavior[cite: 1].

### 2. Data Quality & Preprocessing
* **Integrity Audits**: Performs systematic checks confirming 0 duplicate rows and zero customer ID collisions[cite: 1].
* **Missing Value Imputation**: Systematically handles missing categorical attributes by mapping them to dedicated distinct categories to preserve sample integrity[cite: 1].

### 3. Stratified Data Partitioning
* **Train-Test Split**: Implements a stratified 70/30 split (70 training samples, 30 test samples) on the binary target variable[cite: 1].
* **Risk Preservation**: Guarantees identical target proportions across subsets ($21$ default instances in training and $9$ in testing) to maintain population risk representation[cite: 1].

### 4. Feature Binning & Scorecard Foundations
* **Continuous Feature Binning**: Groups continuous numerical attributes (Age, Income, Loan Amount) into distribution-based intervals[cite: 1].
* **Scorecard Preparation**: Prepares binned features for downstream Information Value (IV) calculation and monotonic transformation.

### 5. Weight of Evidence (WoE) & Information Value (IV)
* **WoE Transformation**: Converts categorical and binned numerical features into continuous Weight of Evidence values to linearize relationships with the target log-odds.
* **Feature Selection (IV)**: Computes Information Value to rank and select predictive features, discarding low-signal variables to prevent overfitting.

### 6. Logistic Regression & Probability of Default (PD) Modeling
* **Model Training**: Fits a generalized linear model (Logistic Regression) on WoE-transformed features to estimate the log-odds of default.
* **Probability Scaling**: Converts model outputs into calibrated Probability of Default (PD) estimates and maps them to standard credit score ranges (score scaling).

### 7. Model Validation & Stability Monitoring
* **Discriminatory Power**: Evaluates model ranking capability using **ROC-AUC** and the **Kolmogorov-Smirnov (KS)** statistic.
* **Gini Coefficient**: Computes the Gini index ($2 \times \text{AUC} - 1$) to quantify classification accuracy.
* **Population Stability Index (PSI)**: Monitors score distribution shifts between training and test (or production) datasets to detect model drift over time.

---

## Tech Stack & Libraries
* **Language**: Python 3.x
* **Data Manipulation & Wrangling**: Pandas, NumPy
* **Statistical Modeling & Machine Learning**: Scikit-Learn, Statsmodels
