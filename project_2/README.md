# Project 2: Ames Housing Data and Kaggle Challenge
-------

## Problem Statement
As part of a team of analysts in a property consultancy agency, which service home buyers/sellers in buying/selling houses for flipping investment purposes, the project aims to explore existing dataset and build a 'Predicting Property Price' (PPP) model that predicts the price of houses in Ames to narrow the gap between the desired selling/buying price of sellers/buyers, resulting in more successful transanction and income for the agency. The model, using linear, ridge or lasso, should serve the following function:
1. Support potential buyer/seller in analysing home prices, based on budget and preferences. 
2. Provide seller advice on features for renovation to sell the property at a higher price. 
3. Provide a reference for seller/buyer to verify if the price offered is above or below the expected price.

The model will be evaluated based on the Root Mean Squared Error (RMSE), which measures the differences between the true selling price and the predicted selling price. The project recommends the models with the lowest RMSE will be proposed to the Senior Management Team for adoption and equipping of all consultants in the agency. 

## Executive Summary

Property sale price is dependant on past comparable sale transanction. With the given data set, this project conducted data cleaning and imputed significant amount of missing data, while preserving the integrity of the data in order to develop an accurate predicting property price model. Thereafter, the data consisting of 80 features were categorised into four data types: Nominal, Ordinal, Continuous and Discrete. 

Exploratory Data Analysis was conducted to understand the features and their relation with the sale prices. Findings from the analysis were used to conduct the preliminary selection of features or re-categorise features. This would reduce the multi-collinearity of features and complexity of the model to be generated. As a result, the final data set has 65 features before One Hot Encoding (OHE) and 75 features after OHE. 

A baseline model using linear regression was built as a reference to evaluate subsequent models developed using Root Mean Squared Error (RMSE). After a few iterative process, the model with the lowest RMSE was selected and proposed to the senior management for adoption and implementation.

The final model, Ridge Model 5, has a total of 50 features. It has achieved a low RMSE of 24839 (about $25k difference between predicted sale price and true sale price) and able to explain 90% of the variability in the Sale Price. 

The model also identified the top 5 features, in terms of absolute coefficients, that has significant effect on sale price. They are 1stFlrSF, ExterQual_OverallQual metric, 2ndFlrSF, BsmtFinSF1_BsmtFinType1 metric and Neighborhood_UpperQuan. 

The model will help buyer/seller to consider the total cost of buying and selling the property and adjusts their requirements accordingly, e.g. buy a poor quality property then renovate to increase its valuation or buy a good quality property with minimal renovation needed. 

It also serve as a tool to provide a reference price to both seller and buyer so that both may agree on a common price. 

## Data Dictionary

