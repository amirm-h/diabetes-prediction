## Project Overview

### Title:

**Predicting Diabetes Risk Based on User Input and Optimized Machine Learning Models**

---

## Dataset Used

The **Pima Indians Diabetes Dataset** was used for training and evaluation.
https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database
---

## Machine Learning Models

The following **8 models** were evaluated:

1. **Random Forest**
2. **Gradient Boosting**
3. **Decision Tree**
4. **Logistic Regression**
5. **Support Vector Machine (SVM)**
6. **K-Nearest Neighbors (KNN)**
7. **Multilayer Perceptron (MLP)**
8. **Gaussian Naive Bayes**

---

## Analysis Workflow

### 1. Data Preprocessing

* **Missing values**, **outliers**, and **skewness** were carefully analyzed.
* **Irrelevant or redundant features** were removed.
* **Meaningless or invalid values** were replaced with appropriate substitutes.

### 2. Model Evaluation

* Each of the **8 machine learning models** was executed **1,000 times** using different random seeds.
* For each model run, the **average accuracy**, **execution time**, and **standard deviation** were recorded to assess **stability and performance**.
* The **best random seed** was selected for each model based on these metrics.

### 3. Sensitivity Testing

* The same process was repeated:
    \* Once with **de-skewed data**
    \* Once with **scaled (normalized) data**

This step was necessary because some models are sensitive to skewness and scaling, while others are not. For sensitive models, **performance before and after preprocessing** was compared to guide model selection.

---

## Final Score Metric

To better evaluate each model, a new metric called **Final Score** was introduced:

```
Final Score = (Accuracy × 2) / Standard Deviation
```

This formula favors models that are both **accurate** and **stable**.

---

## Model Selection Strategy

* The **top 3 models** based on **accuracy** and the **top 3 models** based on **Final Score** were selected.
* If a model ranked first using one version of the data (e.g., raw), but not in others (e.g., scaled or de-skewed), it was considered only in **its best-performing category**.
* This ensures **diversity** and **fairness** in the final model ensemble.

---

## Main Application Logic

* The selected models are trained using:
    \* The **optimized random seed**
    \* The **best-performing version** of the dataset (raw, scaled, or de-skewed)
* **User input** is collected through a set of medical/lifestyle questions.
* Each input is **transformed appropriately** to match the preprocessing used for each model (e.g., normalization or skew correction).
* **User input is validated** to ensure it falls within logical and medically reasonable ranges.

---

## Prediction Output

* The final result is calculated as the **average prediction of all selected models**.
* This ensemble approach enhances both **reliability** and **accuracy** of the diabetes risk estimation provided to the user.
* A **confidence score** is also shown, based on model agreement.

---

## Planned Features

### ✅ Re-run Capability

* Users can **re-run the application** from the interface at any time to input new values or test different scenarios.

### ✅ User Input Validation

* All user inputs are **checked for correctness and plausibility** before being passed into the models.
* Invalid or out-of-range values prompt warnings and suggestions.

### ✅ Graphical User Interface (GUI)

* A **simple and intuitive GUI** was developed to improve accessibility.
* The interface includes:
    \* **Progress bar** during model execution
    \* **Charts** for comparing model accuracy, execution time, and stability
    \* Interactive selection of model preferences
