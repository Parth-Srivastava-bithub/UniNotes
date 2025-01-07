```bash
Relational Data Model and Language
├── Relational Data Model Concepts
│   └── Data structured in tables, rows, and columns with relationships.
├── Integrity Constraints
│   ├── Entity Integrity: Ensures primary keys are unique.
│   └── Referential Integrity: Ensures foreign keys match primary keys.
├── Keys Constraints
│   ├── Primary Key
│   ├── Foreign Key
│   ├── Candidate Key
│   └── Unique Key
├── Domain Constraints
│   └── Specifies valid data types and ranges for attributes.
├── Relational Algebra
│   └── Procedural query language using operators like select, project, join, etc.
├── Relational Calculus
│   └── Non-procedural query language using first-order logic.
├── Tuple and Domain Calculus
│   ├── Tuple Calculus: Uses tuples to define queries.
│   └── Domain Calculus: Uses domain variables to query attributes.

Introduction to SQL
├── Characteristics of SQL
│   └── SQL is declarative for data management and manipulation.
├── Advantages of SQL
│   └── Provides ease, flexibility, and portability for data handling.
├── SQL Data Types and Literals
│   └── Defines types (e.g., INT, VARCHAR) and literals in SQL.
├── Types of SQL Commands
│   ├── DDL (Data Definition Language)
│   ├── DML (Data Manipulation Language)
│   ├── DCL (Data Control Language)
│   └── TCL (Transaction Control Language)
├── SQL Operators and Their Procedure
│   └── Operators like `AND`, `OR`, `NOT` for query manipulation.
├── Tables, Views, and Indexes
│   ├── Tables: Store data.
│   ├── Views: Virtual tables.
│   └── Indexes: Speed up data retrieval.
├── Queries and Sub-Queries
│   └── Queries retrieve data; sub-queries are nested for complex results.
├── Aggregate Functions
│   └── Functions like `SUM()`, `AVG()`, `COUNT()` for data aggregation.
├── Insert, Update, and Delete Operations
│   └── SQL commands for modifying data.
├── Joins, Unions, Intersection, Minus
│   ├── Joins: Combine tables.
│   ├── Union: Combines results from queries.
│   ├── Intersection: Finds common results.
│   └── Minus: Subtracts one result set from another.
├── Cursors
│   └── Database objects to navigate through rows of a result set.
└── Triggers
    └── Automatically invoked procedures in response to events.
```

# Overview
Here’s a summary of all topics in one line:

### **Relational Data Model and Language:**
- **Relational Data Model Concepts**: Describes how data is structured in tables with rows and columns, and relationships between them.
- **Integrity Constraints**: Rules ensuring the accuracy and consistency of data, including entity and referential integrity.
- **Entity Integrity**: Ensures each table has a primary key that uniquely identifies rows.
- **Referential Integrity**: Ensures that foreign keys in one table match primary keys in another, maintaining consistency.
- **Keys Constraints**: Rules defining primary, foreign, candidate, and unique keys to identify records.
- **Domain Constraints**: Specifies valid data types and ranges for attributes in a table.
- **Relational Algebra**: A procedural query language to retrieve data from relational databases using operators like select, project, join, etc.
- **Relational Calculus**: A non-procedural query language, based on first-order logic, for querying relational databases.
- **Tuple and Domain Calculus**: Tuple calculus uses tuples to define queries, while domain calculus focuses on variables from the domain of attributes.

### **Introduction to SQL:**
- **Characteristics of SQL**: SQL is a declarative language used to manage and manipulate relational databases.
- **Advantages of SQL**: SQL provides ease of use, flexibility, and portability for data manipulation and retrieval.
- **SQL Data Types and Literals**: Defines the types of data (e.g., INT, VARCHAR) and literal values used in SQL queries.
- **Types of SQL Commands**: Includes DDL (Data Definition), DML (Data Manipulation), DCL (Data Control), and TCL (Transaction Control).
- **SQL Operators and Their Procedure**: SQL operators (like `AND`, `OR`, `NOT`) are used to filter and manipulate data in queries.
- **Tables, Views, and Indexes**: Tables store data, views are virtual tables, and indexes speed up data retrieval.
- **Queries and Sub-Queries**: SQL queries retrieve data, while sub-queries allow nested queries for more complex results.
- **Aggregate Functions**: Functions like `SUM()`, `AVG()`, and `COUNT()` aggregate multiple rows into a single value.
- **Insert, Update, and Delete Operations**: SQL commands used to insert, modify, or remove data in tables.
- **Joins, Unions, Intersection, Minus**: Joins combine tables; Union and Intersection combine results from queries; Minus subtracts one result set from another.
- **Cursors**: A database object used to retrieve, manipulate, and navigate through rows of a result set.
- **Triggers**: Automatically invoked procedures in response to certain events (like `INSERT`, `UPDATE`).
- **Procedures in SQL/PL SQL**: Stored routines in SQL/PL SQL that can be executed to perform tasks like data manipulation or business logic execution.

This gives a high-level overview of each topic


# **Relational Data Model Concepts**

The **Relational Data Model** represents data in the form of **tables** (relations), where data is organized in rows (tuples) and columns (attributes). Below are the key concepts of the relational data model explained in detail:

---

# **1. Relation**
- **Definition**: A relation is a table in a relational database that consists of rows and columns. It represents a collection of related data.
- **Example**: A `Student` relation might look like this:
  
  | Student_ID | Name        | Age |
  |------------|-------------|-----|
  | S123       | John Doe    | 20  |
  | S124       | Jane Smith  | 22  |
  | S125       | Jim Brown   | 19  |

---

# **2. Tuple (Row)**
- **Definition**: A tuple is a single row in a relation representing a record or an instance of data.
- **Example**: The row `("S123", "John Doe", 20)` is a tuple in the `Student` table. It represents one specific student's data.

---

# **3. Attribute (Column)**
- **Definition**: An attribute represents a data field in a relation, corresponding to a column in the table. It defines the type of data that can be stored in that column.
- **Example**: The `Student` relation has attributes such as `Student_ID`, `Name`, and `Age`. Each column stores a specific type of information.

---

# **4. Domain**
- **Definition**: The domain of an attribute is the set of all possible values that the attribute can take.
- **Example**: The domain of the `Age` attribute could be integers from 0 to 150, representing possible ages.

---

# **5. Primary Key**
- **Definition**: A primary key is a unique identifier for each tuple in a relation, ensuring that every record in the table is unique.
- **Example**: In the `Student` table, `Student_ID` can be the primary key, ensuring that each student has a unique identifier.

---

# **6. Foreign Key**
- **Definition**: A foreign key is an attribute (or a set of attributes) in one table that references the primary key of another table, creating a relationship between the two.
- **Example**: In an `Enrollment` table, the attribute `Course_ID` could be a foreign key referencing the `Course_ID` in the `Course` table, linking students to courses.

---

# **7. Candidate Key**
- **Definition**: A candidate key is a minimal set of attributes that can uniquely identify each tuple in a relation. There can be multiple candidate keys in a table.
- **Example**: In the `Student` table, both `Student_ID` and a combination of `Name` and `DateOfBirth` might be candidate keys (if `Name` and `DateOfBirth` together can uniquely identify a student).

---

# **8. Superkey**
- **Definition**: A superkey is any set of attributes that can uniquely identify a tuple in a relation. A superkey may contain additional attributes beyond what is necessary for uniqueness.
- **Example**: In the `Student` table, `{Student_ID, Name}` is a superkey because it uniquely identifies a student, but `{Student_ID, Name, Age}` is also a superkey (although not minimal).

---

# **9. Non-Prime Attribute**
- **Definition**: A non-prime attribute is an attribute that is not part of any candidate key in a relation.
- **Example**: In the `Student` table, if `Student_ID` is a candidate key, then `Name` and `Age` are non-prime attributes.

---

# **10. Referential Integrity**
- **Definition**: Referential integrity is a property that ensures that foreign keys in a database table always point to valid rows in another table, maintaining consistency across the database.
- **Example**: If a record in the `Enrollment` table refers to a `Course_ID`, it must correspond to a valid `Course_ID` in the `Course` table.

---

# **11. Relational Algebra**
- **Definition**: Relational algebra is a procedural query language used to query the data in a relational database using operators like select, project, join, and union.
- **Example**: The relational algebra expression `π_Name(Student)` will return all the names from the `Student` table.

---

# **12. Relational Calculus**
- **Definition**: Relational calculus is a non-procedural query language that expresses queries using logical formulas rather than operations on relations.
- **Example**: A relational calculus query to select students aged 20 could be expressed as `{s.Name | Student(s) AND s.Age = 20}`.

---

These key concepts form the foundation of the relational data model, allowing for the representation, organization, and manipulation of data in relational databases

# **Integrity Constraints**

