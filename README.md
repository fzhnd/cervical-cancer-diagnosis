# Cervical Cancer Diagnosis (HPV16 & Cyclin D1)

## Overview
This repository presents a machine learning–based analysis for cervical cancer–related data using HPV type 16 oncogene information (E6/E7) and Cyclin D1 expression. The project is implemented in a Jupyter Notebook and focuses on tabular data classification.

The primary objective of the implemented models is to classify Cyclin D1 Immunoreactive Score (IRS) into Weak and Strong categories using supervised learning methods.

## Dataset
The dataset used in this project is obtained from a public Figshare repository:

**Title:** Data of Cervical Cancer HPV 16 oncogen E6 or E7 with Cyclin D1 expression

**DOI:** [https://doi.org/10.6084/m9.figshare.21786644](https://doi.org/10.6084/m9.figshare.21786644)

### Dataset Characteristics
* Total samples: **31**
* Features include:
  * HPV-positive percentage (%)
  * HPV percentage category
  * Oncogene status (Mutation / Wild)
  * Oncogene type (E6 / E7 / None)
* Target variable:
  * Cyclin D1 IRS (Weak / Strong)

The original spreadsheet data were converted into CSV format for processing in Python.

## Workflow
### 1. Data Loading and Inspection
* Dataset is loaded using **Pandas**
* Basic inspection is performed to verify:
  * data shape
  * feature types
  * absence of missing values

### 2. Data Preprocessing
The notebook applies standard preprocessing steps for tabular biomedical data:
* Removal of non-informative identifier columns
* Encoding of categorical variables into numeric form
* Scaling of numerical features to ensure comparable ranges
* Binary encoding of the target variable:
  * Weak → 0
  * Strong → 1

### 3. Model Implementation
The following **supervised machine learning models** are implemented and evaluated:
* **Logistic Regression**
* **Support Vector Classifier (SVC)**
* **Random Forest Classifier**

All models are applied to the same preprocessed feature set to ensure fair comparison.

### 4. Training and Evaluation
* Data are split into training and testing sets
* Model performance is evaluated using:
  * Accuracy
  * Precision
  * Recall
  * F1-score
  * Confusion Matrix

The evaluation focuses on the model’s ability to correctly identify **Strong Cyclin D1 expression**, which is clinically relevant for risk assessment.

## Results
The implemented models demonstrate **high classification performance** on the available dataset. While results are promising, they should be interpreted cautiously due to the **small sample size** and **single-source data**.

## Repository Structure

```text
cervical-cancer-diagnosis/
│
├── cervical_cancer_diagnosis.ipynb
├── Data-of-Cervical-Cancer-HPV-16-oncogen-E6-or-E7-with-Cyclin-D1-expression.csv
├── README.md
```

## Requirements
* Python 3.x
* NumPy
* Pandas
* Scikit-learn
* Matplotlib / Seaborn

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/fzhnd/cervical-cancer-diagnosis.git
   ```
2. Install dependencies:
   ```bash
   pip install numpy pandas scikit-learn matplotlib seaborn
   ```
3. Run the notebook:
   ```bash
   jupyter notebook cervical_cancer_diagnosis.ipynb
   ```

## Limitations
* Very small dataset (31 samples)
* Results are exploratory and not clinically deployable
* No external validation dataset is used
