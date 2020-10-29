---
layout: post
title: Project Report | Regression Analysis on House Price
---

#### _Author: Jinhang Jiang, Maren Olson_
#### _Contributors: Andrew Aviles, Tzu Hsuan Chang_
#### _Master of Science in Business Analytics at Arizona State University, Class 2021_

## Project Summary

This project provided by Kaggle included a dataset of 79 explanatory variables describing aspects of residential homes in Ames, Iowa. You may find all the data sources and description of the project at [here](https://www.kaggle.com/c/house-prices-advanced-regression-techniques). <br/>

The goal of this competition was to predict the final sales price for each home listed. We did this problem because we were looking to apply our regression techniques as well as our stacking and exploratory data analysis skills. This problem set allowed us to use all of the above practices. Moreover, the datasets contain many missing values, which offered us the opportunity to gain experience in handling missing data. <br/>

We ran multiple regression techniques such as XGB regressor, SGD regressor, MLP regressor, Decision Tree regressor, Random Forest regressor, CatBoost regressor, Light GBM, and SVR. We stacked some together and experimented to see which ones ended up with the smallest Root-Mean-Squared-Error. <br/>

The prediction that we submitted was two columns (Figure 1.1). The first column was the ID of the house and the second column was our predicted sales price. The prediction is scored based on the Root-Mean-Squared-Error between the predicted value logarithm and the log of the observed sales price. The smallest RMSE was the best prediction. After running base models and the tuned models, we found that our tubed CatBoost regression model got us the lowest score of 0.12392 of RMSE, which was 863rd place (out of 4525) on the Leaderboard.<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/Figure1.1.png "an image title")<br/>
Figure1.1 - Sample of Submission
{: refdef}

## Data
### -	Overview
The competition offered us two datasets to work on. One of them is the training data with 1460 observations and 81 columns, which contains each house's ID and the sale price. The other dataset is the holdout file, which includes 1459 observations.<br/>

We first looked into the types of features of the training dataset. 
Figure 2.1 shows that the whole dataset has 43 categorical features and 36 numeric variables, including "ID".<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/RegReport/Figure2.2.png "an image title")<br/>
Figure2.1 - The Numbers of Numeric & Categorical Features
{: refdef}

Then, we took the efforts to detect if there were any missing values in the dataset. In the training dataset, 19 variables have missing values. The holdout dataset has 33 features with missing values. Some features have very high percentages of missing values. For example, the feature, PoolQC (Pool Quality), has as high as 99.5% missing values. Features like PoolQC,  may hurt the accuracy of the prediction model and lead us to invalid conclusions. So, we removed the features with at least 80% of the values that are missing. The details are explained in the Data Processing section.<br/>

Before we started to process the data, we also studied the necessary statistical information of the 38 numeric features. In Figure 2.2, we found out that the ranges of some features, like the SalePrice, are relatively large. Many regression models we were going to use would need us to do some types of transformations of those features before processing.<br/>

{:refdef: style="text-align: center;"}
![an image alt text]({{ site.baseurl }}/images/RegReport/Figure22.png "an image title")<br/>
Figure2.2 - Statistical Info of All the Numeric Variables
{: refdef}


