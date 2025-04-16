---
layout: post
title:  "Exploring Renewable Energy and Electricity Prices with Streamlit"
author: Andrew Stradling
description: In this post, I will expand on my previous post's insights. I give some EDA on the electricity prices and renewable energy first, as well as introducing an app I built in Streamlit to explore the data. 
image: /assets/images/leaf.png
--- 

I promised you all that I would talk more about the electricity data, so here we are! I'll give a quick refresher so you don't have to go back. We're trying to see whether the production of renewable energy has any impact on electricity prices in the United States. We have a data set containing average electricity prices for different sectors (residential, industrial, etc.) and total renewable energy produced for each month since 2000. 

The hope is that if we can identify a relationship between renewable energy production and electricity prices, we can adjust production accordingly to lower prices. My initial thought was that because renewable energy is basically infinite (assuming the sun and wind don't give out), increasing renewable energy production would reduce electricity prices. 

Before I introduce the Streamlit app that I built, lets quickly reveiw what the data looks like. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/price_vs_date.png)

This is a scatterplot showing how the average price for electricity (in cents per kilowatt hour) has increased over the past 25 years. This isn't too surprising, considering the increased demand as well as inflation. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/production_vs_price.png)

This is another scatterplot that shows the relationship between total production of renewable energy and average electricity prices. According to this simple graph, it looks like there is a positive relationship between the two, meaning that as we produce more renewable energy, average electricity prices also increase. However, it is important to remember that this is a correlation, not a causal relationship. 

Now, let me introduce you to the app I've made! <a href="https://renewableenergy.streamlit.app/" target="_blank">Click here</a> to be taken to my Streamlit app. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/app.png)

In the app, there are a few functions available to explore the data I've compiled. On the left, there are options to select a range of dates that we want to look at. We can also select which sector's prices (e.g. residential) we want to see. Finally we can also smooth the curves produced so that they are less volatile, averaging over a certain number of months. We can also view the raw data if that interests you.

The first tab shows how both average price and production of renewable energy have changed over time. Changing the options on the left will change how this plot looks. The blue line represents price and the green line represents energy production. Looking at this plot, we can see that generally, both renewable energy production and prices have increased over time. Again, this relationship can likely be attributed to other factors including inflation and increased demand. 

![Figure]({{site.url}}/{{site.baseurl}}/assets/images/app2.png)

The second tab allows us to explore the correlation specifically between production and price. We still have the option of selecting specific dates and sectors. This helps us to visualize exactly how price changes with renewable energy production.

Feel free to explore the app on your own and make your own conclusions! 

Thanks for coming along as I gathered and explored this electricity data! If you'd like to see the source code for the app I built, you can access it on <a href="https://github.com/astrad77/projectapp" target="_blank">my GitHub account</a>. I made it using Streamlit and published it to Streamlit Cloud. For documentation on how to use Streamlit, <a href="https://docs.streamlit.io/" target="_blank">click here</a>. Give it a try with your own data. Thanks for reading! 

