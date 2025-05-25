# Predicting Heart Attack Fatality Rates Using Neural Networks

This project aims to predict 28-day in-hospital mortality for ICU patients with heart failure and hypertension using machine learning techniques applied to the MIMIC-IV v2.2 dataset.

##  Project Overview

Heart failure and hypertension significantly contribute to ICU mortality. Traditional risk scoring systems often fail to capture complex clinical patterns. This project builds predictive models—including neural networks and ensemble methods—to improve mortality prediction and support clinical decision-making.

##  Models Implemented

We compared the performance of multiple machine learning models:
- **Random Forest** (Best Performance: ROC-AUC 0.8863, F1-score 0.88)
- Gradient Boosting
- XGBoost
- Logistic Regression
- Linear Regression
- Gaussian Naïve Bayes
- Neural Network (baseline from original study)

##  Key Features Used

- **Vital Signs**: Heart rate, blood pressure, SpO2, respiratory rate, temperature  
- **Lab Results**: Lactate, serum creatinine, sodium, potassium, WBC, etc.  
- **Treatments**: Diuretics, IV fluids, vasopressors  
- **Demographics**: Age, gender, ethnicity  
- **ICU Data**: Length of stay, comorbidities (diabetes, CKD, COPD, etc.)

##  Methodology

- **Data Source**: MIMIC-IV v2.2 (via Google BigQuery)
- **Preprocessing**: Data cleaning, imputation, normalization
- **Feature Selection**: Recursive Feature Elimination (RFE)
- **Model Tuning**: Grid Search & Bayesian Optimization
- **Evaluation Metrics**: Accuracy, ROC-AUC, F1-score, Precision, Recall
- **Interpretability**: SHAP for feature importance analysis

##  Results Summary

| Model              | Accuracy | ROC-AUC | F1-score |
|-------------------|----------|---------|----------|
| Random Forest      | 0.89     | 0.8863  | 0.88     |
| Gradient Boosting  | 0.90     | 0.8760  | 0.89     |
| XGBoost Classifier | 0.90     | 0.8791  | 0.89     |
| Logistic Regression| 0.75     | 0.7963  | 0.78     |
| Neural Network     | 0.84     | 0.7640  | —        |
| Gaussian NB        | 0.16     | 0.7362  | 0.09     |

##  Key Insights

- Ensemble models outperform the baseline neural network.
- Important predictors include **arterial O₂ pressure**, **WBC count**, and **ICU length of stay**.
- SHAP values revealed that **lactate** and **sodium** levels significantly influence prediction outcomes.

##  Limitations

- Data comes from a single healthcare system (MIMIC-IV), which may limit generalizability.
- Some predictors like ICU length of stay may be subject to circular reasoning.
- Complexity of ensemble models may reduce clinical interpretability.

##  Future Work

- External validation on other datasets
- Integration into real-time ICU dashboards
- Inclusion of socioeconomic/lifestyle variables
- Development of clinician-friendly tools for interpretability

