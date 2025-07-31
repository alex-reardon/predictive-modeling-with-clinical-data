# 📊 PSA Prediction Using Linear Regression

This project builds and evaluates linear regression models to predict **Prostate-Specific Antigen (PSA)** levels using clinical and demographic variables. It compares a full model with all predictors to a reduced model that removes variables with high multicollinearity (VIF > 5).

---

## 🔍 Objective

To model PSA levels in prostate cancer patients using clinical and demographic data such as:

- Age
- Gleason Score
- Prostate Volume
- Biopsy Results
- Race
- Clinical Stage
- Family History
- BMI
- Number of Positive Cores

---

## 📁 Dataset

The dataset (`prostate_psa_low_vif_clean.csv`) contains preprocessed clinical records with no missing values. It includes numeric and binary categorical features.

---

## 🧪 Methodology

1. **Exploratory Data Analysis (EDA)**
   - Distribution of PSA
   - Correlation heatmap
   - Scatterplots (numeric vs PSA)
   - Boxplots (categorical vs PSA)

2. **Modeling**
   - Multiple Linear Regression using:
     - `sklearn` for predictive performance
     - `statsmodels` for statistical inference
   - Residual analysis
   - Multicollinearity assessment using VIF

3. **Reduced Model**
   - Variables with VIF < 5 used to improve statistical stability

---

## 📈 Model Results

### ✅ Full Model (All Predictors)

| Metric                  | Value  |
|------------------------|--------|
| R² (Scikit-learn)      | 0.46   |
| R² (Statsmodels)       | 0.49   |
| Adjusted R²            | 0.47   |
| Mean Squared Error     | 26.51  |
| F-statistic (p < .001) | ✅      |

#### 🧠 Top Predictors (Statsmodels)
- **Clinical Stage (Metastatic):** +2.64, p < 0.001 ✅  
- **Biopsy Cancer:** +1.99, p = 0.003 ✅  
- **Gleason Score:** +1.02, p < 0.001 ✅  
- **Positive Cores:** +0.85, p < 0.001 ✅  
- **Prostate Volume:** −0.11, p < 0.001 ✅  

#### ⚠️ High Multicollinearity (VIF > 10)
- BMI (59.7), Gleason (45.1), Age (35.9)

---

### ✅ Reduced Model (VIF < 5)

| Metric                  | Value  |
|------------------------|--------|
| R² (Scikit-learn)      | 0.24   |
| R² (Statsmodels)       | 0.28   |
| Adjusted R²            | 0.26   |
| Mean Squared Error     | 37.06  |
| F-statistic (p < .001) | ✅      |

#### 🧠 Top Predictors (Statsmodels)
- **Clinical Stage (Metastatic):** +3.30, p < 0.001 ✅  
- **Biopsy Cancer:** +2.04, p = 0.009 ✅  
- **Positive Cores:** +0.79, p < 0.001 ✅  
- **Prostate Volume:** −0.14, p < 0.001 ✅  

#### ✅ All VIFs < 5 — no multicollinearity concerns.

---

## 📉 Residual Diagnostics

- Residual plot shows mostly homoscedastic errors
- No major violations of linear regression assumptions

---

## 📌 Summary

- **Full model** provides higher predictive power but suffers from multicollinearity.
- **Reduced model** is more stable statistically but explains less variance.
- Future improvements:
  - Feature selection or dimensionality reduction
  - Regularized regression (Lasso, Ridge)
  - Tree-based models (e.g., Random Forest, XGBoost)
  - External validation on independent data

---

## 🛠️ Technologies

- Python 3
- Pandas, NumPy
- Scikit-learn
- Statsmodels
- Seaborn, Matplotlib

---

## 👩‍⚕️ Clinical Context

PSA is a biomarker used in the screening, diagnosis, and monitoring of prostate cancer. Understanding the clinical correlates of PSA can assist in better risk stratification and personalized care planning.
