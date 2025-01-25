As a data analyst, my goal extends beyond just building dashboards it's about uncovering the stories within the data to drive informed decisions.

Recently, I analyzed an Uber dataset to reveal key patterns, trends, and actionable insights. Here’s how I approached it:



🔍 Steps Taken

⏩ Data Cleaning: Ensured accuracy and consistency by cleaning and formatting the dataset.



⏩ Time and Date Separation: Using Power Query, I split the combined date and time column into two separate columns. I achieved this by using a space delimiter, making it easier to work with each component independently.



⏩ Grouping and Transformation:



Grouped trips by the day of the week using DAX:



 ⏩ Day_of_the_week = WEEKDAY(UberDataset[START_DATE.1],1)



⏩ Categorized trips into time periods (Morning, Afternoon, Evening) for better granularity:



DAX

Trip_period = 

SWITCH( 

   TRUE(), 

   FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") >= "00:00" && FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") < "06:00", "Early Morning", 

   FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") >= "06:00" && FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") < "12:00", "Morning", 

   FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") >= "12:00" && FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") < "15:00", "Afternoon", 

   FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") >= "15:00" && FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") < "18:00", "Late Afternoon", 

   FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") >= "18:00" && FORMAT('UberDataset'[DEPARTURE_TIME], "HH:MM") <= "23:59", "Evening", 

   "Unknown" 

) 



📊 Observations 



▪️ Total Trips: 1155

▪️ Business Trips: 1078 (93.3%)

▪️ Personal Trips: 77 (6.7%)

▪️ Busiest Month: October

▪️ Busiest Day: Friday (206 trips, 17.8% of total trips)

▪️ The least Busiest Day of the week: Wednesday with 147 trips

▪️ Peak Booking Times: Evening, followed by Late afternoon and Afternoon

▪️ The most common Pick up and Drop off location is Cary City



🛠️ Tools Used

Power BI: Data visualization and modeling

Power Query: For data transformation, including separating date and time.

DAX: For custom calculations and categorizations



💡 Insights & Recommendations



⏩ Optimize for Peak Times: Target Fridays and evenings for marketing and operational readiness.

⏩ Boost Personal Trips: Explore strategies to increase engagement, such as promotions for non-business use.

⏩ Prepare for Seasonal Peaks: October showed the highest trip demand, possibly linked to specific events or trends.
