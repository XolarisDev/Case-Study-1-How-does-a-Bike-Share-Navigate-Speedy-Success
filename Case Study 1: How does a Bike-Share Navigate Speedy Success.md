# Google Data Analytics Professional Capstone
### Case Study 1: How Does A Bike-Share Navigate Speedy Success?


## 1. Introduction

Cyclistic is a bike-share program. The program is popular for leisure rides, but around 30% of users also rely on it for daily commuting. Cyclistic aims to shift its marketing focus towards converting casual riders into annual members as they have proven to be more profitable. By analyzing historical bike trip data, the marketing team aims to understand the differences between annual members and casual riders, determine why casual riders would consider a membership, and explore the impact of digital media on marketing strategies.

## 2. Scenario

As a junior data analyst on the marketing team, the director of marketing believes that the company's success hinges on maximizing annual memberships. Your team's objective is to gain an understanding of how casual riders and annual members utilize Cyclistic bikes differently. With these insights, you will develop a new marketing strategy to convert casual riders into annual members. However, your recommendations must be supported by compelling data insights and professional data visualizations in order to obtain approval from Cyclistic executives.

## 3. Data Analysis Process

In this case study, the six steps of the data analysis process will be used in order to solve this problem. Those 6 steps include:
1. Ask
2. Prepare
3. Process
4. Analyze
5. Share
6. Act

### Step 1: Ask
**Key Task**: Create marketing tactics aimed at converting casual riders into Cyclistic members.

For this case, Lily Moreno who is the director of marketing has assigned me as a junior data analyst to the question: *How do annual members and casual riders use Cyclistic bikes differently?*

### Step 2: Prepare

This step will address the data source that will be used for the analysis and the organization of the data structure.

