# Project 2 - Ames Housing Data and Kaggle Challenge

Problem Statement
Question: Do Dimension qualities in homes affect home prices in Ames and if so, is there a relationship between dimensions factors in home prices? Could this increase, decrease or not impact the prices of homes?

The purpose of this project was to create models that predict the price of houses in Ames Iowa. During the project I was able to gain many insights on this particular data set specifically related to how to make decisions for features. 

For the purposes of the project, there is a Real Estate company called The Real(™) estate dedicated to selling homes across all of the the US. A new estimator that works in the construction department joined the team is looking to gain insight on their next big expansion to Ames Iowa. This estimator is seeking a data scientist for guidance on the landscape of homes in Ames Iowa and trying to figure out if ther is a relatiomnship between dimensions(such as Lot area and frontage)and construction/measurement qualities in homes in Ames which could impact ho they price their home helping them make informed decisions on their home prices.

Our goal as the data scientist will be to inform the estimator on the landscape of Ames Iowa and give some perspective whether dimensions features should be a big factor of how their company price their homes in Ames. The EDA and models that I will present will show the relationship of these elements on the sales prices of homes. Some of the features that I will look at are lots dimensions and bedrooms in homes which are common features that land construction estimators work with. In summary, we are trying to answer if dimensions impact home prices in Ames, Iowa or not, in addition to make recommendations/inform decisions on if dimensions should be a factor when considering pricing homes.


# Data Dictionary
The Ames Iowa Dataset can be found on Kaggle.com, https://www.kaggle.com/competitions/dsi-910-ames-housing-challenge/data  . The data was said to be retrieved from ata set contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010.The three data sets that are provided are labeled as train, test, and sample_sub_reg which was sale price and specifically serve as the purpose of working as testing, training and y variable data being sales price. There were a total of 82 variables in each  training and test data, however, for the purpose of my model, I did not include all features.

Features used for models, X and Y variables
Bedroom --- 'Bedroom AbvGr' - numerical
Square ft --- 'Lot Area' - numerical
'Lot Frontage' - numerical
Feature that was going to be used but used for EDA purpose instead, Year remolded labeled as 'Year Remod/Add' - years

All variables in datasets, organized by attributes.
categorical_attributes: ['MS Zoning', 'Street', 'Alley', 'Lot Shape', 'Land Contour', 'Utilities', 'Lot Config', 'Land Slope', 'Neighborhood', 'Condition 1', 'Condition 2', 'Bldg Type', 'House Style', 'Roof Style', 'Roof Matl', 'Exterior 1st', 'Exterior 2nd', 'Mas Vnr Type', 'Exter Qual', 'Exter Cond', 'Foundation', 'Bsmt Qual', 'Bsmt Cond', 'Bsmt Exposure', 'BsmtFin Type 1', 'BsmtFin Type 2', 'Heating', 'Heating QC', 'Central Air', 'Electrical', 'Kitchen Qual', 'Functional', 'Fireplace Qu', 'Garage Type', 'Garage Finish', 'Garage Qual', 'Garage Cond', 'Paved Drive', 'Sale Type']
numerical_attributes: ['Unnamed: 0', 'Id', 'PID', 'MS SubClass', 'Lot Frontage', 'Lot Area', 'Overall Qual', 'Overall Cond', 'Year Built', 'Year Remod/Add', 'Mas Vnr Area', 'BsmtFin SF 1', 'Bsmt Unf SF', 'Total Bsmt SF', '1st Flr SF', '2nd Flr SF', 'Low Qual Fin SF', 'Gr Liv Area', 'Bsmt Full Bath', 'Bsmt Half Bath', 'Full Bath', 'Half Bath', 'Bedroom AbvGr', 'Kitchen AbvGr', 'TotRms AbvGrd', 'Fireplaces', 'Garage Yr Blt', 'Garage Cars', 'Garage Area', 'Wood Deck SF', 'Open Porch SF', 'Mo Sold', 'Yr Sold', 'SalePrice']

# EDA & Data Cleaning
In my EDA, I explored the features of my training data by viewing their distributions, outliers, counts and then normalized, scaled, filled nulls and explored some of the relationship with sales. After analyzing the data, I decided that I will be expiriementing on features all the following features.

