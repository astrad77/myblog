---
layout: post
title:  "Data Curation in Action: Tracking Renewable Energy’s Impact on Electricity Costs"
author: Andrew Stradling
description: This post gives a quick rundown of some data curation techniques. I use data on renewable energy and electricity prices as an example. 
image: /assets/images/lightbulb.png
--- 

Renewable energy has been a hot topic in recent decades because of things like climate change, air quality, and energy spending. However, I wanted to answer a different question: how does renewable energy affect electricity costs? In order to answer this question, we need some data. This post will explore some techniques of obtaining data that isn't readily available. 

## Motivating Question
First, let's clarify our motivation for asking this question. Since there is (theoretically) an infinite supply of things like sunlight and wind, shouldn't that energy be cheaper? On the other hand, maybe the infrastructure for renewable energy is more expensive, causing electicity prices to go up. In either case, if there is a relationship between renewable energy production and electricity costs, I think we'd all like to know about it!

## Data Source

To answer this question, I obtained data from the <a href="https://www.eia.gov/electricity/data.php" target="_blank">US Energy Information Association</a>. I downloaded two separate data sets: one for energy production and one for average energy prices. Unfortunately, there isn't a single data set that has all of the data that we need, so we will have to combine the data from these two data sets into one. Because this data is freely available on a government website, this use of data is ethical. 

## Combining the Data

To save time, I won't go into every detail of how I cleaned and merged these data sets. I have provided a link to a GitHub repository that contains the final data set and the code I wrote to obtain it. 

Because we are interested in how the growth of **renewable** energy affects prices, I filtered the energy production data to only include renewable sources. Then I added up all renewable energy production (in megawatt hours) for each month. Within the electricity prices data set, I averaged the prices for each month and for each sector (residential, industrial, commercial, and all). Once all of this was done, I cleaned the data to make sure column names matched and that the lengths of each data set was the same. Then I merged the two data sets into one final data set that we can use to answer our question. 

An additional note about gathering and combining data: your data sets must have at least one column in common. That common column is sometimes called a key; it is the link between the two data sets. Without a common column, the data sets cannot be merged. The column names don't necessarily have to match perfectly, but they should be measuring the same thing. In my example, the key between the two data sets was the year and month. 

## Exploring the Data

The data set contains the following columns: `date`, `price_all`,  `price_residential`, `price_industrial`, `price_commercial`, and `Total_Renewable_Generation_MWh`. It contains data for every month from 2001 through 2023 and contains 276 rows. 

Now that we have the data we want, let's take a look at it! 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/histogram.png)

This histogram gives us the distribution of overall average price, which seems to be roughly centered at 10 cents per kilowatt hour and averages as low as 7 cents and as high as 13 cents. Now, lets take a look at how average prices have changed over time. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/price_vs_date.png)

Not surprisingly, we see that average electricity prices have increased over the past couple decades. Some of this is probably due to inflation, but some of this increase is also probably due to depleted natural resources. Either way, average prices have been on the rise. According to the plot, prices have seen a sharp increase over the past couple of years. Time will tell if this trend continues. 

Let's make a plot that investigates the relationship between renewable energy production and average price. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/production_vs_price.png)

Well, shoot. If we take this graph at face value, the data says that as more renewable energy is produced, average energy prices go up (at least for residential areas). Should we stop with renewable energy then? Not necessarily. Remember that correlation does not mean causation: increasing renewable energy production does not necessarily **cause** average prices to go up. In order to discover the true relationship, we will have to do more in-depth analysis. We may even need more data than we currently have available to us. I will do some of this analysis in an upcoming post. 


## Conclusion

Phew. Let's review what we've gone over today. First, we asked an important question: how does the growth of renewable energy affect electricity costs? To answer this question, we downloaded two separate data sets from the <a href="https://www.eia.gov/electricity/data.php" target="_blank">US Energy Information Association</a>. One of these data sets detailed energy production while the other gave information about electricity prices. We manipulated these data sets to get the information we wanted from each one, and then we combined them into one data set. To finish, we took a look at the data set that we just created. We discovered that average prices have been rising over recent years. This led to the realization that higher production of renewable energy is correlated with higher average electricity prices. In my next post, I'll continue with this question and attempt to answer it using the data we have gathered here. 

If you'd like to practice, try creating the data set that I made! If you need hints or help, the code I used can be found in <a href="https://github.com/astrad77/Data-Curation?tab=readme-ov-file" target="_blank">this GitHub repository</a>. Once you've tried that, ask your own data science question and find the data to answer it! 

Thanks for reading!