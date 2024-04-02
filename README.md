# credit-risk-classification Module 20 Challenge Assignment

## Overview of the Analysis
The purpose of this analysis is to create a model which can correctly predict the incidence of fraudulent loan applications within a population of loan applications.  The model assesses a dataset consisting of the following applicant features or variables when determining the likelihood of a loan being fraudulent:  
- loan size - in dollars
- interest_rate 
- borrower income - annualized in dollars
- current debt to income ratio
- number of accounts 
- the number of derogatory credit bureau marks the applicant has accrued
- total debt in dollars
- current loan status - 0 = healthy loan, 1 = fraudulent loan. this element became the dependent variable of the model used to both train the model and test its accuracy.

## Approach
1. The data was split into independent (X) and dependent (y) subsets.  The dependent set (y) consisted of the current loan status.  The remaining elements were used as independent features for training and testing the model.  
2. Both the independent X and dependent y datasets were split into two additional subsets one for training the model and one for test then model. 75% of the data was used for training and 25% was reserved for testing the final model.
3. In order to remove any imbalance in feature influence in the model, the independent training data was used to create a scaling factor which was applied to both the independent training and independent testing data.
4. After scaling, 75% of the independent variable data was used to train the model, the remaining 25% was used to test the model.
5. The resulting data was then assessed with three modelling approaches:
   - Logistic Regression
   - Support Vector Machine
   - [Decision Tree](https://github.com/john-a-ellis/credit-risk-classification/blob/main/Resources/loans_tree.png)
  

## Results
            LogisticRegression      Support Vector Machine       Decision Tree
`Precision:        .84                         .84                     .84`  
`Recall:           .98                         .98                     .85`  
`f1-score:         .91                         .91                     .85`  
`accuracy:         .99                         .99                     .99`  

                    


## Summary
The three models yielded relatively consistent results, with the Logistic Regression and Support Vector Machine models having identical results, only the decision tree model had a slightly weaker recall ability. Given the results the Logistic Regression model is recommended due to the ease of implementation and interpretation.

## Chosen Model Logistic Regression Model
        	Predicted Healthy-0	Predicted Fraud-1
`Healthy-0	       18652	            113`  
`Fraudulent-1	      10	            609`      
`Accuracy Score : 0.9936545604622369`  

                        Classification Report
              precision    recall  f1-score   support

           0       1.00      0.99      1.00     18765
           1       0.84      0.98      0.91       619

`    accuracy                           0.99     19384`  
`   macro avg       0.92      0.99      0.95     19384`  
`weighted avg       0.99      0.99      0.99     19384`  

At first glance the model appears to be very good at predicting loan health given the 99% accuracy.  However upon closer look this accuracy appears to be greatly influenced by the in-balance in the tested dataset where just over 3% of the observations were fraudulent.  Looking closer we see the model predicted 722 fraudulent loans, but only 609 of these loans were actually fraudulent, for a precision of 84.3%.  Conversely, the model correctly predicted a loan as being fraudulent 98% of the time, 609/619. As a result, if we were to use the model in a production environment using it to predict if a loan is likely to be fraudulent this is a good model.  The risk of model error lies in falsely identifying fraud when none exists which may happen in 16% of the cases.  But the financial implication of this (ie lost business) is offset by the fact it can correctly identify fraud 98% of the time, reducing the risk of writing loans which are unrecoverable due to fraud.  If attempts were to be made to improve the accuracy of the model for identifying healthy loans, care would have to be taken to ensure not to compromise the ability of the model to identify fraudulent loans thereby increasing costs overall. 