**Data Source**:  Cyclistic’s historical trip data from Jan 2022 to Dec 2022 which is a public dataset published by Motivate International Inc. will be used to analyze and identify trends. [Click Here](https://divvy-tripdata.s3.amazonaws.com/index.html) for the dataset.

**Data Information**: In the data source, there are 12 files in total following the naming convention of *"YYYYMM-divvy-tripdata"*. Each file contains data for a specific month, including other details such as ride ID, bike type, start time, end time, start station, end station, start location, end location, and member status. 

### Step 3: Process

**Tool**: Microsoft Excel is used to combine the total 12 files into one dataset.

#### Data Combination

Tables representing 12 CSV files have been uploaded, by importing a folder containing the 12 files and then selecting "Combine and Transform Data". This will then open power query, where the rest of the data mangement will happen.

#### Data Exploration

To help ensure data cleanness, we have to check if the dataset has any null values in any column. We can do this in Excel, by using Filters to select empty cells, it appears that there are no ***null*** values in the dataset:

After checking the null values, we also need to check if the dataset has any duplicate values. By selecting the **ride_id** column, go to Home > Conditional Formatting > Highlight Cells Rules > Duplicate Values. It appears that we have no duplicate values:

The trip starts and end times are indicated in the format YYYY-MM-DD hh:mm:ss UTC in the columns *"started_at"* and *"ended_at."* By introducing a new column called ***"ride_time"*** we can compute the total trip duration, by subtracting *"ended_at"* from the *"started_at"* cells. 

We can improve this by categorizing the different times into 4 sections. 
- Under 10 min
- 10 to 30 min
- 30 to 60 min
- 0ver 60 min

This can be done by adding a conditional column, using the ***"ride_time"*** column as an input. There is now a new column, categorizing every row with one of these outputs.

Columns such as ***"day_name"***, ***"hour"*** and ***"month"*** can offer valuable insights into analyzing trips at various times throughout the year. We can do this by selecting the ***"started_at"*** column, then select Add Column > Date and Selecting the appropriate options.

#### Data Cleaning

Part of data cleaning is removing irrelevant, duplicate, corrupted, or incomplete information. With respect to the original question: *How do annual members and casual riders use Cyclistic bikes differently?*

 - With that question in mind, we will delete columns from the dataset that are not relevant to our analysis. We will delete the following columns: ride ID, start time, end time, start station, end station, start location, and end location.
 - 4 new columns are added,***"Month"*** to specify the month, ***Day_Name"*** to specify the day of the week, ***"Hour"*** to specify the hour,***"duration"*** to indicate if the duration category of the trip.
 - we now need to narrow the data down to what is needed by de-duping all of the possible combinations and giving us a count of each possible instance. This can be done by selecting the whole table > Group By > Use the default settings > OK

We now have a new column ***"count"***, finishing our table with a total of 7 columns ready for analysis

![example](Data%20Visualization/Screenshot%202026-03-26%20164239.png)

### Step 4 & 5: Analyze and Share

#### Data Analysis & Visualization

The data has been meticulously stored and prepared for thorough analysis. Relevant information was extracted from multiple tables and then effectively visualized using **Tableau**. The primary objective of this analysis is *to understand the distinct usage patterns of Cyclistic bikes between annual members and casual riders.*

To initiate this comparison, we carefully examine and compare the specific types of bikes that people have utilized this past year.

![TotalBikeType](Data%20Visualization/Screenshot%202026-03-29%20191842.png)

The percentage distribution for each bike type reveals that the electrical bike is the most popular this past year, with a 65.07& total usage. Whereas, about a third of people still prefer classic bikes.

Moving on, we delve into the analysis of trip distributions based on different time parameters. Specifically, we explore the number of trips distributed across months, days of the week, and hours of the day.

![TotalMonth](Data%20Visualization/Screenshot%202026-03-29%20191132.png)

In terms of monthly trips, both casual riders and members exhibit similar patterns, with a higher number of trips occurring during the spring and summer months, and a decline during the winter season. Interestingly, their are more trips from members than casual users, every month throughout the year.

![TotalWeek](Data%20Visualization/Screenshot%202026-03-28%20223919.png)

When comparing trips based on the days of the week, it is evident that casual riders tend to take more journeys over the weekends, while members show a decline in trip frequency during the weekends compared to the rest of the weekdays.

![TotalHour](Data%20Visualization/Screenshot%202026-03-29%20191017.png)

Analyzing trips based on the hours of the day reveals distinct patterns for members and casual riders. Members display two peak periods for trips, occurring in the early morning from around 6 am to 8 am, and in the evening from around 4 pm to 8 pm. In contrast, the number of trips for casual riders steadily increases throughout the day, peaking in the evening and then gradually decreasing.

From these observations, we can infer that members may predominantly use bikes for commuting to and from work on weekdays, while casual riders utilize bikes more frequently throughout the day, particularly on weekends for leisure purposes. Both groups exhibit higher activity levels during the summer and spring months.

To understand the differences in behavior between casual and member riders, the ride duration of trips is compared in the subsequent analysis.

![RideDuration](Data%20Visualization/Screenshot%202026-03-29%20192520.png)

It is important to note that casual riders tend to have longer cycling trips compared to members on average. The average journey length for members remains consistent throughout the year, week, and day. However, there are notable variations in the ride durations of casual riders. Specifically, during the spring and summer seasons, on weekends, and between 10 am and 2 pm during the day, they cover greater distances. Conversely, they have shorter trips between five and eight in the morning.

Based on these findings, it can be inferred that casual riders travel longer distances, approximately twice as much as members, but less frequently. Their longer journeys are often observed on weekends and during the day outside of typical commuting hours, particularly in the spring and summer months, suggesting that they might be cycling for recreational purposes.

***Here are the summary:***

*Casual Rider*

Casual riders exhibit a preference for using bikes throughout the day, with increased usage over the weekends, especially during the summer and spring seasons, for leisure activities. They tend to travel approximately twice the distance of members but take fewer trips overall.

Furthermore, casual riders commonly commence and conclude their journeys near various recreational sites, including parks, museums, coastal areas, and other leisure destinations.

*Member Rider*

Member riders prefer using bikes primarily for commuting purposes during weekdays, particularly in the summer and spring seasons, with higher usage during typical commute hours (8 am and 5 pm). They take more frequent but shorter rides compared to casual riders, with trip durations approximately half as long.

Moreover, member riders tend to start and end their bike journeys near locations such as universities, residential areas, and commercial districts, indicating their reliance on bikes for daily commuting needs.

### Step 6: Act

Following the analysis of disparities between casual and member riders, there is an opportunity to devise marketing strategies to encourage casual riders to convert into members. The following recommendations are suggested:

1. Targeted marketing campaigns could be launched during the spring and summer seasons at tourist and recreational hotspots popular among casual riders.
2. Considering that casual riders are more active on weekends and during the summer and spring, offering seasonal or weekend-only memberships might be an effective approach.
3. Since casual riders tend to have longer bike rides than members, providing discounts for extended ride durations could serve as an incentive for casual riders and possibly encourage members to also ride for longer periods.

