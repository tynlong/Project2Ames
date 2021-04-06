## Overview
In this project, I worked with a dataset on the housing prices in Ames, Iowa from 2001 to 2007.

The goal was to predict housing prices in the test set accurately while creating a model which we could draw insights from.

Using the data in the training set, I created a Linear Regression model to predict housing prices on the test set.


## Data Cleaning
**MISSING DATA**
-Missing at random, or had very few rows: Dropped
-For values that it made sense to be connected to the area, such as Year Built and Garage Year Built, replaced with median neighbourhood values.

## Feature engineering
- Converted the "Quality" and "Condition" columns which rated different aspects of the house(Excellent,Very Good, Good, Fair, Poor etc.) into ordinal values
- Changed various categorical columns into one-hot-encoding
- Created aggregated columns such as 'Baths agg' to count the total number of bathrooms, counting half-baths as 0.5



## Feature selection 
For feature selection, I tried several different methods of selecting features, here are some of the strategies used:
- Dropping of one intercorrelated variables such as 'Year Built' and 'Garage Yr Built' to avoid collinearity
- Dropping variables with low correlation scores with housing price (for non-categorical, as categorical one-hot encoding makes variables have low correlation as their is low variability)
- Using the Lasso regression model, increasing the alpha until the desired number of predictors remain, then doing a polynomial relation between each variable, then lassoing the resulting variables. Even though this is used to reduce overfitting, it is a valid method of selecting features! It worked well and featured heavily in all of my final models.

## Different Methods and results

### Best Score but complicated model with 244 predictors
Steps: Delinearisation->Lasso alpha 2000 to Lasso CV-> with 244 predictors
Private Kaggle RMSE: 24967.88699
Public Kaggle RMSE: 24585.44701 

This score was good enough to place in the top 50 scores, and the close Private and Public scores show that the model is not overfitting either, not bad for just a Linear regression model!


### Aggregation of columns(Simple model with good prediction)
Steps: Delinearisation->Aggregating columns lasso alpha 3000-> polynomial->lasso alpha 5000-> with 26 predictors
Private Kaggle RMSE: 33619.75892
Public Kaggle RMSE: 33885.82882


### Aggregation and ordinalisation (Simple and good model with good predictive power)
Steps: Delinearisation->Lasso->Aggregating columns+ordinalisation->polynomial->lasso alpha9000->
Predictors: 23
Private Kaggle RMSE: 31152.70464
Public Kaggle RMSE: 33012.67842

This gave a good prediction with only 23 predictors. 

### INSIGHTS
As might be expected, the most important factors to a house's value were mostly linked to the Living Area and Quality ratings of the house.
The higher the coefficient, the more important the feature.

- Overall Qual	20417.213314
- Gr Liv Area	17568.039780
- Kitchen Qual	6579.745551
- Garage Area	5495.220478
- Exter Qual	3916.533569
- BsmtFin SF 1	3814.388757
- Bsmt Qual	3805.994516


Certain neighborhoods also had an effect on the prices,
such as Neighborhood_StoneBrand Neighborhood_NridgHt pricing higher than others, though only in connection to certain features in the house. Gr Liv Area is probably there because its such a strong indicator on its own, but its interesting that Masonry Veneer area has a synergy with North Ridge Heights lcoation, perhaps its something that is valued more heavily in the neighborhood, or fits the design of the area.

- Mas Vnr Area X Neighborhood_NridgHt	3264.924939
- Gr Liv Area X Neighborhood_StoneBr	2014.132628
- Gr Liv Area X Neighborhood_NoRidge	1768.745183
- Total Bsmt SF X Neighborhood_NridgHt	1646.863268

It was good to see that one of our aggregated values made it, for bath_agg, other features that were correlated
- bath_agg	1995.955527
- Sale Type_New	685.313395
- Fireplaces	467.917134
- Year Built	109.013330

## Summary
Overall quite a interesting dive into predictive and interpretive models, and my first exposure to multi-linear-regression models, feature selection, feature engineering and of course, data cleaning
