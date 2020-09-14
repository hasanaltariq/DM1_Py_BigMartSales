# Sales Prediction (Big Mart)


## Problem Statement
Find out the sales of a product at a particular store. Data-set used here is the “Big Mart Sales” data, taken from [Analytics Vidhya](https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/).


## Understanding the problem
It seems the data-set is the result of a query over two relations namely “Items” and “Outlets” with following schema:
> Items {Identifier, Weight, Fat_Content, Visibility, Type, MRP, Sales ($)}. 

> Outlets {Identifier, Establishment_Year, Size, Location_Type, Type}. 

The target variable is “Item_Outlet_Sales” representing the sales amount of an item on a particular outlet to tag the outlet information with the item sales information. There are 1559 different items which were sold on 10 different outlets. We can assume that an item let’s say “CocaCola” is sold on multiple Outlets. But the combination of Item_Identifier and Outlet_Identifier makes every record in the Data-set distinct.

The goal is to predict future sales of an item or product at a particular Outlet.

If we had only one item with multiple features (independent variables) to predict it’s future sales, we could have used regression to estimate the unknown future value. Or, if we had target variables with categorical values like “will be sold – Yes” or “will be sold – No” etc. we could have used classification methods to predict some defined set of outputs. But sales amounts are continuous numbers and can be within 0 to infinity.

We can do regression for each of these 1559 items, based on the item features as well as the features of the Outlet where it was sold and make prediction of estimated sales amount.

We can create two new features such as “Units_Sold” from {Item_Outlet_Sales / Item_MRP} and “Outlet_Age” from {Present year - Outlet_Establishment_Year}.


## Assumptions
Based on our knowledge, we can make some assumptions like:
- Item sales would be high at large stores, so Outlet_Size can be an important feature.
- Item sales would be high at large cities, so Outlet_Location_Type can be an important feature.
- Item sales would be high if it is cheap, so MRP can be an important feature.
- Item sales would be high if its fat content is low, so Item_Fat_Content can be an important feature.
- Item sales would be high if it’s clearly visible, so Item_Visibility can be an important feature.


## Result

|Measurement criteria |Linear Regressor |Decision Tree Regressor |Random Forest Regressor |
| ------ | ----- | ------ | ------ |
|RMSE |542.2 |323 |292.7 |


## Methodology
1. Exploration
    - Duplicates
    - Missing
    - Data types
        - if categorical then group by categorical values
        - if numerical then statistical values (description)
    - Exploring outlet size in relation to outlet type and location
    - Average weight of each product
    - Exploring categorical variables

2. Pre-processing
    - Imputing missing values
    - Correcting value errors
    - Fixing zero visibility

3. Feature engineering
    - New feature creation
        - Outlet_Age
        - Item_UnitsSold
        - Reducing 16 item types into three broad types
        - Redistributing item fat content (non-edible item does not have fat content)

4. Processing
    - Numerical conversion of Categorical variables for ML
    - Dropping unnecessary variables 
    - Creating dummies for categorical variables
    - Train test split

5. Model building & testing
    - Standard regression methods: Linear and Decision Tree Regressor
    - Ensemble method: Random Forest Regressor


## Performance Measurement Criteria
    Root Mean Squared Error (RMSE)


## Requirements
    Python 3.8, (Jupyter Notebook), pandas-1.1.1, numpy-1.19.1, scipy-1.5.2, scikit-learn-0.23.2, matplotlib-3.3.1


### Resources that were helpful:

[1](https://www.analyticsvidhya.com/blog/2016/02/bigmart-sales-solution-top-20/)

[2](https://medium.com/analytics-vidhya/bigmart-dataset-sales-prediction-c1f1cdca9af1)



## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.




## License
[MIT](https://choosealicense.com/licenses/mit/)



