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

## Import the Data

Great! Now that we've imported pandas, lets read in our data. The most common method using pandas is to use the `pd.read_csv` function. This is most effective if the values in your data are separated using commas, but can work for other things like URLs or files that do not use commas. 

Here, I use a file called `data.csv` that I obtained from <a href="https://www.kaggle.com/datasets/themrityunjaypathak/pandas-practice-dataset?resource=download" target="_blank">Kaggle</a>. This is a small data set designed for practicing with pandas. Feel free to download this same data set to practice along with me. 

To read this data in, I will use the `pd.read_csv` function (pd is the nickname for pandas that we defined earlier):

`data = pd.read_csv("data.csv")`

I also named the data set `data` in Python for easier use. 

## Preview the Data
With your data now imported, lets get a preview of our data. To get a snapshot of our data, we can use the `head` function:
`data.head()`
If you're using the same data set as I am, the result should look something like this: 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/data_head.png)

We can also get some summary statistics for the numerical columns of our data by using `data.describe`: 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/describe.png)

One other method to explore our data is the `.info` function. This function tells us the names of the columns in our data, how many non-empty entries are in each column, and each column's data type: 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/info.png)
 
In our case, we have 3 integer columns, 1 float column, and an object column. However, we would actually prefer if the Date column is a datetime column rather than an object column. We will do this a bit later. 

## Deal with Missing Values
The next step is to find and deal with any missing values in our data set. To check if missing values exist, we can use `data.isnull().sum()`. This will find any missing values in the data and sum them up for each column. 
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/isnull.png)
We see that we have 1 missing value in the Date column and 2 missing values in the Calories column. 

There are many methods to deal with these missing values. A few include `.dropna` (removes rows with missing values), `.fillna` (fills missing values with a specified rule), `ffill` (fills missing values with the previous non-missing value), and `bfill` (fills missing values with the next non-missing value). For this tutorial, I will use `.dropna` since there are only a few rows with missing values. The code for my example will look like this: `data.dropna(inplace = True)`. Note that the `inplace = True` argument just makes it so that we are modifying the original data rather than making a copy. 

## Change Column Data Types
Perfect! Now that we've dealt with those pesky missing values, we can fix our Date column. We will use a function in pandas called `pd.to_datetime`. The line of code will look like this: 
`data["Date"] = pd.to_datetime(data["Date])`
When we run this code, we get a scary error message!
![Figure]({{site.url}}/{{site.baseurl}}/assets/images/error.png)
It isn't as scary as it looks. Python just wants each entry in the Date column to be in a specific format and for all of the entries to have the same format. It looks like the entries have a couple of different formats, so let's use the suggestion Python provides. Here is the updated code which should fix the issue: `data["Date"] = pd.to_datetime(data["Date], format = 'mixed')`. 

Now, running `data.info()` again, we see that the Date column is now listed as a datetime data type!
There are also pandas functions such as `pd.to_numeric` that can change columns to other data types. 

## Filter Your Data 
Often, you'll want to look at only the part of your data that meets certain conditions. For example, if you had data on NBA players, you might want to only look at those players who average at least 10 points per game. 

In our example, maybe we only want to include the rows where the person burned more than 300 calories. That is, we want our data set to only include entries where the Calories column is more than 300. To do this, we will modify our data set similarly to how we did before: `data = data[data['Calories] > 300]`. By setting `data` equal to the right hand side, we are modifying the original data set. If you would rather not do this, you can name this something else. 

I will also run the code `data = data[data['Duration'] > 100]`. This gets rid of an outlier in the data where duration was listed as 450 when all other durations are 60 or less. 

## Export Your Data
With our data imported, cleaned, and modified, we can now export our data to a new file. This saves all of your changes so that you don't have to do these steps every time you want to use this data! To do this, we can use the function `.to_csv`. This function requires you to name the new file. I will name it "clean_data.csv": `data.to_csv('clean_data.csv')`. This will save the cleaned data file into the folder you are currently working in. You can also specify a location by typing the file path. For help with this, you can check out <a href="https://www.pythoncheatsheet.org/cheatsheet/file-directory-path" target="_blank">this website</a>. 

## Conclusion
Congratulations! You've learned just a few of the basic strategies to import, clean, and manipulate data in Python using pandas. Of course, there are many other steps we could take to modify data to fit our needs. However, these steps you've walked through are fundamental to getting started with data analysis. 

If you didn't try these steps with the data set I provided, try it! If you did, find another data set online and try these steps again. Practice is the best way to get better! 

Thanks for reading!