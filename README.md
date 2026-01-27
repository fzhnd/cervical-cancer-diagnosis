# Cervical Cancer Diagnosis: Cyclin D1 Expression Prediction

## Project Overview
This project aims to classify the expression of **Cyclin D1** (Immunoreactive Score/IRS) in cervical cancer samples based on HPV infection characteristics and oncogene mutations.

Given the **small size of the dataset (n=31)**, this project focuses on robust evaluation strategies using **Stratified K-Fold Cross-Validation** to compare the performance of classic Machine Learning algorithms against Deep Learning architectures.

## Dataset
The dataset used in this project is obtained from a public Figshare repository:
* **Title:** Data of Cervical Cancer HPV 16 oncogen E6 or E7 with Cyclin D1 expression
* **DOI:** [10.6084/m9.figshare.21786644](https://doi.org/10.6084/m9.figshare.21786644)
* **Sample Size:** 31 patients
### Features:
1. **HPV positive (%):** Percentage of HPV infection.
2. **Category based on percentage:** Ordinal category (-, +, ++).
3. **Mutation/wild oncogene:** Status of oncogene mutation.
4. **Oncogene mutation:** Specific type (E6, E7, or None).
### Target:
* **Immunoreactive Score (IRS) of Cyclin D1:**
* `0`: Weak Expression
* `1`: Strong Expression

## Methodology
1. **Preprocessing:**
* Label Encoding for ordinal and nominal categorical features.
* StandardScaler for feature normalization.
2. **Validation Strategy:**
* **Stratified K-Fold CV (k=5):** Ensures class balance in training/validation splits.
* **Holdout Set (10%):** A separate set for final unseen data evaluation.
3. **Handling Imbalance:**
* Applied `class_weight='balanced'` for Deep Learning models.
* Stratified sampling for ML models.

## Evaluation Results
### 1. Machine Learning Models
Aggregated results from 5-Fold Cross-Validation.
| Model | Accuracy (Mean) | Precision | Recall (Sensitivity) | F1 Score | AUC-ROC |
| --- | --- | --- | --- | --- | --- |
| **Logistic Regression** | **96.00%** | 93.33% | 100.00% | 96.00% | 96.67% |
| **SVC** | **96.00%** | 93.33% | 100.00% | 96.00% | 96.67% |
| **Random Forest** | 92.00% | 93.33% | 90.00% | 89.33% | 91.67% |
### 2. Deep Learning Models (ANN)
Sequential Neural Networks with varying architectures.
| Architecture | Accuracy (Mean) | Precision | Recall (Sensitivity) | F1 Score | AUC-ROC |
| --- | --- | --- | --- | --- | --- |
| **Model 1** (Small) | 92.67% | 86.67% | 100.00% | 92.00% | 94.17% |
| **Model 2** (Medium) | **96.00%** | 93.33% | 100.00% | 96.00% | 96.67% |
| **Config 3** (Tanh/Adagrad) | 89.33% | 80.00% | 100.00% | 88.00% | 91.67% |
### Holdout Performance
All top-performing models achieved **100% Accuracy** on the 10% holdout set, correctly classifying all unseen samples.

## Key Findings
* **High Separability:** The high accuracy across simple models (Logistic Regression) suggests a strong linear correlation between `HPV positive (%)` and `Cyclin D1 Score`.
* **Model Selection:** For a small dataset (n=31), complex Deep Learning models are prone to overfitting. **Logistic Regression** or **SVC** are the recommended choices as they offer high performance with lower computational cost and better interpretability.

## Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/fzhnd/cervical-cancer-diagnosis.git
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib scikit-learn tensorflow
   ```
3. Run the notebook:
   ```bash
   jupyter notebook cervical_cancer_diagnosis.ipynb
   ```
