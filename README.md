# Kaggle Competition - Predicting Road Accident Risk

## Introduction

In thie Kaggle Playground Competition, the objective was "Predict the likelihood of accidents on different types of roads.". It was a simple problem, but main focus in Kaggle Competitions is to reach the best accuracy, which in this competition is Root Mean Squared Error (RMSE).

In this repository, I will present my solution that achieved an **RMSE of 0.05567**. Unfortunately, I didn't win the competition, but I would like to share my line of thinking and possible improvements for future competitions.

## Table of Contents
- [Introduction](#introduction)
- [Technologies Used](#tecnologies-used)
- [Structure of Notebooks](#structure-of-notebooks)
  - [First Analysis](#first-analysis)
  - [1. Pre-Processing](#1-pre-processing)
    - [Statistical Analysis](#statistical-analysis)
  - [2. Modeling](#2-modeling)
  - [3. Stacking](#3-stacking)
  - [4. Submission](#4-submission)
- [Solution](#solution)

## Tecnologies Used

- Jupyter
- Pandas
- Numpy
- Sklearn
- cuML
- CatBoost, LightGBM, XGBoost
- Optuna

## Structure of Notebooks

### First Analysis

This step focuses on exploring the dataset to identify missing or duplicated values.

### 1. Pre-Processing
#### Statistical Analysis

Despite the name "Statistical Analysis," the goal of this project was not a full exploratory data analysis (EDA). In this part, I analyzed the distribution of the dependent variable accident_risk and performed a quick multicollinearity check using the Pandas .corr() method and the VIF metric. Outliers were not removed since most variables are not continuous in nature.

### 2. Modeling

Different models were tested to compare performance. XGBoost was expected to deliver the best results from the start.

### 3. Stacking

I implemented a custom class with methods similar to those in scikit-learn to create a stacking-based meta-model. This technique was inspired by Kaggle competitors, as ensemble methods are commonly used by top performers to achieve higher accuracy. It is also well known that ensemble models remain state-of-the-art for tabular data.

### 4. Submission

This section contains the final submission process.

## Solution

No advanced data processing techniques were applied in this solution. Only an OrdinalEncoder was used to handle categorical features.

The final model was built using Stacking combined with Cross-Validation to generate the meta-model. The base layer consisted of the following models: CatBoost, LightGBM, Gradient Boosting Regressor, XGBoost, and a Multi-Layer Perceptron (MLP). The ensemble model achieved an **RMSE of 0.05567** in test set.

One clear area for improvement is the lack of feature creation. Due to my limited experience in this field, I did not engineer additional variables to train the ensemble model. However, feature engineering has proven to be highly effective in Kaggle competitions, as I have seen in several analyses.

Although the solution did not reach the top of the leaderboard, it showed promising results and strengthened my confidence in improving my performance in future competitions.
