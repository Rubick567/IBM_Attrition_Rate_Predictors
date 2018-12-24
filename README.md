# IBM_Attrition_Rate_Predictors
A Study of Attrition Rate Predictors at IBM through Machine Learning algorithms and methods
## Source of Data set
This is a fictional data set created by IBM data scientists. I acquired the data set from a
kaggle competition: https://www.kaggle.com/pavansubhasht/ibm-hr-analytics-attrition-dataset
## Models
Five machine learning models were applied to fit the data set: GLM, LDA, QDA, KNN and RandomForest(Boosted by gbm & SMOTE methods)
## Data Processing
### Exploratory Data Analysis
Three brief conclusions can be drawn from the analysis:
* A majority of the employees who have attrition issues come from the relatively low-MonthlyIncome groups
* Employees from the high attrition rate are generally complaining about the bad worklifebalacne and far distance from their home to work
* There is a also high correlation between OverTime and Attrition
### Model fitting
The main processes of this part are:
* Data Cleansing:  Scaling, ommitting the nulls, simplifying and getting rid of the colums we were not interested(such as Employee Count, Employee Number, Over18 and StandardHours which are all constants and will not influence the model even if we delete them)
* Find the proper variable set:  A process of selecting the predictors suitable for the training models with a comprehensive consideration combining the results from the 'varImp' function and glmulti
* Fitting the data set:  Although I was basically using the glmuti and randomforest for variables subsetting, I still trained them to make predictions and recorded the results from model comparisions later on. Once I had got my "Best-Set" predictor set, I plugged them into LDA, QDA and KNN to check how they performed on those models.
* Comparing the models: For comparision among LDA, QDA and GLM models, graphing ROC curves and computing AUC value respectively would be a good idea. However, since I wanted to compare all of the predicting models so far(RF, GLM, LDA, QDA, KNN), I calculated the Overall Error Rate and Power of these models for comparision
* Results:  In terms of the Overall Error Rate, the KNN model was doing the best with an error rate of 0.1014 while the QDA model achieved the highest predicting power(0.4545)
## Conclusions & Recommendations
### Model Selection
It depends. We are always facing the trade-off between the Type I and Type II error rates. For example, in this case if we want to achieve a higher precitive power of the model, we have to face more false positives. On the contrary, the lower predictive power means that the model is doing better overall but making more Type II errors. From this specific business standpoint, we are probably more interested about endowing the model more powers. Since the employees with attrition issues are usually a minority part of the staff in the company and our null hypothesis is that the employee has "No" Attrition problem, focusing on the Type II errors and the Power(Predicting "Yes" when the employee is actually leaving the company) makes more sense for the company in order to estimate the costs of hiring accurately and design retention packages to keep the employees they want.
### Improvements
Still, more data is required in order to improve the problem of oversampling in the origin data set in which there was an overwhelming number of "Yes" in the Attrition than "No"(that's why, in my opinion, the models are always doing better in avoiding Type I errors than the other). In addition, equipping the models with simulation and optimization- tune parameters is also approvable and will make the model even more practical and precise.

