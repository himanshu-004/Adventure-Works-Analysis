
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

* Conditional Columns allow you to define new fields based 
  on logical rules and conditions (IF/THEN statements)

  For example: 
  In this case we’re creating a new conditional
  column called “QuantityType”, which depends on the values in 
  the “OrderQuantity” column, as follows:
  
  If OrderQuantity =1, QuantityType = “Single Item”

  If OrderQuantity >1, QuantityType = “Multiple Items”

  Otherwise QuantityType = “Other”

 #### Hierarchies

* Hierarchies are groups of nested columns that reflect multiple  
  levels of granularity

*  For example, a “Geography” hierarchy might include Country
   State, and City columns

*  Each hierarchy can be treated as a single item in tables and 
   reports, allowing users to “drill up” and 
   “drill down” through different levels of the hierarchy in a    
   meaningful way
   
![image](https://user-images.githubusercontent.com/81569893/224555212-9e4cf465-f1da-4791-8f0b-563db6e411a3.png)
## Creating table relationships and data models

#### Data models
 Data Modeling is one of the features used to connect multiple data sources in BI tool using a relationship. A relationship defines how data sources are connected with each other and you can create interesting data visualizations on multiple data sources.

 ![image](https://user-images.githubusercontent.com/81569893/224555960-dc1d782c-3212-4797-8113-8c4a73b336df.png)

![image](https://user-images.githubusercontent.com/81569893/224556016-3c6a0484-f8f3-4fcd-9dce-fb4baa1944d6.png)

* The above images shows data Modeling

#### Data tables v/s lookup tables

* Models generally contain two types of tables: data (or “fact”) tables, and lookup (or “dimension”) tables

* Data tables contain numbers or values, typically at a granular level, with ID or “key” columns that can be used to create table relationships

* Lookup tables provide descriptive, often text-based attributes about each dimension in a table

### Creating Snowflake schemas
 
 * Models with chains of dimension tables are often called “snowflake” schemas (whereas “star” schemas usually have individual lookup tables surrounding a central data table)

 ![image](https://user-images.githubusercontent.com/81569893/225237335-43538e80-911a-473c-8b8b-65cac0722697.png)

 * you can see in above screenshort The Sales_Data table can connect to Products using the ProductKey field, but cannot connect directly to the Subcategories or Categories tables

 * By creating relationships from Products to Subcategories (using ProductSubcategoryKey) and Subcategories to Categories (using ProductCategoryKey), we have essentially connected Sales_Data to each lookup table; filter context will now flow all the way down the chain

### Relationship Cardinality 

* Cardinality refers to the uniqueness of values in a column

* For our purposes, all relationships in the data model should follow a “one-to-many” cardinality; one instance of each primary key, but potentially many instances of each foreign key

![image](https://user-images.githubusercontent.com/81569893/225241893-afaf524f-7842-445e-90f1-744e76ce820b.png)

##  calculated columns and DAX measures

### DAX

* Data Analysis Expressions, commonly known as DAX, is the formula language that drives Power BI

With DAX we can

* Add calculated columns and measures to your model, using intuitive syntax

* Go beyond the capabilities of traditional “grid-style” formulas, with powerful and flexible functions built specifically to work with relational data models.

### calculated columns

* Calculated columns are typically used for filtering data, rather than creating numerical values

* Calculated columns generate values for each row, which are visible within tables in the Data view

* Calculated columns understand row context; they’re great for defining properties based on information in each row, but  generally useless for aggregation (SUM, COUNT, etc)

![image](https://user-images.githubusercontent.com/81569893/225292242-314bab1c-e3f4-44ad-a277-db9311914cb2.png)


### Measures

* Measures are DAX formulas used to generate new calculated values

* Use measures to create numerical, calculated values that can be analyzed in the “values” field of a report visual

* Measures are evaluated based on filter context, which means 
they recalculate when the fields or filters around them change 
(like when new row or column labels are pulled into a matrix or 
when new filters are applied to a report)

![image](https://user-images.githubusercontent.com/81569893/225293048-25ef195d-cc0f-422a-b886-f6a41e257c1d.png)

![image](https://user-images.githubusercontent.com/81569893/225293246-03ff5a42-45a3-40fd-b5ca-7dca7518dcb1.png)

### Related

RELATED() = Returns related values in each row of a table based on relationships with other tables

=RELATED(ColumnName)

### Calculate

CALCULATE() = Evaluates a given expression or formula under a set of defined filters

=CALCULATE(Expression, [Filter1], [Filter2],…)

CALCULATE works just like SUMIF or COUNTIF in Excel, except it can evaluate measures based on ANY 
sort of calculation (not just a sum, count, etc); it may help to think of it like “CALCULATEIF”

