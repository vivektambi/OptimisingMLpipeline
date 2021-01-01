# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**In 1-2 sentences, explain the problem statement: e.g "This dataset contains data about... we seek to predict..."**
This dataset contains data about potential customers of a bank and their loan and finalcial history records. 
In our problem statement, we seek to predict weather an individual is likely to be a future customer i.e. is he/she an ideal candidate for our marketing campaign.

**In 1-2 sentences, explain the solution: e.g. "The best performing model was a ..."**
The best performing model was using Python-SDK and Azure Hyperdrive with accuracy of 91.01%. Azure AutoML also performed well with an accuracy of 88.9 %

## Scikit-learn Pipeline
**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**
Pipeline Architecture: 
Data: The data used is bank-marketing data. It is a list of bank-customers along with their information(features) such as gender, marital_status, education etc.
Final number of features after data cleaning and creating dummy variables from given categorical variables is 39. Target variable is "y"; It is a binary variable signifying sucess(1) and failure(0).

Classification Algorithm: 
Clearly, this is a classification problem. The model used for the Python SDK experiment is a Logistic Regression. It is one of the most basic and powerful algorithms for classification problems in machine learning.

Hyperparameter tuning:
Two hyperparameters were tuned for training:
1. C: Inverse of regularisation strength. Decresing value signifies greater regularisation strength.
This value must always be positive ( default=1). For our tuning, we used uniform(min,max) which specifies a uniform distribution between min and max values from which random values are chosen.
2. max_iter: this specifies the maximum number of iterations that the logistic regression model will run before arriving at the best possible set of hyperparameters. 


**What are the benefits of the parameter sampler you chose?**
Among the random sampler and the grid sampler, I have chosen the random sampler for this dataset. 
The main reason for choosing random sampler in this case is that it randomly selects a few combinations of parameter settings allowing us to save time and resource cost for training the model with little differnece in accuracy.
It gives support for both continuous and discrete hyperparameters.

**What are the benefits of the early stopping policy you chose?**
from among three early stopping policies available in azureml library, I chose the Bandit policy for early termination. This policy utlizes the slack_factor to terminate the program early.
Slack factor is the ratio used to calculate the allowed distance from best performing experiment run.


## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML.**
The best model generated by Automl in azure was LightGBM.
Hyperparameters generated by automl are 

## Pipeline comparison
**Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one?**


## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**
Future imrovements: 
1. For goal_metric, AUC is another very important metric to measure model performance. Evaluating model performance with this metric and maximising this in hyperdrive runs as well as auto-ml runs will give new insights into the model.
2. These improvements will help the model 