Integrity constraints are rules applied to ensure that the data stored in a relational database remains accurate, consistent, and reliable. These constraints govern the relationships between tables, values within columns, and records to avoid data anomalies and ensure data integrity.

---

# **Entity Integrity**

- **Definition**: Entity integrity ensures that each row in a table is uniquely identifiable by a primary key, and no primary key attribute can contain null values.
- **Purpose**: Guarantees that each record (tuple) in a table is distinct, and that no two rows can have the same primary key value.
- **Key Point**: The primary key uniquely identifies a record and cannot be null, ensuring that every row has a valid and unique identifier.
- **Example**: In a `Student` table, `Student_ID` might be the primary key. It ensures that each student has a unique ID, and the `Student_ID` column cannot contain null values.
  
  | Student_ID | Name        | Age |
  |------------|-------------|-----|
  | S001       | John Doe    | 20  |
  | S002       | Jane Smith  | 22  |

In this table, `Student_ID` is unique for each student and cannot be null.

---

# **Referential Integrity**

- **Definition**: Referential integrity ensures that foreign keys in a table correctly point to primary keys in another table, maintaining valid relationships between the tables.
- **Purpose**: Guarantees that relationships between tables are consistent. If a foreign key is specified, it must match a valid primary key in the related table, or it must be null.
- **Key Point**: If a foreign key points to a primary key in another table, the foreign key must either reference an existing value or be null.
- **Example**: In an `Enrollment` table, the `Student_ID` could be a foreign key referencing `Student_ID` in the `Student` table. The `Student_ID` in `Enrollment` must match an existing `Student_ID` from the `Student` table.
  
  **Student Table**:
  | Student_ID | Name        |
  |------------|-------------|
  | S001       | John Doe    |
  | S002       | Jane Smith  |

  **Enrollment Table**:
  | Enrollment_ID | Student_ID | Course_ID |
  |---------------|------------|-----------|
  | E001          | S001       | C101      |
  | E002          | S002       | C102      |

Here, `Student_ID` in the `Enrollment` table is a foreign key that must exist in the `Student` table. If a `Student_ID` in `Enrollment` doesn't match a valid `Student_ID` in `Student`, the referential integrity rule is violated.

--- 

Together, **Entity Integrity** and **Referential Integrity** ensure the foundation of a relational database by making sure that data is uniquely identifiable and that relationships between data across tables remain consistent and accurate


# **Keys Constraints**

Key constraints ensure that the database tables maintain uniqueness and proper identification of records. These constraints are essential in relational databases to guarantee that each record is uniquely identifiable and to maintain the relationships between tables.

---

## **1. Primary Key Constraint**

- **Definition**: The primary key constraint ensures that each record in a table has a unique identifier. It must contain unique values, and no attribute in the primary key can be null.
- **Purpose**: Ensures that each record can be uniquely identified and accessed using the primary key.
- **Example**: In a `Student` table, `Student_ID` is a primary key ensuring that each student has a unique identifier.

  | Student_ID | Name       | Age |
  |------------|------------|-----|
  | S001       | John Doe   | 20  |
  | S002       | Jane Smith | 22  |

---

## **2. Foreign Key Constraint**

- **Definition**: The foreign key constraint ensures that the value in a foreign key column in one table matches a primary key value in another table, maintaining referential integrity between related tables.
- **Purpose**: It enforces relationships between tables, ensuring that foreign keys only refer to valid records.
- **Example**: In an `Enrollment` table, the `Student_ID` foreign key references the `Student_ID` primary key in the `Student` table.

  **Student Table**:
  | Student_ID | Name       |
  |------------|------------|
  | S001       | John Doe   |
  | S002       | Jane Smith |

  **Enrollment Table**:
  | Enrollment_ID | Student_ID | Course_ID |
  |---------------|------------|-----------|
  | E001          | S001       | C101      |
  | E002          | S002       | C102      |

---

## **3. Unique Key Constraint**

- **Definition**: The unique key constraint ensures that the values in a column (or a set of columns) are unique, but unlike the primary key, it allows null values.
- **Purpose**: Ensures that no two rows can have the same value for a unique key column, ensuring data uniqueness.
- **Example**: The `Email` column in a `Customer` table might have a unique constraint to ensure each email address is distinct.

  | Customer_ID | Name     | Email            |
  |-------------|----------|------------------|
  | C001        | John     | john@example.com |
  | C002        | Jane     | jane@example.com |

---

# **Domain Constraints**

Domain constraints define the allowable values for a particular column in a table. They enforce data integrity by restricting the types, formats, and ranges of values that can be entered into a column.

---

## **1. Data Type Constraint**

- **Definition**: The data type constraint ensures that the data entered into a column matches the specified data type, such as integer, varchar, date, etc.
- **Purpose**: Ensures that only valid data types are entered into the database columns.
- **Example**: The `Age` column in a `Student` table may be restricted to integers, meaning that only integer values can be entered.

  | Student_ID | Name     | Age |
  |------------|----------|-----|
  | S001       | John     | 20  |
  | S002       | Jane     | 22  |

---

## **2. Range or Value Constraints**

- **Definition**: Range or value constraints limit the values that can be inserted into a column based on a specified range or list of valid values.
- **Purpose**: Enforces valid data entry by restricting values to within an acceptable range or predefined set of values.
- **Example**: A `Salary` column in an `Employee` table might only accept values greater than $10,000 using a check constraint.

  **Check Constraint**: `CHECK (Salary > 10000)`

---

## **3. NULL/NOT NULL Constraints**

- **Definition**: This constraint defines whether a column can have null values. The `NOT NULL` constraint ensures that a column cannot have null values.
- **Purpose**: Ensures that important fields (like a name or ID) must contain valid data, preventing missing or incomplete information.
- **Example**: The `Name` column in a `Customer` table might have a `NOT NULL` constraint to ensure that every customer has a name.

  | Customer_ID | Name       |
  |-------------|------------|
  | C001        | John Doe   |
  | C002        | Jane Smith |

In this case, `Name` cannot be null.

---

Together, **Keys Constraints** and **Domain Constraints** ensure that data is both identifiable and conforms to the required structure and values, promoting consistency and accuracy in the database

# **Relational Algebra**

Relational Algebra is a formal language for querying and manipulating relational databases. It consists of a set of operations that take one or two relations as input and produce a new relation as a result. These operations allow users to retrieve and modify data from relational tables.

### **Key Operations in Relational Algebra**

1. **Select (σ)**: Filters rows based on a specified condition.
   - **Syntax**: σ_condition(Relation)
   - **Example**: `σ_Age > 18(Student)` – Retrieves all students where the `Age` is greater than 18.

2. **Project (π)**: Selects specific columns from a relation.
   - **Syntax**: π_column_list(Relation)
   - **Example**: `π_Name, Age(Student)` – Retrieves the `Name` and `Age` columns from the `Student` table.

3. **Union (∪)**: Combines the rows from two relations, excluding duplicates.
   - **Syntax**: Relation1 ∪ Relation2
   - **Example**: `Student ∪ Employee` – Combines all rows from `Student` and `Employee` tables, excluding duplicates.

4. **Set Difference (−)**: Returns rows from the first relation that do not exist in the second.
   - **Syntax**: Relation1 − Relation2
   - **Example**: `Student − Employee` – Retrieves rows from the `Student` table that are not in the `Employee` table.

5. **Intersection (∩)**: Returns the common rows between two relations.
   - **Syntax**: Relation1 ∩ Relation2
   - **Example**: `Student ∩ Employee` – Retrieves rows common to both the `Student` and `Employee` tables.

6. **Cartesian Product (×)**: Combines each row of the first relation with every row of the second relation.
   - **Syntax**: Relation1 × Relation2
   - **Example**: `Student × Course` – Combines every `Student` row with every `Course` row.

7. **Join (⨝)**: Combines rows from two relations based on a condition.
   - **Syntax**: Relation1 ⨝ Condition Relation2
   - **Example**: `Student ⨝ Student.Student_ID = Enrollment.Student_ID Enrollment` – Joins `Student` and `Enrollment` based on matching `Student_ID`.

8. **Rename (ρ)**: Renames the attributes of a relation.
   - **Syntax**: ρ_new_relation_name(Relation)
   - **Example**: `ρ_NewStudent(Student)` – Renames the `Student` relation to `NewStudent`.

---

# **Relational Calculus**

Relational Calculus is a non-procedural query language for relational databases, focusing on describing what data to retrieve rather than how to retrieve it. There are two main types of relational calculus: Tuple Relational Calculus (TRC) and Domain Relational Calculus (DRC).

---

## **Tuple Relational Calculus (TRC)**

- **Definition**: Tuple Relational Calculus is a declarative query language where queries are expressed using variables that represent tuples (rows) from a relation. A TRC query specifies a set of tuples that satisfy a given condition.
- **Syntax**: `{T | condition(T)}`
  - `T`: A variable representing a tuple.
  - `condition(T)`: A condition on the tuple `T`.
