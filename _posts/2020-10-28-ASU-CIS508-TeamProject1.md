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

<p align="center">
  <img width="125" height="135" src="https://github.com/jinhangjiang/jinhangjiang.github.io/blob/master/images/RegReport/Figure1.1.png">
</p>
