# BostonHousingDataset-EDA-and-Regression
Predicting house price values of Boston using Regression (Linear and Polynomial)

The Boston Housing dataset has various features about the locality and the target value is the median value of a house in the locality. 


The analysis finds features that may be correlated, features that seem more important than others, and any meaningful relationships between features. 


These results can be used in feature engineering to develop more suitable features for modelling the data, or removing irrelevant features.

### Final Inferences (can be used in Feature Engineering)

Median value seems negatively correlated with lower status of the population. (Lower status of population => lower the median value)

Median value is positively correlated with avg rooms ==> avg rooms is an important feature.

Lower status of population is highly correlated with other features like:
    - avg rooms : lower the status, lesser the rooms
    - nox : lower the status, higher the nitrogen oxide concentrations (pollution)
    - non retail business: lower the status, more non retail businesses in the locality.

Avg rooms is almost uniformly distributed. Other features will have to be scaled.

### Feature selection for regression analysis.

The feature median value is not normally distributed. 

![Image of Yaktocat](https://static.wixstatic.com/media/c87105_e1a2823a028c440ea6264f9ed6a527b9~mv2.png/v1/fill/w_740,h_373,al_c,lg_1,q_90/c87105_e1a2823a028c440ea6264f9ed6a527b9~mv2.webp)

The houses with median value as 50 seems like an outlier. I will remove all rows with median value = 50 so it does not negatively affect our regression model. 

![Image of Yaktocat](https://static.wixstatic.com/media/c87105_7d13845e726a46e3b5a634fef0ad714e~mv2.png/v1/fill/w_740,h_200,al_c,q_90,usm_0.66_1.00_0.01/c87105_7d13845e726a46e3b5a634fef0ad714e~mv2.webp)

The final plot of median values in our data is as shown below. It is closer to normal distribution now. 

![Image](https://static.wixstatic.com/media/c87105_dbdc93c6501e474084e94c61f6a92d8a~mv2.png/v1/fill/w_740,h_241,al_c,q_90,usm_0.66_1.00_0.01/c87105_dbdc93c6501e474084e94c61f6a92d8a~mv2.webp)

Feature Analysis

So, I wanted to find the features correlated with median value of prices in a neighborhood. 


It was clear from the heat map and correlation matrix that lower status and average number of rooms in a neighborhood. 


Although correlation does not imply causation, we can safely assume by general knowledge that more number of rooms in a house will mean higher price, and the prosperity of the neighborhood will also positively affect the prices in the neighborhood. 


Hence, we choose avg_rooms and lower_status as our independent variables (X).

median_value is our dependent variable (y).


We split the training and testing data set using sklearn's train_test_split function.

#### Linear Regression 

We first try to predict the house prices using linear regression. 

##### Testing: Linear Regression 

On training data, the linear model gave an R2-Score of 66.3 %
For testing data, the R2 Score is 68% percent. 

Hence, although our linear model doesn't overfit the data, it still isn't very accurate. 


The dependent variable may be dependent on the independent parameters in some polynomial fashion. Thus, we can try polynomial regression of various degrees. I will first look at degree 2. 


#### Polynomial Regression

I converted the current features into polynomial features, and fit the transformed features to linear regression.

##### Testing: Polynomial Regression

Thus, for training data, the R2 score of the polynomial regression model is higher, 80.5 %


For testing data, the R2 score is 80.2 %.

Thus, polynomial regression with degree 2 achieves a higher R2 score and lesser error to predict the median value of houses. 
