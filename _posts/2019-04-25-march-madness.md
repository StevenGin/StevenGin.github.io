---
layout: post
title:  "March Madness meets Chess!"
description: "Improving existing algorithms using recursive elo"
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

## My Approach
The model we built was an ensemble of primarily XGBoost and LightGBM, popular kaggle staples. As a team we engineered plenty of features. Some of the more interesting ones that ended up being significant were elevation

**Offensive Efficiency**:

**Defensive Efficiency**:



**Adjusted Efficiency**

## ELO Regression
