# Databases Fundamentals

---

### Importance of Data

- DATA is the new oil
- Al the apps we use on daily bases store collect data and based on the analysis, New UI elements features are implemented for better attention

---

### What are Databases?

- It is a shared collection of logically related data and description of the data, designed to meet the information needs of an organization
- **Data Storage:** Store large amount of structured data with easy access
- **Data Analysis:** Perform complex analysis, generate reports and provide insights
- **Record Keeping:** Keep records of important things like financial transitions
- **Web Applications:** Essential components of web page, basic example is like login

---

### CRUD Operations

- All the databases follow only these Operations
- Create
- Retrieve
- Update
- Delete

---

### Properties of ideal database

- **Integrity:** Data should be accurate and consistent
- **Availability:** There should be never a down time
- **Security:** Secure all the data with security protocols
- **Independent of application:** Can run on any platform
- **Concurrency:** Update data live from one database to multiple platforms

---

### Types of databases

- **Relational Database**
    - Also Known as SQL Database
    - It uses relational to organize data into tables with rows and columns
    - Example: MySQL, Postgres SQL, Oracle
- **NoSQL Database**
    - It is designed to handle large amount of unstructured data
    - Unstructured data such as document, image, video
    - Example: MongoDB
- **Column Database**
    - Stores data in columns rather than rows
    - Useful for data warehousing and analytical applications
    - Example: Amazon Redshift, Google Big Query
- **Graph Database**
    - It is used to store and query graph structured data
    - Used mostly in social media and recommendation systems
    - Example: Neo4j, Amazon Neptune
- **Key-Value Database**
    - It stores data as a collection of keys and values
    - It is especially used to store cache memory
    - Example: Redis

---

### Relational Databases

- It uses relations to store data in tables as rows and columns
- Columns are known as attributes
- Number of columns gives the degree of the relation
- Rows are known as tuples
- Number of rows gives the cardinality of the relation

---

### DBMS (Data Base Management System)

- A DBMS is a software system that provides the interfaces and tools needed to store, organize and manage data in a database
- It acts as intermediate between the database and the application or user

### Functions of DBMS

- **Data Management:** CRUD operations
- **Integrity:** accurate and consistent data
- **Concurrency:** Updates multiple platforms seamlessly
- **Transaction:** Modified data must be either successful or must not happen
- **Security:** Access authorization
- **Utilities:** Import, Export, Backup

---

### Keys

- A Key in a database is an attribute or set of attributes that uniquely identify a row in a table.
- Key ensures integrity and reliability of a database by enforcing constrains on the data and establish relationships
- **Super Key**
    - A Super Key is combination of columns that uniquely identifies any row within a table
- **Candidate Key**
    - Simplest Super Key
    - It is the smallest set of attributes that can be used to uniquely identify any row within a table
- **Primary Key**
    - A Primary Key is a unique identifier for each tuple in a table
    - There can be only one primary key
    - Primary Key should NOT have any NULL values
- **Alternate Key**
    - An alternate key is a candidate key that is not primary key
- **Composite Key**
    - Composite key is primary key that is made up of two or more attributes
    - This is used when single attribute cannot be a primary key
- **Surrogate Key**
    - Surrogate key is a primary key that is made when any combination of attributes doesn’t form a primary Key
    - We create a new attribute that is assigned as primary key
- **Foreign key**
    - A Foreign Key is primary key from one table that is used to establish relation with another table

---

### Cardinality of Relationships

- Cardinality in database relationships refers to number of occurrences of an entity in a relationship with another entity.
- One to One relationship - person-drivers license - needs only 1 table
- One to Many relationship - student - college branch - needs 2 tables
- Many to Many relationship- Restaurants- food - needs 3 tables

---

### Drawbacks of Databases

- Complexity: Complex and time consuming to maintain
- Cost: hardware, software maintained is high
- Scalability: More data is challenging to manage and perform operations
- Data Integrity: Ensuring consistent data when multiple users update the data
- Security: Cyber attacks
- Data Migration: Moving data from one database to another is challenging
- Flexibility: Structure is often rigid and inflexible

**References:**

Notes from CampusX Bootcamp : [https://learnwith.campusx.in](https://learnwith.campusx.in/)