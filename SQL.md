# SQL

---

### Installation:

- Install XAMPP as it is has good GUI tools and easy to learn

[XAMPP Installers and Downloads for Apache Friends](https://www.apachefriends.org/)

- After installation open the application, start Apache and MySQL modules, so that the computer acts a server
- Open this webpage: `localhost/phpmyadmin`
- Installing Error for Mac: **“xampp-osx-8.2.4-0-installer” cannot be opened because the developer cannot be verified.**
    - Close the installation
    - Open system settings > Privacy & Security > Xamp Open Anyway > Mac Password
    - Try Installing now

---

### SQL ( Structured Query Language)

- It is a query language used for management and manipulating data in relational database
- It allows to perform CRUD operations

---

### Types of SQL commands

- **DDL (Data Definition Language)**
    - **CREATE** - Create new database objects
    - **ALTER** - Modify existing database objects
    - **DROP** - Delete existing database object
    - **TRUNCATE** - Remove all rows from table
- **DML (Data Manipulation Language)**
    - **INSERT** - Create new rows in table
    - **UPDATE** - Modify data in table
    - **DELETE** - Delete data from table
    - **SELECT** - Retrieve data from table
- **DCL (Data Control Language)**
    - **GRANT**- Provide access
    - **REVOKE** - Withdraw access
- **TCL (Transaction Control Language)**
    - **COMMIT** - Save database changes & transactions
    - **ROLLBACK** - Undo changes that are committed

---

### DDL Commands

- To `Create` new database we use
    
    ```sql
    CREATE DATABASE database_name
    
    CREATE DATABASE sample
    
    -- Better way to write the above code
    
    CREATE DATABASE IF NOT EXISTS database_name 
    
    CREATE DATABASE IF NOT EXISTS sample
    ```
    
- To `Drop` a database we use
    
    ```sql
    DROP DATABASE database_name
    
    DROP DATABASE sample
    ```
    
- To `Create` a table to a database
    
    ```sql
    CREATE TABLE table_name(
    	column_name column_type,
    	column_name column_type,
    	column_name column_type,
    	column_name column_type
    )
    
    CREATE TABLE users(
    	user_id INTEGER,
    	name VARCHAR(255),
    	email VARCHAR(255),
    	password VARCHAR(255)
    )
    ```
    
- To `Truncate` a table - Delete data inside the table
    
    ```sql
    TRUNCATE TABLE table_name
    
    TRUNCATE TABLE users
    ```
    
- To `Delete` a table
    
    ```sql
    DROP TABLE table_name
    
    DROP TABLE users
    ```
    

---

### Data Integrity

- It refers to accuracy, completeness and consistency of the data stored in a database
- It refers to trustworthy of the data and ensures data is protected from errors, unauthorized changes

### Constraints

- Constraints are rules or conditions that must be met for data to be inserted, updated or deleted in a database

### Transactions

- A sequence of database operation that are treated as a single unit of work

### Normalization

- It is a design technique that minimizes data redundancy and ensures data consistency

---

### Constraints

- Constraints are rules or conditions that must be met for data to be inserted, updated or deleted in a database
- **NOT NULL**
    - This constrain makes sure the attribute has some value in it
    
    ```sql
    NOT NULL
    
    -- Example
    CREATE TABLE user(
    	user_id INTEGER NOT NULL,
    	name VARCHAR(255) NOT NULL,
    	email VARCHAR(255),
    	password VARCHAR(255),
    )
    
    -- This will make sure to add data in user_id and name as it has the constrain
    ```
    
- **UNIQUE**
    - This constrain makes sure the attribute has unique values in it
    
    ```sql
    CREATE TABLE users(
    	userid INTEGER NOT NULL,
    	name VARCHAR(255),
    	email VARCHAR(255) UNIQUE,
    	password VARCHAR(255)
    )
    
    -- This will make sure the user_id has some data in it and email is unique
    -- If user tries to enter same email, it will throw an error
    
    CREATE TABLE user(
    	user_id INTEGER NOT NULL,
    	name VARCHAR(255) NOT NULL,
    	email VARCHAR(255),
    	password VARCHAR(255),
    	
    	CONSTRAINT users_email_unique UNIQUE(email)
    	CONSTRAINT users_email_unique UNIQUE (email, name)
    )
    
    -- This new way of writing CONSTRAINT will help us to have combinations
    -- Here email and name thogether must be unique
    -- General naming style to name constrain is tablename_attribute_constraint 
    ```
    
- **PRIMARY KEY**
    - It is a constrain that sets the attribute as primary key (It’s an attribute which can identify any row uniquely and is not repeated and doesn't have any null values)
    
    ```sql
    CREATE TABLE users(
    	user_id INTEGER PRIMARY KEY,
    	name VARCHAR(255),
    	email VARCHAR(255),
    	password VARCHAR(255),
    	
    	CONSTRAINT users_pk PRIMARY KEY (user_id)
    )
    ```
    
- **AUTO INCREMENT**
    - This constraint will increment every time when every new data is updated
    
    ```sql
    CREATE TABLE users(
    	user_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	email VARCHAR(255),
    	password VARCHAR(255)
    )
    ```
    
- **CHECK**
    - This constrain checks for conditions
    
    ```sql
    CREATE TABLE students(
    	student_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	age INTEGER CHECK(age>6 and age<25),
    	
    	CONSTRAINT students_age_check CHECK (age>6 and age <25)
    )
    ```
    
- **DEFAULT**
    - This will set a default value when no data is entered
    
    ```sql
    CREATE TABLE tickets(
    	ticket_id INTEGER PRIMARY KEY,
    	name VARCHAR(255) NOT NULL,
    	travel_date DATETIME DEFAULT CURRENT_TIMESTAMP
    )
    
    -- DATETIME is the CONSTRAINT that gives the optionto enter the date
    -- CURRENT_TIMESTAMP is a function and most editor will give suggestions 
    ```
    
- **FOREIGN KEY**
    - A Foreign Key is primary key from one table that is used to establish relation with another table
    
    ```sql
    CREATE TABLE customers(
    	customer_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	email VARCHAR(255) NOT NULL UNIQUE,
    )
    
    CREATE TABLE orders(
    	order_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	cutomer_id INTEGER NOT NULL,
    	order_date DATE DEFAULT CURRENT_DATE,
    	
    	CONSTRAINT orders_fk FOREIGN KEY(customer_id) REFERENCES customers(customer_id)
    )
    
    -- CONSTRAINT constraint_name FOREIGN KEY(attribute) REFERENCES table_name(attribute)
    ```
    

---

### Referential Actions

- It tells us If two tables are related with a FOREIGN KEY, then how a change made in one table will effect the related table
- **RESTRICT**
    - It is by default, that will not allow to delete related tables
- **CASCADE**
    - Update, Delete Operations made on one table will automatically update and reflect on the related table
    - 
    
    ```sql
    CREATE TABLE customers(
    	customer_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	email VARCHAR(255) NOT NULL UNIQUE,
    )
    
    CREATE TABLE orders(
    	order_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	cutomer_id INTEGER NOT NULL,
    	order_date DATE DEFAULT CURRENT_DATE,
    	
    	CONSTRAINT orders_fk FOREIGN KEY(customer_id) REFERENCES customers(customer_id),
    	ON DELETE CASCADE,
    	ON UPDATE CASCADE
    )
    ```
    
- **SET NULL**
    - It will set NULL value if the original table is Deleted
    
    ```sql
    CREATE TABLE customers(
    	customer_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	email VARCHAR(255) NOT NULL UNIQUE,
    )
    
    CREATE TABLE orders(
    	order_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	cutomer_id INTEGER NOT NULL,
    	order_date DATE DEFAULT CURRENT_DATE,
    	
    	CONSTRAINT orders_fk FOREIGN KEY(customer_id) REFERENCES customers(customer_id),
    	ON DELETE SET NULL
    )
    ```
    
- **SET DEFAULT**
    - it will set DEFAULT value if the original table is Deleted
    
    ```sql
    CREATE TABLE customers(
    	customer_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	name VARCHAR(255),
    	email VARCHAR(255) NOT NULL UNIQUE,
    )
    
    CREATE TABLE orders(
    	order_id INTEGER PRIMARY KEY AUTO_INCREMENT,
    	cutomer_id INTEGER NOT NULL,
    	order_date DATE DEFAULT CURRENT_DATE,
    	
    	CONSTRAINT orders_fk FOREIGN KEY(customer_id) REFERENCES customers(customer_id),
    	ON DELETE SET DEFAULT 0
    )
    ```
    

---

### ALTER

- It ALTER TABLE command is used to modify structure of an existing table
    - ADD COLUMN
    - DELETE COLUMN
    - MODIFY COLUMN

```sql
-- Add a single cloumn
ALTER TABLE customers ADD COLUMN password VARCHAR(255) NOT NULL

-- Add a single cloumn after a specific column
ALTER TABLE customers ADD COLUMN surname VARCHAR(255) NOT NULL AFTER name

-- Add a multiple cloumns after a specific column
ALTER TABLE cutomers
ADD COLUMN pan_number VARCHAR(255) AFTER surname,
ADD COLUMN joining_date DATETIME DEFAULT CURRENT_TIMESTAMP,

-- Drop a column
ALTER TABLE customers DROP COLUMN pan_number

-- Drop multiple columns
ALTER TABLE customers
DROP COLUMN password,
DROP COLUMN joining_date

-- Modify column
ALTER TABLE cutomers MODIFY COLUMN surname INTEGER

-- Modify Multiple column
ALTER TABEL customers
MODIFY COLUMN surname VARCHAR,
MODIFY COLUMN email INTEGER,
```

- You can add, delete  CONSTRAINTS using ALTER TABLE

```sql
-- ADD CONSTRAIN
ALTER TABLE customers ADD CONSTRAINT customer_age_check CHECK (age >13)

-- DROP CONSTRAIN
ALTER TABLE customers DROP CONSTRAINT customer_age_check 

-- Use both the commands to modify, first drop and add again
```