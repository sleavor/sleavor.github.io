---
title: "The Difference Between Audience and Critic on Rotten Tomatoes"
categories:
  - Blog
tags:
  - Economics
  - Movies
---

*The difference between the audience and critics on rotten tomatoes*

A while ago, I was browsing Rotten Tomatoes and looking for movies to add to my "want to watch, but will probably never get around to" list and one thing stuck out. One movie was sitting at an 11% critic rating, but an 80% audience rating. I thought that was a huge difference when it seems most people would have similar tastes. So it got me wondering, is there actually a discrepancy between the audience and the critic? And I spent too much time trying to find out, but it's too late to back down.

To start this project, we needed data. A lot of it. So I created a webscraping tool, using [Scrapy](https://scrapy.org/) of course, that would grab all the data from every movie on [Rotten Tomatoes](rottentomatoes.com). Unsurprisingly, this gave us a lot of data. If you ever wanted to know how many movies there are on Rotten Tomatoes, it's somewhere around 41,000. For each movie, we had the critic and audience score, when it was released, who directed it, and more. Now it was time to dive deeper into the data. 

First, I wanted to see how complete our data set was. Many movies lacked the box office, genre, or other information.

![Missing Data Chart for Rotten Tomatoes](/assets/images/RottenTomatoesBlog/missingRTdata.png){:class="img-responsive"}

As you can see, there's a lot of missing data. But with over 40,000 data points, there's still plenty that we can look at. The next thing I did was filter out any data that had under 25 critic reviews and 1000 user reviews to only find 'popular' movies. Once filtering this out, we were left with only 8,600 of our original 41,000 datapoints to use for our analysis. A big hit, but still plenty of data.

Now going back to my original question. With this data, I found that the average difference between critics and audience was only 1.4 points more for the audience than critics. But it had a large standard deviation of 18, with answers ranging from the audience favoring a movie by 78 points to the critics favoring a movie by 80 points. So, while it seems like there's mostly a consensus on average ratings, there's a lot of deviation from movie to movie. Some critics like certain movies and dislike others more than the audience. So it seems that there really isn't a consensus between critics and the audience. Maybe critics want to be different from everybody else. Maybe critics have more consensus on movies while the audience members are split. Maybe, just maybe, we'll never know. 

But I didn't just stop there. I thought, why not take this one step further? I also checked out which movies have the biggest difference in rating between audience in critic. This was sorted by rating, genre, and director, so you could view the moview that had the biggest difference for each of these. For example, Quentin Tarantino's most critic favored movie was Kill Bill Vol: 1, which critics liked 4 points more than the audience. His most audience favored movie was Four Rooms, which the audience favored at a whopping 56 points higher than the critics. Remember that the biggest difference could be a movie with 100% for one and 0% for the other.

Next, I looked through different genres and directors to see if there was any difference in ratings between them. This data was a lot more useful and could be visualized easier as shown below. 

![Graph of Audience and Critic Differences by Director](/assets/images/RottenTomatoesBlog/directorGraph.png){:class="img-responsive"}

Here I chose certain directors to see how their movies compared with audience and critic rating. The graph shows that movies by Paul Thomas Anderson are heavily favored by critics, rather than audience. While David Lynch films are heavily favored by the audience members. It also tells us that some directors, like Quentin Tarantino have a consensus between the critic and the audience. 

Another analysis shows the overall critic and audience ratings for certain genres. This wasn't as telling as the director analysis, but I still find it interesting.

![Graph of Audience Rating by Genre](/assets/images/RottenTomatoesBlog/genreAudience.png){:class="img-responsive"}

The above graph shows the range of audience rating based on the movies genre. This tells us that classic movies are generally rated the highest, while horror movies are rated the lowest. Of course, there's a lot of variance between each movie, especially in the horror category. This makes sense, since many horror movies can be extremely hit or miss. Classics, on the other hand, has a low amount of variance and is generally rated highly all around. Which also makes sense, because classics are classics for that reason. Or people have a hard time saying "even though this is a classic, I don't really like it." 

![Graph of Critic Rating by Genre](/assets/images/RottenTomatoesBlog/genreCritic.png){:class="img-responsive"}

Finally, we have the same graph but for critic ratings instead of audience. Here we see that classics are again rated highly overall, but this time action movies take the biggest hit. It seems that critics aren't big fans of Action or Anime, which have an average rating just below 60. One interesting difference in the two graphs is the faith and spirituality section. Critics seem to have a lot of disagreement on faith and spirituality movies, while audience ratings tend to favor them within a set range. 

So what did we learn today? There surprisingly is a difference between how critics and audience rate movies on Rotten Tomatoes. While the seems to center around the same ratings overall, there's a large variance from movie to movie. Different categories seem to be polarizing for various groups. If you want to see the code you can click [here.](https://github.com/sleavor/RottenTomatoesScraping) I also added some extra graphs below if you wanted to see some more data. 

![Graph of Audience and Critic Differences by Genre](/assets/images/RottenTomatoesBlog/diffGenre.png){:class="img-responsive"}

A graph of the audience and critic differences by genre.

![Graph of Audience and Critic Difference by Popular Directors](/assets/images/RottenTomatoesBlog/directorDiff.png){:class="img-responsive"}

A graph of the audience and critic difference by the most 'popular' directors. Which is those with the most movies meeting the filter criteria.

![Graph of Audience and Critic Difference by Studio](/assets/images/RottenTomatoesBlog/studioDiff.png){:class="img-responsive"}

A graph of the audience and critic difference based on the studio that made the movie.


