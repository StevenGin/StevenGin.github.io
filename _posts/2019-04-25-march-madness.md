---
layout: post
title:  "March Madness meets Chess!"
description: "Improving existing algorithms using recursive elo regression in Kaggle 2018"
tags: blog
---
<script>
$(function () {
  $('[data-toggle="popover"]').popover()
})
</script>

# Welcome

Ever year, **<a href="#" onclick="return false;" style="color: #343a40; text-decoration: none;" data-toggle="popover" data-placement="top" data-trigger="focus" title="Kaggle" data-content="Kaggle is a website that hosts Machine Learning competitions.">Kaggle</a>** hosts a competition to predict the NCAA Division I Men's Basketball Tournament, known better colloquially as **March Madness**. In 2018, I decided to throw my name in the ring and put my predictive mettle to the test. The experience was incredibly arduous but equally rewarding. While I didn't win (or even come close!), I still built a very powerful model built on top of some novel innovations. I'd love to share what I've learned.

## The Competition
You might be familiar with **March Madness brackets**. A longstanding tradition accompanying the tournament asks basketball fans to predict winners for each tournament match. Often putting money on the line. The American Gambling Association estimates Americans will bet $8.5B in 2019 on March Madness alone ([Source](https://www.americangaming.org/wp-content/uploads/2019/03/March-Madness-One-Pager.pdf)). How hard is it to get a perfect bracket? If you were inclined to flip a coin to arbitrarily select winners, your chance to win would be 1 in 2^63 or 1 in 9.2 quintillion. Those are some pretty bad odds.

![Former President George H. W. Bush's Predictions](/assets/images/bush_mm.jpg)

Former President George H. W. Bush's Predictions ([Source](https://twitter.com/georgehwbush/status/974345353322483713?lang=en))

Kaggle challenged participants to do a lot better than that and craft their own set of predictions. These differed from traditional bracket predictions in two key ways.

### Differences
1. Kaggle competitors predict the outcome of every possible match (although they are only evaluated on games that actually occur). This is opposed to regular bracket predictions where wrong early picks can lock you out of matchups deeper in the tournament.

2. Kaggle competitors predict the chance each team will win. Participants are then evaluated using **<a href="#" onclick="return false;" style="color: #343a40; text-decoration: none;" data-toggle="popover" data-placement="top" data-trigger="focus" title="Log Loss" data-content="Log Loss quantifies the accuracy of a classifier by penalizing false classifications.">Log Loss</a>**. In normal brackets, the quality of a prediction is gauged by tallying up the amount of correctly selected winners.

## The Data
Graciously provided in the competition was a treasure trove of NCAA historical data. Not only did we have the outcome of every game, but we had a timestamp of every individual play.


{% assign mydata=site.data.pbp_data %}

<div class="table-responsive">
<table class="table table-hover">
    <caption>Excerpt of NCAA Play-by-Play Data 2010</caption>
    <thead>
    <tr class = "table-dark">
    {% for column in mydata[0] %}
        <th>{{ column[0] }}</th>
    {% endfor %}
    </tr>
    </thead>
    <tbody>
    {% for row in mydata %}
        <tr>
        {% for cell in row %}
            <td>{{ cell[1] }}</td>
        {% endfor %}
        </tr>
    {% endfor %}
    </tbody>
</table>
</div>


For instance, we can see that at 00:00 sank a 3 pointer

## My Approach
### Preface
For this project, I paired up with my good friend **Justin Wong** who helped me greatly with a lot of the feature engineering. Early on, we made some big decisions on the direction of our predictive model.

1. Ignore player level data

Modeling at the individual level was certainly a consideration early on. This was ruled out for a few reasons. Firstly, there was far less data on collegiate level athletes as opposed to their professional counterparts. Secondly, in a team game like basketball, it's extraordinarily difficult to identify a single player's contribution to a game, especially when quantifying defensive contribution. We decided it would be

2. Predict first on **box score**, then convert to probability.

We are ultimately interested in the zero sum outcome of a match. Whether a team wins by 1pt or 100pts isn't relevant for the competition. That being said, it is my notion that the margin of victory has encoded in it valuable information on the true strength of a team.

3. Use XGBoost and LightGBM

These two boosting algorithms are Kaggle staples. Choosing to use these was mainly in the interest of getting more familiar with them! The final model was primarily an ensemble of these two models.



### Basketball Stats
Now that we have identified that we want to try and predict box score, I needed to figure out the predictors that would lead us there.

Surprising as it may be (for someone working on this competition), I knew next to nothing about basketball. I relied a lot on friends to educate me, especially in understanding the perception of what the important factors were in playing good basketball. I wanted to be looking at the same things same statistics that sports analysts in the industry were looking at. My research eventually lead me to Ken Pomeroy. After quitting his job as a meteorologist and working on his stats website fulltime, Ken has since become the de facto expert in college basketball. He's written for the New York Times, ESPN, Sports Illustrated as well as worked with the Houston Rockets. Needless to say, his website kenpom.com was a fantastic resource for me.

On his website, three particular raw statistics caught my eye. In particular, because they are a decomposition of box score.

**Offensive Efficiency**: Points scored per 100 possessions.

**Defensive Efficiency**: Points allowed per 100 enemy possessions.

**Tempo**: Total possessions per 40 min.

https://kenpom.com/blog/national-efficiency/

So, at the end of any given game, a team would have these statistics for that game.
Okay awesome. How do we use these to predict future games? We need to turn these numbers into something that reflective of a team's actual offensive and defensive abilities, and not just a single data point. Numbers which we could use as inputs for our mode. Ken pom achieves this by averaging these statistics by game. He goes on to calculate an expectation of future statistics using a linear formula as follow.


Ken Pom then converts these raw statistics to be adjusted for expected stats versus an average team. He does this


Not only are these some of the more popular metrics, using only these three values we could theoretically calculate an average box score for a team. Theoretically I'd like to include these statistics as inputs into my model. Among lots of other feature engineering, I ran with these inputs for a while.


I had three main issues.


1) Consistency of Expectations
2) Strength of Schedule
3) High variability for early season games




### ELO System

**Adjusted Efficiency**

### ELO Regression
