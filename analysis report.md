# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.

    The purpose of this analysis is to build a logistic_regression model that can learn to tell if a bank loan is healthy or high-risk. It will be very useful for the bank to avoid edgy loan applications. 

* Explain what financial information the data was on, and what you needed to predict.

    The dataset shows the borrower's "loan_size","interest_rate", "borrower_income", "debt_to_income", "num_of_accounts", "derogatory_marks","total_debt". The feature we need to predict is called "loan_status", which is a binary field, 0 stands for healthy loan, while 1 is high-risk loan.

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).

    The dataset has a total of 75036 negative (0) cases, and 2500 positive (1) cases. Therefore, this dataset is extremely imbalanced.

* Describe the stages of the machine learning process you went through as part of this analysis.

    stage 1, data preprocessing - separate the labels from the training dataframe, so the "loan_status" column is saved to variable y, and the original dataframe will drop this column and save to X.

    stage 2, feature engineering - split the data using the train_test_split function from scikit-learn libray and scale the X train and X test data using the StandardScaler class.

    stage 3, model selection - initiate a logistic regression model and train it with X train, y train data. 

    stage 4, prediction and evaluation - test the trained model, and check accurary score, confusion matrix, classification report by comparing the real data to predictions.

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any other algorithm).

    I choose Logistic Regression model, because it is a function for binary classification. For example, the sigmoid function will give a probability between 0 or 1. That will tell us if the predicted case is true or false. Thus, it is very useful in this bank loan case. 

## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
    * Description of Model 1 Accuracy, Precision, and Recall scores.

    1. the accuracy score is 0.9936545604622369, which means that roughly 99.37% cases are predicted corrected. However, it might not be the best indicator in this case, because the original dataset is very imbalanced. It is calculated by using total corrected predictions / total predictions

    2. the model has a prescision score of 1.0 on negative (0) cases, , which is calculated by using True Negatives / (True Negative + False Negatives); but only 0.84 on positive cases (1), which is calculated by using True Positives / (True Positives + False Positves). This score tells us that the model is good at predicating negative cases, but is not as good at telling positive cases.

    3. the model has a recall score of 0.99 on negative (0) cases, , which is calculated by using True Negatives / (True Negative + False Positives); and 0.98 on positive cases (1), which is calculated by using True Positives / (True Positives + False Negatives). Both scores are high, which means the model is good enough to be in a situation where the misclassification costs are. Therefore, the model can be reliable if it is trained properly.

## Summary

Summarise the results of the machine learning models, and include a recommendation on the model to use, if any. For example:

* Which one seems to perform best? How do you know it performs best?

    The logistic regression model is good at predicating negative cases, but is not as good at telling positive cases. This conclusion is based on the precision score. And based on the confusion matrix, the model made too many false positive cases. 

* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

    It is more important to predict the high-risk loans (1), so the performance of this model is actually reliable, since it has a 0.98 recall score on positive cases. Out of 19384 cases, it only reported 10 false negative cases, that can be considered reliable I believe. The only downside of this model is that 16% of its positive predictions are false, which is not that a big deal in this situation because it is rather easy for the bank the review the false positive cases, but it is almost impossible to find out the false negative cases. Since the original dataset is imbalanced, the model can improve further, so it will be more and more reliable if trained properly. 

If you do not recommend any of the models, please justify your reasoning.
