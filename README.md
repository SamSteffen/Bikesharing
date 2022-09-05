# Citi Bike Analysis
An analysis and visualization of NYC Citi Bike data using Tableau.

## Overview
The following is an analysis of NYC Citibike data using Tableau to visualize the findings. The purpose of the analysis is to identify trends and insights from a sample of NYC Citi Bike customer data to make recommendations for implementation of a similar program in Des Moines, Iowa. For this analysis, the data sample was taken from from https://s3.amazonaws.com/tripdata/index.html and shows NYC Citi Bike data for the month of August, 2019.

An initial analysis of the August 2019 sample data revealed the following:
* Total number of trips: 2,344,224

* Total number of customers: 443,865
* Total number of subscribers: 1,900,359
> This suggests that the vast majority of Citi Bike users are subscribers, suggesting that they are probably residents of NYC and intend to utilize the service more than once. 

* Top riding hours: 5-7 p.m.
* Bottom riding hours: 2-5 a.m.
> These findings suggest that the best time to perform necessary maintenance on the bicycles would be between 2-5 a.m.

* Male users: 1,530,272
* Female users: 588,431
* Users of unknown/unspecified gender: 225,521
> These numbers show that the vast majority of Citi bike users identify as male.

We also generated visualizations to show which starting and ending stations were utilized, and with what frequency.

Visualizations of our initial analysis are available here: https://public.tableau.com/app/profile/sam.steffen/viz/Bikeshare_Analysis/NYCStory

To create visualizations of more granular details such as what hour or weekday saw the greatest use of Citi Bikes, changing the datatype of the "trip duration" data was necessary. The results of th

## Results
To convert the "trip duration" data to a datetime datatype, we used Python's pandas dependency. We added an additional column of data to the df so that we could continue to generate length-of-time visualizations, in addition to data pertaining to days of the week and hours/minutes of the day.

We then used this updated data to create additional visualizations representing
1. Bike Utilization (bubble chart)
2. Average Trip Duration (area map)
3. Bike Checkout Times (line graph)
4. Checkout Times by Gender (line graph)
5. Trips by Weekday Per Hour (heat map)
6. Trips by Weekday by Gender (heat map)
7. Trips by Weekday by Gender and User Type (heat map)

