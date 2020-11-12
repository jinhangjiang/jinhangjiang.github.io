---
layout: post
title: Project Report | League of Legends Match Prediction Using Laning Phase Data
---

#### _Author: Jinhang Jiang_
#### _Master of Science in Business Analytics at Arizona State University, Class 2021_

## Introduction

League of Legends is a team-based strategy game where two teams of five powerful champions face off to destroy the other’s base.[(Source)](https://na.leagueoflegends.com/en-us/how-to-play/)<br/>

A typical League of Legends game tends to last 30 to 45 mins, and each game can be divided into three phases: the laning phase, mid game, and late game. Players normally spend the first 10 to 15 minutes to farm in their own lanes (Top, Mid, Bot, JG) to gain early advantages in builds and levels. In the middle game phase, players start to focus on the macro level: push lanes, take down towers, get map objectives, and group fights. In the late game, if the game has not ended, each team has to decide how to close the game, for examples: force a baron/elder dragon or 1–4 push, etc.<br/>

In this project, I used the data collected by the Kaggle named “michel’s fanboi,” and the dataset contains the first 10min. stats of approx. 10k ranked games (SOLO QUEUE) from a high ELO (DIAMOND I to MASTER). You may find the full description and data source [here](https://www.kaggle.com/bobbyscience/league-of-legends-diamond-ranked-games-10-min）.<br/>

The champion combos of each team will significantly impact the results of the games since some champions are strong in the early game, while other champions will be scaling greatly throughout the mid and late game. And that is why all the rank games and professional games will have a ban/pick phase prior to the games. However, a lot of influences that players can make to the game with their skills and map awareness will not be reflected by the champion combos. Especially, some players, like RNG.Uzi, can gain significant advantages in the laning phase regardless of if the opponents have counter-picks or not.<br/>

Also, as we can see, in a lot of high-level games, team combos, especially the combos for the late game, did not always work out as expected since the laning phase tends to have more uncertainties than the mid and late game phases, such as one of the teams was able to create a gap that was too big for the other team to fill up in the late game. My goal is to understand how the laning phase performance (the first 10 mins) affects the final result.<br/>

I used the Jupyter Notebook and R studio as the code editors. I did some data exploration with Pandas, NumPy, and Matlibplot packages. Then, I implemented nine models, including an ensemble model, a stacking model, and seven other classifiers. The most consistent model was the stacking model, whose average accuracy score on cross-validation was 0.732158, with a standard deviation of +/- 0.005171.<br/>
