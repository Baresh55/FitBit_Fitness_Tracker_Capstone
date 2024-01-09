A) HOW DOES THE TOTAL DISTANCE CORRELATE TO CALORIE EXPENDITURE FOR THE MOST ACTIVE USERS?

SELECT 
 id, 
 MAX(TotalDistance) AS highest_total_distance,
 calories
FROM 
 my-data-project-401909.FitBit_Fitness_Tracker_data.daily_activity_merged
GROUP BY 
 id, 
 calories
ORDER BY 
 highest_total_distance DESC
LIMIT
 10

Under SELECT statement, I utilized the ‘MAX’ function to establish the highest total distance. I ‘GROUPED BY’ the id and calories column and then ‘ORDERED BY’ the highest total distance in DESC order. Owing to the big size of the data, I applied ‘LIMIT’ to restrict the results to the 10 user ids with the most distance covered.

B) HOW DO THE VERY ACTIVE MINUTES CORRELATE TO THE VERY ACTIVE DISTANCE AND CALORIES BURNT FOR THE MOST ACTIVE USERS?

SELECT 
 MAX(VeryActiveMinutes) AS highest_active_minutes,
 MAX (VeryActiveDistance) AS highest_active_distance,
 Calories
FROM 
 my-data-project-401909.FitBit_Fitness_Tracker_data.daily_activity_merged
GROUP BY 
 Id, 
 Calories
ORDER BY 
 highest_active_minutes DESC,
 highest_active_distance DESC
LIMIT
 10

I used the ‘MAX’ function to establish highest distance and minutes. I also used the ‘GROUP BY’ and ‘ORDER BY’ functions to group and specify the order of the results in ‘DESC’ order. Lastly due to the vast amount of data, I applied the ‘LIMIT’ function to return only 10 results.

C) HOW DO THE FAIRLY ACTIVE MINUTES, LIGHTLY ACTIVE MINUTES AND SEDENTARY MINUTES CORRELATE TO THE MODERATELY ACTIVE DISTANCE, LIGHT ACTIVE DISTANCE, SEDENTARY ACTIVE DISTANCE?

SELECT 
 ModeratelyActiveDistance,
 LightActiveDistance,
 SedentaryActiveDistance,
 FairlyActiveMinutes,
 lightlyActiveMinutes,
 SedentaryMinutes,
 Calories
FROM 
 my-data-project-401909.FitBit_Fitness_Tracker_data.daily_activity_merged
GROUP BY 
 ModeratelyActiveDistance,
 LightActiveDistance,
 SedentaryActiveDistance,
 FairlyActiveMinutes,
 lightlyActiveMinutes,
 SedentaryMinutes,
 Calories
ORDER BY 
 ModeratelyActiveDistance DESC,
 LightActiveDistance DESC,
 SedentaryActiveDistance DESC,
 FairlyActiveMinutes DESC,
 lightlyActiveMinutes DESC,
 SedentaryMinutes DESC
LIMIT
 10

D) TO WHAT EXTENT DO TOTAL DISTANCE AND CALORIES CHANGE FOR USERS OVER A SHORT PERIOD OF TIME?

SELECT 
    ActivityDate,
    SUM(TotalDistance) AS total_distance_change,
    SUM(Calories) AS calories_change
FROM 
    my-data-project-401909.FitBit_Fitness_Tracker_data.daily_activity_merged

GROUP BY 
    ActivityDate 
ORDER BY 
    ActivityDate ASC -- Change to ASC for ascending order
LIMIT
    10;

I applied the ‘SUM’ function on total distance, total steps and total calories to get the total over the 10-day period. Further to this, I used ‘ORDER BY’ to arrange the same in ‘DESC’ order. Lastly I applied the ‘LIMIT’ function to restrict the result set to 5. 

E) WHAT ARE THE MOST ACTIVE DATES WHEN USERS DISPLAY MORE COMPREHENSIVE ACTIVITY PATTERNS IN TERMS OF VERY ACTIVE DISTANCE AND VERY ACTIVE MINUTES?

SELECT 
    ActivityDate,
    SUM(VeryActiveMinutes) AS total_very_active_minutes,
    SUM(VeryActiveDistance) AS total_very_active_distance
FROM 
    my-data-project-401909.FitBit_Fitness_Tracker_data.daily_activity_merged
GROUP BY 
    ActivityDate
ORDER BY 
    total_very_active_minutes DESC, 
    total_very_active_distance 
LIMIT 5;

I used the ‘SUM’ function on very active distance and very active minutes which I named ‘AS’, ‘total very active distance’ and ‘total very active minutes’ respectively. I ‘grouped by’ activity date in order to aggregate data by the dates and ‘ordered by’ total very active distance and total very active minutes in ‘DESC’ order


