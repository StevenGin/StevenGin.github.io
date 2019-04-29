---
layout: post
title:  "March Madness meets Chess!"
description: "Improving existing algorithms using recursive elo regression in Kaggle 2018"
tags: blog
---


# Welcome

Ever year, **Kaggle** hosts a competition to predict the NCAA Division I Men's Basketball Tournament, known better colloquially as **March Madness**. In 2018, I decided to throw my name in the ring and put my predictive mettle to the test. The experience was incredibly arduous but equally rewarding. While I didn't win (or even come close!), I still built a very powerful model built on top of some novel innovations, that I'd love to share.

## The Competition
Some of you might be familiar with **March Madness brackets**. It's a longstanding tradition for basketball fans  predict winners for each tournament match, often putting money on the line. The American Gambling Association estimates Americans $8.5B in 2019 on March Madness alone ([Source](https://www.americangaming.org/wp-content/uploads/2019/03/March-Madness-One-Pager.pdf)). How hard is it to get a perfect bracket? If you were inclined to just arbitrarily select teams to build your bracket, your chance to win would be 1 in 2^63 or 1 in 9.2 quintillion. Those are some pretty bad odds.

![Former President George H. W. Bush's Predictions](/assets/images/bush_mm.jpg)
<center>
*Former President George H. W. Bush's Predictions ([Source](https://twitter.com/georgehwbush/status/974345353322483713?lang=en))*
</center>

A lot of people Kaggle challenged participants to do a lot better than that and craft their own set of predictions. These differed from traditional bracket predictions in two key ways.

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

1. Ignore player level data

...Modeling at the individual level was certainly a consideration early on. This was ruled out for a few reasons. Firstly, there was far less data on collegiate level athletes as opposed to their professional counterparts. Secondly, in a team game like basketball, it's extraordinarily difficult to identify a single player's contribution to a game, especially when quantifying defensive contribution. We decided it would be

2. Predict first on **box score**, then convert to probability.

...We are ultimately interested in the zero sum outcome of a match. Whether a team wins by 1pt or 100pts isn't relevant for the competition. That being said, it is my notion that the margin of victory has encoded in it valuable information on the true strength of a team.

3. Use XGBoost and LightGBM

...These two boosting algorithms are Kaggle staples. Choosing to use these was mainly in the interest of getting more familiar with them! The final model was primarily an ensemble of these two models.



### Basketball Stats
Now that we've identified we want to try and predict box score, I needed to figure out what were the predictors that would lead us to figure that out.

Surprising as it may be (for someone working on this competition), I knew next to nothing about basketball. I started asking around to try and understand what were the important statistics to look at in professional basketball. All roads seemed to lead me to kenpom.com.

Ken Pom is blah lah blah.

Three particular statistics caught my eye.

**Offensive Efficiency**: Points scored per 100 possessions.

**Defensive Efficiency**: Points allowed per 100 enemy possessions.

**Tempo**: Total possessions per 40 min.

https://kenpom.com/blog/national-efficiency/

Ken Pom then converts these raw statistics to be adjusted for expected stats versus an average team.

Theoretically using solely these statistics, we could generate box scores.

What's the primary flaw

### ELO System

**Adjusted Efficiency**

### ELO Regression