Bedrooms = 'Bedroom AbvGr' - numerical
Square ft of homes = Lot Area - numerical
Square ft of outer exterior = Lot Frontage - numerical
While I believe i will be able to answer my problem statement, I am curious to explore what I will discover along the way. My intention is to bring back categorical data during my modeling process.

# Model Development 
For my models, I decided to create 3 models that used linear regression, lasso and Ridge. The model that I found most successful in was my lasso model so for the purposes of the variables that I chose that was the model that I decided to choose. Although this model had some potential issues such as overfitting, the performance of this model did better than my lasso and ridge model. Throughout this process, I implemented various techniques to obtain my results such as splitting data, analyzing coefficients, distribution, scaling, normalizing, imputing, cross validation, and many other techniques. 


# Analysis 
From my analysis, my lasso model ended up working the best and was able to discover this through comparing my r squared, MSE, RMSE values on my training validation and testing data. 

For my linear regression model, these were my results...
R-squared Score: 0.14910060058115893
Mean Squared Error: 0.8673783481668563
Coeficients: 0.06946567, 0.1107222 , 0.28591783
baseline_mse = 1.2915522751012547
Mean Squared Error for validation: 1.0458471295757363
R-squared Score for validation: 0.13729740330784101

My takeaways from this were that although the current model performs better than the baseline model and is infact performing some predictive analysis and has a positive R-squared value, my linear regression model isint a good fit and does not perform well. The reason for this is because there is a low R-squared, high MSE, and it shows in the validation as well. Overall, the model is overfit and there is a abnormal variance in the model.

For my lasso model, these were my results...
Best alpha value: 0.016941572303849274
Lasso coefficients: [0.05597449 0.10299308 0.27631922]
Test R-squared score: 0.11227315046646114
R-squared score on training data: 0.14859786896205995
MSE: 0.8842237265351621
RMSE: 0.9403317109058708

This model obtained the best results. It had the highest r-squared in both the training and test compared to ridge and linear regression. You are able to tell because of the lower MSE which shows that the model perfomed best. My coefficients were closer to 0 than the other models which shows that is worked better. Lasso also the highest R-squared score on both the training and test sets compared to the other two models. It also showed more potential for feature selection.


For my Ridge model, these were my results...
Training R-squared score: 0.1491005026745612
Test R-squared score: 0.11421534215010576
R-squared: 0.11
RMSE: 0.93
Optimal alpha: 100.00
R-squared (CV): 0.11
RMSE (CV): 0.93

My takeaways from this were that the Ridge regression model did not perform as well as expected similarly to the lasso model as it obatined similar results. The model has a low R-squared scores on both the training and test sets and a high RMSE. Something that I would do next time would be to regularize before creating the model. I would also explore another alpha score as i think that would help improve the model. I belive this alpha may have been high due to prevent any overfitting.


From my findings, my lasso model was the best. It had the highest r-squared in both the training and test compared to ridge and linear regression. My lasso also had the lower MSE which shows that the model perfomed best. my coefficients were closer to 0 than the other models which shows that is worked better Lasso model has the highest R-squared score on both the training and test sets compared to the other two models. It also showed more potential for feature slection.

# Excecutive summary:
In summary, my lasso model was the best. It had the highest r-squared in both the training and test compared to ridge and linear regression. My lasso also had the lower MSE which shows that the model perfomed best. my coefficients were closer to 0 than the other models which shows that is worked better Lasso model has the highest R-squared score on both the training and test sets compared to the other two models. It also showed more potential for feature selection. In terms of asnwering my problem statement and question, I found that There is an impact based on the relationship and may be worth considering for further investigation however, the impact is not stark. My Recommendation would be to onsider it a factor, but not the only one.
While not the only factor(example: bedrooms), dimensions still have an impact on the price of homes in Ames Iowa. 

# Limitations and next steps
Some ways to improve this project would be to implement more features, use pipelines and cross validate my testing data. I only used a couple of features and dropped categorical data. I would also want to regularize my data for my models. I did not bring all dropped data back but my intention was to bring the data back one by one which was shown before my EDA. I also think continuing to fine tune the models would also help increase the model score. I would also implement more further investigation on Ames, Iowa and its current landscape. As always, creating more models may increase my chances of creating a better model with the techniques I have have now learned and would implement in this project.
