---
title: "Does Expensive Beer Taste Better?"
last_modified_at: 2020-01-25T16:20:02-05:00
categories:
  - Blog
tags:
  - Economics
  - Beer
---

I've drank a lot of beer in my day. According to Untappd, I've drank over 700 different beers, which is more than I probably should be proud of. And yes, I've paid a lot of money for those beers. Which got me wondering, is the price I pay for some of these beers actually worth it?

To do that, I decided to look at Total Wine's beer selections and prices and determine the cost per fluid ounce of each beer. I then found the beer's rating on beeradvocate, a site that let's users rate beers on a variety of factors. I plotted the price per ounce along with the average rating of each beer to see if there was any trend. 

At first I tried using the Selenium and BeautifulSoup libraries to grab all the data I needed from totalwine and beeradvocate. But after getting hit with too many captchas on totalwine's website, I realized I had to use another method to get the price of each beer.

Flaws with the collection: 
* Bigger packs will have more value, driving down the cost per fluid ounce versus a single bottle. Ideally, I would only get the prices of single bottles
* People may perceive that more expensive beer is better just because it is more expensive and they don't want to be wrong about the price
* Only looked at beers that you are allowed to buy a single beer of. No 12-packs, etc.
* Some beers were represented twice because they sold multiple singles, such as a 12-oz bottle and 16-oz can