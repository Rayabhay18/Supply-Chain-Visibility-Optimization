Objectives:
Import the supply chain dataset into Power BI.
Perform Data preprocessing:
Handle missing values and duplicates.
Correct data types.
Rename columns where necessary.
Apply required data transformations using Power Query.Design a star schema data model:  
         3. Design a star schema data model:
Create appropriate fact and dimension tables.
Define primary and foreign key relationships.
Ensure the model supports business analysis efficiently.
Data set link : https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis
click Transform data, Move to Power Query Editor (PQE)

Rename the table as Fact_table
Remove columns Customer email, customer password, order zipcode

Duplicate the fact_table. Replace the table as Dim_Customer
Home -> choose columns. select Cusomer_id, Customer_city, customer_contry, Customer_Fname, Customer_Lname, customer_Segment, customer_street, customer_zipcode, customer_state
Remove duplicates (home -> Remove rows -> remove duplicates) as Customer_id 

Duplicate the fact_table. Replace the table as Dim_Product
Home -> choose columns. select Product_card_id, product_category_id, Product_name, Product_price, product_status, Category_id, Department_id
Remove duplicates (home -> Remove rows -> remove duplicates) as Product_card_id

Duplicate the fact_table. Replace the table as Dim_Category
Home -> choose columns. select Category_id
Remove duplicates (home -> Remove rows -> remove duplicates) as category_id

Duplicate the fact_table. Replace the table as Dim_Shipping
Home -> choose columns. select Days for shipping, days for shipment, delivery status, late delivery risk, shipping date, shipping mode 
Select all columns (by pressing ctrl). Remove duplicates
click add_columns -> Index column -> From 1
Rename column name as shipping_id
In PQE select Fact_table, Home -> Merge queries
 (above)Fact table (below) Dim_shipping 
Select Common columns on both table (by pressing ctrl)
Join: Left outer
Click ok

 In fact table, last column table will appear expand it and select only Shipping_id



Duplicate the fact_table. Replace the table as Dim_location
Home -> choose columns. select Market, Order city, order country, order region, order state
Select all columns (by pressing ctrl). Remove duplicates
click add_columns -> Index column -> From 1
Rename column name as Location_id
In PQE select Fact_table, Home -> Merge queries
 (above)Fact table (below) Dim_location
Select Common columns on both tables (by pressing ctrl)
Join: Left outer
Click ok

 In fact table, last column table will appear expand it and select only Location_id

Duplicate the fact_table. Replace the table as Dim_Department
Home -> choose columns. select Department_id
Remove duplicates (home -> Remove rows -> remove duplicates) as Department_id
 
Modeling → New Table
Dim_Date = 
CALENDAR (
    MIN ( Fact_table[order date (DateOrders)] ),
    MAX ( Fact_table[shipping date (DateOrders)] )
)
 Create new columns for each 
Year = YEAR(Dim_Date[Date])
Month Number = MONTH(Dim_Date[Date])
Month = FORMAT(Dim_Date[Date], "MMMM")
Quarter = "Q" & QUARTER(Dim_Date[Date])
Week = WEEKNUM(Dim_Date[Date])
Day = DAY(Dim_Date[Date])
Day Name = FORMAT(Dim_Date[Date], "dddd")
Create relationship between fact_table and dim_Date
   Dim_Date[Date] → Fact_table[order date (DateOrders)] 
Cardinality: one (Dim_date)  to many (Fact table)
Active

Dim_Date[Date] → Fact_Orders[shipping date (DateOrders)]
Cardinality: One-to-Many (1:*)
Inactive
 Click close and apply in PQE
Click save frequently
