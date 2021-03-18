# Project 3 - Web APIs & Classification on subreddit

The objective of this project is to choose two subreddits from Reddit and use natural language processing and classification models to classify.

I choosed scuba diving subreddit and hiking subreddit as my two topics of interest because both of them are under same main community 'travel', but are also differentiated enough that it should be possible to train a machine learning model.

### The problem statement is
Scuba diving and Hiking are adventure sport that allow us to explore the world above and under water. Therefore for travel agency who needs to seek for adventure traveller among the people on the internet. Therefore by knowing a dominant words that people use to discuss and search about scuba diving and hiking can helps these travel agencies spot their customers.

### Data Dictionary
Data dictionary of final to 12 features is here:

| Features              |type         |Description                                                          |
| ---                   |---          |---                                                                  |
| grlivarea             |integer      |Above grade (ground) living area square feet                         |
| overallqual           |integer      |Overall material and finish quality (Scale 1-10)                     |
| bsmtfinsf1            |float        |Basement Type 1 finished square feet                                 |
| neighborhood_NridgHt  |object       |Physical locations within Ames city limits (Northridge Heights)      |
| exterqual             |object       |Exterior material quality (Excellent,Good,Average/Typical,Fair,Poor) |
| kitchenqual           |object       |Kitchen quality (Excellent,Good,Average/Typical,Fair,Poor)           |
| neighborhood_StoneBr  |object       |Physical locations within Ames city limits (Stone Brook)             |
| yearbuilt             |integer      |Original construction date                                           |
| garagearea            |integer      |Size of garage in square feet                                        |
| bldgtype_1Fam         |object       |Type of dwelling (Single-family Detached)                            |
| totalbsmtsf           |integer      |Total square feet of basement area                                   |
| saletype_New          |object       |Type of sale (Home just constructed and sold)                        |
| bsmtexposure          |object       |Walkout or garden level basement walls                               |
| miscfeature_Elev	    |object       |Miscellaneous feature not covered in other categories (Elevetor)     |
|roofmatl_ClyTile	    |object       |Roof material made with clay or tile                                 |
    
Full data dictionary for the original Ames housing price dataset [here](https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/data).


### Model Selection
In this project we used Logistic Regression, Naive Bayes and K nearest neighbors to find best score, by using grid search to find the best parameters.

As Logistic Regression Model with Count Vectorizer got highest score in testing data set at this point Logistic Regression Model with Count Vectorizer shows that CV Score on Traing data set and Test Score was closed together, which mean Logistic Regression Model with Count Vectorizer is the best model compares with others.

| Model | Vectorizer | CV Score on Traing data set | Test Score |
| --- | --- | --- | --- |
|Logistic Regression|Count| 89.35% | 89.85% |
|Logistic Regression|Tfidf| 89.62% | 89.02% |
|Multinomial NB|Count| 89.27% | 89.02% |
|Multinomial NB|Tfidf| 88.45% | 88.61% |
|Binomial NB|Count| 71.71% | 71.42% |
|Binomial NB|Tfidf| 71.71% | 71.42% |
|KNeighbors NB|Count| 72.40% | 75.77% |
|KNeighbors NB|Tfidf| 87.41% | 89.23% |

### Analysis and Recommendation

In Model 4, lasso regression model was selected as its had best prediction value on house price in AMES shows in Kaggle out perform other linear regression models.  

After increased alpha ny 1500 to elimited the features, afterall we have got final 52 features (if count  same categorical as 1 features it will be final at 39 features) with RMSE in train data at 29403 and on Kaggle at 29377.

**This showing that the final model can predict the house price +- around $29000**

As of lasso was able to reveal which features affect sale price the most.

The validation set errors are then plotted against number of predictors. RMSE appears to stop decreasing significantly from 30 predictors onwards.  
Therefore, for the purpose of having a simpler and more easily interpretable model, look closer at 15 predictors onward RMSE tend to slightly decrese which the top 15 predictors will be used for the interpret the model which are:


|Features|Coefficient|
|---|---|
|grlivarea|3223.872588|
|overallqual|14035.774287|
|bsmtfinsf1|8729.217990|
|neighborhood_NridgHt	|7050.805490|
|exterqual	|6996.110155|
|kitchenqual	|5595.558339|
|neighborhood_StoneBr	|5021.050500|
|yearbuilt	|4839.733343|
|garagearea	|4799.303515|
|bldgtype_1Fam	|4738.694615|
|totalbsmtsf	|4677.522978|
|saletype_New	|4373.543453|
|bsmtexposure	|4130.057381|
|miscfeature_Elev	|-8993.741428|
|roofmatl_ClyTile	|-11156.215150|

![PJ2_RSMEbyFEATURES](https://user-images.githubusercontent.com/76549565/110248082-ebf38780-7fa1-11eb-9065-810ab4434ef4.png)

### Recommendation to steakholders

##### In conclusion the factors the result to house price that owner should consider: 
<ul>
    <li>Above ground living area</li>
    <li>Quality of overall condition </li>
    <li>Age of the house</li>
    <li>House in the area of Northridge Heights, Stone Brook are likely to have a good price</li>
    <li>Size of garage</li>
    <li>House with single family Detached</li>
    <li>Size of the basement</li>
    <li>New constructed house appears to have better sale price</li>
    <li>Size of the basement</li>
    <li>Lot size </li>
    <li>property has significant slope from side to side </li>
</ul> 

##### Value added to the house:  
<ul>
    <li>Renovate basement finished area (if exist)</li>
    <li>Renovate external area of the house</li>
    <li>Renovate kitchen </li>
    <li>Renovate basement with good exposure </li>
</ul> 
    
##### Thing that should avoid:  
<ul>
    <li>Clay or Tile roof material </li>
    <li>Elevator in the house</li>
</ul> 

#### Limitation

As this model is a prediction house price in Ames, Iowa which will not be able to use to predict the house price in others area.
