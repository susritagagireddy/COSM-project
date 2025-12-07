
# 📘 Project Report

## Student Performance Analysis Using Simple and Multiple Linear Regression

---

## 1. Abstract

This project analyzes the relationship between students’ study habits and their academic performance using statistical and machine learning techniques. The primary objective is to understand how **study hours** influence final grades and how additional academic factors contribute using **Multiple Linear Regression**. Hypothesis testing is applied to validate the significance of the results. The study proves that study hours and attendance have a statistically significant positive effect on student performance.

---

## 2. Introduction

Education plays a crucial role in personal and professional development. With the increasing availability of educational data, statistical models can be used to identify important predictors of academic success. This project applies both simple and multiple regression models to measure the effect of study habits and attendance on student outcomes.

---

## 3. Problem Statement

Students and educators often lack quantitative evidence regarding how study hours, attendance, and learning habits influence academic results. This project aims to bridge this gap using regression analysis and statistical testing.

---

## 4. Objectives

* To analyze the impact of study hours on student grades
* To build Simple and Multiple Linear Regression models
* To evaluate the importance of attendance and study methods
* To apply hypothesis testing to validate results
* To interpret statistical outputs and model performance

---

## 5. Dataset Description

The dataset contains student academic information with the following key variables:

* `study_hours` – hours spent studying
* `attendance_percentage` – attendance rate
* `study_method` – learning style/category
* `final_grade_num` – numeric form of final grade

The dataset was cleaned by handling missing values, removing duplicates, and encoding categorical variables.

---

## 6. Methodology

### 6.1 Data Preprocessing

* Missing values were handled
* Duplicate records were removed
* Categorical variables (e.g., `study_method`) were encoded
* Numerical variables were normalized

### 6.2 Exploratory Data Analysis (EDA)

* Scatter plots for study hours vs final grades
* Correlation analysis
* Outlier detection

---

## 7. Simple Linear Regression Model

The simple regression model was developed using:

[
Final_Grade = \beta_0 + \beta_1 \times Study_Hours
]

**Estimated Model:**

[
Final_Grade = -0.168 + 0.543 \times Study_Hours
]

This shows that each additional hour of study increases the score by approximately **0.54 marks**.

---

## 8. Multiple Linear Regression Model

### 8.1 Model Construction

The simple regression was extended to **Multiple Linear Regression** using the following model:

[
Final_Grade_Num = \beta_0 + \beta_1 \times Study_Hours + \beta_2 \times Attendance_Percentage + \beta_3 \times Study_Method
]

Implemented as:

```python
lm = smf.ols(formula='final_grade_num ~ study_hours + attendance_percentage + study_method', data=df).fit()
```

### 8.2 Model Coefficients Interpretation

**Intercept = –2.202724**
This is the baseline predicted score when:

* `study_hours = 0`
* `attendance_percentage = 0`
* and the study method is the reference category

**Study Hours (β₁ ≈ 0.54):**
For every extra hour of study, the student’s score increases by about **0.54 marks** on average.
→ This is a strong positive factor.

**Attendance Percentage (β₂ ≈ 0.027):**
For every 1% increase in attendance, the score increases by **0.027 marks**.
→ This has a small but positive effect.

**Study Method (β₃):**
The coefficients are very small, indicating that **study method has very little effect** on the final score.

---

### 8.3 Model Performance

From the regression summary:

* **R-squared = 0.858**
  → The model explains **85.8%** of the variation in students’ final grades, indicating a very strong fit.

* **Adjusted R-squared = 0.858**
  → Almost the same as R², showing that the model is not overfitting.

* **F-statistic = 1.292 × 10⁴**
  → Indicates the overall model is highly statistically significant.

* **Prob(F-statistic) = 0.00**
  → Confirms the model as a whole is statistically significant.

---

### 8.4 Hypothesis Testing Results (Multiple Regression)

* **Study Hours and Attendance Percentage:**
  p-values < 0.05 → statistically significant
  ✅ Reject null hypothesis

* **Study Method Variables:**
  p-values > 0.05 → not statistically significant
  ❌ Fail to reject null hypothesis

This shows:

* Study hours and attendance are **positively and significantly associated** with final grades.
* Study method does **not** meaningfully affect grades in this model.

---

### 8.5 Model Comparison (Feature Importance Check)

Model without `study_method`:

```python
lm = smf.ols(formula='final_grade_num ~ study_hours + attendance_percentage', data=df).fit()
lm.rsquared = 0.8578009583255622
```

Model with `study_method`:

```python
lm = smf.ols(formula='final_grade_num ~ study_hours + attendance_percentage + study_method', data=df).fit()
lm.rsquared = 0.8578169404257358
```

✅ Adding `study_method` improved R² by only **0.000016**, which is negligible.
✅ This proves that `study_method` does not meaningfully improve the predictive power of the model.

Also, in general, R² usually increases when more features are added, even if they are unrelated to the target variable.

---

## 9. Hypothesis Testing Summary

* t-tests were used to test individual coefficients.
* F-test was used to test overall model significance.
* Chi-square and Z-tests were discussed conceptually.

Decision rule:
If **p-value < 0.05**, reject the null hypothesis.

---

## 10. Discussion

The multiple regression results confirm that **study hours and attendance** are the strongest predictors of student performance. Study method had minimal impact and did not significantly improve the model.

---

## 11. Limitations

* Limited number of variables
* Linear model assumptions
* Potential unmeasured confounding variables

---

## 12. Future Scope

* Use more academic and personal predictors
* Apply regularization (Ridge, Lasso)
* Try non-linear models
* Perform cross-validation

---

## 13. Conclusion

This project demonstrates that **study hours and attendance percentage** are the most important predictors of student final grades. Multiple Linear Regression provided a stronger and more realistic model than simple regression, and hypothesis testing confirmed the reliability of the findings.

---

## 14. References

* Python Documentation
* Statsmodels Documentation
* Scikit-learn Documentation
* Statistical Learning Resources

---
