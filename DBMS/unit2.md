
## **1. Relational Data Model Concepts**

### **Relational Data Model**:
- **Definition**: A way to structure and organize data into tables (also called relations) consisting of rows (tuples) and columns (attributes).
  - **Example**: A `Students` table with columns `RollNo`, `Name`, and `Class` and rows of student data.

### **Relations**:
- **Definition**: A table that contains data, represented by rows and columns.
- **Example**: `Students(RollNo, Name, Class)`.

### **Attributes**:
- **Definition**: The columns of the table, representing data fields.
  - **Example**: `RollNo`, `Name`, `Class`.

### **Tuples**:
- **Definition**: A row in a table, representing a single data record.
  - **Example**: `(101, 'Ankit', '10A')` is a tuple in the `Students` table.

---

## **2. Integrity Constraints**

### **Entity Integrity**:
- **Definition**: Ensures that each row (tuple) in a table has a unique, non-null primary key.
  - **Example**: A `Students` table with `RollNo` as the primary key cannot have two rows with the same `RollNo`.

### **Referential Integrity**:
- **Definition**: Ensures that foreign keys in a table point to valid primary keys in another table.
  - **Example**: In the `Enrollments` table, the `StudentRollNo` foreign key must match a valid `RollNo` in the `Students` table.

### **Keys Constraints**:
- **Definition**: Ensures the uniqueness of rows based on the **primary key** and **foreign key** constraints.
  - **Primary Key Constraint**: Uniquely identifies each record.
  - **Foreign Key Constraint**: Ensures referential integrity.

### **Domain Constraints**:
- **Definition**: Specifies the valid values for an attribute (column), ensuring data consistency.
  - **Example**: The `Age` attribute in the `Students` table must be a valid integer between 5 and 25.

---

## **3. Relational Algebra**

### **Relational Algebra**:
- **Definition**: A procedural query language used to query relational databases.
- **Operations**:
  - **Select (σ)**: Filters rows based on conditions.
    ```sql
    SELECT * FROM Students WHERE Class = '10A';
    ```
  - **Project (π)**: Extracts specific columns from a table.
    ```sql
    SELECT Name, Class FROM Students;
    ```
  - **Union (∪)**: Combines results from two queries.
  - **Difference (−)**: Returns rows in one table that are not in another.
  - **Cartesian Product (×)**: Combines every row in one table with every row in another.

---

## **4. Relational Calculus**

### **Relational Calculus**:
- **Definition**: A non-procedural query language that uses logical expressions to describe the query result.

#### **Tuple Calculus**:
- **Definition**: Specifies queries based on rows (tuples).
  - **Example**: `{T | T ∈ Students AND T.Class = '10A'}` returns all students in `10A`.

#### **Domain Calculus**:
- **Definition**: Specifies queries based on individual columns (domains).
  - **Example**: `{C | ∃S (S ∈ Students AND S.Class = '10A' AND S.Name = C)}` returns all student names in `10A`.

---

## **5. Introduction to SQL**

### **Characteristics of SQL**:
- **Structured Query Language** is used for managing and manipulating relational databases.
- **Declarative**: Specifies what to do, not how to do it.
- **Platform Independent**: Works across different database systems (e.g., MySQL, Oracle).

### **Advantages of SQL**:
- **Simplicity**: Easy to understand and use.
- **Efficiency**: Allows efficient querying of large datasets.
- **Portability**: SQL works across various systems.

---

## **6. SQL Data Types and Literals**

### **SQL Data Types**:
- **Integer**: Used for whole numbers (`INT`, `BIGINT`).
- **String**: For text data (`VARCHAR`, `CHAR`).
- **Date/Time**: For date and time (`DATE`, `TIME`, `DATETIME`).
- **Boolean**: For true/false values (`BOOLEAN`).

### **SQL Literals**:
- **String Literals**: `'Ankit'`
- **Numeric Literals**: `101`
- **Date Literals**: `'2024-12-25'`

---

## **7. Types of SQL Commands**

### **1. DDL (Data Definition Language)**:
- Defines and manages database structures (e.g., `CREATE`, `ALTER`, `DROP`).

### **2. DML (Data Manipulation Language)**:
- Deals with data manipulation (e.g., `SELECT`, `INSERT`, `UPDATE`, `DELETE`).

### **3. DCL (Data Control Language)**:
- Controls access to data (e.g., `GRANT`, `REVOKE`).