Data Dictionary was provided for this project. Refer to data dictionary [here](https://www.kaggle.com/competitions/dsi-us-11-project-2-regression-challenge/data).

## Overview of all models

|Model|Description|Value of $\alpha$|Related Model|Training RMSE|Testing RMSE|Training Cross Validation RMSE|
|-|-|-|-|-|-|-|
|<center>Model 1 (lr_base): <br />Simple Linear Regression Model|<center>NA|<center>NA|<center>**Baseline Model**|<center>28446|<center>27062|<center>33517|
|<center>Model 2 (ridge_base): <br />Ridge Model|<center>NA|<center>335|<center>NA|<center>29084|<center>27557|<center>31493|
|<center>Model 3 (lasso_base): <br />Lasso Model|<center>NA|<center>534|<center>NA|<center>28830|<center>26463|<center>31961|
|<center>Model 4: <br />Ridge Model|<center>With outliers removed, <br />Zero Lasso Coefficient features removed|<center>266|<center>Model 2|<center>24354|<center>25070|<center>25825|
|<center>Model 5: <br />Ridge Model|<center>Engineered new features, <br />Zero Lasso Coefficient features removed|<center>23|<center>Model 4|<center>23463|<center>24280|<center>24840|
    

## Evaluation
1. Of all the models created, Model 5 (Ridge Model) performed the best based on the lowest Training Cross Validation RMSE of 24840. This is a significant improvement from the Model 1 (Baseline Model), with a reduction of about 8700 RMSE (26% reduction).
2. The difference in the testing and training RMSE also reduced from about 1400 (Model 1) to about 800 (Model 5) (40% reduction).
3. The model has a Training Cross Validation $R^2$ score of 90%. This means that 90% of the variability in SalePrice is explained by the features in Model 5.
4. The top 5 features in terms of absolute coefficients are `1stFlrSF`, `ExterQual_OverallQual` metric, `2ndFlrSF`, `BsmtFinSF1_BsmtFinType1` metric and `Neighborhood_UpperQuan`. This means that the price varies significantly with these features. For example, an increase in 1 $????????^2$  in first floor area corresponds to an increase in sale price of \$22,046, holding all else constant.
5. The improvement in the accuracy of the model is likely due to reduction in multi-colinearity in the model and eliminating of redundant features(features with zero or near zero coefficient), resulting in lower biasness and higher variance. 
6. It is recommended that Model 5 is the best Predicting Property Price model of all the models and will be proposed to the senior management to equip all consultants. 
7. LINEM assessment.
    - **Linear Relationships**: 
        - As seen from the scatterplots of individual features, there is a linear relationship with SalePrice in general.
    - **Independ error:** 
        - It is assumed that the errors are independent.
    - **Normally distributed errors**: 
        - It is observed from the histplot of residuals against frequency that the residual's are somewhat normally distributed around 0. 
    - **Equal variance of errors:** 
        - In the scatterplot of residual against predicted sale price, it is observed that range of error have equal variance up to about \$330k sale price and diverge slightly with increasing predicted sale price. This is likely due to the lack of data with higher sale price in the training set (refer to the boxplot for SalePrice).
        - The model is assessed to be accurate in predicting houses up to about S$330k.
    - **Multicollinearity/Independence of Predictors** 
        - Based on the heatmap, only one pair of features(`KitchenQual_ExterQual` and `ExterQual_OverallQual`) exhibits high correlation (>0.7). It is assessed that the predictors are mostly independent.

## Proposed Predicting Property Price Model: Model 5

The project proposed the adoption of Model 5 to the Senior Management Team of the agency.
1. The model has significant coefficient(change of more than \$5000 in saleprice against an unit change in the features) for last than 10 features despite having 50 features.
2. The model has a low RMSE (about \$25k between predicted price and true price). 
3. The features in the model is able to explain up to 90% of the variability in SalePrice.
4. The top 5 features in terms of absolute coefficients are `1stFlrSF`, `ExterQual_OverallQual` metric, `2ndFlrSF`, `BsmtFinSF1_BsmtFinType1` metric and `Neighborhood_UpperQuan`. This means that the price varies significantly with these features. 
    - Looking at the top 3 features, it is evident that the bigger the property (1stFlrSF and 2ndFlrSF, as well as BsmtFinSF1_BsmtFinType1) will likely have a higher selling price. Seller of such house should renovate it so that the ExterQual and OverallQual are good to increase selling price.
    - It is an added bonus if the house is located in neighborhoods where median selling price is above the 75% quantile of the selling price distribution. They are: 'ClearCr', 'GrnHill', 'NoRidge', 'NridgHt', 'Somerst', 'StoneBr', 'Veenker'.  

## Future Work to Improve Accuracy (Reduce RMSE) of the Model
1. The range of error have equal variance up to about \\$330k sale price and diverge slightly with increasing predicted sale price. This is likely due to the lack of data with higher sale price in the training set. Future work include gather data for sale price more than \\$330k to increase the accuracy of the model. 
2. Multi-colinearity in one pair of features: `KitchenQual_ExterQual` and `ExterQual_OverallQual` (high correlation of 0.91). In addition, both features have significant coefficient in the model. Further analysis should be considered in future work. 
3. Review of sub-categories in Nominal Data types as they seem to display notable coefficients. 
4. Analysis on sale price based on time. As the year sold was dropped after translating it into property age, the model does not take into consideration the trends in recent transanction. Property age was also subsequently dropped after Lasso assigned coefficient of zero to it.  

## Kaggle Submissions Result

![](./images/kaggle_score.png)
- Public:  28944.37892
- Private: 22833.12214

## 5. Conclusion

The solution to the buyer and sellers should be customised based on their desires and budget. 

The Ridge Model 5 developed in the project is able to explain 90% of the variability in SalePrice of past transaction and has low RMSE of about $25k between predicted price and true price. 
- It will help buyer/seller to consider the total cost of buying and selling the property and adjusts their requirements accordingly, e.g. buy a poor quality property then renovate to increase its valuation or buy a good quality property with minimal renovation needed. 
- It also serve as a tool to provide a reference price to both seller and buyer so that both may agree on a common price. 
- It also provide the significance of features which contributes to the sale price. The top 5 factors for buyer and seller to consider when buying/selling a house are `1stFlrSF`, `ExterQual_OverallQual` metric, `2ndFlrSF`, `BsmtFinSF1_BsmtFinType1` metric and `Neighborhood_UpperQuan`, which affect the sale price significantly.