- **Example**: ` {T.Name | Student(T) ∧ T.Age > 18}` – Retrieves the `Name` of all students whose `Age` is greater than 18.

---

## **Domain Relational Calculus (DRC)**

- **Definition**: Domain Relational Calculus is similar to TRC but uses variables that represent values (domains) instead of tuples. The query specifies what values should be retrieved based on the condition.
- **Syntax**: `{D1, D2, ..., Dn | condition(D1, D2, ..., Dn)}`
  - `D1, D2, ..., Dn`: Variables representing the domains (values) of attributes.
  - `condition(D1, D2, ..., Dn)`: A condition involving the domains.
- **Example**: `{Name | ∃ Age (Student(Name, Age) ∧ Age > 18)}` – Retrieves the `Name` of all students whose `Age` is greater than 18.

---

# **Key Differences between TRC and DRC**

1. **Tuple Variables vs Domain Variables**:
   - **TRC** uses tuple variables that refer to entire rows.
   - **DRC** uses domain variables that refer to individual values in columns.

2. **Type of Query**:
   - **TRC** queries retrieve sets of tuples.
   - **DRC** queries retrieve sets of values for specific columns.

---

Together, **Relational Algebra** and **Relational Calculus** provide two different approaches to query and manipulate data in relational databases. Relational Algebra is procedural and focuses on operations, while Relational Calculus is declarative and describes the properties of the desired result

# **Introduction to SQL**

SQL (Structured Query Language) is a standard programming language used for managing and manipulating relational databases. SQL is used to perform tasks such as querying data, updating data, inserting records, and deleting records in a database. It allows users to interact with databases by using commands and statements.

---

# **Characteristics of SQL**

1. **Declarative Language**: SQL is a declarative language, meaning that users specify what data they want, but not how to get it. The database management system (DBMS) handles the execution plan for retrieving the data.

2. **Platform-Independent**: SQL is a standardized language and is supported by almost all relational database management systems (RDBMS) like MySQL, PostgreSQL, Oracle, SQL Server, and SQLite. The basic structure of SQL queries remains the same across platforms.

3. **High-Level Language**: SQL is a high-level language, meaning it is easy to use and understand. It allows users to work with complex data structures without needing to know the underlying implementation details.

4. **Support for Complex Queries**: SQL allows users to write complex queries that can involve multiple tables, joins, aggregations, and subqueries to extract valuable insights from the data.

5. **Data Manipulation**: SQL supports a wide range of data manipulation tasks, including selecting, inserting, updating, and deleting data in relational tables.

6. **Data Definition**: SQL allows users to define the structure of the database, create tables, set constraints, and define relationships between tables using commands like `CREATE`, `ALTER`, and `DROP`.

7. **Integrity Constraints**: SQL enables users to define constraints like primary keys, foreign keys, and unique keys to ensure data integrity and accuracy.

---

# **Advantages of SQL**

1. **Ease of Use**: SQL provides a simple and human-readable syntax, making it easy for users to interact with databases. Its commands are intuitive and closely resemble natural language queries.

2. **Standardized**: SQL is a standardized language, meaning it is recognized across various database systems. This reduces the learning curve and enables portability across different platforms.

3. **Data Security**: SQL provides robust mechanisms for securing data, including user authentication, access control, and data encryption, ensuring that sensitive information is protected.

4. **Efficiency**: SQL allows for optimized query execution, making it suitable for handling large amounts of data. Many DBMSs come with advanced query optimizers that improve the performance of SQL queries.

5. **Scalability**: SQL databases are highly scalable and can handle a significant increase in data volume without sacrificing performance. This makes it suitable for both small and large-scale applications.

6. **Flexibility**: SQL is flexible and can be used for a wide variety of applications, from simple data retrieval tasks to complex data analysis and reporting.

7. **Transaction Control**: SQL supports transaction control, allowing multiple queries to be executed as a single unit. It ensures data consistency and integrity even in the event of errors or system failures (using features like `COMMIT` and `ROLLBACK`).

8. **Wide Adoption and Community Support**: SQL is the most widely used language for database management, ensuring that there is a large community of developers, extensive documentation, and numerous tools available for support.

---

In summary, SQL is a powerful and easy-to-use language that simplifies database management and data manipulation tasks, offering advantages such as efficiency, scalability, and robust data security. It plays a crucial role in modern database-driven applications


# **SQL Data Types and Literals**

SQL data types define the type of data that can be stored in a column of a table. They help in ensuring the correct storage of data and enable SQL to perform operations on the data more effectively. SQL also supports literals, which are constant values used directly in queries.

---

# **SQL Data Types**

SQL provides a wide range of data types to store different kinds of information. Below are the most commonly used SQL data types:

### **1. Numeric Data Types**

- **INT / INTEGER**: Used to store integer values. 
  - **Example**: `Age INT`
  
- **DECIMAL / NUMERIC**: Used to store fixed-point numbers with a specified precision and scale.
  - **Example**: `Salary DECIMAL(10,2)` – Stores a number with up to 10 digits, 2 of which are after the decimal point.

- **FLOAT / REAL**: Used to store floating-point numbers with approximate precision.
  - **Example**: `Weight FLOAT`

- **SMALLINT**: Used to store small integer values.
  - **Example**: `Quantity SMALLINT`

- **BIGINT**: Used to store large integer values.
  - **Example**: `Population BIGINT`

### **2. Character and String Data Types**

- **CHAR(n)**: Fixed-length character string. The value is padded with spaces to reach the specified length.
  - **Example**: `Gender CHAR(1)` – Can store 'M' or 'F'.
  
- **VARCHAR(n)**: Variable-length character string. It stores strings with a maximum length of `n` characters.
  - **Example**: `Name VARCHAR(100)`

- **TEXT**: Stores long text strings. The length is not fixed.
  - **Example**: `Description TEXT`

### **3. Date and Time Data Types**

- **DATE**: Stores the date in the format `YYYY-MM-DD`.
  - **Example**: `BirthDate DATE`

- **TIME**: Stores time in the format `HH:MM:SS`.
  - **Example**: `StartTime TIME`

- **DATETIME**: Stores both date and time in the format `YYYY-MM-DD HH:MM:SS`.
  - **Example**: `EventDate DATETIME`

- **TIMESTAMP**: Similar to `DATETIME`, but also stores time-zone information.
  - **Example**: `LastLogin TIMESTAMP`

### **4. Boolean Data Type**

- **BOOLEAN**: Stores a boolean value (`TRUE` or `FALSE`).
  - **Example**: `IsActive BOOLEAN`

### **5. Binary Data Types**

- **BLOB**: Stores binary large objects, such as images, audio, or any file in binary format.
  - **Example**: `Image BLOB`

- **VARBINARY(n)**: Stores variable-length binary data.
  - **Example**: `FileData VARBINARY(255)`

### **6. Special Data Types**

- **ENUM**: Stores a predefined list of values. The column can only take one value from the list.
  - **Example**: `Color ENUM('Red', 'Green', 'Blue')`
  
- **SET**: Stores multiple values from a predefined list of values (like an array of options).
  - **Example**: `Permissions SET('Read', 'Write', 'Execute')`

---

# **SQL Literals**

Literals are constant values used directly in SQL queries. They represent fixed values that are used in operations or conditions in queries.

### **1. Numeric Literals**

- **Definition**: Numeric literals are numbers directly used in SQL statements.
  - **Example**: `SELECT * FROM Employees WHERE Age = 30`

### **2. String Literals**

- **Definition**: String literals are characters enclosed in single quotes (' ').
  - **Example**: `SELECT * FROM Students WHERE Name = 'John'`

### **3. Date and Time Literals**

- **Definition**: Date literals are enclosed in single quotes and are written in the `YYYY-MM-DD` format, while time literals are written as `HH:MM:SS`.
  - **Example**: `SELECT * FROM Events WHERE EventDate = '2025-12-01'`
  - **Example**: `SELECT * FROM Orders WHERE OrderTime = '10:30:00'`

### **4. Boolean Literals**

- **Definition**: Boolean literals are either `TRUE` or `FALSE`.
  - **Example**: `SELECT * FROM Employees WHERE IsActive = TRUE`

---

In conclusion, SQL provides a wide variety of data types for storing different kinds of data, including numeric, character, date/time, boolean, binary, and special types. Literals in SQL are constant values that are used directly in queries to filter or define data. The proper use of data types and literals is essential for maintaining data integrity and performing efficient queries

# **Types of SQL Commands**

SQL commands are divided into several categories based on their functionality. These categories allow users to define, manipulate, control, and query data in relational databases. Below are the primary types of SQL commands:

---

## **1. Data Definition Language (DDL)**

DDL commands are used to define and manage the structure of database objects, such as tables, schemas, and views.

### **Key DDL Commands:**

