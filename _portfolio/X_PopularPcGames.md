---
title: "Most Popular PC Games"
excerpt: "Who's the top dog in gaming?"
header:
  teaser: /assets/images/Popular_PC_Games_viz.png
number: 3
---

## PC Games

I love video games. And I'm also of the opinion that PC gaming is superior to all other gaming. Don't get me wrong though, I have a couple consoles and they've got some good exclusives, but the best gaming can only be done on PC. 

The most popular platform for PC gaming is Steam, which provides an all-in-one client with a store and library where gamers can buy and play games. 

While playing one day I was curious as to what games were the most popular and how many monthly players they see on average. So, I searched around and was able to find a great dataset on Kaggle (linked below).

The data, scraped from Steamcharts, contained the average and peak monthly viewers for all games available on Steam as far back as 2012. 

After some basic data cleaning, I was able to pull the current top 5 games with the highest average monthly players (as of Jan 2021):
1. Counter Strik: Global Offensive - 743,210 
2. DOTA 2 - 432,671
3. Player Unknown: Battlegrounds - 201,247
4. GTA V - 142,117
5. RUST - 101,250

Clearly, CS:GO and DOTA 2 hold firm positions as the most popular games with about 2-3x the players as the third place game, PUBG. These games also boast a thriving esports scene despite being released in 2012 and 2013, respectively. 

I plotted out the monthly average players all the way back to 2012 for these 5 games to see the trends over the past decade and it was pretty interesting. It also gave me an excuse to use <a href="https://flourish.studio/">Flourish Charts</a>  to make a race chart (although be aware if you want to make one yourself, you may have do some data pivoting because it wants a particular format).

<div class="flourish-embed flourish-chart" data-src="visualisation/5291017"><script src="https://public.flourish.studio/resources/embed.js"></script></div>

Overall, most of these games have seen healthy growth of the past 8 years, and even saw some decent bumps in the first half of 2020 as quarantine started. 

But clearly the most interesting part is how Player Unknown: Battlegrounds (aka PUBG) burst onto the scene when it was released in 2018. In fact, PUBG holds the record for most concurrent players on steam with 3.2 million. 

However, the hype couldn't be maintained and it came crashing down rather fast settling into third place currently. Still not a bad place to be though.

Now I'll go back to enjoying my favorite game on Steam, SMITE, which boasts a whopping 14,000 average monthly players. It's still a better MOBA than DOTA 2 (sorry to DOTA 2 fans).
<hr>
<h3> Source Data</h3>
<a href="/assets/source_data/SteamCharts.csv"> Steam Games Data File <i style="margin-left:5px;" class="fa fa-file-download"></i></a>

Dataset on Kaggle: <a href="https://www.kaggle.com/michau96/popularity-of-games-on-steam">https://www.kaggle.com/michau96/popularity-of-games-on-steam</a>