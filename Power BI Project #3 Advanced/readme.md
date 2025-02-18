# Power-BI Project #2
This project includes a complete data transformation using the Power Query Editor, data models are configured and set up in the Model View (relationships). Table features and calculatios are added in the Data View and finally, visuals and reports are designed in the Report View. 

## Loading and Transforming Data
For this project I used the AdventureWorks* datasets that include raw data (Product Categories, Returns Data, Customer Lookup, Calendar Lookup, etc.) and sales data (sales data from 2020 to 2022). All these datasets are imported and loaded into this project as text/csv files.

Using the Power Query Editor I made several changes to the data that included some best practice steps and some more detailed transformation to reduce data redundancy and in other cases to isolate columns to be used into the data model. Note that not all steps of the data transformation process are here but rather a summary of what was done with the data. 

In the data transformation process all the table names were updated to improve readability and follow a single naming convention. In addition, all column hearders were confirmed to be correct and all data types were matched according to the column data type. News columns were added, for example the new column SKU Type to extract all characters before the dash from the Product SKU column. In the Product Style column all zeros (0) were replaced with 'NA'. 

In order to have a general idea of what the composition of the columns is I used data profiling-column quality to check on valid, errors, and empty values. For the effects of this project no duplicates were removed because of the repeating order numbers corresponding to multiple items in stocks as well as customer names across multiple orders. The column distribution gave me a overall idea of the number of distinct and unique records within tables. 
![transform data](https://github.com/user-attachments/assets/c9adb5d1-a5f4-40e4-9c88-d8b854926eef)


## Setting up relationships
Creating a data model means to connect tables via relationships based on a common column field (for example ProductKey or Customer ID). For this project I used a start schema to create relationships between the Sales/Returns Tables and the Calendar, Customer, Product and Territories tables. On the other hand, all product tables (Product, Subcategory, and Category were related in a snowflake schema. For this data model I used only one active relationship between tables to avoid data redundany. In addition, all these single relationships are filtered in a 1:* (one instance of each primary key to many instances of each foreign key) cardinality. 

In this project, there are two fact tables: Sales and Return tables. This means that Calendar, Customer, and Product tables are dimensional and server as the connection between Sales and Returns. 

As part of the data model two hierarchies were created. The first being a geopraphy hierarchy that includes Continent, Country, State and City, and a second hierarchy that include Start of Year, Start of Month, Start of Week, Date. These two hierarchies will be used to filter and drill speficic location and date points were transactions and returns took place. Addionatlly, these will be helpful to identify product sales and returns trends across different geographical zones and data time specific throughout the year, as well using filter context to look at data.  

![Setting up relationships](https://github.com/user-attachments/assets/ed88ac7e-b9a3-475d-b33f-9b3eafc69508)

Some of the DAX measures used:
All Returns: calculates the total number of returns regarless of filter context
All Returns = 
CALCULATE(
    [Total Returns],
    ALL(
        'Returns Data'
    )
)

% of All Returns: divides Total Returns by All Returns
% of All Orders = 
DIVIDE(
    [Total Orders],
    [All Orders]
)

Total Cost= multiplies order quantities in the Sales Data table by the product cost in the Product Lookup table, then calculates the sum
Total Cost = 
SUMX(
    'Sales Data',
    'Sales Data'[OrderQuantity] *
    RELATED(
        'Product Lookup'[ProductCost]
    )
)

*There are over 30 DAX formulas so only these example were described. To see all of them open the Final Project BI-AW.pbix file in this repository. 

## Report View
To construct the report view and visual elements of this report I worked on seven different tabs which I will describe in order. Starting from the Executive Dashboard, this tab highlights the most important facts of the data model and trends discovered by using the DAX formulas. In a snapshot, on the top of the tab there are four cards showing the Total Revenue, Profit, Orders, and Return Rate across the entire dataset from January 2020 to January 2022. 

In addition to these cards, the Executive Dashboard tab includes other visuals elements being a line chart to display the Revenue Trending from January 2020 to January 2022 and it includes a slider filter to change the date range to be shown on the chart. The Clustered bar chart is used to shows the number of Orders by Category (Accessories, Bikes, Clothing), this bar chart is related to all the other visuals in the tab meaning that it will filter the Revenue Trending, Cards, Top 10 Products and the other information based on the category filter that is selected. The Top 10 Products Matrix will also filter the selected product to display the information in the information Cards that are at the top and at the button of the tab. 

![summary](https://github.com/user-attachments/assets/e2d911b2-407f-489f-a055-769473d29a4d)

## Map Tab
This tab contains two visual elements that are a Treemap and an interactive selection map that filters the continent/region to show the total number of orders for that area. 

![map tab](https://github.com/user-attachments/assets/c229b8d7-96ff-45d1-a393-99712907fcd6)

## Product Detail Tab 
In this tab you will find a line chart and an area chart. The first one compares the Total Profit and Adjusted Profit (adjusted profit based on the filter to the left of the chart). The second chart (area chart) reflects the trending filtered by the Product Metric Selection (Orders, Revenue, Profit, Returns, Return %). In addition, this section of the report contains three gauge visuals to illustrate comparison between actual monthly orders, revenue, profit, and their targets. 
![product detail tab](https://github.com/user-attachments/assets/9a4a2d8d-cd02-4e24-ac2a-b241f6e1db16)

## Customer Detail Tab
To describe the Total Customer and Revenue Per Customer the line chart contains a date range with four level of granularity that are Start of Year, Start of Month, Start of Week, and Day. With the different levels of granularity it is possible to drill down to specific data points on the line as well as drilling up to higher periods of time. The Top 1oo Customers table summarizes the N top 100 customer IDs with the highest revenue for the company. In addition, by selecting a customer row the chart will filter other visuals in the section to show the Revenue per Customer and the number of Orders from that selected customer. 
![customer detail tab](https://github.com/user-attachments/assets/33d6e8b0-64f4-4a8f-adec-4f2d572ceabc)

## Decomposition Tree Tab
For this section the decomposition tree visual is used to better understand the distribution of Total Orders for the entire period of the dataset. From the Total Orders the decomposition tree breaks down into category names (Accessories, Bikes, Clothing) and continues to break down into more detailed categories that are Subcategory Name and Product Name. To better understand this visual, see that from the 25,164 Total Orders only 16,983 correspond to Accessories which breaks down to Subcategory Names (Tires and Tubes: 9084, Helmets: 8034, Bottles and Cages: 4485, etc). 
![decomposition tree tab](https://github.com/user-attachments/assets/e6a02c96-e644-4f12-bb02-9f1f474aa555)

## Key Influencers Tab 
In this last section of the report the Key Influencers are used to help understand the factors that drive specific metrics or outcomes. Note that this type of visual is an Artificial Intelligence feature, although it is not entirely relevant to this report itself these key influencers analyze categorical or continious outcomes and identify segments based on a combination of factors which can be used to target specific customer segments and strategize marketing/production efforts. 
![key influencers tab](https://github.com/user-attachments/assets/e3a235b5-6032-4585-aff3-112639765696)



