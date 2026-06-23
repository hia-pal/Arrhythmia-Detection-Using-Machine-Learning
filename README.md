# Arrhythmia Detection Using Machine Learning

## Overview

Cardiac arrhythmias are abnormalities in the heart's electrical activity that can lead to serious health complications, including stroke, heart failure, and sudden cardiac arrest. Early detection is critical, yet diagnosis often requires expert interpretation of ECG signals.

This project develops and compares multiple machine learning models for the binary classification of patients as **Arrhythmic** or **Non-Arrhythmic** using ECG-derived and clinical features. The study emphasizes model interpretability, feature selection, and robustness in a healthcare setting.

---

## Objectives

* Identify key clinical and ECG features associated with arrhythmia.
* Explore relationships between demographic and cardiac measurements.
* Address multicollinearity among ECG variables.
* Compare multiple classification algorithms.
* Evaluate predictive performance using clinical classification metrics.

---

## Dataset

The dataset contains approximately **450 patient observations** with ECG measurements and clinical characteristics. Data cleaning was performed prior to analysis, including removal of inconsistent and missing observations.

### Features Used

Clinical Variables:

* Age
* Sex
* BMI

ECG Variables:

* QRS Duration
* PR Interval
* QT Interval
* QRS Axis

Redundant variables such as P Interval and T Interval were removed after multicollinearity analysis due to their strong relationship with PR and QT intervals.

---

## Exploratory Data Analysis

Key findings from the exploratory analysis include:

* Arrhythmic patients tend to be older than non-arrhythmic patients.
* Higher BMI is associated with increased arrhythmia risk.
* QRS Duration and QT Interval are generally larger among arrhythmic patients.
* Age appears to be positively associated with arrhythmia occurrence.
* Class distribution remains relatively balanced, reducing concerns regarding severe class imbalance.

---

## Feature Selection & Multicollinearity

To improve interpretability and reduce redundancy:

* Pearson correlation analysis was performed.
* Variance Inflation Factor (VIF) analysis was used to assess multicollinearity.
* P Interval and T Interval were removed due to high redundancy.
* All remaining variables exhibited acceptable VIF values, indicating low multicollinearity.

---

## Models Implemented

### 1. Logistic Regression

A standardized logistic regression model was developed as an interpretable baseline classifier.

**Advantages**

* Interpretable coefficients
* Probabilistic predictions
* Strong baseline performance

### 2. Gaussian Naive Bayes

A probabilistic classifier assuming conditional independence among predictors.

**Advantages**

* Fast training
* Minimal computational requirements
* Useful baseline comparison

### 3. Random Forest

An ensemble learning model using bootstrap aggregation and multiple decision trees.

**Advantages**

* Captures non-linear relationships
* Robust to noise and outliers
* Provides feature importance measures

---

## Model Evaluation

Performance was evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* 5-Fold Cross Validation

### Test Set Results

| Model               | Accuracy | Precision | Recall | F1 Score |
| ------------------- | -------- | --------- | ------ | -------- |
| Logistic Regression | 71.96%   | 65.38%    | 73.91% | 69.39%   |
| Naive Bayes         | 70.09%   | 70.59%    | 52.17% | 60.00%   |
| Random Forest       | 70.09%   | 66.67%    | 60.87% | 63.64%   |

### ROC-AUC

| Model               | AUC                    |
| ------------------- | ---------------------- |
| Logistic Regression | 0.794                  |
| Naive Bayes         | 0.762                  |
| Random Forest       | Comparable performance |

---

## Key Findings

* Logistic Regression achieved the strongest overall balance between precision and recall.
* QRS Duration emerged as the most influential predictor across models.
* Age and QT Interval were consistently associated with higher arrhythmia risk.
* Naive Bayes exhibited low recall, missing a substantial proportion of true arrhythmia cases.
* Random Forest successfully captured non-linear relationships while maintaining strong predictive performance.
* Feature reduction had only a minor impact on model accuracy, suggesting that a smaller clinically interpretable feature set can be effective.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Matplotlib
* Seaborn

---

## Future Improvements

* Incorporate additional ECG waveform features.
* Explore Gradient Boosting and XGBoost classifiers.
* Apply SHAP-based explainability techniques.
* Evaluate deep learning approaches on raw ECG signals.
* Deploy the model as a real-time clinical screening application.

---

## Disclaimer

This project is intended for educational and research purposes only and should not be used as a substitute for professional medical diagnosis.
