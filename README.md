## Capstone-Project_Students-Dropout-And-Academic-Success

##Summary of Project Stages

--Summary of Initial Results and Coding

1. Data Collection & Exploration-

Retrieved two datasets from the UCI Machine Learning Repository. "Predict Students' Dropout and Academic Success" (ID 697) covers 4,424 students with 36 features. "Higher Education Students Performance Evaluation" (ID 856) covers 145 students with 31 features.

Checked feature types, target variables and missing values. Neither dataset has missing values. In the dropout dataset, 2,209 students graduated, 1,421 dropped out and 794 were still enrolled.

Visualized the target distribution and compared admission and semester grades across Dropout, Enrolled and Graduate students with boxplots.


2. Data Preprocessing-

Removed leading and trailing spaces from column names.

Encoded categorical variables with one-hot encoding for the regression models and label encoding for the Random Forest targets. Standardized features before fitting logistic regression.

Converted the three-class target into a binary dropout variable (Dropout = 1, Enrolled or Graduate = 0) for dropout prediction.

Mapped categorical bands in the Higher Education dataset, such as GPA ranges and scholarship levels, to numeric midpoints to estimate averages.

Addressed class imbalance with SMOTE, random oversampling and random undersampling.


3. Model Development-

Built a logistic regression model to predict dropout. It reached 0.87 accuracy, with 0.88 precision and 0.72 recall for dropouts. Retraining with SMOTE raised dropout recall to 0.76 but lowered accuracy to 0.84.

Evaluated the model with classification reports, confusion matrices, the ROC-AUC score (0.91) and the Matthews Correlation Coefficient (0.71).

Trained Random Forest classifiers to rank the features that influence dropout and graduation. Approved curricular units and grades in both semesters, along with tuition payment status, ranked highest.

Compared SMOTE, oversampling and undersampling on a three-class Random Forest. Oversampling gave the highest accuracy (0.78). Undersampling gave the highest recall for Enrolled students (0.62) but the lowest accuracy (0.73). Enrolled students remained the hardest class to predict under every method.

Used k-nearest neighbours to compare parents' occupations and qualifications among similar students in each outcome group.


4. Statistical and Regression Analysis-

Fitted logistic regressions with statsmodels. Admission grade did not significantly predict scholarship status (p = 0.209). Scholarship holders were significantly less likely to be debtors (coefficient -0.56, p < 0.001).

Calculated descriptive rates. The dropout rate is 32.12%. Among dropouts, 32.16% had unpaid tuition, compared with 1.31% of graduates. Among debtors, 62.03% dropped out, compared with 28.28% of non-debtors.

Developed linear regression models to predict students' output grade from their last-semester and expected cumulative GPA.

Rescaled the output grade from its original 0 to 7 scale to a 1 to 5 scale and a 4.0 GPA scale. RMSE fell from 2.08 to 1.42 and then 1.16. Because each target uses a different scale, part of this drop reflects the narrower range rather than better prediction.


5. Results Interpretation & Visualization-

Analyzed feature importance and model coefficients. Academic progress, measured by approved units and semester grades, was the strongest predictor of dropout. In the GPA regression, each additional last-semester GPA band raised the predicted grade by 0.30, while expected GPA had almost no effect (-0.02).

Created boxplots, bar charts, a count plot and confusion matrices to show grade distributions, outcomes by debtor status and feature importance.



--Summary of Repository Contents

1. Data Descriptions of "Higher_Education_Students_Performance_Evaluation"-
Data summary, missing value check, mean and standard deviation of each feature, distribution of last-semester GPA, categorical bands converted to continuous values, Pearson correlations between each feature and the target column

2. Data Descriptions of "Predict_Students'_Dropout_and_Academic_Success"-
Data summary, missing value check, feature type counts, target distribution, grade boxplots by outcome, comparison of SMOTE, oversampling and undersampling with Random Forest, mean, standard deviation and Pearson correlations for the Higher Education dataset

3. Q1_Technical_Report_Final Results -
Logistic regression with and without SMOTE, classification reports, confusion matrices, k-nearest neighbours analysis of family background, logistic regression coefficients, ROC-AUC score, Matthews Correlation Coefficient, Random Forest feature importance, visualizations

4. Q2_Technical_Report_Final Results -
Logistic regression for dropout and its coefficients, grade and GPA boxplots, Random Forest feature importance scores, linear regression of output grade on GPA, RMSE across three target scales, regression coefficients

5. Q3_Technical_Report_Final Results -
Logistic regression of scholarship status and debt, outcomes by debtor status, dropout rate and unpaid tuition rates, comparison of SMOTE, oversampling and undersampling with Random Forest, classification reports, visualization
