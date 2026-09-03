# malaria_symptoms_triage_helper_project

This repository contains a **Malaria Symptoms Triage Helper** — a machine learning project that builds a binary classification model to identify severe malaria cases based on clinical symptoms.

### **Project Overview**

**Purpose**: Develop a high-sensitivity triage system to distinguish between severe and non-severe malaria cases, prioritizing the detection of severe cases to minimize false negatives (missed diagnoses).

### **Key Components**

1. **Data Processing**
   - Loads the `ogunMedical.csv` dataset
   - Creates three engineered clinical features aligned with WHO malaria triage criteria:
     - `neurological_risk`: Combines convulsion and prostration
     - `severe_anemia_jaundice`: Combines anemia and jaundice
     - `high_fever_rigor`: Combines fever, rigor, and hyperpyrexia

2. **Model Development**
   - Trains three classification models:
     - Logistic Regression
     - Random Forest Classifier
     - Gradient Boosting Classifier
   - Uses stratified train/validation/test split (70/15/15)
   - Optimizes hyperparameters via GridSearchCV with **recall as the primary metric** (maximizing sensitivity to catch severe cases)

3. **Model Evaluation** (Test Set Results)
   - **Selected Model**: Logistic Regression (highest validation recall: 58.82%)
   - **Performance Metrics**:
     - Sensitivity (Recall): 72.22% — catches severe cases effectively
     - Specificity: 66.67%
     - Precision: 54.17%
     - F1-Score: 61.90%
     - ROC-AUC: 76.26%

4. **Outputs**
   - Confusion matrix and ROC curve visualizations
   - Feature importance analysis showing which clinical symptoms most influence predictions
   - Trained pipeline saved as `malaria_triage_binary_pipeline.pkl`

### **Clinical Rationale**

The model prioritizes **sensitivity over specificity** because missing a severe malaria case (false negative) has serious clinical consequences, while false positives can be managed through follow-up clinical evaluation. The engineered features combine related symptoms to capture WHO-defined severe malaria risk profiles more effectively than individual features alone.