- **CREATE**: Creates a new database object, such as a table, index, or view.
  - **Example**: `CREATE TABLE Students (ID INT, Name VARCHAR(50), Age INT);`

- **ALTER**: Modifies an existing database object, like adding or dropping columns in a table.
  - **Example**: `ALTER TABLE Students ADD Email VARCHAR(100);`

- **DROP**: Deletes an existing database object, such as a table, view, or index.
  - **Example**: `DROP TABLE Students;`

- **TRUNCATE**: Removes all records from a table but keeps the structure intact.
  - **Example**: `TRUNCATE TABLE Students;`

---

## **2. Data Manipulation Language (DML)**

DML commands are used to manipulate the data stored within tables. These commands allow users to insert, update, delete, and retrieve data.

### **Key DML Commands:**

- **SELECT**: Retrieves data from one or more tables.
  - **Example**: `SELECT * FROM Students;`

- **INSERT**: Adds new records to a table.
  - **Example**: `INSERT INTO Students (ID, Name, Age) VALUES (1, 'John Doe', 22);`

- **UPDATE**: Modifies existing data in a table.
  - **Example**: `UPDATE Students SET Age = 23 WHERE ID = 1;`

- **DELETE**: Removes data from a table.
  - **Example**: `DELETE FROM Students WHERE ID = 1;`

---

## **3. Data Control Language (DCL)**

DCL commands are used to control access to data in the database. They deal with permissions and security.

### **Key DCL Commands:**

- **GRANT**: Gives specific privileges to users or roles.
  - **Example**: `GRANT SELECT, INSERT ON Students TO User1;`

- **REVOKE**: Removes specific privileges from users or roles.
  - **Example**: `REVOKE SELECT ON Students FROM User1;`

---

## **4. Transaction Control Language (TCL)**

TCL commands are used to manage transactions in a database. These commands ensure that the database remains in a consistent state even in the event of errors.

### **Key TCL Commands:**

- **COMMIT**: Saves all changes made during the current transaction.
  - **Example**: `COMMIT;`

- **ROLLBACK**: Undoes changes made during the current transaction.
  - **Example**: `ROLLBACK;`

- **SAVEPOINT**: Sets a point within a transaction that you can roll back to.
  - **Example**: `SAVEPOINT save1;`

- **SET TRANSACTION**: Configures the properties of the current transaction.
  - **Example**: `SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;`

---

## **5. Data Query Language (DQL)**

DQL is primarily concerned with querying and retrieving data from the database. While technically a subset of DML, DQL focuses on SELECT queries.

### **Key DQL Command:**

- **SELECT**: Retrieves data from a table or multiple tables.
  - **Example**: `SELECT Name, Age FROM Students WHERE Age > 20;`

---

### **Summary of SQL Command Types**

- **DDL (Data Definition Language)**: Defines database objects (`CREATE`, `ALTER`, `DROP`, `TRUNCATE`).
- **DML (Data Manipulation Language)**: Manages data in tables (`SELECT`, `INSERT`, `UPDATE`, `DELETE`).
- **DCL (Data Control Language)**: Controls access and permissions (`GRANT`, `REVOKE`).
- **TCL (Transaction Control Language)**: Manages transactions (`COMMIT`, `ROLLBACK`, `SAVEPOINT`).
- **DQL (Data Query Language)**: Queries data (`SELECT`).

SQL commands are essential for creating, managing, and manipulating data in relational databases, with each type of command serving a specific purpose in the database management process
# **SQL Operators and Their Procedure**

SQL operators are special symbols used to perform operations on data. Operators in SQL can be classified into several types, including arithmetic, comparison, logical, and others. These operators are used in SQL queries to manipulate or compare data values and filter results.

---

## **1. Arithmetic Operators**

Arithmetic operators are used to perform mathematical operations on numerical data.

### **Common Arithmetic Operators:**

- **+ (Addition)**: Adds two operands.
  - **Example**: `SELECT Price + Tax AS Total FROM Products;`

- **- (Subtraction)**: Subtracts one operand from another.
  - **Example**: `SELECT Salary - Deduction AS NetSalary FROM Employees;`

- **\* (Multiplication)**: Multiplies two operands.
  - **Example**: `SELECT Quantity * Price AS TotalPrice FROM Orders;`

- **/ (Division)**: Divides one operand by another.
  - **Example**: `SELECT TotalAmount / Quantity AS UnitPrice FROM Sales;`

- **% (Modulus)**: Returns the remainder of the division.
  - **Example**: `SELECT 10 % 3 AS Remainder;`

---

## **2. Comparison Operators**

Comparison operators are used to compare two values and return true or false based on the comparison.

### **Common Comparison Operators:**

- **= (Equal to)**: Checks if two values are equal.
  - **Example**: `SELECT * FROM Students WHERE Age = 20;`

- **!= or <> (Not equal to)**: Checks if two values are not equal.
  - **Example**: `SELECT * FROM Products WHERE Price != 100;`

- **> (Greater than)**: Checks if the left operand is greater than the right operand.
  - **Example**: `SELECT * FROM Orders WHERE Quantity > 50;`

- **< (Less than)**: Checks if the left operand is less than the right operand.
  - **Example**: `SELECT * FROM Employees WHERE Age < 30;`

- **>= (Greater than or equal to)**: Checks if the left operand is greater than or equal to the right operand.
  - **Example**: `SELECT * FROM Students WHERE Score >= 60;`

- **<= (Less than or equal to)**: Checks if the left operand is less than or equal to the right operand.
  - **Example**: `SELECT * FROM Products WHERE Quantity <= 100;`

- **BETWEEN**: Checks if a value is within a specified range (inclusive).
  - **Example**: `SELECT * FROM Orders WHERE OrderDate BETWEEN '2023-01-01' AND '2023-12-31';`

- **LIKE**: Matches a pattern in a string.
  - **Example**: `SELECT * FROM Customers WHERE Name LIKE 'A%';`

- **IN**: Checks if a value matches any value in a list.
  - **Example**: `SELECT * FROM Employees WHERE Department IN ('HR', 'Finance');`

- **IS NULL**: Checks if a value is null.
  - **Example**: `SELECT * FROM Employees WHERE Department IS NULL;`

---

## **3. Logical Operators**

Logical operators are used to combine multiple conditions in a query.

### **Common Logical Operators:**

- **AND**: Returns true if both conditions are true.
  - **Example**: `SELECT * FROM Employees WHERE Age > 30 AND Department = 'Sales';`

- **OR**: Returns true if either condition is true.
  - **Example**: `SELECT * FROM Employees WHERE Department = 'Sales' OR Department = 'HR';`

- **NOT**: Reverses the result of a condition.
  - **Example**: `SELECT * FROM Products WHERE NOT Category = 'Electronics';`

---

## **4. Set Operators**

Set operators are used to combine results from two or more queries.

### **Common Set Operators:**

- **UNION**: Combines the result of two queries, removing duplicates.
  - **Example**: `SELECT Name FROM Customers WHERE Age > 30 UNION SELECT Name FROM Employees WHERE Age > 30;`

- **UNION ALL**: Combines the result of two queries, including duplicates.
  - **Example**: `SELECT Name FROM Customers WHERE Age > 30 UNION ALL SELECT Name FROM Employees WHERE Age > 30;`

- **INTERSECT**: Returns the common result of two queries.
  - **Example**: `SELECT Name FROM Customers WHERE Age > 30 INTERSECT SELECT Name FROM Employees WHERE Age > 30;`

- **EXCEPT (or MINUS)**: Returns the result of the first query that does not exist in the second query.
  - **Example**: `SELECT Name FROM Customers WHERE Age > 30 EXCEPT SELECT Name FROM Employees WHERE Age > 30;`

---

## **5. String Operators**

String operators are used to perform operations on string data types.

### **Common String Operators:**

- **CONCAT()**: Concatenates two or more strings together.
  - **Example**: `SELECT CONCAT(FirstName, ' ', LastName) AS FullName FROM Employees;`

- **|| (Concatenation)**: Some SQL databases use `||` to concatenate strings.
  - **Example**: `SELECT FirstName || ' ' || LastName AS FullName FROM Employees;`

- **LENGTH()**: Returns the length of a string.
  - **Example**: `SELECT LENGTH(FirstName) FROM Employees;`

- **SUBSTRING()**: Extracts a portion of a string.
  - **Example**: `SELECT SUBSTRING(Description, 1, 5) FROM Products;`

---

## **6. Miscellaneous Operators**

These operators serve specialized purposes in SQL.

### **Common Miscellaneous Operators:**

- **EXISTS**: Checks if a subquery returns any rows.
  - **Example**: `SELECT * FROM Employees WHERE EXISTS (SELECT * FROM Projects WHERE EmployeeID = Employees.ID);`

- **ALL**: Compares a value to all values in another result set.
  - **Example**: `SELECT * FROM Employees WHERE Salary > ALL (SELECT Salary FROM Employees WHERE Department = 'HR');`

