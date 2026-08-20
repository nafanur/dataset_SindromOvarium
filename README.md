# Sindrom Ovarium (SO) Data Analysis and Predictive Modeling

## Project Overview
This project focuses on data preparation, exploratory analysis, statistical analysis, and predictive modeling using patient data related to Sindrom Ovarium (SO). The analysis was conducted as part of the **BNSP Data Analyst Competency Certification Project 2026**.
The project follows a complete data analysis workflow, from data understanding and cleaning to model development and evaluation.

---

## Research Question
Can patient characteristics, including demographic, anthropometric, clinical, hormonal, reproductive, lifestyle, and ovarian characteristics, be used to predict the status of Sindrom Ovarium (SO)?

### Target Variable

**SO (Y/N)**
* `0` = No SO
* `1` = SO

---

## Dataset

The dataset contains:

* **541 observations (patients)**
* **44 variables**
* **31 numerical variables**
* **13 categorical variables**

The variables cover several groups of patient characteristics:

* Demographic
* Anthropometric
* Clinical
* Hormonal and laboratory
* Reproductive
* Physical symptoms
* Lifestyle
* Ovarian characteristics

The original patient-level dataset is **not included in this repository** due to data confidentiality and privacy considerations.

---

## Data Preparation

The dataset was prepared through several data preprocessing steps:
* Data type checking
* Missing value identification and handling
* Data cleaning
* Duplicate checking
* Outlier detection
* Outlier treatment using IQR-based capping
* Categorical variable coding
* Data validation

### Outlier Treatment
A total of **31 numerical variables** were examined for outliers.
**30 variables** were treated using IQR-based capping, while **No. of abortions** was retained without capping because its extreme values represent actual patient conditions.

---

## Exploratory Data Analysis
Descriptive analysis and visualization were conducted to understand the characteristics and distribution of the dataset.

The analysis included:
* Descriptive statistics
* Histograms
* Bar charts
* Scatter plots
* Cross-tabulation
* Cramer's V
* Independent samples t-test

The target variable was imbalanced:

* **67.28%** of patients were classified as No SO
* **32.72%** of patients were classified as SO

Data balancing was therefore performed before model development.

---

## Statistical Analysis

The relationship between patient characteristics and SO status was explored using categorical and numerical analysis.
For categorical variables, contingency tables and association measures were used.
For numerical variables, differences between SO and No SO groups were examined using an independent samples t-test.
Several characteristics showed clearer differences between SO and No SO groups, particularly:
* Hair growth
* Weight gain
* Menstrual cycle
* Skin darkening
* Pimples
* Follicle numbers

---

## Predictive Modeling
Two classification approaches were evaluated:
1. **Logistic Regression**
2. **Decision Tree**

The models were developed using the training data and evaluated using classification metrics.

### Evaluation Metrics

The following metrics were used:

* Accuracy
* Precision
* Recall
* F1-score
* AUC

---

## Model Comparison

Logistic Regression demonstrated better performance than Decision Tree across the evaluated performance metrics.

### Logistic Regression Performance

| Metric    |     Result |
| --------- | ---------: |
| Accuracy  | **85.32%** |
| Precision | **73.81%** |
| Recall    | **86.11%** |
| F1-score  | **79.49%** |
| AUC       | **92.77%** |

Based on the evaluation results, **Logistic Regression was selected as the best-performing classification model**.

---

## Confusion Matrix

The Logistic Regression model produced the following classification results:
<img width="651" height="534" alt="image" src="https://github.com/user-attachments/assets/9393def2-7f8e-4524-aa5d-df99c5c348e4" />

The model correctly classified:
* **62** No SO patients
* **31** SO patients

while:
* **11** No SO patients were incorrectly classified as SO
* **5** SO patients were incorrectly classified as No SO

---

## ROC-AUC

The ROC curve produced an **AUC of 0.928 (92.8%)**, indicating strong discrimination between patients classified as SO and No SO within the evaluated dataset.

