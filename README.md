# Retail Sales Forecasting using Time Series & Machine Learning (Rossmann Store Sales)

This repository contains the **source code, figures, outputs, and experimental workflow** for a retail demand forecasting project using the **Rossmann Store Sales** dataset.

The project compares multiple forecasting approaches for **store-level sales prediction** and includes a separate **aggregate-level time series analysis** to study trend and seasonality.

---

## Project Overview

The objective of this project is to forecast **daily retail sales** using historical store sales data and store metadata from the Rossmann dataset.

The project evaluates:

- **Store-level forecasting** using machine learning models
- **Aggregate daily sales forecasting** using a statistical time series model
- Forecasting performance using business-relevant error metrics
- Feature importance and practical business insights for retail demand planning

This repository is intended as a practical portfolio project demonstrating **time series forecasting, feature engineering, machine learning, and business-oriented analytics**.

---

## Project Objective

The aim of this project is to compare how different forecasting approaches support:

- Daily store-level sales prediction
- Trend and seasonality analysis
- Demand pattern understanding
- Practical retail forecasting workflows
- Business-oriented model evaluation and interpretability

The goal is to assess both **forecast accuracy** and **practical usefulness** for retail operations such as inventory planning, staffing, and promotion analysis.

---

## Dataset

**Rossmann Store Sales Dataset**  
(Source: Kaggle competition dataset)

Files used in this project:

- `train.csv` → historical daily sales data
- `store.csv` → store-level metadata and attributes

Files not directly used in this implementation:

- `test.csv`
- `sample_submission.csv`

### Key Variables
- `Sales` → target variable
- `Store` → store identifier
- `Date` → transaction date
- `Promo` → promotion flag
- `StateHoliday` → holiday indicator
- `SchoolHoliday` → school holiday flag
- `StoreType` → store category
- `Assortment` → assortment type
- `CompetitionDistance` → competitor distance
- `Promo2` / `PromoInterval` → extended promotion information

---

## Models Used

The following forecasting approaches were implemented and compared:

### Store-Level Forecasting
- **Baseline (Naive Lag-Based Forecast)**
- **Random Forest Regressor**
- **XGBoost Regressor**

### Aggregate-Level Forecasting
- **Prophet**

---

## Forecasting Approaches

### Store-Level Forecasting
The main forecasting task was performed at the **store-day level**, where each observation represents sales for a specific store on a specific date.

This level was used for:

- Baseline forecasting
- Random Forest
- XGBoost

These models are directly comparable because they predict the **same target at the same granularity**.

---

### Aggregate-Level Forecasting
A separate time series analysis was conducted by aggregating sales across all stores by date.

This level was used for:

- Prophet forecasting

This approach supports:

- Trend analysis
- Seasonality analysis
- Portfolio-level demand understanding

> Note: Prophet results are presented separately because the target is **aggregate daily sales**, which is not directly comparable to the **store-level** machine learning forecasts.

---

## Feature Engineering

The project includes extensive feature engineering to improve forecasting performance.

### Time-Based Features
- Year
- Month
- Day
- Week of Year
- Is Weekend
- Is Month Start
- Is Month End

### Lag Features
- `lag_1`
- `lag_7`
- `lag_14`
- `lag_28`

### Rolling Features
- `rolling_mean_7`
- `rolling_mean_14`
- `rolling_mean_28`
- `rolling_std_7`

### Business Features
- Promotion indicators
- Promotion interval activity
- Competition-related variables
- Store metadata (type, assortment, etc.)

### Encoding
Categorical features were encoded using one-hot encoding:
- `StoreType`
- `Assortment`
- `StateHoliday`

---

## Evaluation Metrics

Forecasting performance was evaluated using the following metrics:

- **MAE (Mean Absolute Error)**
- **RMSE (Root Mean Squared Error)**
- **MAPE (Mean Absolute Percentage Error)**

These metrics were chosen to capture:

- average forecast deviation
- sensitivity to large errors
- percentage-based business interpretability

---

## Results

## Store-Level Forecasting Results

| Model | MAE | RMSE | MAPE |
|------|------:|------:|------:|
| Baseline | 1362.50 | 2096.21 | 19.97% |
| Random Forest | 769.84 | 1108.03 | 11.50% |
| XGBoost | 686.29 | 971.54 | 10.08% |

### Key Findings
- **XGBoost** achieved the best performance across all store-level metrics
- **Random Forest** significantly improved over the baseline
- The **Baseline model** served as a simple benchmark and demonstrated the value of feature-based machine learning forecasting

### Overall Result
- **XGBoost** reduced forecast error by nearly **50%** compared with the naive baseline

---

## Aggregate-Level Forecasting (Prophet)

Prophet was used separately to model **total daily sales aggregated across all stores**.

### Purpose of Prophet in this project
- Analyze overall sales trend
- Capture recurring weekly and yearly seasonality
- Explore portfolio-level forecasting behavior

### Important Note
Prophet was intentionally evaluated as a **separate forecasting task** because it models **aggregate daily sales**, while the machine learning models forecast **store-level daily sales**.

---

## Key Insights

The project produced several practical retail forecasting insights:

- Recent sales history (lag features) was highly predictive
- Rolling averages improved short-term demand estimation
- Promotions had a meaningful impact on forecast performance
- Calendar effects and seasonality played an important role
- Store-level metadata improved model performance by capturing structural differences between stores
- XGBoost was particularly effective for structured retail time series with engineered features

---

## Repository Structure

```bash
Rossmann-Sales-Forecasting/
│
├── data/                # Raw and processed datasets
├── notebooks/           # Main forecasting notebook(s)
├── outputs/             # Saved model results, predictions, and comparison tables
├── figures/             # Forecast plots, feature importance, and visual outputs
├── docs/                # Notes, methodology, and project documentation
├── README.md
└── requirements.txt

---

## Thank You