### **4. TCL (Transaction Control Language)**:
- Manages transactions (e.g., `COMMIT`, `ROLLBACK`).

---

## **8. SQL Operators and Procedures**

### **SQL Operators**:
- **Arithmetic Operators**: `+`, `-`, `*`, `/`
  - **Example**: `SELECT Price * Quantity FROM Orders;`
- **Comparison Operators**: `=`, `!=`, `<`, `>`, `<=`, `>=`
  - **Example**: `SELECT * FROM Students WHERE Age > 18;`
- **Logical Operators**: `AND`, `OR`, `NOT`
  - **Example**: `SELECT * FROM Students WHERE Class = '10A' AND Age > 15;`
- **LIKE**: Used for pattern matching.
  - **Example**: `SELECT * FROM Students WHERE Name LIKE 'A%';`
- **IN**: Used to match multiple values.
  - **Example**: `SELECT * FROM Students WHERE Class IN ('10A', '10B');`
- **BETWEEN**: Filters values within a range.
  - **Example**: `SELECT * FROM Students WHERE Age BETWEEN 15 AND 18;`

---

## **9. Tables, Views, and Indexes**

### **Tables**:
- **Definition**: Basic units of data storage in SQL. They consist of rows and columns.
  - **Example**:
    ```sql
    CREATE TABLE Students (
      RollNo INT PRIMARY KEY,
      Name VARCHAR(50),
      Class VARCHAR(10)
    );
    ```

### **Views**:
- **Definition**: Virtual tables derived from a query. Do not store data but present it dynamically.
  - **Example**:
    ```sql
    CREATE VIEW StudentView AS SELECT Name, Class FROM Students WHERE Class = '10A';
    ```

### **Indexes**:
- **Definition**: A performance optimization feature that speeds up data retrieval.
  - **Example**:
    ```sql
    CREATE INDEX idx_students_name ON Students (Name);
    ```

---

## **10. Queries and Subqueries**

### **Queries**:
- **Definition**: SQL statements used to retrieve data from tables.
  - **Example**:
    ```sql
    SELECT * FROM Students WHERE Class = '10A';
    ```

### **Subqueries**:
- **Definition**: Queries nested inside other queries. Often used in `WHERE`, `FROM`, or `SELECT` clauses.
  - **Example**:
    ```sql
    SELECT * FROM Students WHERE RollNo IN (SELECT RollNo FROM Enrollments WHERE Course = 'Math');
    ```

---

## **11. Aggregate Functions**

### **Aggregate Functions**:
- **Definition**: Functions that operate on a set of rows and return a single value.
  - **COUNT**: Returns the number of rows.
    ```sql
    SELECT COUNT(*) FROM Students WHERE Class = '10A';
    ```
  - **SUM**: Returns the sum of a column's values.
    ```sql
    SELECT SUM(Amount) FROM Orders;
    ```
  - **AVG**: Returns the average value of a column.
    ```sql
    SELECT AVG(Age) FROM Students;
    ```
  - **MAX**: Returns the maximum value in a column.
    ```sql
    SELECT MAX(Age) FROM Students;
    ```
  - **MIN**: Returns the minimum value in a column.
    ```sql
    SELECT MIN(Age) FROM Students;
    ```

---

## **12. Insert, Update, and Delete Operations**

### **INSERT**:
- Adds new rows to a table.
  - **Example**:
    ```sql
    INSERT INTO Students (RollNo, Name, Class) VALUES (101, 'Ankit', '10A');
    ```

### **UPDATE**:
- Modifies existing rows.
  - **Example**:
    ```sql
    UPDATE Students SET Class = '10B' WHERE RollNo = 101;
    ```

### **DELETE**:
- Removes rows from a table.
  - **Example**:
    ```sql
    DELETE FROM Students WHERE RollNo = 101;
    ```

---

## **13. Joins, Unions, Intersection, Minus**

### **Joins**:
- **INNER JOIN**: Combines rows with matching values in both tables.
  - **Example**:
    ```sql
    SELECT Students.Name, Enrollments.Course FROM Students INNER JOIN Enrollments ON Students.RollNo = Enrollments.StudentRollNo;
    ```

###

 **UNION**:
- Combines results from multiple queries (eliminates duplicates).
  - **Example**:
    ```sql
    SELECT Name FROM Students WHERE Class = '10A' UNION SELECT Name FROM Students WHERE Class = '10B';
    ```