<img width="1076" height="758" alt="image" src="https://github.com/user-attachments/assets/295d1749-2267-4338-a539-02bf46ab23fb" />


---

## Significant Predictors
Based on the logistic regression analysis, several variables showed statistically significant relationships with SO status, including:
* Follicle No. (R)
* Hair growth
* Weight gain
* Cycle
* Skin darkening
* Marriage Status
* Pimples
* Follicle No. (L)

The analysis also indicated that irregular menstrual cycles, hair growth, and weight gain were among the characteristics associated with higher odds of SO in the selected model.

---


## Logistic Regression Model

Let \(p = P(SO=1)\), where \(SO=1\) represents patients classified as having **Syndrom Ovarium**.
The fitted logistic regression model obtained using **Forward Selection** is:

**log(p / (1 − p)) = −3.9129 + 0.4451X<sub>1</sub> + 1.7599X<sub>2</sub> + 1.5263X<sub>3</sub> + 1.9300X<sub>4</sub> + 1.3605X<sub>5</sub> − 0.1435X<sub>6</sub> + 0.9877X<sub>7</sub> + 0.1615X<sub>8</sub>**


where:

- \(X_1\) = Follicle No. (R)
- \(X_2\) = Hair Growth
- \(X_3\) = Weight Gain
- \(X_4\) = Cycle (R/I = 4.0)
- \(X_5\) = Skin Darkening
- \(X_6\) = Marriage Status
- \(X_7\) = Pimples
- \(X_8\) = Follicle No. (L)

The predicted probability of \(SO=1\) is calculated as:

$$
p = \frac{\exp(\eta)}{1+\exp(\eta)}
$$

where:
**linear predictor =**
**−3.9129 + 0.4451X1 + 1.7599X2 + 1.5263X3 + 1.9300X4**
**+ 1.3605X5 − 0.1435X6 + 0.9877X7 + 0.1615X8**

### Model Performance
- **Accuracy:** 85.32%
- **Precision:** 73.81%
- **Recall:** 86.11%
- **F1-score:** 79.49%
- **AUC:** 0.928

### Model Interpretation
The model indicates that higher values of right ovarian follicle count,
hair growth, weight gain, irregular menstrual cycle, skin darkening,
pimples, and left ovarian follicle count are associated with higher
log-odds of SO status, while the coefficient for marriage status is negative.

## Key Findings
1. The dataset contained **541 patient observations and 44 variables** covering demographic, clinical, hormonal, reproductive, lifestyle, and ovarian characteristics.
2. Data preprocessing included missing value handling, duplicate checking, outlier treatment, and categorical variable coding.
3. The target variable was imbalanced, with **67.28% No SO** and **32.72% SO** observations.
4. Logistic Regression performed better than Decision Tree based on the evaluated classification metrics.
5. Logistic Regression achieved **85.32% accuracy, 86.11% recall, 79.49% F1-score, and 92.77% AUC**.
6. Several patient characteristics were statistically associated with SO status, particularly menstrual cycle, hair growth, weight gain, skin darkening, pimples, and ovarian follicle numbers.


## Tools
* Python
* Microsoft Excel
* Data Cleaning
* Exploratory Data Analysis
* Statistical Analysis
* Logistic Regression
* Decision Tree
* Model Evaluation
* Data Visualization


## Project Workflow
```text
Data Understanding
        ↓
Data Cleaning
        ↓
Missing Value & Duplicate Checking
        ↓
Outlier Detection & Treatment
        ↓
Exploratory Data Analysis
        ↓
Association Analysis
        ↓
Data Balancing
        ↓
Model Development
        ↓
Logistic Regression vs Decision Tree
        ↓
Model Evaluation
        ↓
Model Selection
        ↓
Interpretation
```


**BNSP Data Analyst Competency Certification Project – 2026**
**Author:** Nafa Nurhanifah
