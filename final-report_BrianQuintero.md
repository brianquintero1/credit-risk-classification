# Module 12 Report Template

## Overview of the Analysis

<!-- In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.     
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any other algorithms). -->

The purpose of the analyis is to create a data model that is accurate enough to predict the creditworthiness of potential borrowers at a peer-to-peer lending company. The financial information was provided in a csv file containing 77,536 records and distributed among 8 columns. The target variable was the loan_status column and the remaining seven columns were the factors considered in the analysis. The seven columns in the y variable described these loan attributes:

    1. Size of loan (loan_size)
    2. Interest rate for loan (interest_rate)
    3. Borrower's income (borrower_income)
    4. Debt-to-income ratio (debt_to_income)
    5. The number of accounts possessed by the borrower/customer (num_of_accounts)
    6. Any derogatory marks against the borrower (derogatory_marks)
    7. The customer's total debt (total_debt)

The process started with an analysis of historical data, followed by identifying the target y variable and the features which are stored in the x variable. After this, the data was split into training and testing data sets with an assigned random state of '1'. Next, the logistic regression model was created by fitting a logistic regression model using the training data. Finally, we evaluated the model's performance by generating a confusion matrix and printing the classification report. The modules, submodules, and classes used to accomplish important machine learning tasks were these:

sklearn.linear_model.LogisticRegression

sklearn.metrics.classification_report

sklearn.metrics.confusion_matrix

sklearn.model_selection.train_test_split


## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
    * Description of Model 1 Accuracy, Precision, and Recall scores.

    * Accuracy: This model's accuracy was 99%.
    * Precision: The model's precision is measured by looking at its precision for the two different types of loans, based on the target variables. Low risk loans had a precision of 100% and high risk loans had a precision of 87%. Looking at the weighted average precision, we see a 99% precision. This weighted average is highly influenced by the fact that the data was not resampled to account for the imbalance presented by the uneven distribution of the target variable: Low Risk loans were = 18759 and high risk loans = 625.
    * Recall scores: similar to Precision, we evaluate the recall scores by looking at each target variable. Low risk loans had a recall score of 1.00 while high risk loans had a recall score of 0.89. These values provide more of an insight into performance class rather than the overall model.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:

* Which one seems to perform best? How do you know it performs best?
    This exercise only looked at a single machine learning model. The next step after this, in order to conclude the model, is to perform a second logistic regression model using resampled training data. We could use the imblearn.over_sampling module to upsample the High Risk loans in order to create synthetic data in order to make both labels have around 18759. In this case we prefer to oversample rather than scale down the low risk loans in order to have more records with which to train and test the model.
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )
    Low-risk (healthy) loans = 0 and High-risk loans = 1. The problem we are trying to solve is to identify which loans would produce high risk loans = 1. It is more important to identify the 67 false negatives than to identify 80 false positives because if we miss any false negatives then we will have originated 67 high risk loans.
    

If you do not recommend any of the models, please justify your reasoning.
