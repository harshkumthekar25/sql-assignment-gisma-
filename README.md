# sql-assignment-gisma-
assignment on ecommerce domain sql 

Introduction: 
1)	Project objectives: 
The objectives of this project is to design and implement a relational data base system for an Ecommerce platform. The system must manage the data for products, customers, orders and payments, suppliers and order details .
Key goals are: 
-	Applying normalization ( up to 3NF) to eliminate redundancy and anomalies .
-	Defining integrity constraints ( primary keys, foreign keys, NOT NULL , UNIQUE)
-	Implementing CRUD operators ( INSERT, SELECT, UPDATE , DELETE) .
-	Demonstrating advanced SQL queries ( joins, aggregations, subqueries, views, stored procedures, triggers ).
-	Providing clear documentation and a working GitHub repository.

2)	Chosen Domain : 
E- commerce platform 
An e-commerce platform handles: 
-	Customers who register and place orders.
-	Products with prices, stock, suppliers .
-	Orders and Order details
-	Transaction for payments
-	Suppliers who provide products 

This domain involves meaningful one – to many (customers -> orders) and many-to-many (Orders <-> Products via Order_Details) relationships making it ideal for showing a relational database design. 

Relationships: 
Customers ( one – to – many) Orders ( one customer has many orders)
Orders (one-to-many) Order_details ( one order has many line items)
Order_details (many-to-one) Products ( many order details for one product) 
Products (many-to-one) : 1 suppliers (many products from one supplier)
Orders ( one-to-one) Transactions ( one order has 1 payment, optional)

4)	Normalization :
The design follows Third normal form (3NF) .
Unnormalized example ( before normalization ) 
 A single Orders table with repeating groups :


Problems : insertion, update, deletion anomalies .

First Normal Form (1NF) : 
-	Atomic values, no repeating groups. 
-	Each order -  product combination becomes a separate row in Order_Details . 

Second Normal Form (2NF): 
-	Removed partial dependencies 
-	Eg: in a composite key ( order_id, product_id) , Product_Name depends only on product_id.
-	Solution : split into products table 


Third normal form (3NF)
-	Removed dependencies 
Eg: supplier_name depends on supplier_id , not on product_id.
Solution : Separate supplier table 

All tables are in 3NF , ensuring data integrity and this eliminates anomalies .

 Column names of tables : 

Customers(customer_id, first_name, last_name, email, phone_number, registration_date, country)
Orders(order_id, order_date, total_amount, o_status, customer_id)
Order_Details( order_detail_id, order_id, product_id, quantity, price_each)
Products(product_id, product_name, category, price, stock, supplier_id)
Suppliers(supplier_id, supplier_name, contact_name, phone, country)
Transactions(transaction_id, order_id, transaction_date, payment_method, amount)


Foreign keys : Orders.customer_id -> Customers.customer_id; Order_Details.order_id -> Orders.order_id;  
Order_Details.product_id -> Products.product_id ; 
Products.supplier_id -> Suppliers.supplier_id;
Transactions.order_id -> Orders.order_id. 

