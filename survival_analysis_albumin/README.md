# Albumin Levels and Cancer Survival

This project investigates whether **albumin levels at diagnosis** are predictive of **1-year survival in cancer patients** using clinical and lab data.

## 📊 Objective

To determine if **albumin levels measured within 100 days of cancer diagnosis** can predict survival outcomes at 1 year using:

- **Kaplan-Meier survival curves**
- **Cox proportional hazards model**
- **Logistic regression**

---

## 📁 Data

Two CSV files:

- `onc.csv`: Oncologic patient data (diagnosis date, follow-up date, death status)
- `labs.csv`: Lab chemistry values (including albumin, with variable units)

### Key Columns
- `ID`: Patient identifier  
- `DaysFromAnchorDateToDiagnosisDate`: Diagnosis date (relative to anchor)  
- `DaysFromAnchorDateToFollowUp`: Last follow-up or death date  
- `Dead`: 1 = dead at follow-up, 0 = alive  
- `LabChemTestName`: e.g., albumin  
- `Value` and `Units`: Raw lab value and its unit  

---

## 🔧 Preprocessing Steps

- Filter `labs.csv` for entries where `LabChemTestName` == "albumin"
- Standardize units to **ng/mL**
- Join lab and oncologic data on `ID`
- Keep **only the albumin value closest (±100 days) to diagnosis**
- Drop subjects with missing or duplicate records

---

## 📈 Analyses

### 1. **Survival Analysis**
- Compute `Duration` as time from diagnosis to last follow-up
- Split albumin into `High` / `Low` groups based on the median
- Run:
  - **Kaplan-Meier survival curves**
  - **Log-rank test**
  - **Cox proportional hazards model**

### 2. **Logistic Regression**
- Create a binary label `Survived1year` (1 if alive ≥365 days after diagnosis)
- Regress `Survived1year` on `albumin_cat` (Low vs High)

---

## 📌 Results

- **Kaplan-Meier curves** show similar survival probabilities for both albumin groups.
- **Log-rank test** shows **no statistically significant difference** between groups.
- **Cox model**: Albumin level was **not a significant predictor** of survival time.
- **Logistic regression**: Being in the "Low albumin" group **decreased log-odds** of 1-year survival (coef = -0.51).

---

## ⚠️ Assumptions

- Only "albumin" entries (exact match) are analyzed
- Albumin values must be within ±100 days of diagnosis
- Alive/dead status inferred from `Dead` column
- Units conversion assumed consistent across all entries
- Median split effectively separates low vs. high albumin

---

## 🔍 Limitations

- Small dataset (**n = 51**)
- No demographic or clinical covariates (e.g., age, cancer stage)
- No test/train split due to limited sample size

---

## 🛠️ Technologies

- Python 3, Jupyter Notebook  
- Libraries: `pandas`, `matplotlib`, `seaborn`, `lifelines`, `scikit-learn`, `patsy`

---

## ✅ To Run

1. Install dependencies:
   ```bash
   pip install pandas matplotlib seaborn lifelines scikit-learn patsy
