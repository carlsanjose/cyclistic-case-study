# Cyclistic Case Study: Converting Casual Riders into Members
The first case study in my Google Data Analytics Capstone.
> Cyclistic is a fictional company created for this case study.
> Scenario: I'm a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share
company in Chicago. The director of marketing believes the company’s future success
depends on maximizing the number of annual memberships. Therefore, your team wants to
understand how casual riders and annual members use Cyclistic bikes differently. From these
insights, your team will design a new marketing strategy to convert casual riders into annual
members. But first, Cyclistic executives must approve your recommendations, so they must be
backed up with compelling data insights and professional data visualizations.
> About the company: In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown
to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across
Chicago. The bikes can be unlocked from one station and returned to any other station in the
system anytime.Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to
broad consumer segments. One approach that helped make these things possible was the
flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships.
Customers who purchase single-ride or full-day passes are referred to as casual riders.
Customers who purchase annual memberships are Cyclistic members.Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers,
Moreno believes that maximizing the number of annual members will be key to future growth.
Rather than creating a marketing campaign that targets all-new customers, Moreno believes
there is a solid opportunity to convert casual riders into members. She notes that casual riders
are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into
annual members. In order to do that, however, the team needs to better understand how
annual members and casual riders differ, why casual riders would buy a membership, and how
digital media could affect their marketing tactics. Moreno and her team are interested in
analyzing the Cyclistic historical bike trip data to identify trends.

## Business Question:
How do casual riders and annual members use bikes differently, and how can Cyclistic convert casual riders into members?

## Key Findings
- Casual riders ride about 60% longer than members (median monthly average 19:31 vs. 12:17).
- Casual riders ride less often than members.
- Casual use peaks on Sundays and in May to July; member use stays steady all year.

## Recommendations
1. Pilot a summer weekend membership
2. Show cost savings on long rides
3. Prompt in the app after a long ride

## Tools and methods
Excel (XLOOKUP, COUNTIF, pivot tables) for analysis, Tableau for visualization, HTML/CSS/JS for the presentation.

## Data and limitations
- Source: can be found in the /data folder.
- Most monthly maximum ride lengths sit just under 60 minutes, which suggests capped data.
- This analysis uses monthly summaries, so it can't explain why riders behave this way.
- Add rider surveys for feedback to diversify data.

## Files
| File | Description |
|---|---|
| index.html | Stakeholder presentation |
| data/summary_table.xlsx | Cleaned summary tables |
| images/ | Tableau chart exports |

## What I learned during the analysis
- I found out that CSV files are prone to data loss. I noticed that the datatime format in the started_at and ended_at only had the timestamps left after saving the data as CSV. So, I saved each CSV as an Excel workbook and proceeded with the analysis from there.
- I organized all the workbooks into a single folder. I thought having all the data inside just one workbook would make 12 months' worth of data easier to work with, so I tried to use SQLite to combine all the workbooks in a single local database. However, I realized that the SQLite db I was using could only import data from CSV files so I had to convert files into xlsx then csv and v.v., so that wouldn't be as efficient, specially since I was uploading the files manually. Then I thought, "What if I used a Python script to automate the conversion?", so I moved to using Python.
- I used Claude to generate a Python script using pandas to combine my 12 months' of Excel workbooks into one. Only to find out that Excel has a row limit of 1,048,576 rows, so I asked Copilot in VSCode to split the output into several sheets in the same workbook. (Because I had a total of 6,294,451 rows of data across the 12 individual workbooks).
- I changed my approach: the Python script reads the data from the 12 Excel workbooks, outputs a combined CSV to bypass Excel's row limit. This approach worked, no data was lost and I was able to import CSV data into the SQLite database.
- I then realized that writing SQL scripts wouldn't be as efficient if I could've performed my analyses with Excel's pivot tables instead. So I switched my approach again to performing my analysis on each month's workbook.
- The pivot tables showed the average ride length of members and casual riders per month, and the days of the week that each customer type rode longest and shortest.