- **ANY**: Compares a value to any value in another result set.
  - **Example**: `SELECT * FROM Employees WHERE Salary > ANY (SELECT Salary FROM Employees WHERE Department = 'HR');`

- **DISTINCT**: Returns unique values in a result set.
  - **Example**: `SELECT DISTINCT Department FROM Employees;`

---

## **SQL Operators Procedure**

1. **Start with the SELECT Statement**: Define the columns you want to retrieve and the table you want to query.
2. **Apply Comparison Operators**: Filter rows based on conditions using comparison operators (`=`, `>`, `<=`, etc.).
3. **Combine Conditions Using Logical Operators**: Use `AND`, `OR`, or `NOT` to combine multiple conditions.
4. **Manipulate Data Using Arithmetic Operators**: Perform calculations (e.g., addition, subtraction) on numeric data.
5. **Use Set Operators to Combine Results**: If you need to combine multiple queries, use `UNION`, `INTERSECT`, or `EXCEPT`.
6. **Use Functions for String or Date Manipulations**: Use string functions like `CONCAT()` or date functions to manipulate string or date data types.

---

In summary, SQL operators allow you to perform a variety of tasks such as arithmetic operations, data comparison, logical conditions, set operations, string manipulations, and more. Understanding how to use these operators in SQL queries helps in effectively retrieving, filtering, and manipulating data in a relational database

# **Tables, Views, and Indexes**

In SQL, tables, views, and indexes are fundamental components that help organize and manage data efficiently in relational databases. Below is a detailed explanation of each, along with examples.

---

## **1. Tables**

A table is the primary structure used to store data in a relational database. It consists of rows (records) and columns (fields), where each column holds a specific type of data, and each row represents a data record.

### **Key Points About Tables:**

- **Structure**: Defined by columns, each with a specified data type (e.g., `INT`, `VARCHAR`, `DATE`).
- **Primary Key**: A unique identifier for each record in a table.
- **Foreign Key**: A column that links one table to another, establishing relationships.

### **Example:**

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Department VARCHAR(50),
    Salary DECIMAL(10, 2)
);
```

In this example:
- `EmployeeID` is the primary key.
- `FirstName`, `LastName`, `Department`, and `Salary` are columns.

---

## **2. Views**

A view is a virtual table in a database that provides a way to present data from one or more tables. It doesn't store data itself but stores a query that fetches data from base tables.

### **Key Points About Views:**

- **Virtual Table**: Views don’t contain data but display data dynamically when queried.
- **Data Simplification**: Views can simplify complex queries and provide a customized way of viewing the data.
- **Read-Only or Updatable**: Some views are updatable (allowing you to insert, update, or delete data through them), while others are read-only.

### **Example:**

```sql
CREATE VIEW EmployeeInfo AS
SELECT EmployeeID, FirstName, LastName, Department
FROM Employees
WHERE Salary > 50000;
```

In this example:
- The view `EmployeeInfo` simplifies the query to display only employees with a salary greater than 50,000.

To query the view:

```sql
SELECT * FROM EmployeeInfo;
```

---

## **3. Indexes**

An index is a database object that improves the speed of data retrieval operations on a table at the cost of additional space and slower data modification operations (like `INSERT`, `UPDATE`, and `DELETE`).

### **Key Points About Indexes:**

- **Improves Query Performance**: Indexes are used to speed up retrieval operations, especially in large tables.
- **Unique Index**: Ensures that no two rows in a table have the same values for the indexed columns.
- **Composite Index**: An index that includes multiple columns from a table.
- **Automatic Indexing**: Many databases automatically create indexes on primary keys and unique constraints.

### **Example:**

```sql
CREATE INDEX idx_salary ON Employees (Salary);
```

In this example:
- `idx_salary` is the name of the index, and it is created on the `Salary` column of the `Employees` table.
- This index will speed up queries filtering or sorting by the `Salary` column.

To query using the index:

```sql
SELECT * FROM Employees WHERE Salary > 50000;
```

---

### **Summary of Tables, Views, and Indexes**

- **Tables**: Store actual data and are the foundation of a relational database.
- **Views**: Virtual tables that provide a way to query data without storing it physically, often used for simplifying complex queries.
- **Indexes**: Improve query performance by providing faster access to rows in a table, especially for large datasets.

These elements—tables, views, and indexes—are essential in building efficient and effective relational databases, ensuring that data is stored correctly, queried efficiently, and presented in the desired format


# **Queries and Subqueries**

In SQL, queries are used to interact with the database and retrieve, manipulate, or modify data. A subquery is a query nested within another query. Subqueries can be used to make more complex queries and to retrieve data for use in the main query.

---

## **1. Queries**

A query is a request to retrieve or modify data from a database. The most common type of query is a `SELECT` query, but SQL also includes queries for inserting, updating, and deleting data (`INSERT`, `UPDATE`, `DELETE`).

### **Types of Queries**:

- **SELECT Query**: Retrieves data from the database.
  - **Example**:
    ```sql
    SELECT FirstName, LastName, Salary FROM Employees WHERE Department = 'Sales';
    ```
    This query selects the first name, last name, and salary of employees in the "Sales" department.

- **INSERT Query**: Adds new data to a table.
  - **Example**:
    ```sql
    INSERT INTO Employees (EmployeeID, FirstName, LastName, Department, Salary) 
    VALUES (1, 'John', 'Doe', 'Marketing', 50000);
    ```

- **UPDATE Query**: Modifies existing data in a table.
  - **Example**:
    ```sql
    UPDATE Employees SET Salary = 55000 WHERE EmployeeID = 1;
    ```

- **DELETE Query**: Removes data from a table.
  - **Example**:
    ```sql
    DELETE FROM Employees WHERE EmployeeID = 1;
    ```

---

## **2. Subqueries**

A subquery is a query embedded inside another query. Subqueries can be used in various parts of the SQL statement, such as in the `SELECT`, `FROM`, `WHERE`, or `HAVING` clauses. Subqueries are often used when you need to perform operations that involve multiple steps, such as retrieving a value from one table to use in a condition in another table.

### **Types of Subqueries**:

- **Single-Row Subquery**: Returns a single value and is used when the outer query expects a single value to be returned.
  - **Example**:
    ```sql
    SELECT FirstName, LastName 
    FROM Employees 
    WHERE Salary > (SELECT AVG(Salary) FROM Employees);
    ```
    In this example, the subquery `(SELECT AVG(Salary) FROM Employees)` calculates the average salary, and the outer query retrieves the employees earning more than the average salary.

- **Multiple-Row Subquery**: Returns multiple rows and is used when the outer query expects multiple values.
  - **Example**:
    ```sql
    SELECT FirstName, LastName 
    FROM Employees 
    WHERE Department IN (SELECT Department FROM Employees WHERE Salary > 60000);
    ```
    The subquery returns departments where employees earn more than 60,000, and the outer query retrieves employees who belong to those departments.

- **Correlated Subquery**: A subquery that references columns from the outer query. Each row of the outer query can produce a different result in the subquery.
  - **Example**:
    ```sql
    SELECT FirstName, LastName 
    FROM Employees e1 
    WHERE EXISTS (SELECT * FROM Employees e2 WHERE e1.Department = e2.Department AND e2.Salary > 50000);
    ```
    In this case, the subquery references the `Department` from the outer query (`e1.Department`) to check if there are other employees in the same department earning more than 50,000.

- **Nested Subquery**: A subquery within a subquery. Multiple levels of subqueries are used to break down complex queries.
  - **Example**:
    ```sql
    SELECT FirstName, LastName 
    FROM Employees 
    WHERE Department = (SELECT Department FROM Departments WHERE DepartmentID = (SELECT DepartmentID FROM Employees WHERE EmployeeID = 1));
    ```
    This example uses two levels of subqueries: one to find the department of employee 1 and another to fetch employees from that department.

---

## **3. Using Subqueries in Different Clauses**

- **Subquery in WHERE Clause**: Subqueries in the `WHERE` clause are used to filter the results of the main query based on the result of the subquery.
  - **Example**:
    ```sql
    SELECT Name FROM Products 
    WHERE CategoryID = (SELECT CategoryID FROM Categories WHERE CategoryName = 'Electronics');
    ```
    This query finds all products in the 'Electronics' category by using a subquery to get the `CategoryID`.

- **Subquery in FROM Clause**: Subqueries in the `FROM` clause are used when you need to treat the result of a subquery as a table for the outer query.
  - **Example**:
    ```sql
    SELECT Department, AVG(Salary) 
    FROM (SELECT Department, Salary FROM Employees WHERE Salary > 50000) AS HighSalaryEmployees 
    GROUP BY Department;
    ```
    The subquery retrieves employees with a salary greater than 50,000, and the outer query calculates the average salary by department from the result of the subquery.

- **Subquery in SELECT Clause**: Subqueries in the `SELECT` clause are used to return a value for each row of the result set.
  - **Example**:
    ```sql
    SELECT FirstName, LastName, 
           (SELECT COUNT(*) FROM Orders WHERE EmployeeID = Employees.EmployeeID) AS TotalOrders
    FROM Employees;
    ```
    The subquery counts the number of orders for each employee and includes this information in the result set.

---

### **Advantages of Subqueries**

- **Modular Queries**: Subqueries allow you to break complex queries into smaller, manageable parts.
- **Nested Logic**: Useful when the result of one query is needed in another query.
- **Flexibility**: Can be used in various parts of a query, such as `SELECT`, `WHERE`, `FROM`, or `HAVING`.

### **Disadvantages of Subqueries**

- **Performance**: Subqueries, especially correlated ones, can be slower compared to joins in some cases.
- **Readability**: Queries with multiple subqueries can become difficult to read and maintain.

---

## **Summary**

- **Query**: A request to retrieve or modify data from the database. The most common queries are `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.
- **Subquery**: A query nested within another query. It is used to perform operations that depend on the results of another query.
  - **Types**: Single-row, multiple-row, correlated, and nested subqueries.
