```bash
Relational Database Concepts
├── Functional Dependencies
│   ├── Definition
│   ├── FDs Examples
│   └── Inclusion Dependence
├── Normalization
│   ├── 1NF
│   │   └── Example: Atomic Values
│   ├── 2NF
│   │   ├── Example: Partial Dependency Removal
│   └── 3NF
│       ├── Example: Transitive Dependency Removal
│       └── Includes BCNF
│           └── Example: Superkey Constraint
├── Lossless Join Decomposition
│   └── Example: Splitting and Rejoining Tables
└── Alternative Approaches to Database Design
    ├── ER Model Design
    │   └── Example: Visual Design
    ├── Denormalization
    │   └── Example: Performance Optimization
    └── DKNF
        └── Example: Domain-Key Constraints

```
### **1. Functional Dependencies (FD)**
- **Definition**: A relationship between attributes in a table where one attribute uniquely determines another.
- **Notation**: `A → B` means if two rows have the same value for `A`, they must have the same value for `B`.

#### Example:
**Table: StudentDetails**  
| RollNo | Name    | Class | Marks |  
|--------|---------|-------|-------|  
| 1      | Ankit   | 10A   | 85    |  
| 2      | Priya   | 10B   | 90    |  
| 3      | Rahul   | 10A   | 78    |  

**FDs in the table**:  
- `RollNo → Name, Class, Marks`: RollNo uniquely identifies all other attributes.  
- `Class → Marks` is **not valid** because multiple students can have the same Class but different Marks.

---

### **2. Normal Forms**
Normalization eliminates redundancy and ensures data integrity by organizing data into structured forms.

#### **First Normal Form (1NF)**:
- A table is in 1NF if:
  - Each column contains atomic (indivisible) values.
  - There are no repeating groups.

**Invalid Table (Repeating Groups)**:  
| RollNo | Name  | Subjects      |  
|--------|-------|---------------|  
| 1      | Ankit | Math, Science |  
| 2      | Priya | Math          |  

**Normalized Table (1NF)**:  
| RollNo | Name  | Subject   |  
|--------|-------|-----------|  
| 1      | Ankit | Math      |  
| 1      | Ankit | Science   |  
| 2      | Priya | Math      |  

---

#### **Second Normal Form (2NF)**:
- A table is in 2NF if:
  - It is in 1NF.
  - No partial dependency exists (i.e., no non-prime attribute depends only on part of a composite key).

**Example of Partial Dependency**:  
| RollNo | CourseID | CourseName | Marks |  
|--------|----------|------------|-------|  
| 1      | 101      | Math       | 85    |  
| 1      | 102      | Science    | 90    |  

Here, `CourseName` depends only on `CourseID`, not on the full key (`RollNo, CourseID`).  
**Normalized Table (2NF)**:  

**Table 1: StudentCourses**  
| RollNo | CourseID | Marks |  
|--------|----------|-------|  
| 1      | 101      | 85    |  
| 1      | 102      | 90    |  

**Table 2: Courses**  
| CourseID | CourseName |  
|----------|------------|  
| 101      | Math       |  
| 102      | Science    |  

---

#### **Third Normal Form (3NF)**:
- A table is in 3NF if:
  - It is in 2NF.
  - No transitive dependency exists (i.e., non-prime attributes depend on other non-prime attributes).

**Example of Transitive Dependency**:  
| RollNo | Class | ClassTeacher |  
|--------|-------|--------------|  
| 1      | 10A   | Mr. Sharma   |  
| 2      | 10B   | Ms. Gupta    |  

Here, `ClassTeacher` depends on `Class`, not directly on `RollNo`.  
**Normalized Table (3NF)**:  

**Table 1: Students**  
| RollNo | Class |  
|--------|-------|  
| 1      | 10A   |  
| 2      | 10B   |  

**Table 2: Classes**  
| Class | ClassTeacher |  
|-------|--------------|  
| 10A   | Mr. Sharma   |  
| 10B   | Ms. Gupta    |  

---

### **3. Boyce-Codd Normal Form (BCNF)**
- A table is in BCNF if:
  - It is in 3NF.
  - For every functional dependency `A → B`, `A` must be a superkey.

**Example of BCNF Violation**:  
| StudentID | Subject   | Teacher     |  
|-----------|-----------|-------------|  
| 1         | Math      | Mr. Sharma  |  
| 2         | Science   | Ms. Gupta   |  
| 1         | Science   | Ms. Gupta   |  

Here, `Subject → Teacher`, but `Subject` is not a superkey.  
**Normalized Table (BCNF)**:  

**Table 1: Subjects**  
| Subject   | Teacher     |  
|-----------|-------------|  
| Math      | Mr. Sharma  |  
| Science   | Ms. Gupta   |  

**Table 2: StudentSubjects**  
| StudentID | Subject   |  
|-----------|-----------|  
| 1         | Math      |  
| 1         | Science   |  
| 2         | Science   |  

---

### **4. Inclusion Dependence**
- **Definition**: Ensures that values in one table must match values in another, similar to referential integrity.

**Example**:  
**Table 1: Students**  
| RollNo | Name  |  
|--------|-------|  
| 1      | Ankit |  
| 2      | Priya |  

**Table 2: Enrollments**  
| RollNo | CourseID |  
|--------|----------|  
| 1      | 101      |  
| 2      | 102      |  
- `Enrollments.RollNo` must match `Students.RollNo`.

---

### **5. Lossless Join Decomposition**
- **Definition**: Splitting a table into smaller tables without losing data when they are joined back.

#### Example:
**Original Table**:  
| RollNo | CourseID | Marks | CourseName |  
|--------|----------|-------|------------|  
| 1      | 101      | 85    | Math       |  

**Decomposed Tables**:  

**Table 1: StudentCourses**  
| RollNo | CourseID | Marks |  
|--------|----------|-------|  
| 1      | 101      | 85    |  

**Table 2: Courses**  
| CourseID | CourseName |  
|----------|------------|  
| 101      | Math       |  

Join Result: Matches the original table.

---

### **6. Normalization Using FDs, MVDs, and JDs**
#### **Multivalued Dependencies (MVDs)**:
- Occurs when one attribute determines multiple independent values of another attribute.
- **Example**:  
  | StudentID | Course | Hobby      |  
  |-----------|--------|------------|  
  | 1         | Math   | Painting   |  
  | 1         | Math   | Singing    |  

Here, `StudentID →→ Hobby` (MVD), and it’s independent of `Course`.

#### **Join Dependencies (JDs)**:
- A table can be decomposed into smaller tables and then joined without losing data.

---

### **7. Alternative Approaches to Database Design**
1. **ER Model Design**:
   - Use Entity-Relationship diagrams to design databases visually.
2. **Denormalization**:
   - Combine tables for performance optimization, sacrificing normalization.
3. **Domain-Key Normal Form (DKNF)**:
   - Ensures every constraint is a logical consequence of domain and key constraints.