To see these visualizations, scroll down or visit the Citi Bike Analysis story on [Tableau Public.](https://public.tableau.com/app/profile/sam.steffen/viz/NYCCitiBikeAnalysis_16623496395200/NYCCitiBike?publish=yes)


1. Bike Utilization (Bubble Chart)

<img width="320" alt="Bike_Utilization" src="https://user-images.githubusercontent.com/104729703/188501010-daa9e665-da78-41df-85bf-22f5d722dd1f.png">

The bubble chart above represents all of the bicycles by ID number in the dataset, and the sum of the length of time they are utilized in seconds. It would probably benefit our analysis to clean the data for the removal of outliars, as some of the larger bubbles here show that customers rent bikes for durations lasting longer than a complete month, which, considering that customers are charged for the time they use the bike, suggests this is probably an error on the user's end or a malfunction of the software used to check a bike in and out.

2. Average Trip Duration (Area Map)

<img width="643" alt="Avg_Trip_Duration" src="https://user-images.githubusercontent.com/104729703/188501025-8373f295-83d7-436f-9d85-eb5516f670ef.png">

The above area map shows the average length of each bike ride by rider age, according to birth year. It's unlikely that riders born prior to 1930 would be utilizing Citi Bikes in 2019 in the quantities indicated, suggesting that the data here is tainted; the error here is likely the cause of user input  or deliberate efforts on the part of the user to obscure personal information. If we isolate the data for users born after 1930, we can see a definitive correlation between age and trip distance. The younger the person, the longer the average length of trip on a Citi Bike, with the exception (outliar) being individuals born in 1969.

3. Bike Checkout Times (Line Graph)

<img width="550" alt="Checkout_times_for_users" src="https://user-images.githubusercontent.com/104729703/188501034-a2d1ebd5-20e2-4df7-ac33-70779372bd30.png">

The above line graph shows the length of time a Citi Bike was checked out for each user. This map is filterable by hour and shows that the vast majority of riders are using Citi Bike for rides that take less than an hour to complete.

4. Checkout Times by Gender (Line Graph)

<img width="674" alt="Checkout_times_by_gender" src="https://user-images.githubusercontent.com/104729703/188501047-ac45ac51-b129-4688-9ff5-cb871c8682d6.png">

The above line graph shows the same information, but creates a distinct line for users who identify as male, female, and those who did not specify their gender. Males utilize the Citi Bike more than females and those who did not specify their gender.

5. Trips by Weekday Per Hour (Heat Map)

<img width="676" alt="Trips_by_wkdy_per_hour" src="https://user-images.githubusercontent.com/104729703/188501061-102424da-e817-4c8c-bf8c-7bb343f29256.png">


The above is a heatmap illustrating the quantity of bikes checked out at certain times of day for all users for each day of the week. The darker the color, the greater quantity of bikes checked out. The map clearly illustrates that customers utilize Citi Bike with greatest frequency on weekday mornings between 6 and 10 a.m., and on weekday afternoons between 4 and 7 p.m. This suggests that most users of Citi Bike use it as a means of commuting to or from work.

6. Trips by Weekday by Gender (Heat Map)

<img width="673" alt="Trips_by_gender" src="https://user-images.githubusercontent.com/104729703/188501107-258dee37-6aea-4fbf-8a50-df7f99a2bd1b.png">

The above is a heatmap illustrating the quantity of bikes checked out at certain times of day for males, females and those who did not specify their gender. The darker the color, the greater quantity of bikes checked out. The map clearly illustrates that males and females both utilize Citi Bike with greatest frequency on weekday mornings between 6 and 10 a.m., and on weekday afternoons between 4 and 7 p.m. This suggests that most users of Citi Bike use it as a means of commuting to or from work.

7. Trips by Weekday by Gender and User Type (Heat Map)

<img width="678" alt="User_trips_by_gender_wkdy" src="https://user-images.githubusercontent.com/104729703/188501124-9fce2d9d-1f74-48a1-b698-5b36d49b409b.png">

The above is a heatmap illustrating the quantity of bikes checked out for each user type (customer/subscriber) and gender (male/female/unknown) for each weekday. The darker the color, the greater the quantity of bikes checked out. The map clearly illustrates that male subscribers are the greatest user population of the Citi Bike program, and that they seem to use Citi Bikes with greater frequency at the end of the week (Thursday and Friday) as opposed to the beginning of the week (Monday and Tuesday). There is also a noticable drop in use on Wednesdays.


## Summary
A high-level summary of our findings yield the following recommendations for implementing a Citi Bike program in Des Moines, Iowa:
- The Citi Bike program would probably fare best to have stations set up within an hours' ride of male-dominated workplaces, and the greatest number of stations within 5 minutes' ride of workplaces, bus stations and other public transit hubs.
- Maintenance on bikes should be performed outside of peak hours, between 2-5 a.m.

Before going ahead and implementing a new Citi Bike program in Des Moines, Iowa, it is worth considering and researching some of the differences between Des Moine and New York City. Among the factors to consider are:
- Bike infrastructure:
    - Does Des Moines have bike lanes/bike paths that would make a high volume of cyclists on the road feasible/safe or would additional infrastructure be required?
- Public transit infrastructure:
    - The fact that the majority of Citi bike users in NYC are utilizing them to take rides that last less than five minutes suggests that users could be riding Citi Bikes to get to and from other modes of faster transportation, such as bus-stops or subway stations. Whether a similar behavior pattern would be the case in a far less densely populated city like Des Moines would require additional research. 
- Population density
- Geographical ratio of residences to workplaces.

### Ideas for Additional Visualizations and Research:
* Utilizing the data we have from NYC, it would also be interesting to look at the average rider pace. Because we know the length of time bikes were checked out for and the geo-coordinates of the starting and ending stations, we should be able to calcuate the geographical distance between starting and ending stations and divide it by the length of time the bike was checked out for to determine each rider's riding pace. This could give us a better sense of the general health/fitness profile of Citi Bike users. We could also look at that data over time and see if transit times get faster for riders as time progresses, and leverage implementation as being in the interest of those in favor of improving public health.

* If we knew how much it costs to rent a Citi Bike, we could also provide helpful data around how much revenue a program stands to generate for the city of Des Moines, or for the company/investor that initiates the program.

* We could also look at traffic data for each city to determine the extent to which fuel emissions are reduced with the implementation of a program that incentivizes people to drive personal vehicles less, exercise more, and otherwise utilize public tranpsortation.
