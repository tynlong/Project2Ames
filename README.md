## Overview
In this project, I worked with a dataset on the housing prices in Ames, Iowa from 2001 to 2007.

Using the data in the training set, I created a Linear Regression model to predict housing prices on the test set.


## Data Cleaning
-Dropped rows with missing data where data was missing at random, or had very few rows.  
-Replaced Garage Year Built with the neighborhood median values  
-Converted ordinals into proper ordinals, with values that  
  

## Different Methods and results

### Best Score but complicated model with 244 predictors
Steps: Delinearisation->Lasso alpha 2000 to Lasso CV-> with 244 predictors
Private Kaggle RMSE: 24967.88699
Public Kaggle RMSE: 24585.44701 


### Aggregation of columns(Simple model with good prediction)
Steps: Delinearisation->Aggregating columns lasso alpha 3000-> polynomial->lasso alpha 5000-> with 26 predictors
Private Kaggle RMSE: 33619.75892
Public Kaggle RMSE: 33885.82882


### Aggregation and ordinalisation (Simple and good model with good predictive power)
Steps: Delinearisation->Lasso->Aggregating columns+ordinalisation->polynomial->lasso alpha9000->
Predictors: 23
Private Kaggle RMSE: 31152.70464
Public Kaggle RMSE: 33012.67842
