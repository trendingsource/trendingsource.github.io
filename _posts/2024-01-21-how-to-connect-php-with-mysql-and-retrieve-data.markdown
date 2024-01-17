---
layout: post
title: "How to Connect PHP with MySQL and Retrieve Data"
date:   2024-01-21 17:51:39 +0000
categories: "Programming"
excerpt_image: https://www.zend.com/sites/default/files/image/2020-04/code.png
image: https://www.zend.com/sites/default/files/image/2020-04/code.png
---

### Connecting to Database
To connect to your MySQL database and retrieve data using PHP, you will first need to establish a connection. This is done with the mysqli_connect() function. You will need to provide the hostname, username, password, and database name as parameters:
```php
$db = mysqli_connect("hostname", "username", "password", "database_name");
```
You should then check that the connection was successful, and handle any connection errors:
```php 
if (!$db) {
die("Connection failed: " . mysqli_connect_error());
}
```

![](https://www.devopsschool.com/blog/wp-content/uploads/2020/02/xampp-1.png)
### Executing a Query
Once connected, you can execute queries to retrieve data from your database tables. For example, to select all records from a 'users' table:
```php
$sql = "SELECT * FROM users";
$result = mysqli_query($db, $sql);
```
The mysqli_query() function executes the SQL query on the database connection. 
### Fetching and Outputting Data
To fetch the data and output it, you can use a while loop with mysqli_fetch_assoc(): 
```php
if(mysqli_num_rows($result) > 0) {
while($row = mysqli_fetch_assoc($result)) {
echo "ID: " . $row["id"] . " - Name: " . $row["name"] . "<br>"; 
}
} else {
echo "No results";
}
```
This will loop through each row returned and output the data.
### Closing the Connection
Lastly, you should close the database connection when done to free up resources:
```php
mysqli_close($db);
```
By following these steps, you can easily **connect PHP to MySQL** and retrieve data from your database tables to use or display on your website.
### Performing Multiple Queries
To execute multiple queries in one database connection, you can use the mysqli_multi_query() function. This allows running multiple SQL statements sequentially without reconnecting.
For example, to update a table and select the updated data:
```php
$sql = "UPDATE users SET name='John' WHERE id=1; SELECT * FROM users";
mysqli_multi_query($db, $sql);
```
The queries are separated by semicolons. mysqli_multi_query() returns TRUE on success. You can then retrieve results from each query statement.
### Creating Tables Programmatically
While you cannot directly create tables from PHP code, you can use PHP to dynamically generate and execute SQL CREATE TABLE statements on your database. 
For example:
```php 
$table_name = "products";
$sql = "CREATE TABLE $table_name (
id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, 
name VARCHAR(30) NOT NULL
)";
mysqli_query($db, $sql);
```
This allows your PHP application to programatically generate table schemas rather than writing static CREATE statements. Just be sure to validate and sanitize any user-provided table details.
So in summary, through functions like mysqli_connect(), mysqli_query(), and mysqli_multi_query() - PHP provides an easy way to interface with MySQL for **creating, updating, selecting and manipulating data** on your database directly from your application code.
 ![How to Connect PHP with MySQL and Retrieve Data](https://www.zend.com/sites/default/files/image/2020-04/code.png)