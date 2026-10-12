# Student Dropout and Academic Success

## Datasets

Both datasets come from the UCI Machine Learning Repository.

| Dataset | UCI ID | Students | Features |
|---|---|---|---|
| Predict Students' Dropout and Academic Success | 697 | 4,424 | 36 |
| Higher Education Students Performance Evaluation | 856 | 145 | 31 |

## Summary of Project Stages

### 1. Data Collection and Exploration

- Checked feature types, target variables and missing values. Neither dataset has missing values.
- In the dropout dataset, 2,209 students graduated, 1,421 dropped out and 794 were still enrolled.
- Visualized the target distribution and compared admission and semester grades across Dropout, Enrolled and Graduate students with boxplots.

### 2. Data Preprocessing

- Removed leading and trailing spaces from column names.
- Encoded categorical variables with one-hot encoding for the regression models and label encoding for the Random Forest targets.
- Standardized features before fitting logistic regression.
- Converted the three-class target into a binary dropout variable (Dropout = 1, Enrolled or Graduate = 0) for dropout prediction.
- Mapped categorical bands in the Higher Education dataset, such as GPA ranges and scholarship levels, to numeric midpoints to estimate averages.
- Addressed class imbalance with SMOTE, random oversampling and random undersampling.

### 3. Model Development

**Logistic regression for dropout**

| Model | Accuracy | Dropout precision | Dropout recall |
|---|---|---|---|
| Baseline | 0.87 | 0.88 | 0.72 |
| With SMOTE | 0.84 | – | 0.76 |

- Evaluated with classification reports, confusion matrices, ROC-AUC (0.91) and the Matthews Correlation Coefficient (0.71).

**Random Forest**

- Ranked the features that influence dropout and graduation. Approved curricular units and grades in both semesters, along with tuition payment status, ranked highest.
- Compared resampling methods on a three-class Random Forest.

| Method | Result |
|---|---|
| Oversampling | Highest accuracy (0.78) |
| Undersampling | Highest recall for Enrolled students (0.62), lowest accuracy (0.73) |

- Enrolled students remained the hardest class to predict under every method.

**K-nearest neighbours**

- Compared parents' occupations and qualifications among similar students in each outcome group.

### 4. Statistical and Regression Analysis

**Logistic regression (statsmodels)**

- Admission grade did not significantly predict scholarship status (p = 0.209).
- Scholarship holders were significantly less likely to be debtors (coefficient −0.56, p < 0.001).

**Descriptive rates**

- The overall dropout rate is 32.12%.
- Among dropouts, 32.16% had unpaid tuition, compared with 1.31% of graduates.
- Among debtors, 62.03% dropped out, compared with 28.28% of non-debtors.

**Linear regression of output grade**

- Predicted students' output grade from last-semester GPA and expected cumulative GPA.
- Rescaled the output grade from its original 0 to 7 scale to a 1 to 5 scale and a 4.0 GPA scale.

| Target scale | RMSE |
|---|---|
| 0 to 7 | 2.08 |
| 1 to 5 | 1.42 |
| 4.0 GPA | 1.16 |

Because each target uses a different scale, part of this drop reflects the narrower range rather than better prediction.

### 5. Results Interpretation and Visualization

- Academic progress, measured by approved units and semester grades, was the strongest predictor of dropout.
- In the GPA regression, each additional last-semester GPA band raised the predicted grade by 0.30, while expected GPA had almost no effect (−0.02).
- Created boxplots, bar charts, a count plot and confusion matrices to show grade distributions, outcomes by debtor status and feature importance.

## Repository Contents

| File | Contents |
|---|---|
| `Higher_Education_Students_Performance_Evaluation` | Data summary, missing value check, mean and standard deviation of each feature, distribution of last-semester GPA, categorical bands converted to continuous values, Pearson correlations between each feature and the target |
| `Predict_Students'_Dropout_and_Academic_Success` | Data summary, missing value check, feature type counts, target distribution, grade boxplots by outcome, comparison of SMOTE, oversampling and undersampling with Random Forest, mean, standard deviation and Pearson correlations for the Higher Education dataset |
| `Q1_Technical_Report_Final Results` | Logistic regression with and without SMOTE, classification reports, confusion matrices, k-nearest neighbours analysis of family background, logistic regression coefficients, ROC-AUC, Matthews Correlation Coefficient, Random Forest feature importance, visualizations |
| `Q2_Technical_Report_Final Results` | Logistic regression for dropout and its coefficients, grade and GPA boxplots, Random Forest feature importance, linear regression of output grade on GPA, RMSE across three target scales, regression coefficients |
| `Q3_Technical_Report_Final Results` | Logistic regression of scholarship status and debt, outcomes by debtor status, dropout and unpaid tuition rates, comparison of SMOTE, oversampling and undersampling with Random Forest, classification reports, visualization |