- **Usage**: Subqueries can be placed in `WHERE`, `FROM`, and `SELECT` clauses, and are a powerful tool to solve complex database problems

# **Aggregate Functions**

Aggregate functions in SQL perform a calculation on a set of values and return a single value. These functions are typically used with the `GROUP BY` clause to group rows based on specified columns, and are frequently used for data summarization and analysis.

---

## **1. Common Aggregate Functions**

### **COUNT()**
- **Description**: Counts the number of rows in a result set or the number of non-NULL values in a specific column.
- **Example**:
  ```sql
  SELECT COUNT(*) FROM Employees;
  ```
  This query counts the total number of employees.

  ```sql
  SELECT COUNT(Salary) FROM Employees WHERE Department = 'Sales';
  ```
  This query counts the number of employees in the "Sales" department with a non-NULL salary.

---

### **SUM()**
- **Description**: Returns the total sum of a numeric column.
- **Example**:
  ```sql
  SELECT SUM(Salary) FROM Employees WHERE Department = 'HR';
  ```
  This query calculates the total salary of employees in the "HR" department.

---

### **AVG()**
- **Description**: Returns the average value of a numeric column.
- **Example**:
  ```sql
  SELECT AVG(Salary) FROM Employees;
  ```
  This query calculates the average salary of all employees.

---

### **MIN()**
- **Description**: Returns the minimum value from a set of values.
- **Example**:
  ```sql
  SELECT MIN(Salary) FROM Employees WHERE Department = 'Marketing';
  ```
  This query finds the minimum salary among employees in the "Marketing" department.

---

### **MAX()**
- **Description**: Returns the maximum value from a set of values.
- **Example**:
  ```sql
  SELECT MAX(Salary) FROM Employees WHERE Department = 'Engineering';
  ```
  This query finds the highest salary among employees in the "Engineering" department.

---

## **2. Using Aggregate Functions with GROUP BY**

Aggregate functions are often used in conjunction with the `GROUP BY` clause to perform calculations on groups of rows rather than on individual rows.

### **Example**:
```sql
SELECT Department, AVG(Salary)
FROM Employees
GROUP BY Department;
```
This query calculates the average salary for each department by grouping employees based on their department.

---

## **3. Using Aggregate Functions with HAVING**

The `HAVING` clause is used to filter the results of a `GROUP BY` query based on the result of an aggregate function, much like `WHERE` filters individual rows.

### **Example**:
```sql
SELECT Department, COUNT(EmployeeID)
FROM Employees
GROUP BY Department
HAVING COUNT(EmployeeID) > 5;
```
This query retrieves departments with more than 5 employees.

---

## **4. Handling NULL Values**

- **COUNT()** counts non-NULL values, whereas **SUM()**, **AVG()**, **MIN()**, and **MAX()** ignore NULL values when calculating results.
- **Example** (for handling NULLs):
  ```sql
  SELECT AVG(Salary) FROM Employees WHERE Salary IS NOT NULL;
  ```
  This ensures that only non-NULL salaries are included in the average calculation.

---

## **5. Summary of Common Aggregate Functions**

| **Function** | **Description** | **Example** |
|--------------|-----------------|-------------|
| `COUNT()`    | Counts the number of rows or non-NULL values in a column. | `SELECT COUNT(*) FROM Employees;` |
| `SUM()`      | Calculates the sum of a numeric column. | `SELECT SUM(Salary) FROM Employees;` |
| `AVG()`      | Calculates the average of a numeric column. | `SELECT AVG(Salary) FROM Employees;` |
| `MIN()`      | Returns the minimum value in a column. | `SELECT MIN(Salary) FROM Employees;` |
| `MAX()`      | Returns the maximum value in a column. | `SELECT MAX(Salary) FROM Employees;` |

---

## **6. Nested Aggregate Functions**

You can also nest aggregate functions in SQL to perform multiple levels of aggregation.

### **Example**:
```sql
SELECT MAX(AVG(Salary)) 
FROM Employees 
GROUP BY Department;
```
This query finds the highest average salary across all departments.

---

## **Conclusion**

Aggregate functions are essential tools in SQL for performing summarization and analysis of data. Whether you're calculating totals, averages, or finding the minimum and maximum values, these functions provide a powerful way to work with large datasets and perform meaningful data aggregation

# **Insert, Update, and Delete Operations**

In SQL, the `INSERT`, `UPDATE`, and `DELETE` operations are used to modify data in the database. These operations allow you to add new data, modify existing data, or remove data from a table.

---

## **1. INSERT Operation**

The `INSERT` statement is used to add new rows of data to a table. You can either insert specific values into the table or insert values from another table.

### **Syntax**:
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

### **Example**:
```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, Department, Salary) 
VALUES (1, 'John', 'Doe', 'Sales', 50000);
```
This query inserts a new employee with the given details into the `Employees` table.

### **Insert Data from Another Table**:
```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, Department, Salary) 
SELECT EmployeeID, FirstName, LastName, Department, Salary 
FROM TempEmployees
WHERE Department = 'HR';
```
This query inserts employees from the `TempEmployees` table into the `Employees` table where the department is 'HR'.

---

## **2. UPDATE Operation**

The `UPDATE` statement is used to modify the existing data in a table. It can update one or more columns in one or more rows of the table based on a given condition.

### **Syntax**:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### **Example**:
```sql
UPDATE Employees
SET Salary = 55000, Department = 'Marketing'
WHERE EmployeeID = 1;
```
This query updates the `Salary` and `Department` of the employee with `EmployeeID` 1.

### **Update Multiple Columns**:
```sql
UPDATE Employees
SET Salary = Salary + 5000, Department = 'Operations'
WHERE Department = 'Sales';
```
This query increases the salary by 5000 and changes the department of all employees in the 'Sales' department to 'Operations'.

---

## **3. DELETE Operation**

The `DELETE` statement is used to remove one or more rows from a table based on a condition.

### **Syntax**:
```sql
DELETE FROM table_name
WHERE condition;
```

### **Example**:
```sql
DELETE FROM Employees
WHERE EmployeeID = 1;
```
This query deletes the employee with `EmployeeID` 1 from the `Employees` table.

### **Delete All Rows**:
If you want to delete all rows in a table without removing the table structure:
```sql
DELETE FROM Employees;
```
This query removes all rows from the `Employees` table.

### **Delete Without WHERE Clause**:
**Warning**: If the `WHERE` clause is omitted, all rows in the table will be deleted, so it's important to use this with caution.

---

## **4. Important Notes on Insert, Update, and Delete**

- **Insert**: Adds new records to the table.
  - If a record with the same primary key or unique constraint exists, it will cause an error.
- **Update**: Modifies existing records.
  - Make sure to use the `WHERE` clause to avoid updating all rows in the table.
- **Delete**: Removes records.
  - Without the `WHERE` clause, all rows will be deleted.
  - Deleting rows can sometimes violate referential integrity if there are foreign key constraints.

---

## **Conclusion**

- The `INSERT` statement adds new data to a table.
- The `UPDATE` statement modifies existing data.
- The `DELETE` statement removes data from a table.
  
Proper use of these operations ensures that the database reflects accurate and up-to-date information. Be cautious while performing `UPDATE` and `DELETE` operations to avoid unintended data modifications


# **Joins, Unions, and Intersection with Table Examples**

Let’s dive into each concept with table examples for better understanding.

---

## **1. Joins**

### **1.1 INNER JOIN**

An `INNER JOIN` returns only the rows where there is a match in both tables.

### **Tables:**

**Employees Table:**

| EmployeeID | FirstName | LastName | DepartmentID |
|------------|-----------|----------|--------------|
| 1          | John      | Doe      | 10           |
| 2          | Jane      | Smith    | 20           |
| 3          | Mike      | Brown    | 10           |

