PROJECT - Predicting Stroke Events:Integrating Real-World and Synthetic Data for Accurate Prognostication


1- Data Loading:

The code reads four CSV files: "train.csv", "test.csv", "sample_submission.csv", and "healthcare-dataset-stroke-data.csv" using the pandas library and assigns them to respective variables: train_set, test_set, sample_submission, and combined_data.

2- Data Exploration and Preprocessing:

The code performs basic data exploration and preprocessing steps on the datasets.
It checks for missing values in each dataset using the isna().sum() method.
It displays the first 5 rows of each dataset using the head() method.

3-Data Merging and Column Removal:

A new dataset temp is created by selecting rows from combined_data where the "stroke" column is equal to 1.
The temp dataset and train_set are concatenated vertically using pd.concat() along the axis 0 (rows) to create a merged dataset, and the "id" column is dropped.
The "id" column is also dropped from the test_set dataset.

4-Data Transformation:

Categorical variables are encoded using ordinal encoding techniques.
For selected columns, specific values are replaced with numerical representations.
The missing values in the "bmi" column are filled with the mean value using fillna().

5-Feature Engineering:

A new feature called "risk_factor" is created based on the values of several columns using the apply() method.
Additional binary features, "obese_category1" and "obese_category2", are created based on the "bmi" column.
Missing values in the "bmi" column are imputed using the median value from the SimpleImputer class.

6-Data Visualization:

Various visualizations are created using the seaborn library to explore relationships between variables and the target variable "stroke".

7-Model Training and Evaluation:

Logistic Regression and LightGBM models are trained using the LogisticRegression and LGBMClassifier classes, respectively.
Stratified K-fold cross-validation is performed with 5 folds.
The ROC-AUC score is calculated for each fold, and the average score is computed.
Feature importances are calculated and plotted.
The trained model is used to make predictions on the test dataset.

8-Submission:

The predictions are stored in a DataFrame and saved to a CSV file named "submission.csv" using the to_csv() method.
