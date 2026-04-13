# 🚴 Bike Sharing Demand Forecasting

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![License](https://img.shields.io/badge/License-Academic-green.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

**M.Sc. Data Science Dissertation Project**  
**University of Hertfordshire**  
**Author:** Sai Ram Charan

*Predicting hourly bike rental demand using Time Series and Machine Learning*

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Research Question](#-research-question)
- [Models Compared](#-models-compared)
- [Results](#-results)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [Dataset](#-dataset)
- [Methodology](#-methodology)
- [References](#-references)
- [Author](#-author)

---

## 🎯 Overview

Bike sharing systems face persistent **demand-supply imbalances** — stations run empty during rush hours while bikes accumulate unused elsewhere. This project develops and compares forecasting models to predict **hourly bike rental demand**, enabling proactive fleet management.

### Key Contributions

✅ Systematic 3-model comparison (SARIMA vs SARIMAX vs XGBoost)  
✅ Novel feature engineering (cyclical encoding, weather interactions)  
✅ ACF/PACF-informed tuning (faster than auto_arima)  
✅ Comprehensive evaluation (MAE, RMSE, MAPE)

---

## ❓ Research Question

> *Can historical bike usage and weather data be used to accurately forecast short-term (hourly) bike rental demand using time-series and machine learning models?*

**Answer: Yes!** XGBoost achieves 0.32% MAPE, and SARIMAX improves over SARIMA by 24%.

---

## 🤖 Models Compared

| Model | Type | Description |
|:------|:-----|:------------|
| **SARIMA** | Univariate | Uses only historical demand with seasonal differencing |
| **SARIMAX** | + External Features | Adds weather & calendar as exogenous variables |
| **XGBoost** | Machine Learning | Gradient-boosted trees with lag features |

---

## 📊 Results

### Performance Comparison (Test Set)

| Model | MAE ↓ | RMSE ↓ | MAPE ↓ |
|:------|------:|-------:|-------:|
| SARIMA | 281.4 | 343.6 | 15.3% |
| SARIMAX | 214.1 | 264.1 | 10.5% |
| **XGBoost** | **26.4** | **41.7** | **0.32%** |

### Key Findings

| Finding | Insight |
|:--------|:--------|
| 📈 **SARIMAX +24%** | External features significantly improve forecasts |
| 🏆 **XGBoost +88%** | Non-linear patterns captured via lag features |
| 🔧 **Feature Engineering** | Cyclical encoding & temp² critical for linear models |
| ⚙️ **Tuning** | Marginal gains — good baselines already chosen |

---

## 📁 Project Structure

```
Bike_Sharing_Forecasting_Project/
│
├── 📄 README.md                    ← You are here
├── 📄 requirements.txt             ← Python dependencies
│
├── 📂 code/
│   ├── 📓 bike_sharing_*.ipynb     ← Main analysis notebook
│   └── 🐍 generate_project_report.py  ← Report generator
│
├── 📂 report/
│   └── 📝 Bike_Sharing_Project_Report.docx  ← Full academic report
│
├── 📂 presentation/
│   └── 🐍 bike_sharing_presentation_v4.py  ← PPT generator
│
└── 📂 graphs/
    └── 🖼️ *.png                    ← Exported visualizations
```

---

## ⚙️ Installation

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook

### Quick Setup

```bash
# 1. Install dependencies
pip install -r requirements.txt

# Or install manually:
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn xgboost python-pptx python-docx
```

---

## 🚀 Usage

### 1️⃣ Run Main Analysis

```bash
cd code
jupyter notebook bike_sharing_withFEnLossFunction_viva_ordered_final.ipynb
```

Execute all cells to:
- Download UCI dataset automatically
- Run EDA and feature engineering
- Train all 3 models
- Generate comparison visualizations

### 2️⃣ Generate Project Report

```bash
cd code
python generate_project_report.py
```

Opens Word document → Save as PDF for submission.

### 3️⃣ Generate Presentation

```bash
cd presentation
python bike_sharing_presentation_v4.py
```

Creates 16-slide academic PowerPoint.

---

## 📊 Dataset

| Property | Value |
|:---------|:------|
| **Source** | [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset) |
| **Location** | Capital Bikeshare, Washington D.C. |
| **Period** | January 2011 – December 2012 |
| **Records** | 17,379 hourly observations |
| **Target** | `cnt` (total hourly bike rentals) |

### Features

| Category | Features |
|:---------|:---------|
| 🌡️ Weather | `temp`, `hum`, `windspeed` |
| 📅 Calendar | `workingday`, `holiday`, `weekday` |
| 🔧 Engineered | `hr_sin`, `hr_cos`, `rush_hour`, `temp_sq`, `temp_hum`, `is_weekend` |
| ⏰ Lag | `lag_1h`, `lag_24h`, `lag_48h`, `lag_168h`, `rolling_24h_mean` |

---

## 🔬 Methodology

### 1. Preprocessing
- Constructed hourly timestamp index
- 90/10 chronological train-test split
- No data leakage

### 2. Feature Engineering
- **Cyclical encoding**: `sin(2πh/24)`, `cos(2πh/24)` for hour continuity
- **Non-linear terms**: `temp²` for inverted-U pattern
- **Interactions**: `temp × humidity` for perceived discomfort
- **Lag features**: Autoregressive memory for ML models

### 3. Model Configurations

```
SARIMA:  (1,1,1) × (1,1,1,24)  — tuned to (2,1,1) × (1,0,0,24)
SARIMAX: (1,1,1) × (1,1,1,24) + 11 exog features
XGBoost: n_estimators=1000, max_depth=6, early_stopping=50
```

---

## 📚 References

1. **Fanaee-T & Gama (2014)** — UCI Bike Sharing Dataset paper
2. **Hyndman & Athanasopoulos (2021)** — *Forecasting: Principles and Practice*
3. **Chen et al. (2020)** — Hybrid SARIMA bike-sharing prediction
4. **Sathishkumar et al. (2020)** — ML benchmarks on bike sharing

---

## 👨‍💻 Author

**Sai Ram Charan**  
M.Sc. Data Science  
University of Hertfordshire  
April 2026

---

<div align="center">

⭐ *If this project helped you, consider giving it a star!* ⭐

</div>
