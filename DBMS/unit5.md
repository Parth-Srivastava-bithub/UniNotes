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
Concurrency control ensures that multiple transactions execute simultaneously without conflicts and maintain data consistency. It prevents issues like lost updates, dirty reads, and uncommitted dependency problems.  

#### **Problems in Concurrency**:  
1. **Lost Update**: Two transactions overwrite each other’s changes.  
2. **Dirty Read**: A transaction reads uncommitted changes of another.  
3. **Uncommitted Dependency**: A transaction depends on uncommitted changes.  

---

### **Locking Techniques for Concurrency Control**  
Locks prevent conflicts by controlling access to data.  

#### **Types of Locks**:  
1. **Binary Locks**:  
   - Data can either be locked or unlocked.  
   - Example: If T1 locks a row, T2 must wait.  
2. **Shared and Exclusive Locks**:  
   - **Shared Lock**: Multiple transactions can read but not write.  
   - **Exclusive Lock**: Only one transaction can read or write.  

#### **Two-Phase Locking Protocol (2PL)**:  
1. **Growing Phase**: Transaction acquires locks.  
2. **Shrinking Phase**: Transaction releases locks.  

#### Example:  
- T1 locks Account A → T2 waits.  
- T1 releases lock → T2 executes.  

---

### **Time Stamping Protocols for Concurrency Control**  
Each transaction is assigned a unique timestamp to determine execution order.  

#### **Rules**:  
1. **Read Rule**: A transaction can only read data if its timestamp is greater than the last write timestamp.  
2. **Write Rule**: A transaction can only write data if its timestamp is greater than the last read and write timestamps.  

#### Example:  
- T1 has timestamp 5, T2 has 10.  
- T1 executes first, followed by T2, ensuring no conflicts.  

---

### **Validation-Based Protocol**  
Transactions go through three phases:  
1. **Read Phase**: Transaction reads data but doesn’t modify it.  
2. **Validation Phase**: Checks if the transaction conflicts with others.  
3. **Write Phase**: Updates the database if validation succeeds.  

#### Example:  
- T1 and T2 read data.  
- During validation, if T1 writes and conflicts with T2, T2 is aborted.  

---

### **Multiple Granularity**  
Locks are applied at different levels of the database hierarchy (e.g., table, row).  

#### Lock Types:  
1. **Intent Locks**: Show intention to lock a lower-level item.  
2. **Shared and Exclusive Locks**: Applied to specific levels.  

#### Example:  
- T1 locks a table → T2 locks specific rows.  
- Intent locks ensure T2 waits if T1 modifies the table.  

---

### **Multi-Version Schemes**  
Maintains multiple versions of data to allow concurrent transactions.  
- **Read-Only Transactions**: Access the latest committed version.  
- **Update Transactions**: Create new versions of data.  

#### Example:  
- Version 1 of a row has value 100.  
- T1 updates it to 200 (Version 2).  
- T2 reads Version 1 until T1 commits.  

---

### **Recovery with Concurrent Transactions**  
Concurrent transactions need special recovery techniques to ensure consistency after failure.  

#### **Techniques**:  
1. **Undo Logs**: Reverse uncommitted changes.  
2. **Redo Logs**: Reapply committed changes.  
3. **Checkpoints**: Save database state periodically.  

#### Example:  
- T1 updates data → T2 reads data → System crashes.  
- Logs are used to restore the correct state.  

---

### **Case Study of Oracle**  
Oracle uses advanced concurrency control techniques:  
1. **Locks**: Implements row-level locking for granular control.  
2. **Multi-Version Concurrency Control (MVCC)**:  
   - Readers access a consistent snapshot of the database, ensuring no blocking.  
3. **Automatic Recovery**: Uses undo and redo logs for crash recovery.  
4. **Deadlock Detection**: Automatically identifies and resolves deadlocks by aborting one of the transactions.  

#### Example in Oracle:  
- T1 updates a row.  
- T2 tries to update the same row.  
- Oracle uses locks to serialize access, and T2 waits until T1 commits.  


