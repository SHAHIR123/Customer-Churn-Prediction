# Customer Churn Prediction in a Telecommunication Company

## USE CASE
In this project, we will create a model to predict customer churning (leaving) of a telecommunications company based on the data set containing details like customer demographics, their behaviour, and whether they end up churning. 


## DATA SET
The data set down loaded from watson analytics and can be dwonloaded from the belo link.  
"https://community.watsonanalytics.com/wp-content/uploads/2015/03/WA_Fn-UseC_-Telco-Customer-Churn.csv"

### Data Description
Dataset on customer demographics, their behaviour, and whether or not they end up churning (leaving). This data set provides info to help you predict behavior to retain customers. You can analyze all relevant customer data and develop focused customer retention programs. A telecommunications company is concerned about the number of customers leaving their landline business for cable competitors. They need to understand who is leaving. Imagine that you’re an analyst at this company and you have to find out who is leaving and why.

* The data set on customer churn includes information about:

* Customers who left within the last month – the column is called Churn

* Services that each customer has signed up for phone, multiple lines, internet, online security, online backup, - device      protection, tech support, and streaming TV and movies

* Customer account information- How long they’ve been a customer (tenure), contract, payment method, paperless billing, monthly charges, and total charges

* Demographic info about customers - gender, age range, and if they have partners and dependents

This data set was containing 7043 observation and 21 variables. Her we consider "Churn" as dependant variable and other variables as independant variables.

### Data Cleaing
We convert columns 'MonthlyCharges' and 'TotalCharges' to categorical. 
'TotalCharges' is object data type. So we have to convert to numeric data type and then categorize. Also some rows containing missing values as ' ' character. So we need to replace these rows with 'nan' and then fill with '0'.


## EXPLORATORY DATA ANALYSIS
We will drop columns like "customerID", "MonthlyCharges", "TotalCharges", "TotalCharges_num" as it not required for analysis and modeling.

### Chi-square Test of Independence using scipy.stats.chi2_contingency
We will check the relation ship of depndent variabel "Churn" against all other independent variables in the data set.
(The first value  is the Chi-square value, followed by the p-value , then comes the degrees of freedom, and lastly it outputs the expected frequencies as an array. if all of the expected frequencies are greater than 5, the chi2 test results can be trusted. We can reject the null hypothesis as the p-value is less than 0.05). 

Based on the chi-square test performed on the above features against the churn feature, we drop "gender" feature from the features selected for model. Because the as the p-value is higher than 0.05. So the null hypothesis is valid and there is no relationship for customer churning on customer "gender".


## MODELING
### Select Target Variable
We select "Churn" as target variable and encode the "YES" and "NO" responses to "1" and "0" values for the purpose of easy modeling.

### Select feature variables
We selected below variables as our features for model.
'SeniorCitizen', 'Partner', 'Dependents', 'tenure', 'PhoneService', 'MultipleLines','InternetService', 'OnlineSecurity', 'OnlineBackup', 'DeviceProtection', 'TechSupport','StreamingTV', 'StreamingMovies', 'Contract', 'PaperlessBilling', 'PaymentMethod','MonthlyCharges_cat', 'TotalCharges_cat'.

### Encode features for modeling
Here we use pandas get_dummies function to create dummy variable of the features.


## SPLIT DATA FOR TRAINING
We split data to training and test set to evaluate the accuracy of the model.


## MODELING
We tried with RandomForestClassifier and LogisticRegressionClassifier algorithms for modeling.


## EVALUATION
We got "76%" accuracy for RandomForest algorithm and '79%' accuracy for LogisticRegression algorithm. Logistic Regression algorthm is giving more accuracy. F1 score is also better with Logistic Regression Model.

This score is without any para meter turning. So further exploration is reccomended to achieve higher accuracy.






