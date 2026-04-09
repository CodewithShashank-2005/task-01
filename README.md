# task-01
For a basic E-commerce system, we need four primary entities:  Users: The customers.  Products: The items for sale.  Orders: The record of a purchase.  Order_Items: A junction table to handle the many-to-many relationship between Orders and Products (since one order can have many products, and one product can be in many orders).

-- 1. Create the Database
CREATE DATABASE EcommerceDB;
USE EcommerceDB;

-- 2. Create Users Table
CREATE TABLE Users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 3. Create Products Table
CREATE TABLE Products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    stock_quantity INT DEFAULT 0
);

-- 4. Create Orders Table (1-to-Many with Users)
CREATE TABLE Orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10, 2),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- 5. Create Order_Items Table (Many-to-Many Junction)
CREATE TABLE Order_Items (
    order_item_id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT NOT NULL,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);

For a basic E-commerce system, we need four primary entities:

Users: The customers.

Products: The items for sale.

Orders: The record of a purchase.

Order_Items: A junction table to handle the many-to-many relationship between Orders and Products (since one order can have many products, and one product can be in many orders).