**Departments Table:**

| DepartmentID | DepartmentName |
|--------------|----------------|
| 10           | Sales          |
| 20           | HR             |
| 30           | IT             |

### **INNER JOIN Query:**

```sql
SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
FROM Employees
INNER JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### **Result:**

| EmployeeID | FirstName | LastName | DepartmentName |
|------------|-----------|----------|----------------|
| 1          | John      | Doe      | Sales          |
| 2          | Jane      | Smith    | HR             |
| 3          | Mike      | Brown    | Sales          |

The query returns only the rows where there is a match between `Employees.DepartmentID` and `Departments.DepartmentID`.

---

### **1.2 LEFT JOIN**

A `LEFT JOIN` returns all rows from the left table and matched rows from the right table. If no match is found, NULL is returned for the right table columns.

### **LEFT JOIN Query:**

```sql
SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### **Result:**

| EmployeeID | FirstName | LastName | DepartmentName |
|------------|-----------|----------|----------------|
| 1          | John      | Doe      | Sales          |
| 2          | Jane      | Smith    | HR             |
| 3          | Mike      | Brown    | Sales          |

If an employee’s `DepartmentID` didn't exist in the `Departments` table, their `DepartmentName` would be `NULL`.

---

### **1.3 RIGHT JOIN**

A `RIGHT JOIN` returns all rows from the right table and matched rows from the left table. If no match is found, NULL is returned for the left table columns.

### **RIGHT JOIN Query:**

```sql
SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### **Result:**

| EmployeeID | FirstName | LastName | DepartmentName |
|------------|-----------|----------|----------------|
| 1          | John      | Doe      | Sales          |
| 2          | Jane      | Smith    | HR             |
| 3          | Mike      | Brown    | Sales          |
| NULL       | NULL      | NULL     | IT             |

If no employee is in a department (like `IT`), the `EmployeeID`, `FirstName`, and `LastName` columns will be `NULL`.

---

### **1.4 FULL JOIN**

A `FULL JOIN` returns all rows from both tables. If no match is found, NULL is returned for missing values from the non-matching table.

### **FULL JOIN Query:**

```sql
SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
FROM Employees
FULL JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### **Result:**

| EmployeeID | FirstName | LastName | DepartmentName |
|------------|-----------|----------|----------------|
| 1          | John      | Doe      | Sales          |
| 2          | Jane      | Smith    | HR             |
| 3          | Mike      | Brown    | Sales          |
| NULL       | NULL      | NULL     | IT             |

Here, all rows from both tables are returned. Missing matches are filled with NULLs.

---

## **2. UNION**

The `UNION` operator combines the result sets of two or more `SELECT` statements and removes duplicates.

### **Tables:**

**Employees Table:**

| FirstName | LastName |
|-----------|----------|
| John      | Doe      |
| Jane      | Smith    |
| Mike      | Brown    |

**Customers Table:**

| FirstName | LastName |
|-----------|----------|
| Mary      | Johnson  |
| Jane      | Smith    |
| Lisa      | White    |

### **UNION Query:**

```sql
SELECT FirstName, LastName FROM Employees
UNION
SELECT FirstName, LastName FROM Customers;
```

### **Result:**

| FirstName | LastName |
|-----------|----------|
| John      | Doe      |
| Jane      | Smith    |
| Mike      | Brown    |
| Mary      | Johnson  |
| Lisa      | White    |

The query combines the `FirstName` and `LastName` columns from both tables, removing duplicate rows like `Jane Smith`.

---

### **2.1 UNION ALL**

The `UNION ALL` operator combines the result sets of two or more `SELECT` statements without removing duplicates.

### **UNION ALL Query:**

```sql
SELECT FirstName, LastName FROM Employees
UNION ALL
SELECT FirstName, LastName FROM Customers;
```

### **Result:**

| FirstName | LastName |
|-----------|----------|
| John      | Doe      |
| Jane      | Smith    |
| Mike      | Brown    |
| Mary      | Johnson  |
| Jane      | Smith    |
| Lisa      | White    |

The `UNION ALL` query includes all rows from both tables, even the duplicate `Jane Smith`.

---

## **3. INTERSECTION**

The `INTERSECTION` operator returns only the rows that are common between two result sets.

### **INTERSECTION Query:**

```sql
SELECT FirstName, LastName FROM Employees
INTERSECT
SELECT FirstName, LastName FROM Customers;
```

### **Result:**

| FirstName | LastName |
|-----------|----------|
| Jane      | Smith    |

This query returns only the row that is common in both `Employees` and `Customers`, which is `Jane Smith`.

---

## **Summary of Examples**

- **INNER JOIN**: Returns only the rows with matching values in both tables.
- **LEFT JOIN**: Returns all rows from the left table, matched rows from the right table.
- **RIGHT JOIN**: Returns all rows from the right table, matched rows from the left table.
- **FULL JOIN**: Returns all rows from both tables, with NULLs for non-matching rows.
- **UNION**: Combines results from multiple queries and removes duplicates.
- **UNION ALL**: Combines results from multiple queries without removing duplicates.
- **INTERSECTION**: Returns only the common rows from both result sets.

By understanding these operations with table examples, you can effectively combine and manipulate data from multiple tables in your SQL queries


# **Minus, Cursors, and Triggers in SQL**

Let's dive into the details of the `MINUS` operator, `Cursors`, and `Triggers` in SQL.

---

## **1. MINUS**

The `MINUS` operator is used to return the rows that are present in the first result set but not in the second result set. It is similar to the `EXCEPT` operator in some SQL dialects.

### **Syntax**:
```sql
SELECT columns FROM table1
MINUS
SELECT columns FROM table2;
```

### **Example:**

**Employees Table:**

| EmployeeID | FirstName | LastName |
|------------|-----------|----------|
| 1          | John      | Doe      |
| 2          | Jane      | Smith    |
| 3          | Mike      | Brown    |

**Customers Table:**

| CustomerID | FirstName | LastName |
|------------|-----------|----------|
| 1          | John      | Doe      |
| 2          | Alice     | Johnson  |

### **MINUS Query:**

```sql
SELECT FirstName, LastName FROM Employees
MINUS
SELECT FirstName, LastName FROM Customers;
```

### **Result:**

| FirstName | LastName |
|-----------|----------|
| Jane      | Smith    |
| Mike      | Brown    |

The query returns the rows that exist in `Employees` but do not exist in `Customers` based on the `FirstName` and `LastName` values.

---

## **2. Cursors**

A **Cursor** in SQL is a database object that allows you to retrieve, manipulate, and navigate through a result set row by row. Cursors are typically used when working with large sets of data and when complex operations need to be performed on each row individually.

### **Types of Cursors**:

1. **Implicit Cursor**: Automatically created by SQL when a SELECT statement is executed and it processes the query result without user interaction.
2. **Explicit Cursor**: Created and controlled by the programmer. It gives more control over how rows are fetched and processed.

### **Steps to Use Explicit Cursors**:
1. **Declare the cursor**.
2. **Open the cursor**.
3. **Fetch rows from the cursor**.
4. **Close the cursor**.

### **Syntax for Explicit Cursor**:

```sql
DECLARE cursor_name CURSOR FOR
SELECT column1, column2 FROM table;
 
OPEN cursor_name;
FETCH NEXT FROM cursor_name INTO @var1, @var2;
 
-- Process each row

CLOSE cursor_name;
DEALLOCATE cursor_name;
```

### **Example**:

```sql
DECLARE EmployeeCursor CURSOR FOR
SELECT FirstName, LastName FROM Employees;
 
OPEN EmployeeCursor;

FETCH NEXT FROM EmployeeCursor INTO @FirstName, @LastName;

WHILE @@FETCH_STATUS = 0
BEGIN
    PRINT 'Employee: ' + @FirstName + ' ' + @LastName;
    FETCH NEXT FROM EmployeeCursor INTO @FirstName, @LastName;
END

CLOSE EmployeeCursor;
DEALLOCATE EmployeeCursor;
```

This cursor retrieves and prints the `FirstName` and `LastName` of each employee in the `Employees` table, one at a time.

---

## **3. Triggers**

A **Trigger** is a special kind of stored procedure in SQL that is automatically executed or "triggered" when a specified event occurs on a table or view. Triggers are typically used to enforce business rules or integrity constraints on data modification operations like `INSERT`, `UPDATE`, or `DELETE`.

### **Types of Triggers**:
1. **BEFORE Trigger**: Executes before an `INSERT`, `UPDATE`, or `DELETE` operation.
2. **AFTER Trigger**: Executes after an `INSERT`, `UPDATE`, or `DELETE` operation.
3. **INSTEAD OF Trigger**: Executes in place of the triggering action, useful for modifying or replacing standard actions like inserts or updates.

### **Syntax for Trigger**:

