# PL/SQL Assignment 1:Sunrise Supermarket
**Names:** Kirenga Ngamije Serge
**ID:** 29098
**DBMS Tool used:** Oracle SQL Developer
**1.Business Scenario Summary**
Sunrise Supermarket sells various products to customers who are registered to the system. Customers can place orders which have one or more items. Management wants to know who their customers are, what they buy and how the sales are trending over time. So we are going to create tables with 5 customers, 8 products across 3 categories, 15 orders and 25 order items across multiple dates.

**2.Database Schema and Setup**
Database Schema :This is where we will create tables where data will be placed. Using the code given in the assignment document, we will insert it in our developer and it will generate the tables successfully.

Data Setup: This is where Data will be inserted including customer names, emails, cities; products' data, order dates and order items in general. The table data for query use is as below.

Customers Table: <img width="368" height="135" alt="Customers Table" src="https://github.com/user-attachments/assets/76424acd-ca9a-4697-82f9-2b8e070d94a5" />

Products Table: <img width="278" height="182" alt="Products Table" src="https://github.com/user-attachments/assets/782ff34b-b6db-4e8c-a4b7-78334293905f" />

Orders Table: <img width="243" height="288" alt="Orders Table" src="https://github.com/user-attachments/assets/9748515c-2c24-4e99-a8c2-7376a4094780" />

Order Items Table: <img width="295" height="368" alt="Order Items Table" src="https://github.com/user-attachments/assets/855071d5-e188-4b74-92e5-842968d8c878" />

**3.SQL Queries**
**A.JOIN Queries**
***1.List every order with customer details***
We will use the INNER JOIN to join the orders and customers so that we see each transaction with the customer who made it along with their city.
Syntax: <img width="302" height="36" alt="INNER JOIN Syntax" src="https://github.com/user-attachments/assets/16331615-a108-49a9-8a71-9b4031301d60" />
Query result: <img width="353" height="290" alt="INNER JOIN Query result" src="https://github.com/user-attachments/assets/a53f0bd8-73c3-4780-b2e2-f4ae9147cd06" />

***2.Order items with product attributes***
This is to join order items with products using JOIN to show product category, order item details, product quantity, price and quantities purchased per item.
Syntax: <img width="459" height="39" alt="JOIN Syntax" src="https://github.com/user-attachments/assets/35b11006-cddc-409e-8b2f-20f0873dce7c" />
Query result: <img width="411" height="370" alt="JOIN Query result" src="https://github.com/user-attachments/assets/d0526709-e6bd-47e9-a94b-771fd0527032" />

***3.All customers including those without orders***
We will use LEFT JOIN to join customers and orders to show all customer records, even if a customer has not made an order.
Syntax: <img width="345" height="40" alt="LEFT JOIN Syntax" src="https://github.com/user-attachments/assets/406deee0-f566-451a-8a81-b32c8dfc1296" />
Query result (displaying the null order customer): <img width="325" height="301" alt="LEFT JOIN Query result" src="https://github.com/user-attachments/assets/952085ef-fb36-4e64-9be8-71314e564cf0" />

**B.CTE Query**
***Customers total spend & return customers above average spend***
This query computes each customer's total expenditure using a Common Query Expression (CTE) first, then filters customers
who exceed the average spend.
Syntax: <img width="386" height="156" alt="CTE Query Syntax" src="https://github.com/user-attachments/assets/cbdc39e6-0adc-4827-ad53-9d5732116e79" />
Query result: <img width="305" height="126" alt="CTE Query result" src="https://github.com/user-attachments/assets/440e65fc-d209-4e05-be7d-2bd5df656909" />

**C.Window-function queries**
***1.Rank customers by total spend***
This query ranks customers' total spend from the highest spender to the lowest using DENSE_RANK Based on their purchase amounts.
Syntax: <img width="422" height="110" alt="Window-function query syntax 1" src="https://github.com/user-attachments/assets/f054f74a-8cd9-4d1b-921a-6418196755cd" />
Query result: <img width="308" height="126" alt="Window-function query result 1" src="https://github.com/user-attachments/assets/06ca40ce-491e-49d6-a0d0-c57b4102a39c" />

***2.Numbering customers' orders***
This query assigns a number to each customers' orders using ROW_NUMBER.
Syntax: <img width="495" height="43" alt="Window-function query syntax 2" src="https://github.com/user-attachments/assets/75b9b023-257a-4e5a-ac72-d867af67bb2e" />
Query result: <img width="311" height="288" alt="Window-function query result 2" src="https://github.com/user-attachments/assets/cf4f82cf-2f75-485a-809c-ce905e2cb977" />

***3.Running total of revenue over time***
This query calculates the total of daily revenue with SUM and puts it over the order date with OVER to generate the total of revenue over time.
Syntax: <img width="401" height="133" alt="Window-function query syntax 3" src="https://github.com/user-attachments/assets/7f967bca-ff78-4f4d-ac9a-618738ff741b" />
Query result: <img width="299" height="272" alt="Window-function query result 3" src="https://github.com/user-attachments/assets/fa6e360a-bf2a-45a0-8394-01e33dbf0b84" />

***4.Days between current and previous order***
This query uses LAG to get the previous order date for each customer with more than one order and generates the gap between the previous order and current one.
Syntax: <img width="542" height="136" alt="Window-function query syntax 4" src="https://github.com/user-attachments/assets/7bd5ba6e-7bca-4774-b8b1-887e59a87a28" />
Query result: <img width="440" height="229" alt="Window-function query result 4" src="https://github.com/user-attachments/assets/e6465999-ac5f-4b56-a049-6a2d9d05c294" />

**4.Business Interpretation**
Using the data we have, customers Alice Smith and Bob Jones are the main purchasers of the supermarket which is a very positive sign, but customer Evan Wright hasn't made a purchase, so management should make new promotion tactics like coupons and welcome discounts for new customers to buy products. Overall, Sunrise is on a continuous growth in sales revenue and on a very good level.

**5.Challenges encountered and how they were resolved**
A challenge that was faced was in the CTE Query with handling non-ordering customers in the calculations. It was solved by putting the calculation in NVL function within CTE to force zero outputs for those customers and ensure accurate records.
Another challenge faced was in calculating gaps between orders of customers. Other programs like MySQL have the EXTRACT function for this specific challenge.It was solved by subtracting dates between orders manually to get the result. 

***3.Running total of revenue overcollect cus time***
*8
