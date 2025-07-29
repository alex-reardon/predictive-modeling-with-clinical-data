# 🔬 Predicting PSA Levels in Prostate Cancer Using Linear Regression

## 📘 Overview

This project demonstrates a **multiple linear regression analysis** to predict **Prostate-Specific Antigen (PSA)** levels in men with prostate cancer. PSA is a key biomarker used in diagnosis and monitoring of prostate cancer. The dataset is mock clinical data designed to resemble typical findings in the literature.

The analysis explores how PSA is associated with tumor burden, demographic variables, and diagnostic features.

---

## 🎯 Objective

To model and interpret how clinical and demographic features contribute to PSA levels using linear regression, and assess the predictive utility of these features.

---

---

## 🧪 Data Description

**Outcome Variable:**
- `psa`: Prostate-Specific Antigen level (ng/mL)

**Predictor Variables:**
- `age`: Age in years  
- `gleason`: Gleason score (tumor aggressiveness)  
- `prostate_volume`: Prostate size (mL)  
- `positive_cores`: Number of positive biopsy cores  
- `biopsy_cancer`: Presence of cancer in biopsy (0/1)  
- `family_history`: Family history of prostate cancer (0/1)  
- `bmi`: Body Mass Index  
- `psad`: PSA Density (PSA / volume)  
- `race_black`, `race_white`, `race_hispanic`: Race dummies  
- `clinical_stage_metastatic`: 1 if metastatic, 0 if localized  

---

## 📊 Exploratory Data Analysis (EDA)

- **Distribution of PSA**: Right-skewed but approximately normal.  
- **Correlation Heatmap**: Strong correlations between PSA and PSAD, Gleason score, biopsy results, and tumor burden.  
- **Scatter and Box Plots**: Visualized linear relationships and group differences across predictors.  

---

## 📈 Linear Regression Results

**Model Performance**

| Metric      | Value |
|-------------|-------|
| R² (Sklearn)        | 0.76  |
| R² (Statsmodels)    | 0.797 |
| Adj. R²             | 0.789 |
| MSE                 | 5.37  |

**Top Predictors**

| Variable                    | Coefficient | p-value |
|-----------------------------|-------------|---------|
| PSA Density (`psad`)        | 23.79       | <0.001  |
| Positive Biopsy Cores       | 0.70        | <0.001  |
| Gleason Score               | 1.10        | <0.001  |
| Clinical Stage (Metastatic) | 1.86        | <0.001  |
| Biopsy Cancer (Yes)         | 2.33        | <0.001  |
| Age                         | 0.30        | <0.001  |
| Prostate Volume             | -0.095      | <0.001  |

---

## ⚠️ Multicollinearity Warning

Several variables had **high VIF values**, suggesting **multicollinearity**:

| Variable       | VIF  |
|----------------|------|
| Age            | 65.9 |
| Gleason Score  | 39.2 |
| BMI            | 38.0 |
| Prostate Volume | 22.1 |
| PSAD           | 10.6 |

**Implications**:
- Inflated standard errors
- Reduced interpretability of coefficients

**Recommendations**:
- Remove or combine correlated variables (e.g., PSAD and prostate volume)
- Use regularized regression (e.g., Lasso, Ridge)

---

## 📉 Residual Diagnostics

- **Residuals**: Symmetrical and centered around zero  
- **Durbin-Watson**: ≈ 1.96 — no autocorrelation  
- **Normality & Homoscedasticity**: Assumptions appear reasonable  
- **Outliers**: No major violations observed  

---

## ✅ Conclusion

This regression model provides a strong predictive framework for PSA levels based on clinical and demographic data. Key findings include:

- PSA Density, Gleason Score, tumor burden, and metastatic stage are strong predictors
- Race and age remain significant even after adjusting for clinical variables
- Multicollinearity should be addressed in future models

---

## 📎 Future Improvements

- Address multicollinearity through feature selection or dimensionality reduction
- Explore Ridge and Lasso regression
- Test external generalization with real-world data

---

## 🛠️ Requirements

- Python 3.8+
- pandas  
- seaborn  
- matplotlib  
- statsmodels  
- scikit-learn  

```bash
pip install pandas seaborn matplotlib statsmodels scikit-learn
