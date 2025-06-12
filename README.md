# 🏡 House Prices Prediction - Kaggle Competition

This project addresses the **"House Prices - Advanced Regression Techniques"** competition on Kaggle. The objective is to predict the final sale price of residential properties in **Ames, Iowa**, using a dataset with **79 explanatory variables** that describe various aspects of the homes.

The notebook walks through a **complete machine learning pipeline**, including:
- Data cleaning and imputation
- Feature engineering and selection
- Model training, comparison, and evaluation
- Generating a competition-ready submission file

---

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Methodology](#methodology)
  - [1. Data Cleaning and Imputation](#1-data-cleaning-and-imputation)
  - [2. Feature Selection](#2-feature-selection)
  - [3. Feature Engineering](#3-feature-engineering)
  - [4. Model Training and Evaluation](#4-model-training-and-evaluation)
- [📊 Results](#results)
- [🚀 How to Use](#how-to-use)
- [🧩 Dependencies](#dependencies)

---

## 📘 Project Overview

This regression problem involves predicting **SalePrice** (a continuous target variable). The dataset presents challenges such as:
- High dimensionality (79 features)
- Missing values
- A mix of numerical and categorical data

The notebook systematically addresses these issues to build a reliable model that generalizes well.

---

## 🧪 Methodology

### 1. Data Cleaning and Imputation

- **Dataset Loading:** `train.csv` and `test.csv` are loaded using `pandas`.
- **Dropping Columns:** High-missing-value columns (`Alley`, `PoolQC`, `Fence`, `MiscFeature`) are removed.
- **Numerical Imputation:** Missing values (e.g., `LotFrontage`) are filled with **mean**.
- **Categorical Imputation:** Missing values (e.g., `GarageType`) are filled with **mode**.

---

### 2. Feature Selection

- The `Id` column is dropped.
- Correlation analysis is used to remove features with low correlation (|r| < 0.2) to `SalePrice`.

---

### 3. Feature Engineering

- **One-Hot Encoding:** All categorical variables are converted using `pandas.get_dummies`.
- **Concatenated Encoding:** Train and test sets are encoded together for consistency.
- **Feature Scaling:** `StandardScaler` is applied to numerical features to standardize them.

---

### 4. Model Training and Evaluation

Several models were trained and evaluated using **Root Mean Squared Error (RMSE)**:

#### 📐 Linear Models:
- Linear Regression
- Ridge Regression (L2)
- Lasso Regression (L1)
- Elastic Net (L1 + L2)

#### 🌲 Ensemble Models:
- Random Forest Regressor
- XGBoost Regressor
- LightGBM Regressor

#### 🧠 Other Models:
- Support Vector Regressor (SVR)

Cross-validation was used to ensure robustness of the selected model.

---

## 📊 Results

| Model                  | Training RMSE (approx.) |
|------------------------|-------------------------|
| Linear Regression      | ~21,752                 |
| Ridge Regression       | ~21,697                 |
| Lasso Regression       | ~21,697                 |
| Elastic Net            | ~21,742                 |
| Random Forest          | ~10,849                 |
| XGBoost                | ~139                    |
| LightGBM               | ~140                    |
| SVR                    | ~81,378                 |

✅ **Final Model Selected:** `Random Forest Regressor`  
Despite gradient boosting models having extremely low training error, the **Random Forest** offered a better **cross-validation RMSE (~30,053)**, indicating better generalization performance.

---

## 🚀 How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/house-prices-prediction.git
   cd house-prices-prediction
