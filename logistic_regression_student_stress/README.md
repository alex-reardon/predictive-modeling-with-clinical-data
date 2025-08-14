# Academic Stress Prediction

This project analyzes survey data on academic stress among students and builds predictive models to estimate the **Academic Stress Index** based on various personal, environmental, and behavioral factors.

## Features

**Categorical Variables:**
- `academic_stage` – student’s academic level  
- `study_environment` – type of study environment  
- `coping_strategy` – strategies used to cope with stress  
- `bad_habits` – habits like smoking or drinking  

**Numerical Variables:**
- `peer_pressure` – pressure from peers  
- `home_pressure` – academic pressure from home  
- `academic_competition` – perceived competition in academics  
- `stress_index` – target variable, self-reported stress level (1–5)  

---

## Workflow

1. **Data Cleaning & Preprocessing**  
   - Standardize column names  
   - Consolidate categories for simplicity  
   - Handle missing values and duplicates  

2. **Exploratory Data Analysis (EDA)**  
   - Visualize distributions of categorical variables (pie charts)  
   - Visualize numerical variables (histograms with KDE)  
   - Correlation analysis (Spearman correlation heatmap)  

3. **Modeling**  

Two models are built and compared:  

- **Ordinal Ridge Regression** (`mord.OrdinalRidge`)  
  - Suitable for ordered outcomes  
  - Hyperparameter tuning with cross-validation for `alpha`  
  - Evaluated using exact-match accuracy and ±1 category accuracy  

- **Multinomial Logistic Regression** (`sklearn.LogisticRegression`)  
  - General multi-class classifier without assuming order  
  - Uses preprocessing pipeline for numeric scaling and categorical one-hot encoding  
  - Evaluated using exact-match accuracy and ±1 category accuracy  

4. **Feature Importance**  
   - For both models, features are ranked by the absolute value of their coefficients.  

---

## Metrics

- **Exact-Match Accuracy:** Proportion of predictions exactly equal to the true stress index.  
- **±1 Category Accuracy:** Predictions within ±1 stress level of the true value are considered correct.

---

## Visualization Examples

- Pie charts of categorical variables  
- Histograms with KDE for numeric variables  
- Spearman correlation heatmap  

---

## Requirements

```r
# Python packages used
numpy
pandas
matplotlib
seaborn
scikit-learn
mord
