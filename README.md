# MySQL-dump-of-restaurants-table
MySQL dump of restaurants table. A collection of JSON documents

For demo purpose only

Popular restaurant example collection/table from another popular NoSQL solution.


1/ Unzip the file with your favourite tool

2/ Load the data inside your MySQL database:

mysql> CREATE DATABASE restaurant;

mysql> USE restaurant;

mysql> SOURCE /tmp/restaurants.sql






Misc


mysql> DESC restaurants;


+-------+---------------+------+-----+---------+------------------+

| Field | Type          | Null | Key | Default | Extra            |

+-------+---------------+------+-----+---------+------------------+

| doc   | json          | YES  |     | NULL    |                  |

| _id   | varbinary(32) | NO   | PRI | NULL    | STORED GENERATED |

+-------+---------------+------+-----+---------+------------------+



mysql> SHOW CREATE TABLE restaurants\G

*************************** 1. row ***************************

Table: restaurants

Create Table: CREATE TABLE `restaurants` (

`doc` json DEFAULT NULL,

`_id` varbinary(32) GENERATED ALWAYS AS (json_unquote(json_extract(`doc`,_utf8mb4'$._id'))) STORED NOT NULL,

PRIMARY KEY (`_id`)

) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci



mysql> SHOW TABLE STATUS\G

*************************** 1. row ***************************

Name: restaurants

Engine: InnoDB

Version: 10

Row_format: Dynamic

Rows: 23907

Avg_row_length: 814

Data_length: 19464192

Max_data_length: 0
 
 Index_length: 0
 
 Data_free: 2097152
 
 Auto_increment: NULL
 
 Create_time: 2018-07-18 17:54:40
 
 Update_time: NULL
 
 Check_time: NULL
 
 Collation: utf8mb4_0900_ai_ci
 
 Checksum: NULL
 
 Create_options: 
        
        Comment: 
