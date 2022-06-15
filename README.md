# Data-Analysis-Twitter-Data

At first we read 1st data sheet from xlsx into Dataframe. Then we access 2nd data sheet. 

We merge the two sheet based on their common username column. We had to change the column name in data sheet 2 for that to work.

We find the null values. We observe that two columns where all null. We removed those columns as no information will be gained from that.

We study the dataframe's basic statistics. Std deviation, percentiles, max, min. We get a general statistical behaviour of data.

We convert date column from object to datetime datatype for easier analysis.

Time column had to split into two columns Time and UTC based on '+'. We convert time column from object to timedelta, for easier analysis. We get extra strings. We remove those extra strings from each row of the time column.

We add year, month, date, week column for visualisation.

We create new metrics. Total Engagement= Shares + Likes + Citations.
Engagement rate (ER)=  (Total Engagement/Total Followers)*100(Assuming friedns and followers are same)

# Visulisation

We plot a Lineplots using seaborn to visulaise Gender based User activity using Engament rate/Total Engagements through time.

We plot a Barplot to visualise cumulative gender based activity(TotalEngagement) on each date. We observe Males get more engagement.

We plot the Engagement rate and Total Engament of each month of year.

We plotted a scatterplots between followersCount and EngagementRate/Total Engagement. We observe many of the engagement happens at lower end of followers count. This uncovers the democratic nature of twitter.

We plot a correlation heat map. As expected total engagement and Engagement Rate is highly correlated. Followers count is positively correlated to total engagement.

Plotting all the time series data with date on x axis and Share, likes, totalEngagement and EngagementRate on y axis. We can see the spikes. These spike may relate to a specific event in time or some developing news.

# User with highest Engagement rate

Next we find user with most engagement for every month. We add the engagement rate of user for each year and month. We then sort it so that user with higher rate of engagement comes on top. Then we select those users for each month and year.

# Classifying users

Since Engagement rate is highly correlated with Total Engagement. And Follower count is less correlerated to Engagement rate. We decided to classify users based on engagement rate.

We add engagement rate for each user and create a new dataframe. From ~40,000 usernames we get unique 15467 usernames. We will classify 15,467 user. Engagement rate is widely spread among user. 75% of users have below 3.125 engament rate. Mean engagement rate is 33.
Some users will have high engagement, even though many engagements happens at lower end of followers

We will Classify users based on quantiles.

We use pandas library qcut method to classify users. Qcut method chooses the bins so that you have the same number of records in each bin. But our data is highly skewed hence we try to divide data into 20 parts and then we saw that mmost of them are zeros and only 10 quantiles have usernames.
We label those quantiles using labels A B C D E F G H I and J. We classify/label the user data as per quantiles column. We use value count to measure number of users in each quantiles.


A     644.
B     898.
C     753.
D     799.
E     768.
F     778.
G     774.
H     770.
I     776.
J    8507.

We have classified users successfully based on Engagement Rate.
We can access any quantile eg.A quantile to classify more labelled data by repeating the process, i.e. We can go further and divide our data more to get top useres.






















