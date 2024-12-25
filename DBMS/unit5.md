```bash
Concurrency Control
|
├── Locking Techniques for Concurrency Control
|   ├── Shared Lock
|   ├── Exclusive Lock
|   ├── Two-Phase Locking
|   └── Deadlock Handling
|
├── Time Stamping Protocols for Concurrency Control
|   ├── Basic Timestamp Ordering
|   ├── Thomas' Write Rule
|   └── Multiversion Timestamp Protocol
|
├── Validation-Based Protocol
|   ├── Read Phase
|   ├── Validation Phase
|   └── Write Phase
|
├── Multiple Granularity
|   ├── Coarse Granularity
|   ├── Fine Granularity
|   └── Locking Hierarchy
|
├── Multi-Version Schemes
|   ├── Read-Only Transactions
|   ├── Versioned Data Items
|   └── Snapshot Isolation
|
├── Recovery with Concurrent Transactions
|   ├── Undo/Redo Logging
|   ├── Checkpoints
|   └── ARIES Recovery Algorithm
|
└── Case Study of Oracle
    ├── Locking Mechanisms in Oracle
    ├── Oracle’s Multi-Versioning (MVCC)
    ├── Oracle’s Transaction Recovery
    └── Oracle’s Real-Time Query Execution
```

### **Concurrency Control**
Concurrency control ensures that multiple database transactions can happen simultaneously without causing issues like data inconsistency, lost updates, or dirty reads. This is crucial for systems where many users access and modify the database at the same time.  

#### **Problems in Concurrency**:  
1. **Lost Update**: When two transactions try to update the same data, the changes of one are overwritten by the other.  
2. **Dirty Read**: A transaction reads data that has been changed by another transaction but not committed yet.  
3. **Uncommitted Dependency**: A transaction depends on data that hasn’t been finalized yet by another transaction.  

---

### **Locking Techniques for Concurrency Control**  
Locks are used to control access to data. By using different lock types, we can prevent multiple transactions from causing conflicts.  

#### **Types of Locks**:  
1. **Shared Lock**: Multiple transactions can read the data, but no transaction can modify it.  
2. **Exclusive Lock**: Only one transaction can read or write to the data at a time.  

#### **Two-Phase Locking Protocol (2PL)**:  
- In **Growing Phase**, transactions acquire locks.  
- In **Shrinking Phase**, they release locks.  
  This ensures no conflicting access happens while data is being updated.

#### **Deadlock Handling**:  
Deadlock occurs when two transactions are waiting for each other to release locks, causing a standstill. Systems handle this by either detecting and resolving the deadlock or aborting one transaction.

---

### **Time Stamping Protocols for Concurrency Control**  
Each transaction is assigned a unique timestamp that determines its order of execution. This helps in maintaining a sequence of actions.  

#### **Rules**:  
1. **Read Rule**: A transaction can read data only if its timestamp is greater than the last write timestamp.  
2. **Write Rule**: A transaction can write data only if its timestamp is greater than the last read and write timestamps.  

---

### **Validation-Based Protocol**  
This protocol involves three phases to avoid conflicts during concurrent transactions:  
1. **Read Phase**: The transaction reads the data but doesn’t modify it.  
2. **Validation Phase**: The transaction checks if its actions would conflict with others.  
3. **Write Phase**: If validation is successful, the transaction writes its changes to the database.

---

### **Multiple Granularity**  
Locks can be applied at different levels of granularity, such as on a table, row, or column. This allows for finer control of transactions.  

#### **Lock Types**:  
1. **Coarse Granularity**: Locks are applied at a higher level (like a whole table).  
2. **Fine Granularity**: Locks are applied at a more detailed level (like individual rows).  

---

### **Multi-Version Schemes**  
To improve concurrency, databases can maintain multiple versions of the same data, allowing transactions to work with different versions.  

- **Read-Only Transactions**: These transactions can access older versions without waiting for updates.  
- **Update Transactions**: These transactions create new versions when they modify data.  

---

### **Recovery with Concurrent Transactions**  
To ensure that the database can recover from crashes or failures while keeping transactions consistent, different recovery techniques are used.  

1. **Undo/Redo Logging**: Keeps logs of what was changed, so we can undo uncommitted changes or redo committed ones after a crash.  
2. **Checkpoints**: Save the state of the database at regular intervals to speed up recovery.  
3. **ARIES Recovery Algorithm**: A sophisticated recovery method that uses logs to restore database consistency.

---

### **Case Study of Oracle**  
Oracle uses advanced techniques to handle concurrency in its databases:  

1. **Locking Mechanisms**: It uses row-level locking, so multiple users can modify different rows without interfering with each other.  
2. **Multi-Version Concurrency Control (MVCC)**: Multiple versions of data are maintained, allowing transactions to access the most recent committed version without blocking.  
3. **Transaction Recovery**: Oracle uses undo and redo logs to restore consistency after system crashes.  
4. **Real-Time Query Execution**: Oracle optimizes query execution in real-time, ensuring fast responses even with concurrent transactions.