### **INTERSECTION**:
- Returns common rows between two queries.
  - **Example**:
    ```sql
    SELECT Name FROM Students WHERE Class = '10A' INTERSECT SELECT Name FROM Students WHERE Age > 15;
    ```

### **MINUS**:
- Returns rows from the first query that aren't in the second.
  - **Example**:
    ```sql
    SELECT Name FROM Students WHERE Class = '10A' MINUS SELECT Name FROM Students WHERE Age < 16;
    ```

---

## **14. Cursors, Triggers, and Procedures**

### **Cursors**:
- **Definition**: Used to retrieve rows one at a time from a result set.
  - **Example**: 
    ```sql
    DECLARE cursor_name CURSOR FOR SELECT * FROM Students;
    ```

### **Triggers**:
- **Definition**: Automatically execute SQL statements when certain events occur in a table (e.g., `INSERT`, `UPDATE`, `DELETE`).
  - **Example**:
    ```sql
    CREATE TRIGGER after_insert_students
    AFTER INSERT ON Students
    FOR EACH ROW
    BEGIN
      INSERT INTO Log (Action, Date) VALUES ('INSERT', NOW());
    END;
    ```

### **Stored Procedures (PL/SQL)**:
- **Definition**: Precompiled SQL code that can be executed repeatedly.
  - **Example**:
    ```sql
    CREATE PROCEDURE AddStudent(IN RollNo INT, IN Name VARCHAR(50), IN Class VARCHAR(10))
    BEGIN
      INSERT INTO Students (RollNo, Name, Class) VALUES (RollNo, Name, Class);
    END;
    ```

### **Examples of Joins, Unions, Intersection, and Minus with Tables**

#### **Given Tables**:

**Table 1: Students**
| RollNo | Name    | Class |
|--------|---------|-------|
| 1      | Ankit   | 10A   |
| 2      | Priya   | 10B   |
| 3      | Rohan   | 10A   |
| 4      | Sunita  | 10C   |

**Table 2: Enrollments**
| RollNo | Course    |
|--------|-----------|
| 1      | Math      |
| 2      | Science   |
| 3      | Math      |
| 5      | English   |

---

### **1. INNER JOIN**
- **Definition**: Combines rows with matching values in both tables.

**Query**:
```sql
SELECT Students.RollNo, Students.Name, Enrollments.Course 
FROM Students 
INNER JOIN Enrollments ON Students.RollNo = Enrollments.RollNo;
```

**Result**:
| RollNo | Name    | Course    |
|--------|---------|-----------|
| 1      | Ankit   | Math      |
| 2      | Priya   | Science   |
| 3      | Rohan   | Math      |

---

### **2. LEFT JOIN**
- **Definition**: Returns all rows from the left table and matching rows from the right table. Unmatched rows in the right table are `NULL`.

**Query**:
```sql
SELECT Students.RollNo, Students.Name, Enrollments.Course 
FROM Students 
LEFT JOIN Enrollments ON Students.RollNo = Enrollments.RollNo;
```

**Result**:
| RollNo | Name    | Course    |
|--------|---------|-----------|
| 1      | Ankit   | Math      |
| 2      | Priya   | Science   |
| 3      | Rohan   | Math      |
| 4      | Sunita  | NULL      |

---

### **3. UNION**
- **Definition**: Combines results from two queries and removes duplicates.

**Query**:
```sql
SELECT Name FROM Students 
UNION 
SELECT Course AS Name FROM Enrollments;
```

**Result**:
| Name    |
|---------|
| Ankit   |
| Priya   |
| Rohan   |
| Sunita  |
| Math    |
| Science |
| English |

---

### **4. INTERSECT**
- **Definition**: Returns only rows that are common to both queries.

**Query**:
```sql
SELECT RollNo FROM Students 
INTERSECT 
SELECT RollNo FROM Enrollments;
```

**Result**:
| RollNo |
|--------|
| 1      |
| 2      |
| 3      |

---

### **5. MINUS**
- **Definition**: Returns rows from the first query that are not in the second.

**Query**:
```sql
SELECT RollNo FROM Students 
MINUS 
SELECT RollNo FROM Enrollments;
```

**Result**:
| RollNo |
|--------|
| 4      |

---

This breakdown shows how **Joins**, **Unions**, **Intersect**, and **Minus** work with simple tables and queries. Each query retrieves specific types of data relationships. Let me know if you’d like a deeper dive into any of these!
