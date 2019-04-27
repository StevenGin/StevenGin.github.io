---
layout: post
title:  "March Madness meets Chess!"
description: "Improving existing algorithms using recursive elo regression in Kaggle 2018"
tags: blog
---


# Welcome

Ever year **Kaggle** hosts a competition to predict the NCAA collegiate basketball playoffs. Known better colloquially as **March Madness**. In 2018, I decided to throw my name in the ring. While I didn't win, I made some novel improvements over existing approaches worth discussing.   

## The Competition
Some of you might be familiar with **March Madness brackets**. It's a longstanding tradition to fill out your expected winner of each match and see how you fare against actual competition results. If you were to guess the outcome of each match randomly your chance to win would be 1 in 2^63 or 1 in 9.2 quintillion. That's a pretty tall task!

![Former President George H. W. Bush's Predictions](/assets/images/bush_mm.jpg)
*Former President George H. W. Bush's Predictions ([Source](https://twitter.com/georgehwbush/status/974345353322483713?lang=en))*

Kaggle also challenged participants to predict the outcome of matches albeit with two key differences.

### Differences
1. Kaggle competitors predict the outcome of every possible match (although they are only evaluated on games that actually occur). This is opposed to regular bracket predictions where wrong early picks can lock you out of matchups deeper in the tournament.

2. Kaggle competitors predict the chance each team will win. Participants are then evaluated using **Log Loss**. In normal brackets, the quality of a prediction is gauged by tallying up the amount of correctly selected winners.

## The Data
Graciously provided in the competition was a treasure trove of NCAA historical data. Not only did we have the outcome of every game, but we had a timestamp of every individual play.

EXAMPLE Data

For instance, we can see that at 00:00 sank a 3 pointer

## My Approach
### Preface
For this project, I paired up with my good friend **Justin Wong** who helped me greatly with a lot of the feature engineering. Early on, we made some big decisions on the direction of our predictive model.

1. Ignoring player level data

Modeling at the individual level was certainly a consideration early on. This was ruled out for a few reasons. Firstly, there was far less data on collegiate level athletes as opposed to their professional counterparts. Secondly, in a team game like basketball, it's extraordinarily difficult to identify a single player's contribution to a game, especially when quantifying defensive contribution. We decided it would be

2. Predict first on **box score**, then convert to probability.

We are ultimately interested in the zero sum outcome of a match. Whether a team wins by 1pt or 100pts isn't relevant for the competition. That being said, it is my notion that the margin of victory has encoded in it valuable information on the true strength of a team.

3. Using XGBoost and LightGBM

These two boosting algorithms are Kaggle staples. Choosing to use these was mainly in the interest of getting more familiar with them!



### Basketball Stats
**Offensive Efficiency**:

**Defensive Efficiency**:

**Tempo**:


### ELO System

**Adjusted Efficiency**

### ELO Regression
