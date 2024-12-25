```bash
Overview of Database Concepts
├── Database System vs File System
│   ├── Database System: Data integrity, multi-user support
│   └── File System: Limited data sharing, no relationships
├── Database System Concepts and Architecture
│   ├── Layers
│   │   ├── Physical Layer
│   │   ├── Logical Layer
│   │   └── View Layer
│   ├── Components
│   │   ├── DBMS Engine
│   │   ├── Query Processor
│   │   └── Storage Manager
├── Data Models, Schema, and Instances
│   ├── Data Models
│   │   ├── Relational
│   │   ├── Hierarchical
│   │   └── Network
│   ├── Schema
│   │   ├── Physical Schema
│   │   ├── Logical Schema
│   │   └── View Schema
│   └── Instance: Snapshot of data
├── Data Independence
│   ├── Logical Independence
│   └── Physical Independence
├── Database Language and Interfaces
│   ├── Data Definition Language (DDL)
│   ├── Data Manipulation Language (DML)
│   ├── Query Languages (SQL)
│   └── User Interfaces
├── Data Modeling Using ER Model
│   ├── ER Model Concepts
│   │   ├── Entities
│   │   ├── Attributes
│   │   └── Relationships
│   ├── Notation for ER Diagram
│   │   ├── Rectangles: Entities
│   │   ├── Ovals: Attributes
│   │   └── Diamonds: Relationships
│   ├── Mapping Constraints
│   │   ├── 1:1
│   │   ├── 1:N
│   │   └── M:N
│   ├── Keys
│   │   ├── Super Key
│   │   ├── Candidate Key
│   │   └── Primary Key
│   ├── Generalization and Aggregation
│   │   ├── Generalization: Combining entities
│   │   └── Aggregation: Abstracting relationships
│   ├── Reduction of ER Diagrams to Tables
│   └── Extended ER Model
│       ├── Specialization
│       ├── Generalization
│       └── Subclasses
└── Relationships of Higher Degree
    ├── Ternary Relationships
    └── Higher-Degree Relationships

```

## **1. Database System vs File System**

### **File System**:
- **Definition**: A system for storing and organizing files in a computer's storage. Files are managed individually.
- **Limitations**: 
  - Data redundancy (duplicate data).
  - Lack of efficient querying.
  - Inconsistent data.
  - No support for concurrent access or security.

### **Database System**:
- **Definition**: A system that stores, manages, and processes data in a structured way using a database management system (DBMS). It provides organized storage, retrieval, and manipulation.
- **Advantages**:
  - **Data Integrity**: Avoids redundancy and inconsistency.
  - **Data Independence**: Changes in database structure don't affect the applications.
  - **Concurrency Control**: Multiple users can access data simultaneously without conflict.
  - **Security**: Allows controlled access to data.

---

## **2. Database System Concepts and Architecture**

### **Database System Architecture**:
1. **Internal Level**: Physical storage of data (how data is stored).
2. **Conceptual Level**: Logical view of the entire database (what data is stored).
3. **External Level**: User's view of the data (how users interact with the data).

### **Data Independence**:
- **Logical Data Independence**: Ability to change the logical (conceptual) schema without changing the external schema or application programs.
- **Physical Data Independence**: Ability to change the physical storage of data without affecting the conceptual schema.

---

## **3. Data Model, Schema, and Instances**

### **Data Model**:
- **Definition**: A conceptual framework used to define the structure and relationships of data in a database (e.g., relational, hierarchical, network).
- **Example**: The **Relational Model** uses tables to represent data.

### **Schema**:
- **Definition**: The logical structure of the database (how the data is organized). It defines the tables, their columns, and relationships.
  - **Example**: `Students (RollNo, Name, Class)` is the schema for a `Students` table.

### **Instance**:
- **Definition**: The data stored in the database at a particular moment in time.
  - **Example**: 
    | RollNo | Name  | Class |  
    |--------|-------|-------|  
    | 101    | John  | 10A   |  
    | 102    | Mary  | 10B   |

---

## **4. Data Language and Interfaces**

### **DDL (Data Definition Language)**:
- **Mnemonic**: **DAC** (*Drop, Alter, Create*)
- **Commands**:
  - **CREATE**: Creates a new table or structure.
  - **ALTER**: Modifies an existing structure.
  - **DROP**: Deletes a table or structure.
  - **Example**:
    ```sql
    CREATE TABLE Students (
      RollNo INT PRIMARY KEY,
      Name VARCHAR(50),
      Class VARCHAR(10)
    );
    ```

### **DML (Data Manipulation Language)**:
- **Mnemonic**: **SIDU** (*Select, Insert, Delete, Update*)
- **Commands**:
  - **SELECT**: Retrieves data.
  - **INSERT**: Adds new data.
  - **DELETE**: Removes data.
  - **UPDATE**: Modifies data.
  - **Example**:
    ```sql
    INSERT INTO Students (RollNo, Name, Class) VALUES (101, 'Ankit', '10A');
    SELECT * FROM Students WHERE Class = '10A';
    ```

