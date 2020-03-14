## Introduction
Banks exist to provide monetary services to people and to make profit. With that in mind, banks devote significant resources and activity to gain capital. One way banks do this is to engage in direct marketing campaigns to sell and provide services. This data set contains result of a Portuguese Bank direct marketing campaign to sell term deposits.

## Problem Statement
The first objective was to classify if the client would subscribe to term deposit or not and to determine which variables have the highest influence on term deposit purchase

Data The Data Set is the Portuguese Bank Marketing Data Set in the University of California, Irvine (UCI) Machine Learning Repository located at the following URL: https://archive.ics.uci.edu/ml/datasets/Bank+Marketing. The data is a result of a direct marketing campaign performed by a Portuguese banking institution to sell term deposits/certificate of deposits. The banking institution made phone calls to potential buyers from May 2008 to November 2010. Often, more than 1 contact to the same client was required to assess whether a client would place an order. The full data set, bankadditional-full.csv, was used. There are 41,188 observations and 21 Variables in the Data Set. There are 10 continuous measure variables and 10 categorical variables. The target response (y) is a binary response indicating whether the client subscribed to a term deposit or not. ‘Yes’ (numeric value 1) indicated the client subscribed to a term deposit. ‘No’ (numeric value 0) indicated the client did not subscribe to a term deposit.The variables are broken into 4 categories: Client Data, Last Contact Info, Other, and Social and Economic Variables.

## In general, datasets which contain marketing data can be used for 2 different business goals:
1.	Prediction of the results of the marketing campaign for each customer and clarification of factors which affect the campaign results. This helps to find out the ways how to make marketing campaigns more efficient.
2.	Finding out customer segments, using data for customers, who subscribed to term deposit. This helps to identify the profile of a customer, who is more likely to acquire the product and develop more targeted marketing campaigns.

## 	Initial Findings about Data:

1.	The Data Set is the Portuguese Bank Marketing Data Set in the University of California, Irvine (UCI) Machine Learning Repository located at the following URL: https://archive.ics.uci.edu/ml/datasets/Bank+Marketing.
2.	The data is a result of a direct marketing campaign performed by a Portuguese banking institution to sell term deposits/certificate of deposits.
3.	There are we have 41188 observations of 21 variables in original dataset (10-Numerical Variables and 10-Categorical Variables). The target response (y) is a binary response indicating whether the client subscribed to a term deposit or not. ‘Yes’ (numeric value 1) indicated the client subscribed to a term deposit. ‘No’ (numeric value 0) indicated the client did not subscribe to a term deposit.
4.	The variables are broken into 4 categories: Client Data, Last Contact Info, Other, and Social and Economic Variables.
5.	 No explicit missing values but there are many ‘unknowns’ values for some Categorical Variables that will be treated as missing values. 
6.	From the distribution of Target variable: "is_success" it is found that data is imbalanced because there is approx. 88% is 'no' and 12% is 'yes'. 

##  Exploratory Data Analysis and Data Cleaning

The variables are broken into 4 categories: Client Data, Last Contact Info, Other, and Social and Economic Variables. I have performed EDA on each category separately to get a better picture

A. For Numerical Variables 
1. Analysis of each Numerical variable by plotting Boxplot with respect to target variable. 
2. Some Independent numerical variable ('balance', 'duration', 'campaign', 'pdays', 'previous') contains many outliers. 
3.I choose a range based on formula (Q1+- 1.5IQR) . Any value out of this range will be treated as Outlier and If there were more than 5% same will be imputed by Mean of corresponding variable.

B. For Categorical Variables 
1. Analysis of each Categorical variable by plotting Crosstab with respect to target variable.
2. If any Categorical variable has more than 50% unknown values or seems highly unbalanced, we can drop that variable from dataset. If unknown values are less than 50% than we can replace them by Mode of respective variable.

## Feature Engineering

For Variables which have more unique different values 
1. Plot Boxplot, count plot and selected the intervals to create groups and encoded them accordingly.
2. After EDA’s of all four parts I concat the data and made final data which was having all encoded variables.
4. Model Training 
1. Classes are imbalanced, and the ratio of no-subscription to subscription instances is 88:12 so I used SMOTE to make balanced Classes.
2. Implement Logistic Regression, K-Nearest Neighbor, Decision Tree, Random Forest , Naive Bayes along with Cross Validation, confusion matrix and AUC-ROC curve 


## Model Selection 
1. "Random Forest " has highest Accuracy ( 94.98%) but it is taking more time compare to other algorithms. 
2. “K nearest neighbor” has accuracy (91%) and "Logistic Regression" has (85 %) and it is very faster than Random Forest. 
3. F1 score of Logistic is 0.54 where as F1 score for KNN is 0.49 
4. So I have considered Logistic Regression  as Best model for prediction. 


## Prediction 
1. Prediction on Validation Dataset by Logistic Regression with following result: 
	 Accuracy -  0.85
	 F1- score  - 0.54

## Feature Importance
The most important features are:
Customer's account balance, Customer's age, Number of contacts performed during this campaign and contact duration, Number of contacts performed before this campaign.

## Outcomes of the modelling are:
1.	Customers of greater age are more likely to subscribe for the term deposit. Future campains should concentrate on customers from age categories below 30 years old and above 50 years old.
2.	Customers with greater account balance are more likely to subscribe for the term deposit. People with account balance above 1490$ are more likely to subscribe for term deposit, so future address those customers.
3.	Number of contacts with the customers really matters. Too many contacts with the customer could make him decline the offer. The number of contacts with the customer shouldn't exceed 4.
