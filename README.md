# Child-Mind-Institute

This repository contains the code and documentation for a machine learning project aimed at predicting the severity of Problematic Internet Use (PIU) in children using physical activity data collected via accelerometers.

## 📘 Project Overview

**Objective:**  
To determine if temporal patterns in physical activity, captured via accelerometer time series data, can predict the severity of problematic internet use in children and adolescents.

**Key Research Question:**  
Can time-series data from wearable devices be used as reliable, objective indicators of internet use severity, in contrast to self-reported surveys?

---

## 🗃️ Dataset

**Source:** Child Mind Institute  
**Data Includes:**
- Accelerometer time series (ENMO, anglez, light, etc.)
- Demographics (age, sex, BMI)
- Severity Impairment Index (0 = None, 3 = Severe)
- PCIAT (Problematic Computer/Internet Activity Test) scores

**Preprocessing Steps:**
- Handling missing values (model-based imputation)
- Filtering non-wear periods
- Feature engineering (activity bouts, day/night segmentation)
- Dimensionality reduction using PCA
- Normalization of numeric features

---

## ⚙️ Methodology

### 🔍 Feature Extraction
Time-based statistical summaries extracted for:
- ENMO, anglez, light, battery_voltage
- Day vs. night activity patterns
- Movement intensity and variability

### 📈 Models Used
- LightGBM Regressor
- XGBoost Regressor (two variants)
- CatBoost Regressor
- Extra Trees Regressor
- Ensemble models (weighted and voting)

### 📊 Evaluation Metric
- **Quadratic Weighted Kappa (QWK)** for ordinal classification performance

---

## 🧪 Results

| Model             | QWK Score |
|------------------|-----------|
| LightGBM         | 0.4628    |
| XGBoost          | 0.4699    |
| CatBoost         | 0.4487    |
| Extra Trees      | 0.4483    |
| **Ensemble**     | **0.4727** |

- Best performance achieved using an ensemble model
- Prediction accuracy strongest for “None” and “Mild” severity cases
- Top features: Depression score, self-reported internet usage, physical attributes, PCA components from time series data

---

## 📌 Limitations
- Class imbalance, especially for the "Severe" category
- High correlation among models limits ensemble diversity
- QWK performance sensitive to threshold tuning
- Moderate missing data in several features

---

## 🔮 Future Work
- Explore deep learning models (LSTM, Transformers)
- Incorporate additional biosensor data (e.g., heart rate, sleep)
- Improve class balancing techniques
- Study causal relationships between physical activity and internet use

---