### **DCL (Data Control Language)**:
- **Mnemonic**: **GR** (*Grant, Revoke*)
- **Commands**:
  - **GRANT**: Gives permissions.
  - **REVOKE**: Removes permissions.
  - **Example**:
    ```sql
    GRANT SELECT ON Students TO 'user123';
    REVOKE SELECT ON Students FROM 'user123';
    ```

### **TCL (Transaction Control Language)**:
- **Mnemonic**: **CRaST** (*Commit, Rollback, Savepoint, Transaction*)
- **Commands**:
  - **COMMIT**: Saves changes permanently.
  - **ROLLBACK**: Reverts changes.
  - **SAVEPOINT**: Creates a rollback point.
  - **Example**:
    ```sql
    COMMIT;
    ROLLBACK;
    SAVEPOINT BeforeUpdate;
    ```

---

## **5. Keys in Databases**

### **Primary Key**:
- **Definition**: A unique identifier for each record. Cannot be NULL.
- **Example**:
  ```sql
  CREATE TABLE Students (
    RollNo INT PRIMARY KEY,
    Name VARCHAR(50),
    Class VARCHAR(10)
  );
  ```

### **Candidate Key**:
- **Definition**: Any set of attributes that can uniquely identify a record. One of them is chosen as the Primary Key.
- **Example**: 
  - In `Students`, both `RollNo` and `Email` can be **Candidate Keys**.
  - **Primary Key**: `RollNo`, **Alternate Key**: `Email`.

### **Super Key**:
- **Definition**: A set of attributes that can uniquely identify a record but may include redundant attributes.
- **Example**: `{RollNo, Name}` is a **Super Key**.

### **Foreign Key**:
- **Definition**: A key that links one table to another by referencing the **Primary Key** of another table.
- **Example**:
  ```sql
  CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentRollNo INT,
    FOREIGN KEY (StudentRollNo) REFERENCES Students(RollNo)
  );
  ```

### **Composite Key**:
- **Definition**: A key that combines multiple columns to uniquely identify a record.
- **Example**:
  ```sql
  CREATE TABLE Orders (
    OrderID INT,
    ProductID INT,
    PRIMARY KEY (OrderID, ProductID)
  );
  ```

### **Alternate Key**:
- **Definition**: A **Candidate Key** that is not chosen as the **Primary Key**.
- **Example**: If `RollNo` is Primary Key, then `Email` is an **Alternate Key**.

### **Unique Key**:
- **Definition**: Ensures that all values in a column are unique, but can have NULL values.
- **Example**:
  ```sql
  CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Email VARCHAR(50) UNIQUE
  );
  ```

### **Surrogate Key**:
- **Definition**: A system-generated key (often auto-incremented).
- **Example**:
  ```sql
  CREATE TABLE Users (
    UserID INT AUTO_INCREMENT PRIMARY KEY,
    Username VARCHAR(50)
  );
  ```

### **Natural Key**:
- **Definition**: A key that comes from real-world data.
- **Example**:
  ```sql
  CREATE TABLE Users (
    Email VARCHAR(50) PRIMARY KEY,
    Name VARCHAR(50)
  );
  ```

### **Compound Key**:
- **Definition**: Similar to a Composite Key, but typically used in **many-to-many relationships**.
- **Example**:
  ```sql
  CREATE TABLE StudentCourse (
    StudentID INT,
    CourseID INT,
    PRIMARY KEY (StudentID, CourseID)
  );
  ```

---

## **6. Entity-Relationship Model (ER Model)**

### **ER Model Concepts**:
- **Entities**: Objects in the database (e.g., `Students`, `Courses`).
- **Attributes**: Properties of an entity (e.g., `RollNo`, `Name`).
- **Relationships**: Associations between entities (e.g., `Enrolls` relationship between `Student` and `Course`).

### **Keys in ER Model**:
- **Super Key**: A set of attributes that uniquely identify an entity.
- **Primary Key**: The chosen Super Key for identifying an entity.
- **Candidate Key**: A set of potential keys that could serve as the Primary Key.

### **ER Diagram Notations**:
- **Rectangle**: Represents an entity.
- **Diamond**: Represents a relationship.
- **Ellipse**: Represents an attribute.
- **Line**: Represents relationships between entities.

### **Mapping ER to Tables**:
- **Entities**: Become tables.
- **Attributes**: Become columns.
- **Relationships**: Become foreign keys.

---

## **7. Extended ER Model**
- **Generalization**: A process where common attributes of multiple entities are generalized into a parent entity.
- **Aggregation**: A higher-level abstraction where a relationship is treated as an entity.
- **Higher-Degree Relationships**: Relationships that involve more than two entities.


