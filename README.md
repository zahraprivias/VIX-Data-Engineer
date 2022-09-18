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
2. Identifying how many customers (Top 10) will be attrited according to gender divided by age groups  
Male Customers  
```sql
SELECT TOP 10 status AS Status, Customer_Age AS Age, [Total] = COUNT(Gender)
FROM ClientData
WHERE status LIKE 'Attrited Customer' AND
Gender LIKE 'M'
GROUP BY status, Customer_Age
ORDER BY Total DESC
```  
Results:  
<img width="145" alt="image" src="https://user-images.githubusercontent.com/96785017/190904692-07798a60-6b83-4fa5-8d4b-42bbe0c23003.png">  
Female Customers  
```sql
SELECT TOP 10 status AS Status, Customer_Age AS Age, [Total] = COUNT(Gender)
FROM ClientData
WHERE status LIKE 'Attrited Customer' AND
Gender LIKE 'F'
GROUP BY status, Customer_Age
ORDER BY Total DESC
```  
Result:  
<img width="147" alt="image" src="https://user-images.githubusercontent.com/96785017/190904597-4a910a3e-6394-4385-a91a-341d058268ad.png">  
3. Identifying the amount of attrited customers according to income category  
```sql
SELECT Income_Category, [Total Customer] = COUNT(CLIENTNUM)
FROM ClientData
WHERE status LIKE 'Attrited Customer'
GROUP BY Income_Category
ORDER BY [Total Customer] DESC
```  
Result:  
<img width="161" alt="image" src="https://user-images.githubusercontent.com/96785017/190905092-a4c7447b-8b20-48c6-a8e4-b1c84a19527e.png">  

## Visualization  
1. Male Attrited Customers by Age  
![image](https://user-images.githubusercontent.com/96785017/190914961-9143ce80-cf1f-4af5-a221-7279080de302.png)





