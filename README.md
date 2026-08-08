# Student Performance Prediction

A machine learning project that analyzes student performance and predicts final grades using demographic, academic, and behavioral factors.

## Project Overview

The goal of this project is to investigate which factors are associated with students' final academic performance and build machine learning models that can predict the final grade (`G3`).

Previous-period grades (`G1` and `G2`) were intentionally excluded from the models to make the prediction task more meaningful and avoid relying on information that directly reflects previous academic performance.

## Dataset

The project uses the Student Performance dataset containing information about 649 students.

The dataset includes features related to:

- Student demographics
- Parents' education
- Study time
- Previous failures
- Absences
- Social activities
- Alcohol consumption
- Health
- Family relationships
- Travel time

The target variable is:

- `G3` — final student grade

## Exploratory Data Analysis

The dataset was first analyzed to check:

- Missing values
- Data types
- Target statistics
- Correlations between numerical features
- Relationships between student characteristics and final grades

### Key Correlations

Some of the strongest correlations with the final grade were:

| Feature | Correlation with G3 |
|---|---:|
| G2 | 0.919 |
| G1 | 0.826 |
| failures | -0.393 |
| studytime | 0.250 |
| Medu | 0.240 |
| Fedu | 0.212 |
| Dalc | -0.205 |
| Walc | -0.177 |

Although `G1` and `G2` showed very strong correlations with `G3`, they were excluded from the final models.

## Features Used

The final models used 13 numerical features:

```text
age
Medu
Fedu
traveltime
studytime
failures
famrel
freetime
goout
Dalc
Walc
health
absences
Machine Learning Models

Three regression models were trained and compared:

Linear Regression
Random Forest Regressor
Gradient Boosting Regressor

The dataset was split into:

80% training data
20% testing data

The test set contained 130 students.

Model Results
Model	MAE	MSE	R²
Linear Regression	2.124	8.046	0.175
Random Forest	2.071	8.099	0.169
Gradient Boosting	2.177	8.202	0.159
Results Analysis

Linear Regression achieved the highest R² score and the lowest MSE.

Random Forest achieved the lowest MAE, meaning it had the smallest average absolute prediction error.

Overall, Linear Regression performed slightly better according to R² and MSE, while Random Forest performed slightly better according to MAE.

Feature Importance

Random Forest feature importance showed that failures was the most important feature used by the model.

Top features included:

Feature	Importance
failures	0.212
absences	0.092
freetime	0.077
Fedu	0.074
age	0.072
goout	0.066
Medu	0.065

This suggests that previous academic failures contained more predictive information than the other behavioral and demographic features included in the model.

Feature importance should not be interpreted as causation. It only describes how useful each feature was for the Random Forest model's predictions.

Error Analysis

The prediction results showed that the models generally performed better for students with grades closer to the middle of the distribution.

The models had more difficulty predicting students with unusually high or low final grades.

For example, one student with an actual final grade of 19 received a predicted grade of approximately 13.83.

This indicates that the available features do not contain enough information to accurately predict every student's final performance.

Limitations

Several limitations should be considered:

The dataset contains only 649 students.
Only numerical features were used in the first modeling stage.
The models intentionally exclude G1 and G2.
The relatively low R² score indicates that many factors influencing final grades are not captured by the available features.
Correlation and feature importance do not imply causation.
Technologies
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Joblib
Google Colab
Project Structure
student-performance-prediction/
│
├── student_performance_predictor.ipynb
├── student_grade_model.pkl
├── requirements.txt
├── README.md
└── LICENSE
Future Improvements

Possible improvements include:

Hyperparameter tuning
Cross-validation
Testing additional regression algorithms
Including categorical variables through proper encoding
Feature engineering
Comparing models using cross-validation
Building a simple interface for making predictions
Author

Arslan Jamalov

This project was created as part of my independent study of machine learning and data science.
