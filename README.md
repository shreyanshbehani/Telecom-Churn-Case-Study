# Telecom-Churn-Case-Study
Predicting Customers who will churn and not churn based upon the usage 

# Problem Statement 
In the telecom industry, customers are able to choose from multiple service providers and actively switch from one operator to another. In this highly competitive market, the telecommunications industry experiences an average of 15-25% annual churn rate. Given the fact that it costs 5-10 times more to acquire a new customer than to retain an existing one, customer retention has now become even more important than customer acquisition.
For many incumbent operators, retaining high profitable customers is the number one business goal.
To reduce customer churn, telecom companies need to predict which customers are at high risk of churn.
In this project, you will analyse customer-level data of a leading telecom firm, build predictive models to identify customers at high risk of churn and identify the main indicators of churn.

# Data Understanding and Approach
1. Data consist of various features showing the usage of voice and data services of a customer for four months june, july, august and september.
2. There are some features with high missing values we'll treat these missing values 
3. Some features have only one value 0 which should be remove as these features will become redundant while modelling.
4. Features attributed to total data recharge and avg data recharge is imputed with zero as we can conclude that the missing values in these columns are present because the customer haven't recharged or using data services.
5. For date columns we will use mode imputation technique and for other missing features we will be using iterative imputer which uses linear regression to impute the missing values in the data set.
6. It has been said that the in the telecom industry the 80% of the revenue is generated from top 20% of the customers so our business problem is to identify the churners and retain them if they belong to that 20% customer base.
7. To identify the top customers we will take the avg of the amount spend on the recharge by the customers in good phase and the ones whose average spending is above 70% quantile will be considered as the value customer.
8. Now to identify the churners, in the month of churn phase which is september, if there is zero voice and data services used by the customers we will tag them as churners 
9. For feature engineereing the averages of average revenue per month is taken, difference of avg attribute from good phase to action phase citing that if the usage is less the customer is going to churn and the number of days since last recharge is calculated from 1st of September if the number of days since las recharge is high we can conclude that the customer is going to churn.

# Modelling 
1. We have to make 2 models one which will check to predict if high value customers are going to churn or not and another one to determine what are the features through which the customers are churning 
2. PCA is used as a dimensionality reduction technique and with the help of scree plot we will able to find 55 prinicipal components features for our modelling
3. Logistic regression and decision trees are used for the modelling and logistic regression gave us better accuracy and sensitivity of 84% as compared to decision trees with 79% recall. 
4. For 2nd model to determine the variables causes churning, Recursive featutre elimination technique is used to filter out 20 important features which will be used for modelling.
5. After modelling the features with high p-value and high vif will be dropped and new model with remaining number of features will be created. 
6. We want to identify the churners correctly so we need high sensitivity rate, from plot of different probability vs accuracy, sensitivity and specificity we set our cutoff probability at 0.1, annyone above 0.1 probability rate will be tagged as a churner. Final accuracy on test set is .84 and sensitivity at 0.82.
