---
title: "Building an Arbitrage Bot with Copilot"
categories:
  - Blog
tags:
  - GenAI
  - Statistics
---

*Using GitHub CoPilot to Build and Odds Arbitrage App in Python*

Looks like it's been exactly four years since I last posted on here, but I haven't completely given up on this idea. It's just been a busy 4 years you could say and a lot of changes have happened in the AI space. And I wanted to challenge myself to get more up to date with these changes, so I decided to use GitHub Copilot to build an application to grab sports betting odds from multiple bookmakers and look for arbitrage opportunities. It was surprisingly easy to get the bot to build what I wanted.

I started off with a simple enough prompt: Build me an app to find arbitrage using JavaScript and python. Then it built me a large scale app with docker and other tools that I didn't need (or understand), so I prompted it again to just use flask, which got me to something familiar. That's when I got the first version of the `flask-only-arbitrage` folder that you see. But copilot did everything, including creating the entire file structure and writing the code to each of the files. It even gave me an environment variable to put the api keys in for each bookmaker and set up example code for the bookmakers to run once the endpoint and API key were established. So I ran the code to see what we had so far and this is what it looked like: 

[First App Iteration](/assets/images/ArbitrageBot/first_look.png){:class="img-responsive"}

Not bad, but a little plain. It's good to see what we're working with and where we can go. The next step was to find somewhere to get the odds and incorporate some actual data into the webapp. After doing a little bit of research (clicking the first link on Google), I decided to go with [the-odds-api](https://the-odds-api.com/). It was simple enough to sign up, get an API key, and understand their documentation. Next, I played around with the API and did some calls in a Jupyter notebook to see how the calls work. And I actually had copilot also write the code into this file to test the API. I decided that I wanted to write as little code as possible, so I just had it pick up the API key from the environment and run the code.

This helped me understand the structures of the calls and I fed the options that needed to go into the URL to copilot, then it updated the bookmaker.py file to take in that format. At first, the webapp was still not showing the odds, but using a print statement, I could see that the odds were being called, so it just wasn't pushing to the webapp correctly. I prompted copilot again and it updated the code once again. This time we were able to see the odds and arbitrage opportunities for the MLB (theoretically)!

[First Look at Odds](/assets/images/ArbitrageBot/odds_showing_initial.png){:class="img-responsive"}

Finally, we got something, but there's still an issue where it's only showing the odds for one book. I decided to compile `example_json.json`, which showed the json output from the-odds-api, and feed that into copilot so that it could understand the format. Once it understood that, it was able to update our bookmaker.py code to read in the data correctly. I also told it to make the layout look better and here's what we got:

[Updated Output](/assets/images/ArbitrageBot/fixed_with_bookies.png){:class="img-responsive"}

Finally, it put together all the books and showed us the book with the best odds for each bet. Unfortunately, we're not seeing any arbitrage opportunities at the moment, which was disappointing. How am I supposed to win free money now? Naturally, the next step was to add in more leagues where there may be more opportunities. I thought that the big leagues wouldn't have much for arbitrage, but maybe the books would ignore lower leagues more. I looked at Minor League Baseball, but unfortunately they didn't have many games on there. So I just asked copilot to add a few more leagues like NBA, NHL, and EPL. Anyways, after telling the robot to add in some other leagues and tabs, we got this:

[Added New Leagues](/assets/images/ArbitrageBot/added_leagues.png){:class="img-responsive"}

I mean, it's pretty cool that we can switch between a few different tabs now and find more opportunities. However, there were issues with it picking up only one team name, but I knew what it meant, so I couldn't be too mad. Next, I wanted to add a feature that would let me switch between different types of bets, like head to head versus point totals. Telling copilot the options for the variables, it put together everything and we finally found some arbitrage opportunities.

[Arbitrage Opportunities](/assets/images/ArbitrageBot/arbitrage.png){:class="img-responsive"}

Hey, the arbitrage side works! At least, it shows opportunities, but the problem here is that soccer has 3 outcomes, not 2, which is why we're seeing arbitrage. But we'd be screwed if there was a tie. But y'know it works and even found a slight edge in the other sports depending on totals or head to head matchups. So we may be on to something here.

This is where I wrapped up the project after a couple of days of work. I may improve upon it more, but between GitHub making me wait a few hours between more copilot calls and laziness, I said this is good enough. In the future, it would be cool to use the apis `/sports/` call to get a list of all the sports and list them instead, so that we always have the most in-season sport and more options for gambling. I'd also like to fix it so we have the date / time of the matchup and get the correct sports teams instead of seeing penguins vs penguins. But, those are problems for a future me and for now, I'm happy that I can at least find small advantages for now, that is if the code Copilot wrote is calculating returns correctly. 

Finally, if you're interested in seeing the code it can be found on my [GitHub Account](https://github.com/sleavor/odds-arbitrage)