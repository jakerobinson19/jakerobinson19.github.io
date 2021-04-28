---
title: "Superbowl Scores By Decade"
excerpt: "Have Superbowls really gotten better over the years?"
header:
  teaser: /assets/images/football.jpg
number: 1
---

## Superbowls

This past Sunday was Superbowl LV and the Tampa Bay Buccaneers took home the trophy after beating the Kansas City Chiefs 31-9. I can't say that I watched all of it though because despite Patrick Mahomes' heroics, it was quite a snoozefest. 

In the end, I didn't care too much about who won, but with how the game went it got me thinking about how so many people say we've been spoiled with great Superbowls in modern years.

I wanted to see if that was statistically accurate and it gave me an excuse to flex my data viz chops.

So I grabbed a dataset from Kaggle that had all the superbowl scores from 1967-2020. 

To compare them over time, I clustered them based on the decade (60s, 70s, etc.). I chose the point differential as the major measure since I figured the closer a game is, the more fun it is to watch, especially for a Superbowl. 

Once that was all in place, I used <a href="https://flourish.studio/">Flourish Charts</a> to spice up the box plots with some football themed colors and shapes. You'll can see the final product below (you can hover over it for more info too).

<div class="flourish-embed flourish-scatter" data-src="visualisation/5290711"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

Each vertical cluster of circles represents a decade and the lower the circle is vertically shows that it was a closer game.

Visually, you can see how the circles cluster closely and trend to the bottom of the graph in the later decades. The shaded brown zones are a visual aid that represents the density of where the data points are clustered to help illustrate this point. 

The median score differential for each decade is as follows: 
- 1960s: 19
- 1970s: 13
- 1980s: 18
- 1990s: 14.5
- 2000s: 5.5
- 2010s: 7

So basically, before the 2000s most Superbowls were decided by at least two scores, with most being at least two touchdowns (14+ pts). On the other hand, since then the majority of Superbowls have been decided by less than a touchdown and, in fact, 50% of them were decided by 6 points or less.

Moreover, since 2000 only 3 Superbowls have ended with a differential greater than 14 points. Yet, in both the 1970s and 1980s at least half of the Superbowls in those decades were decided by greater than two touchdowns (5 in the 70s and 6 in the 80s). The 80s also have the Superbowl with the largest differential of 45: XXIV 49ers v Broncos (55-10)

After seeing this, I think its safe to say that we've have some pretty good modern Superbowls. 

For me though, the best one will always be Superbowl XLIII in 2009 because it was an amazing game that ended 23-27 with a score in the final moments. Also, it happens to be the only one the Arizona Cardinals have been in. 

It'll probably be my favorite until they win one. But I'm not sure that'll happen anytime soon...

<hr>
<h3> Source Data</h3>
<a href="/assets/source_data/superbowl.csv"> Superbowl Data File <i style="margin-left:5px;" class="fa fa-file-download"></i></a>

Dataset on Kaggle: <a href="https://www.kaggle.com/timoboz/superbowl-history-1967-2020">https://www.kaggle.com/timoboz/superbowl-history-1967-2020</a>