#  Severity Classification of Migration Incidents

##  Project Description

This project builds a complete Machine Learning pipeline to classify the severity of migration-related incidents using the **Global Missing Migrants Dataset**.

The goal is to predict the severity level of an incident (`Low`, `Medium`, `High`) based on geographical, temporal, and contextual features.

The project includes:

-  Data Understanding
-  Robust Data Cleaning
-  Target Variable Creation
-  Data Leakage Prevention
-  Stratified Train/Test Split
-  Training and comparison of multiple ML models
-  Advanced statistical evaluation

---

##  Dataset

The dataset contains historical information about migration incidents, including:

- Number of deaths
- Estimated number of missing persons
- Region of incident
- Year
- Cause of death
- Geographic coordinates

Original target variable:

Total Number of Dead and Missing

---

##  Target Variable Creation

The problem is transformed into a multiclass classification task:

| Total Dead & Missing | Severity |
|----------------------|----------|
| 0 – 2                | Low      |
| 3 – 10               | Medium   |
| > 10                 | High     |

---

##  Data Cleaning

Includes:

- Duplicate removal
- Safe numeric conversion
- Negative value correction
- Coordinate parsing and validation
- Total reconstruction consistency checks
- Removal of inconsistent records

---

##  Leakage Removal

The following columns are removed to prevent target leakage:

- Total Number of Dead and Missing
- Number of Dead
- Minimum Estimated Number of Missing
- Number of Survivors
- Number of Females
- Number of Males
- Number of Children

---

##  Train/Test Split

- 80% Training
- 20% Testing
- Stratified by class
- Academic validation of split strategy

---

## ⚙️ Preprocessing

- Leakage-free imputation (median/mode from training set)
- Cardinality reduction
- Outlier treatment
- OneHot Encoding
- Feature scaling (for linear/distance models)
- Feature selection (SelectKBest)

---

##  Models Trained

- Naive Bayes
- KNN
- SVM (Linear, Polynomial, RBF)
- Decision Tree
- Random Forest
- Extra Trees
- AdaBoost
- Bagging

Hyperparameter tuning performed using GridSearchCV with:

F1-weighted as optimization metric.

---

##  Final Results

| Model          | Accuracy | F1-weighted |
|---------------|----------|------------|
| SVM           | 0.808    | 0.7848     |
| Random Forest | 0.806    | 0.7900     |
| Extra Trees   | 0.792    | 0.7827     |
| AdaBoost      | 0.801    | 0.7632     |
| Decision Tree | 0.767    | 0.7667     |
| KNN           | 0.727    | 0.7520     |
| Naive Bayes   | 0.583    | 0.6426     |

Random Forest and SVM show the most stable and competitive performance.

---

##  Statistical Evaluation

- McNemar Test (model comparison)
- 95% Confidence Intervals (Wilson)
- Bootstrap confidence intervals for F1
- Precision–Recall Curves
- Confusion matrices comparison

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Imbalanced-learn
- Seaborn
- Matplotlib
- Statsmodels

---

## ▶ How to Run

Install dependencies:

pip install -r requirements.txt

Run the notebook:

PRACTICA_JESIKA_JIMENEZ_GERARD_CHAPARRO.ipynb

---

##  Authors

- Jesika Jiménez  
- Gerard Chaparro  

---

##  Project Status

Complete project with statistical validation and robust model comparison.