```sql
CREATE TRIGGER trigger_name
AFTER INSERT ON table_name
FOR EACH ROW
BEGIN
   -- Trigger action (e.g., logging, enforcing constraints)
END;
```

### **Example:**

Let's say we have an `Employees` table, and we want to automatically log any changes to the `Salary` column.

**Employees Table:**

| EmployeeID | FirstName | LastName | Salary |
|------------|-----------|----------|--------|
| 1          | John      | Doe      | 5000   |
| 2          | Jane      | Smith    | 6000   |

### **Trigger Query**:

```sql
CREATE TRIGGER SalaryUpdateTrigger
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
   IF OLD.Salary <> NEW.Salary THEN
      INSERT INTO SalaryChangeLog (EmployeeID, OldSalary, NewSalary, ChangeDate)
      VALUES (NEW.EmployeeID, OLD.Salary, NEW.Salary, NOW());
   END IF;
END;
```

This trigger inserts a record into the `SalaryChangeLog` table whenever an employee's salary is updated.

**SalaryChangeLog Table**:

| EmployeeID | OldSalary | NewSalary | ChangeDate          |
|------------|-----------|-----------|---------------------|
| 1          | 5000      | 5500      | 2025-01-07 12:00:00 |
| 2          | 6000      | 6500      | 2025-01-07 14:00:00 |

### **Explanation:**
- The `SalaryUpdateTrigger` will be triggered **after** any update on the `Employees` table.
- If the `Salary` has been changed (i.e., `OLD.Salary` != `NEW.Salary`), a record is inserted into the `SalaryChangeLog` table, tracking the change.

---

## **Summary**

| **Concept**    | **Description**                                                         | **Example**                                                                 |
|----------------|-------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **MINUS**      | Returns rows in the first result set that are not in the second.        | Employees who are not customers (`Employees MINUS Customers`)               |
| **Cursors**    | Allows row-by-row processing of query results.                          | Using cursors to process employee records and print their names.           |
| **Triggers**   | Automatically executes actions when a specific database event occurs.   | Trigger to log salary changes after an employee’s salary is updated.       |

By understanding and utilizing `MINUS`, `Cursors`, and `Triggers`, you can handle more complex database operations and automate processes effectively in SQL


# **Procedures in SQL/PL SQL**

Procedures in SQL and PL/SQL are essential for encapsulating logic that can be reused and executed repeatedly. They allow for executing multiple SQL statements or PL/SQL blocks in a stored way, improving performance, readability, and maintainability.

---

## **1. What is a Procedure?**

A **procedure** is a named block of SQL or PL/SQL code that performs a specific task. It can take input parameters, execute a sequence of SQL commands or operations, and optionally return values.

In SQL, procedures are often written in PL/SQL (Oracle's procedural extension to SQL) to enable more complex operations like looping, conditional logic, and exception handling.

---

## **2. Syntax of a Procedure (PL/SQL)**

### **Basic Syntax**:
```sql
CREATE [OR REPLACE] PROCEDURE procedure_name 
    [ (parameter1 datatype, parameter2 datatype, ...) ]
AS
BEGIN
    -- SQL or PL/SQL code
    -- Optional: operations like SELECT, INSERT, UPDATE, DELETE, etc.
END;
```

- `CREATE PROCEDURE`: Used to create a procedure.
- `OR REPLACE`: Allows redefinition of an existing procedure.
- `parameter1 datatype`: Optional parameters that can be passed to the procedure.
- `BEGIN ... END;`: The body of the procedure that contains executable code.

---

## **3. Types of Parameters**

Procedures can have different types of parameters:

- **IN**: Input parameters that are passed to the procedure.
- **OUT**: Output parameters that are used to return values from the procedure.
- **IN OUT**: Parameters that can be both passed into and returned from the procedure.

---

## **4. Example of a Simple Procedure**

Let's create a procedure that inserts a new employee into the `Employees` table.

**Employees Table:**

| EmployeeID | FirstName | LastName | Salary |
|------------|-----------|----------|--------|
| 1          | John      | Doe      | 5000   |
| 2          | Jane      | Smith    | 6000   |

### **Procedure:**

```sql
CREATE OR REPLACE PROCEDURE AddEmployee(
    p_EmployeeID IN INT,
    p_FirstName IN VARCHAR2,
    p_LastName IN VARCHAR2,
    p_Salary IN NUMBER
) AS
BEGIN
    INSERT INTO Employees (EmployeeID, FirstName, LastName, Salary)
    VALUES (p_EmployeeID, p_FirstName, p_LastName, p_Salary);
    COMMIT;
END AddEmployee;
```

### **Explanation**:
- This procedure `AddEmployee` takes 4 parameters (`EmployeeID`, `FirstName`, `LastName`, and `Salary`) and inserts a new employee into the `Employees` table.
- The `COMMIT;` statement ensures that the changes are saved to the database.

---

## **5. Executing a Procedure**

To execute the procedure `AddEmployee`, you use the following `EXECUTE` command or `CALL` statement:

```sql
EXEC AddEmployee(3, 'Mike', 'Brown', 7000);
```

This call will insert a new employee into the `Employees` table with the given details.

---

## **6. Procedures with OUT Parameters**

You can also create procedures that return values via `OUT` parameters. Here's an example where we retrieve the salary of an employee based on their `EmployeeID`.

### **Example Procedure with OUT Parameter**:

```sql
CREATE OR REPLACE PROCEDURE GetSalary(
    p_EmployeeID IN INT,
    p_Salary OUT NUMBER
) AS
BEGIN
    SELECT Salary INTO p_Salary
    FROM Employees
    WHERE EmployeeID = p_EmployeeID;
END GetSalary;
```

### **Executing the Procedure**:

```sql
DECLARE
    v_Salary NUMBER;
BEGIN
    -- Call the procedure to get the salary
    GetSalary(2, v_Salary);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_Salary);
END;
```

### **Explanation**:
- `p_Salary` is an `OUT` parameter that will hold the employee's salary.
- The `SELECT INTO` statement is used to fetch the salary based on `EmployeeID` and store it into the `OUT` parameter.
- The result is then printed using `DBMS_OUTPUT.PUT_LINE`.

---

## **7. Error Handling in Procedures (Exception Handling)**

PL/SQL provides robust error handling mechanisms with `EXCEPTION` blocks. Here’s how you can handle errors in a procedure:

### **Example with Error Handling**:

```sql
CREATE OR REPLACE PROCEDURE AddEmployeeWithErrorHandling(
    p_EmployeeID IN INT,
    p_FirstName IN VARCHAR2,
    p_LastName IN VARCHAR2,
    p_Salary IN NUMBER
) AS
BEGIN
    BEGIN
        INSERT INTO Employees (EmployeeID, FirstName, LastName, Salary)
        VALUES (p_EmployeeID, p_FirstName, p_LastName, p_Salary);
        COMMIT;
    EXCEPTION
        WHEN DUP_VAL_ON_INDEX THEN
            DBMS_OUTPUT.PUT_LINE('Error: EmployeeID already exists.');
        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
    END;
END AddEmployeeWithErrorHandling;
```

### **Explanation**:
- The `EXCEPTION` block catches specific errors, such as trying to insert a duplicate `EmployeeID` (handled by `DUP_VAL_ON_INDEX`).
- The `OTHERS` clause catches any other errors and returns a general error message using `SQLERRM`.

---

## **8. Advantages of Using Procedures**

- **Reusability**: Once defined, procedures can be executed multiple times with different parameters.
- **Maintainability**: SQL code is centralized in the procedure, making it easier to maintain and modify.
- **Security**: You can restrict access to the underlying table and allow users to only execute the procedure, ensuring better security.
- **Performance**: Procedural logic can reduce the number of SQL calls, as multiple operations can be bundled into a single call.

---

## **Summary Table:**

| **Aspect**         | **Description**                                                            | **Example**                                        |
|--------------------|----------------------------------------------------------------------------|----------------------------------------------------|
| **Procedure**      | A stored program to perform specific tasks.                                | `CREATE PROCEDURE AddEmployee...`                  |
| **IN Parameter**   | Input parameter to pass values into the procedure.                         | `p_EmployeeID IN INT`                              |
| **OUT Parameter**  | Output parameter used to return values.                                    | `p_Salary OUT NUMBER`                              |
| **IN OUT Parameter** | Can pass values in and receive values out of the procedure.              | `p_Salary IN OUT NUMBER`                          |
| **Exception Handling** | Handle errors during execution using the `EXCEPTION` block.             | `WHEN DUP_VAL_ON_INDEX THEN...`                    |
| **Execution**      | Procedures can be executed using `EXEC` or `CALL` commands.               | `EXEC AddEmployee(3, 'Mike', 'Brown', 7000);`      |

By using SQL/PL SQL procedures, you can encapsulate complex logic, enforce business rules, and reduce redundant code in your database applications





