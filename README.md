# VIX-Data-Engineer
Analyzing the amount of attrited customers in a credit card database using Microsoft SQL Server and Tableau.

## Table of content  

## Business Objective  
1. Identifying the characteristics of customers who are late in paying credit arrears  
2. Visualizing the characteristics of customers who are late in paying credit arrears  
3. Analyzing the biggest factors that causes customers to be in arrears  

## Exploration  
1. Creating the view ClientData using JOIN to join tables  
```sql
CREATE VIEW ClientData
AS
	SELECT CLIENTNUM, status, Customer_Age, Gender, Dependent_count, Education_Level, Marital_Status, Income_Category, Card_Category, Months_on_book, Total_Relationship_Count, Months_Inactive_12_mon, Contacts_Count_12_mon, Credit_Limit, Total_Revolving_Bal, Avg_Open_To_Buy, Total_Trans_Amt, Total_Trans_Ct, Avg_Utilization_Ratio
	FROM customer_data_history cdh JOIN category_db c ON cdh.card_categoryid = c.id JOIN education_db e ON cdh.Educationid = e.id JOIN marital_db m ON cdh.Maritalid = m.id JOIN status_db s ON cdh.idstatus = s.id
GO
```  
Result:  
![image](https://user-images.githubusercontent.com/96785017/189926743-6b92b7ad-5157-4392-a12c-448350f94f9b.png)  
2. 

