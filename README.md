## Overview
In this project, I worked with a dataset on the housing prices in Ames, Iowa from 2001 to 2007.

The goal was to predict housing prices in the test set accurately while creating a model which we could draw insights from.

Using the data in the training set, I created a Linear Regression model to predict housing prices on the test set.


## Data Cleaning
**MISSING DATA**
-Missing at random, or had very few rows: Dropped
-For values that it made sense to be connected to the area, such as Year Built and Garage Year Built, replaced with median neighbourhood values.

**Conversion to numerical values**
- Converted the "Quality" and "Condition" columns which rated different aspects of the house(Excellent,Very Good, Good, Fair, Poor etc.) into ordinal values
- Changed various categorical columns into one-hot-encoding
-

## Feature selection
For feature selection, I tried several different methods of selecting features, here are some of the strategies used:
- Dropping of one intercorrelated variables such as 'Year Built' and 'Garage Yr Built' to avoid collinearity
- Dropping variables with low correlation scores with housing price (for non-categorical, as categorical one-hot encoding makes variables have low correlation as their is low variability)
- Using the Lasso regression model, increasing the alpha until the desired number of predictors remain, then doing a polynomial relation between each variable, then lassoing the resulting variables. (gave the best results, so was the main method used)

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

This gave a good prediction with only 23 predictors. Interesting insights
