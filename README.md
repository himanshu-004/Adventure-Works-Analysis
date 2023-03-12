
![AdventureWorks_Logo](https://user-images.githubusercontent.com/81569893/224526374-bb428d04-fc58-4e07-a1e8-e7aadfc04490.png)



# Adventure Works Analysis

Adventure Works Cycles is a global manufacturing company,to 
design and deliver an end-to-end business intelligence solution.

Adventure Works Cycles needs a way to track KPIs (sales, revenue, profit, returns), compare regional performance, analyze product-level trends and forecasts, and identify high-value customers.



## Contents

* Connect and transform the raw data

* Creating table relationships and data models

* Create new calculated columns and DAX measures

* Design an interactive report to analyze and visualize the data

## Documentation

Check the datasets used in the project [Documentation](https://github.com/himanshu-004/AdventureWorks/tree/main/Documentation)


## Connect and transform the raw data

Access data from database tables, flat files, folders and 
created fully automated data shaping and loading (ETL) procedures

#### The Query Editor

* The Power Query Editor consist various Query Editing tools like 
  table transformations, calculated columns, etc it also consist of
  Formula Bar to write 'M' code and applied steps pane to see the  
  steps applied 

* The main tabs of Power Query Editor are 'Transform' and 
  'Add column'

* The TRANSFORM tab includes tools to modify existing columns   
  (splitting/grouping, transposing, extracting text, etc)

* The ADD COLUMN tools create new columns 
  (based on conditional rules, text operations, calculations, 
  dates, etc)
  

#### Created a calender table
![image](https://user-images.githubusercontent.com/81569893/224528127-249a9291-e00d-40d3-82bc-73757c07f2e4.png)

#### Conditional Columns

* Conditional Columns allow you to define new fields based on logical rules and conditions (IF/THEN statements)

  For example: 
  In this case we’re creating a new conditional
  column called “QuantityType”, which depends on the values in 
  the “OrderQuantity” column, as follows:
  
  If OrderQuantity =1, QuantityType = “Single Item”

  If OrderQuantity >1, QuantityType = “Multiple Items”

  Otherwise QuantityType = “Other”

 #### Hierarchies

* Hierarchies are groups of nested columns that reflect multiple levels of granularity

*  For example, a “Geography” hierarchy might include Country State, and City columns

*  Each hierarchy can be treated as a single item in tables and 
   reports, allowing users to “drill up” and “drill down” through different levels of the hierarchy in a meaningful way
   
 ![image](https://user-images.githubusercontent.com/81569893/224555212-9e4cf465-f1da-4791-8f0b-563db6e411a3.png)
               
## Creating table relationships and data models

#### Data models
 * Data Modeling is one of the features used to connect multiple data sources in BI tool using a relationship. 
   A relationship defines how data sources are connected with each other and you can create interesting data visualizations on multiple data sources.

 ![image](https://user-images.githubusercontent.com/81569893/224555960-dc1d782c-3212-4797-8113-8c4a73b336df.png)

![image](https://user-images.githubusercontent.com/81569893/224556016-3c6a0484-f8f3-4fcd-9dce-fb4baa1944d6.png)

* The above images shows data Modeling
