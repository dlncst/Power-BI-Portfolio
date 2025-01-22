# Power-BI Project #2
This folder contains my second project of the Business Intelligence Power BI series. This project includes a more in depth data cleaning, transformation and visualization. Within this folder you will find the dataset used, StudentData.csv that contains the data of students and StudentTestingData that contains the scores for math and reading subjects. 

This project followed the structure below:
1. Data discovery:
  - Establishing connections to data sourcers
  - Power Query for data cleaning and transformation
2. Data modeling:
  - Build relationships between datasets
  - An intro to DAX calculations
3. Data visualization: 
  - Creating visuals 
  - Adding pages
4. Data sharing:
  - Creating understandable visual reports
  - Share reports to Power Service and external destinations
  - Share, access and security
  - Set up automatic data updates

Why having a structured data model and using POWER BI (mainly start vs snowflake)
1. Performance optimization
2. Strong data model
3. Scalability
4. Enhance usability 

In the making of this project I achieved the following: 
- Connect to a cloud data source (github) and load the data
- Power query/data transformation: replace values blank to null, fill, sample columns (to merge columns etc), renaming
-Visual with stacked bar chart for TestScores
-Visual with stacked column chart for Students
-Created relationship (model view) for TestScores and Students (studentid and student number)
-Created hierarchies (grouping information into smaller levels of granularity) and grouping columns into folders 
-Created matrix table
-Create DAX for TestScores
-Visual edits: labels, titles, gridlines, x and y axis, change defaults from sum to averages, etc.
-Customized themes 
-Actionable buttons, images
-Conditional formatting 
-Text filter function
-Added QA AI feature
-Set up pages>tooltip for charts tooltips
-Share to Power BI service and publish to myworkspace powerbi.con
-Scheduled data auto refresh
