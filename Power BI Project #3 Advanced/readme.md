# Power-BI Project #2
This project includes a complete data transformation using the Power Query Editor, data models are configured and set up in the Model View (relationships). Table features and calculatios are added in the Data View and finally, visuals and reports are designed in the Report View. 

## Final Report View 
![summary](https://github.com/user-attachments/assets/e2d911b2-407f-489f-a055-769473d29a4d)

## Loading and Transforming Data
For this project I used the AdventureWorks* datasets that include raw data (Product Categories, Returns Data, Customer Lookup, Calendar Lookup, etc.) and sales data (sales data from 2020 to 2022). All these datasets are imported and loaded into this project as text/csv files.

Using the Power Query Editor I made several changes to the data that included some best practice steps and some more detail transformation to reduce data redundancy and in other cases to isolate columns to be used into the data model. Note that not all steps of the data transformation process are here but rather a summary of what was done with the data. 

In the data transformation process all the table names were updated to improve readability and follow a single naming convention. In addition, all column hearders were confirmed to be correct and all data types were matched according to the column data type. News columns were added, for example the new column SKU Type to extract all characters before the dash from the Product SKU column. In the Product Style column all zeros (0) were replaced with 'NA'. 

In order to have a general idea of what the composition of the columns is I used data profiling-column quality to check on valid, errors, and empty values. For the effects of this project no duplicates were removed because of the repeating order numbers corresponding to multiple items in stocks as well as customer names across multiple orders. The column distribution gave me a overall idea of the number of distinct and unique records within tables. 
![transform data](https://github.com/user-attachments/assets/c9adb5d1-a5f4-40e4-9c88-d8b854926eef)


Setting up relationships

![Setting up relationships](https://github.com/user-attachments/assets/ed88ac7e-b9a3-475d-b33f-9b3eafc69508)

Map Tab
![map tab](https://github.com/user-attachments/assets/c229b8d7-96ff-45d1-a393-99712907fcd6)

Product Tab 
![product detail tab](https://github.com/user-attachments/assets/9a4a2d8d-cd02-4e24-ac2a-b241f6e1db16)

Customer Detail Tab
![customer detail tab](https://github.com/user-attachments/assets/33d6e8b0-64f4-4a8f-adec-4f2d572ceabc)

Decomposition Tree Tab
![decomposition tree tab](https://github.com/user-attachments/assets/e6a02c96-e644-4f12-bb02-9f1f474aa555)

Key Influencers Tab 
![key influencers tab](https://github.com/user-attachments/assets/e3a235b5-6032-4585-aff3-112639765696)


