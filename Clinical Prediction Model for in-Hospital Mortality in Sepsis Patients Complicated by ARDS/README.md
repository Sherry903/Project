#  Clinical Prediction of In-Hospital Mortality in Sepsis Patients with ARDS

This project develops a machine learning-based clinical prediction model to estimate in-hospital mortality among patients suffering from sepsis complicated by Acute Respiratory Distress Syndrome (ARDS), using data from the MIMIC-IV database.

---

##  Background

Sepsis and ARDS frequently co-occur in ICU patients, resulting in significantly higher mortality. However, existing clinical scoring systems lack specificity for this high-risk group. This project addresses the gap by building and evaluating predictive models specifically tailored to sepsis-induced ARDS.

---

##  Data Source

- **Database**: [MIMIC-IV v3.1](https://physionet.org/content/mimiciv/3.1/)
- **Population**: 4,379 adult ICU patients with both Sepsis-3 and ARDS
- **Target**: In-hospital mortality (binary classification)

---

##  Methodology

###  Feature Engineering
- 60 features including demographics, vital signs, lab values, comorbidities, severity scores, and treatment variables
- Final model trained on **21 clinically significant features** selected via univariate and multivariate logistic regression with backward elimination

###  Preprocessing
- Median/mode imputation for missing values  
- Log transformation for outliers  
- One-hot encoding for categorical data  
- Feature scaling  
- Class imbalance handled using **SMOTE**

---

##  Models Implemented

| Model               | Accuracy | ROC-AUC | Sensitivity | Specificity |
|--------------------|----------|---------|-------------|-------------|
| Random Forest    | 82.88%   | **0.8682** | 60.00%      | 89.21%      |
| XGBoost            | 83.56%   | 0.8660  | 63.16%      | 89.94%      |
| LightGBM           | 83.10%   | 0.8634  | 68.42%      | 87.32%      |
| SVM                | 81.61%   | 0.8608  | **74.74%**  | 85.19%      |
| Logistic Regression| 80.46%   | 0.8574  | 73.68%      | 84.14%      |
| KNN                | 79.88%   | 0.8387  | 68.42%      | 82.99%      |

---

##  Model Interpretability

- **Feature Importance** via Random Forest
- **SHAP (SHapley Additive exPlanations)** used to interpret model predictions  
  - Top predictors: systolic arterial blood pressure (protective), PEEP (risk), heart rate, glucose, creatinine
  - Severity scores (APACHE II, SOFA) and comorbidities (CHF, diabetes, renal disease) were also influential

---

##  Limitations

- Single-center dataset (BIDMC only)
- Model generalizability requires external validation
- Feature set may omit unrecorded but clinically relevant factors

---

##  Future Work

- External validation on multi-center data  
- Deployment as a real-time ICU clinical tool  
- Integration with EMRs for early-warning systems  
- Expansion to include longitudinal and post-discharge outcomes



