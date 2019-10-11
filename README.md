### Cleaning

Steps taken: Converted Garage Yr blt missing columns into neighborhood means
Converted ordinals into proper ordinals


### Methodologies tested, and results

##### Best Score but complicated model(Best score sheet)
Steps: Delinearisation->Lasso alpha 2000 to Lasso CV-> with 244 predictors
Private score: 24967.88699
public score: 24585.44701 

##### Aggregation of columns(Simple model with good prediction)
Steps: Delinearisation->Aggregating columns lasso alpha 3000-> polynomial->lasso alpha 5000-> with 26 predictors
Private score: 33619.75892
Public score: 33885.82882


## This sheet 
###### Aggregation and ordinalisation (Simple and good model with good predictive power)
Steps: Delinearisation->Lasso->Aggregating columns+ordinalisation->polynomial->lasso alpha9000->
Predictors: 23
Private score: 31152.70464
Public score: 33012.67842