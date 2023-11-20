# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal of this project was to:
- retrive data using APIs
- understand and parse data from JSON format to dataframes
- perform EDA and clean data
- merge different dataframes
- clean data within the merged dataframe
- identifying trends and patterns in data using statistical models

## Process
1. Accessing and Retrieving Data through APIs and Parsing to dataframe

I accessed City Bike API to retrieve stations data for Portland, USA. There were a total of 238 bike stations in Portland at the time of data retrival. This data was then parsed to a dataframe and different manipulations were performed to further asses and understand the data. A subset of the dataframe containing only latitude and longitude data was used in subsequent tasks to access and retrieve required data from Foursquare and Yelp API

For my project, I chose to retrieve data for all art galleries within 1000m radius of the bike stations. I was able to iterate over city bikes dataframe to retrieve required data for art galleries. I iterated over the 238 city bike stations using itterows for foursquare (which proved to be quite slow) and itertuples for Yelp.

![image](https://github.com/Zarmeena667/Statistical-Modelling-with-Python-Project2-LHL/assets/145514413/bfa7d5dc-dacf-4074-9de8-489bd9bd6fb2)


2. Data cleaning, EDA and storage

Once data was retrieved for art galleries location from Foursquare and Yelp the dataframes were further manipulated to a cleaner and more usable form. I also performed EDA to assess the data and finally stored the data to CSV files to be used in other specified tasks.

3. Joining/Merging Dataframes and data manipulation

For this task, I import the CSV files created earlier for citybikes, foursquare and yelp to dataframes. I then merged the three dataframes using inner and outer merge condition. The resulting dataframe from my first merge (final_df = pd.merge(fsqdf, yelpdf, on=['Name'], how='inner'))  had common columns appended with suffixes(-x, -y). I had to then format the merged data frames to have a single lat, longitude, distance and address. I accomplished this through taking the mean of lat_x, lat_y and longitude_x, longitude_y.

4. EDA, data cleaning and data manipulation

I further removed duplicates from  merged dataframe and checked the statistical composition of my data to assess how nulls are affecting my columns. I also used visualization techniques/EDA to explore patterns between different variables as we would be building a linear regression model for the next task. Observing my scatterplots, I decided to run a model for distance and rating. In order to avoid too many null values affecting my data, I further imputed mean values for Rating and Distance using mean.

5. Saving merged dataframe

I finally saved the clean merged dataframe as ff_df as a CSV. 

6. Sqlite database

I used CSV files (citybikes, fsq, yelp and merged data) to create an sqlite database titled 'project_database'.

7. Linear Regression model

I used simple linear regression to test the relationship between distance and rating variable (dependent variable). 


![image](https://github.com/Zarmeena667/Statistical-Modelling-with-Python-Project2-LHL/assets/145514413/7e01f24c-51b6-49b6-8905-c0c936d0da5e)


## Results

It is evident from the supremely low R-squared value of 0.008 that this is not the best fit model. A p-value of less than 0.05 is considered to be statistically significant. The regression output for my model shows a p-value of 0, which means that the distance does not impact the rating.


## Challenges 
1. Itterows is slower compared to itertuples, thereby it wasn't the best choice to access data via Foursquare API.
2. I queried the YELP API a few times and reached the rate limit. I had to create three accounts to get over this problem.
3. Dealing with merged dataframe was challenging due to repeat columns with suffixes.
4. Dealing with NaN values is not as easy as it seems. I am always cautious while deleting NaN values and I think that might pose a problem when creating models in the future.
5. The most amount of time in my data was spent retrieving data and parsing json to dataframes which limited my time for modeling. I'd want to time it better in the future.

## Future Goals
- I'd like to explore apply function from numpy as a faster alternative to itterows and itertuples
- I couldn't find the time to perform multivariate or logistic model and would like to explore for future projects
