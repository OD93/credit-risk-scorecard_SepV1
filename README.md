# Credit Risk Probability of Default (PD) Scorecard Pipeline

## Overview
This repository contains an end-to-end credit risk analytics and modeling pipeline developed in Python. The project focuses on building a traditional credit risk scorecard to predict customer default risk, incorporating rigorous data quality checks, stratified data partitioning, and feature binning for Weight of Evidence (WoE) and Information Value (IV) transformations.

## Key Pipeline Components

### 1. Dataset & Target Analysis
* **Portfolio Scope**: Processes a structured credit dataset containing 100 customer records and 34 variables[cite: 1].
* **Target Distribution**: Analyzes the binary target variable (`Default_y`), establishing an overall portfolio default rate of $30.0\%$ ($70\%$ non-defaults vs. $30\%$ defaults)[cite: 1].
* **Risk Segmentation**: Evaluates default distributions across demographic and behavioral factors, including education level, marital status, and historical payment behavior[cite: 1].

### 2. Data Quality & Preprocessing
* **Integrity Audits**: Validates dataset cleanliness, confirming zero duplicate rows or customer ID collisions[cite: 1].
* **Missing Value Imputation**: Systematically handles missing categorical attributes by mapping them to dedicated distinct categories to preserve sample size and information value[cite: 1].

### 3. Stratified Data Partitioning
* **Train-Test Split**: Implements a stratified 70/30 split (70 training samples, 30 test samples) on the target variable[cite: 1].
* **Risk Preservation**: Ensures identical target proportions are maintained across subsets ($21$ default instances in training and $9$ in testing) to prevent portfolio risk distortion[cite: 1].

### 4. Feature Engineering & Scorecard Foundations
* **Continuous Feature Binning**: Groups continuous numerical predictors (such as Age, Income, Employment Years, and Loan Amount) into distribution-based intervals[cite: 1].
* **Scorecard Preparation**: Prepares binned attributes for downstream Weight of Evidence (WoE) transformation and Information Value (IV) feature selection.

## Tech Stack
* **Language**: Python
* **Libraries**: Pandas, NumPy, Scikit-Learn, Statsmodels
