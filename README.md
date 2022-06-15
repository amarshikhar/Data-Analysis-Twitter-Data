# Data-Analysis-Twitter-Data

At first, we read 1st datasheet from xlsx into Dataframe. Then we access 2nd datasheet.

We merge the two sheets based on their common username column. We had to change the column name in data sheet 2 for that to work.

We find the null values. We observe that two columns were all null. We removed those columns as no information will be gained from that.

We study the dataframe's basic statistics. Std deviation, percentiles, max, min. We get a general statistical behaviour of data.

We convert the date column from object to DateTime datatype for easier analysis.

The time column had to be split into two columns Time and UTC based on '+'. We convert the time column from object to timedelta, for easier analysis. We get extra strings. We remove those extra strings from each row of the time column.

We add the year, month, date, and week column for visualisation.

We create new metrics. Total Engagement= Shares + Likes + Citations. Engagement rate (ER)= (Total Engagement/Total Followers)*100(Assuming friends and followers are the same)

# Visualisation

We plot a Lineplots using seaborn to visualise Gender based User activity using Engagement rate/Total Engagements through time.

We plot a Barplot to visualise cumulative gender-based activity(TotalEngagement) on each date. We observe Males get more engagement.

We plot the Engagement rate and Total Engagement for each month of the year.

We plotted scatterplots between followersCount and EngagementRate/Total Engagement. We observe many of the engagement happens at the lower end of the follower's count. This uncovers the democratic nature of Twitter.

We plot a correlation heat map. As expected total engagement and Engagement Rate are highly correlated. Followers count is positively correlated to total engagement.

Plotting all the time series data with the date on the x axis and Share, likes, totalEngagement and EngagementRate on the y axis. We can see the spikes. These spikes may relate to a specific event in time or some developing news.

# User with the highest Engagement rate

Next, we find the user with the most engagement for every month. We add the engagement rate of users for each year and month. We then sort it so that the user with a higher rate of engagement comes on top. Then we select those users for each month and year.

# Classifying users

Since Engagement rate is highly correlated with Total Engagement. And the Follower count is less correlated to the Engagement rate. We decided to classify users based on engagement rate.

We add an engagement rate for each user and create a new dataframe. From ~40,000 usernames we get unique 15467 usernames. We will classify 15,467 users. 

The engagement rate is widely spread among users. 75% of users have a below 3.125 engagement rate. The mean engagement rate is 33. Some users will have high engagement, even though many engagements happen at the lower end of followers

We will Classify users based on quantiles.

We use the pandas library qcut method to classify users. Qcut method chooses the bins so that you have the same number of records in each bin. But our data is highly skewed hence we try to divide data into 20 parts and then we saw that most of them are zeros and only 10 quantiles have usernames. We label those quantiles using labels A B C D E F G H I and J. We classify/label the user data as per the quantiles column. We use value count to measure the number of users in each quantile.

A 644. B 898. C 753. D 799. E 768. F 778. G 774. H 770. I 776. J 8507.

We have classified users successfully based on Engagement Rate. We can access any quantile eg. A quantile to classify more labelled data by repeating the process, i.e. We can go further and divide our data more to get top users.





















