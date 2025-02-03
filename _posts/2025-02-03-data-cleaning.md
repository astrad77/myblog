---
layout: post
title:  "From Raw to Ready: Data Cleaning in Python"
author: Andrew Stradling
description: This is a quick tutorial to help you understand how to get set up for data analysis in Python. 
image: /assets/images/tree.jpg
--- 

So, you've got your hands on a data set. But how do you start using it in Python? How do you get it into the format that you need so that you can analyze it? Don't worry! In this post, I'll show you a few of the basic tools in Python that will help you get started. 

## Pandas
In this tutorial, I will be using a well-known library in Python called pandas. Pandas provides the tools that we need to import, manipulate, and clean data. To use Pandas, we will import it by running this line of code: 

```import pandas as pd```

By specifying that we are importing the pandas library as the nickname "pd", we reduce the amount of typing we will have to do later. 

## Step 1: Import the Data

Great! Now that we've imported pandas, lets read in our data. The most common method using pandas is to use the `pd.read_csv` function. This is most effective if the values in your data are separated using commas, but can work for other things like URLs or files that do not use commas. 

Here, I use a file called `data.csv` that I obtained from <a href="https://www.kaggle.com/datasets/themrityunjaypathak/pandas-practice-dataset?resource=download" target="_blank">Kaggle</a>. Feel free to download this same data set to practice along with me. 

To read this data in, I will use the `pd.read_csv` function (pd is the nickname for pandas that we defined earlier):

```data = pd.read_csv("data.csv")```

I also named the data set `data` in Python for easier use. 

## Step 2: Preview the Data
With your data now imported, lets get a preview of our data. To get a snapshot of our data, we can use the `head` function:
```data.head()```
If you're using the same data set as I am, the result should look something like this: 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/data_head.png)

We can also get some summary statistics for the numerical columns of our data by using `data.describe`: 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/describe.png)