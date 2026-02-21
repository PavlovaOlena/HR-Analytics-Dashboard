# HR Analytics Dashboard

This project presents an interactive Power BI dashboard designed to analyze employee engagement, satisfaction, and work-life balance across different business units. The dashboard provides a clear overview of key HR metrics, helping management identify strengths, areas for improvement, and trends over time.

⚙️ <b>Project Development Steps</b>

1. Data Connection & ETL Process: 
- Connected to raw data sources in CSV format.
- Used Power BI Query Editor to perform ETL (Extract, Transform, Load) operations, including data cleaning, error correction, and table standardization.
- Ensured that all datasets were accurate, reliable, and ready for analytical use.

2. Data Modeling : Built a data model by defining logical relationships between data tables.

3. Data Visualization: 
- Designed KPI indicators to display key performance metrics.
- Created bar charts, line charts, and histograms for category comparison and trend detection.
- Applied interactive filters and slicers to allow dynamic data exploration.

4. Advanced DAX Calculations: 
Developed custom DAX (Data Analysis Expressions) measures to enable deeper insights and precise calculations across metrics.

<b>IsActive (Employee Status):</b>
IsActive = IF('employee_data'[EmployeeStatus] = "Active", 1, 0)

<b>Age:</b>
Age = DATEDIFF(employee_data[BirthDate], TODAY(), YEAR)


<b>TenureYears (Employee Tenure):</b>
TenureYears =
VAR EndDate =
    IF(
        ISBLANK('employee_data'[ExitDate]),
        TODAY(),
        'employee_data'[ExitDate]
    )
RETURN
DATEDIFF('employee_data'[StartDate], EndDate, YEAR)

<b>Average Satisfaction (%):</b>
% AverageSatisfaction = AVERAGE(employee_engagement_survey_data[Satisfaction])/5

<b>Calendar Table (continuous date list):</b>
Calendar = CALENDAR(MIN('employee_engagement_survey_data'[Survey Date]), MAX('employee_engagement_survey_data'[Survey Date]))

<b>Month-Year Label:</b>
MonthYear = FORMAT('Calendar'[Date], "MMM-YYYY")

<b>Month Start Date:</b>
MonthStart = DATE(YEAR('Calendar'[Date]), MONTH('Calendar'[Date]), 1)

5. Dashboard Creation: Combined all visuals and insights into a cohesive, interactive dashboard for HR analytics that answers the following <b>questions</b>:
   
<b>What is the overall level of employee engagement and satisfaction?</b>

The overall level of employee engagement and satisfaction remains stable at approximately 60% across all divisions of the company. This indicates a relatively stable dynamic of employees’ emotional involvement in work processes and their overall satisfaction with working conditions.

<b>Are there specific departments or business units where engagement and satisfaction are lower than the company average?</b>

Yes, the analysis of the indicators shows that the level of engagement is lower than the company average in the Production and Admin Offices divisions, while the level of satisfaction is lower than the average in Admin Offices. This may indicate the need to study the reasons for such results in more detail and implement targeted measures to increase motivation and improve working conditions in these departments.

<b>How has the work-life balance changed over the past year?</b>

The work-life balance has remained stable at around 60% over the past year. This means that there have been no significant changes in the perception of the balance between professional and personal responsibilities by employees, but there is potential for further improvement in this indicator.

<b>How many employees have we lost, and can we see their performance indicators?</b>

During the reporting period, the company lost 387 employees. At the same time, the vast majority of them (approximately 90%) had performance indicators at the level of "fully meets" or "exceeds".

🚀 <b>Tools & Technologies:</b>
- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query
- CSV Data Sources
