# IEEE ML Challenge – Device Fault Detection

Author: Bhumi Rana  
B.Tech CSE

## Overview

This repository contains my solution for the IEEE SB GEHU ML Challenge Qualifiers.

The objective of this challenge is to determine whether a device is operating normally or experiencing a faulty condition based on 47 numerical features (F01–F47). These features represent measurements recorded by a monitoring system during device operation.

This task is formulated as a binary classification problem:

Class = 0 → Device operating normally  
Class = 1 → Device exhibiting faulty behavior

## Repository Structure

ieee-ml-fault-detection

solution.ipynb – Complete machine learning workflow, code, and explanation  
FINAL.csv – Model predictions generated for TEST.csv  
requirements.txt – Required Python libraries  
README.md – Project description

## Approach Summary

The detailed methodology and explanation of each step are included in the notebook (solution.ipynb) using markdown cells.

The overall workflow includes:

1. Dataset Understanding  
The dataset structure was examined to understand the feature types and target distribution.

2. Data Inspection  
The dataset consists entirely of numerical features and no missing values were observed.

3. Class Distribution Analysis  
The dataset contains both normal and faulty device conditions with approximately a 60:40 distribution.

4. Feature Analysis  
Correlation analysis was performed between the features and the target variable to ensure there was no direct label leakage.

5. Model Training  
A gradient boosting model using XGBoost was trained to learn relationships between the input features and the device state.

6. Validation Strategy  
A stratified train-validation split was used to maintain class balance.  
Additionally, 5-fold stratified cross-validation was performed to evaluate model stability.

7. Prediction Generation  
The model was trained on the full training dataset and used to generate predictions for the test dataset.

## Model Used

XGBoost Classifier

Parameters used:

n_estimators = 500  
learning_rate = 0.05  
max_depth = 6  
subsample = 0.8  
colsample_bytree = 0.8  

Tree-based gradient boosting models were selected because they perform well on structured tabular datasets and can effectively capture nonlinear relationships between features.

## Performance

5-fold cross-validation was used to evaluate model performance.

Mean ROC-AUC ≈ 0.9984

This indicates strong separation between normal and faulty device states.

## How to Run

1. Install the required Python libraries:

pip install pandas numpy scikit-learn xgboost seaborn matplotlib

2. Place TRAIN.csv and TEST.csv in the same directory as the notebook.

3. Run the notebook:

solution.ipynb

4. The notebook will generate the submission file:

FINAL.csv

## Submission Format

The generated submission file follows the required format:

ID, CLASS

ID corresponds to the device ID from TEST.csv and CLASS contains the predicted label (0 or 1).

## Notes

The notebook contains detailed explanations of the methodology, data analysis, model training process, and evaluation steps used to build the final model.
