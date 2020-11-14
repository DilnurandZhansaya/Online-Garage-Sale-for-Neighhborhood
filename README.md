# Online-Garage-Sale-for-Neighborhood
Database for online ad platform that brings people together to buy, sell, or exchange utilized things.

CREATE TABLE Customers (
customer_id INT,
fname VARCHAR(50),
lname VARCHAR(50),
email CHAR(50),
phone_number INT,
PRIMARY KEY(customer_id)
);

CREATE TABLE customers_order(
order_id INT,
purchase_time DATE,
arrival_time DATE,
PRIMARY KEY (order_id),

customer_id INT,
FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
--Customers should have an order
);

CREATE TABLE Order_details (
delivery_method VARCHAR(50),

order_id INT,
FOREIGN KEY (order_id) REFERENCES customers_order(order_id)
--There can be some details of the order
);

CREATE TABLE Cart (
cart_id INT,
PRIMARY KEY (cart_id),

customer_id INT,
FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
--Customers have a cart where they put their products
);

CREATE TABLE Products (
product_id INT,
name VARCHAR(255),
description TEXT,
price INT,
parking_spaces INT,
area CHAR(12),
category VARCHAR(50),
PRIMARY KEY (product_id)
);

CREATE TABLE Cart_product (
cart_id INT,
FOREIGN KEY (cart_id) REFERENCES Cart (cart_id),

product_id INT,
FOREIGN KEY (product_id) REFERENCES Products(product_id)
--Selected product(s) by customer in cart
);

CREATE TABLE Product_photo (
product_photo_id INT,
url VARCHAR(255),

product_id INT,
FOREIGN KEY (product_id) REFERENCES Products(product_id)
--Product can have a photo
);

CREATE TABLE Dates (
date_of_publication DATE,

product_id INT,
FOREIGN KEY (product_id) REFERENCES Products(product_id)
--A product should have a date of publication
);

CREATE TABLE Seller (
seller_id INT,
fname VARCHAR(50),
lname VARCHAR(50),
PRIMARY KEY(seller_id)
);

CREATE TABLE Contact (
email CHAR(50),
phone_number INT,

seller_id INT,
FOREIGN KEY (seller_id) REFERENCES Seller(seller_id)
--The ways a customer can contact the seller
);
