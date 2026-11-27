# Cyclistic Case Study: Converting Casual Riders into Members
The first case study in my Google Data Analytics Capstone.
> Cyclistic is a fictional company created for this case study.
> ### Scenario:
> I'm a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share
company in Chicago.
> ### About the company:
> Customers who purchase single-ride or full-day passes are referred to as casual riders.
> Customers who purchase annual memberships are Cyclistic members.
> Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders.

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

