# Term_Deposit_Marketing
**INTRODUCTION**

We are a small startup focusing mainly on providing machine learning solutions in the European banking market. We work on a variety of problems including fraud detection, sentiment classification and customer intention prediction and classification.

We are interested in developing a robust machine learning system that leverages information coming from call center data.

Ultimately, we are looking for ways to improve the success rate for calls made to customers for any product that our clients offer. Towards this goal we are working on designing an ever evolving machine learning product that offers high success outcomes while offering interpretability for our clients to make informed decisions.

**Data Description**:

The data comes from direct marketing efforts of a European banking institution. The marketing campaign involves making a phone call to a customer, often multiple times to ensure a product subscription, in this case a term deposit. Term deposits are usually short-term deposits with maturities ranging from one month to a few years. The customer must understand when buying a term deposit that they can withdraw their funds only after the term ends. All customer information that might reveal personal information is removed due to privacy concerns.

Goal(s):

Predict if the customer will subscribe (yes/no) to a term deposit (variable y)

Success Metric(s):

Hit %81 or above accuracy by evaluating with 5-fold cross validation and reporting the average performance score.

Current Challenges:

We are also interested in finding customers who are more likely to buy the investment product. Determine the segment(s) of customers our client should prioritize.

What makes the customers buy? Tell us which feature we should be focusing more on.

REPORT 
1. Data Cleaning and Missing Value Handling

A thorough analysis confirmed that none of the original variables contained missing values.

2. Data Preprocessing
   
•	Feature Encoding:
o	Label Encoding was applied to nominal categorical variables.
o	One-Hot Encoding was used for ordinal categorical variables.
•	Feature Scaling:
o	StandardScaler was applied to continuous variables with a Gaussian distribution and a low proportion of outliers.
o	RobustScaler was used for variables with a significant number of outliers.
•	Class Imbalance Handling:
o	The Synthetic Minority Over-sampling Technique (SMOTE) was implemented to balance the target variable (y).
o	The minority class (y=1, indicating subscription) was highly underrepresented, so we performed upsampling to generate X_smote and y_smote.

3. Exploratory Data Analysis (EDA)
   
•	A univariate analysis was conducted using boxplots and histograms to guide the selection of appropriate scaling techniques.
•	The target variable (y) showed strong linear correlation only with the duration feature.

4. Machine Learning Models
   
Several classification algorithms were tested, including Logistic Regression (4.1.1, 4.1.2, 4.1.3, 4.1.4) , Decision Trees – CART (4.2.1, 4.2.2 and 4.2.3), K-Nearest Neighbors or KNN (4.3.1 and 4.3.2) , and XGBoost (4.4.1, 4.4.2 and 4.4.3). Models were evaluated under three different scenarios:
1.	Using X_before_SMOTE, the dataset obtained after encoding and scaling but without applying SMOTE.
2.	Using X_smote, the dataset obtained after applying SMOTE to balance the target classes.
3.	Applying SMOTE and Feature selection (using a feature selection subset derived from X_smote).
KNN with K=3 achieved a good performance for the minority class (y=1, subscribed) when using the balanced dataset (y_smote). The model achieved an F1-score of 0.70 for the minority class.
Through hyperparameter optimization of XGBoost trained on the X_smote dataset (balanced classes), a significant improvement in Recall and Precision for the minority class was achieved compared to previous models (4.4.1 and 4.4.2). The model now demonstrates excellent performance in predicting the minority class (𝑦=1), achieving an F1-Score of 0.95, which indicates a more than acceptable balance between Precision and Recall for this class.

The XGBoost with optimization of hyperparameters is most robust machine learning model to predict the target, solving the problem to predict minority class.

