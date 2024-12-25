```bash
Transaction Systems and Distributed Databases
├── Transaction System
│   ├── ACID Properties
│   │   ├── Atomicity
│   │   ├── Consistency
│   │   ├── Isolation
│   │   └── Durability
│   └── Example: Bank Transfer
├── Serializability
│   ├── Testing of Serializability
│   │   ├── Conflict Serializability
│   │   └── View Serializability
│   └── Serializability of Schedules
│       ├── Conflict Serializable Schedule
│       └── View Serializable Schedule
├── Recoverability
│   ├── Definition: Dependent transactions commit order
│   └── Example: Ensuring T1 commits before T2
├── Recovery from Transaction Failures
│   ├── Types of Failures
│   │   ├── Transaction Failure
│   │   ├── System Crash
│   │   └── Disk Failure
│   ├── Log-Based Recovery
│   │   ├── Undo Log
│   │   └── Redo Log
│   └── Checkpoints
│       └── Saves intermediate states
├── Deadlock Handling
│   ├── Prevention
│   │   └── Avoid circular wait
│   ├── Detection
│   │   └── Deadlock graphs
│   └── Resolution
│       └── Abort or restart transactions
├── Distributed Database
│   ├── Distributed Data Storage
│   │   ├── Partitioning
│   │   └── Replication
│   ├── Concurrency Control
│   │   ├── Two-Phase Commit Protocol (2PC)
│   │   └── Distributed Locks
│   └── Directory System
│       ├── Manages metadata
│       └── Maps queries to nodes
```


### **1. Transaction System**  
A **transaction system** ensures consistency, reliability, and integrity in databases through transactions. A transaction is a sequence of operations treated as a single unit.  

#### **Key Concepts**:  
- **ACID Properties**:  
  - **Atomicity**: All operations complete successfully, or none are applied.  
  - **Consistency**: The database moves from one valid state to another.  
  - **Isolation**: Transactions operate independently without interfering with each other.  
  - **Durability**: Once a transaction commits, changes are permanent.  

#### Example:  
If a user transfers $100 from Account A to Account B:  
- Debit $100 from A (Step 1).  
- Credit $100 to B (Step 2).  
If any step fails, the transaction is rolled back to maintain consistency.  

---

### **2. Testing of Serializability**  
Serializability ensures that the result of executing transactions concurrently is the same as executing them in some serial order.  

#### **Types of Serializability**:  
1. **Conflict Serializability**:  
   - Focuses on conflicts (read-write, write-read, or write-write).  
   - A schedule is conflict-serializable if conflicts are resolved in a way equivalent to a serial schedule.  

2. **View Serializability**:  
   - Focuses on ensuring the final state of the database matches a serial schedule.  
   - Less strict than conflict serializability.  

#### Example:  
- T1 writes A → T2 reads A → T2 writes B.  
- This schedule is serializable if T1 is executed before T2 or vice versa.  

---

### **3. Serializability of Schedules**  
Schedules define the order in which operations of transactions are executed.  
- **Conflict Serializable Schedule**: Ensures no conflicting operations (e.g., T1 reads while T2 writes).  
- **View Serializable Schedule**: Focuses on the final database state being equivalent to a serial execution.  

#### Example:  
If T1 transfers $100 and T2 updates an account balance:  
- Conflict Serializable: Ensure T1 and T2 don’t access the same account simultaneously.  
- View Serializable: Ensure the final balances match a serial execution.  

---

### **4. Recoverability**  
A schedule is **recoverable** if transactions commit only after all dependent transactions commit.  

#### Example:  
- T1 updates A.  
- T2 reads A.  
- T1 must commit before T2 commits; otherwise, T2 would rely on uncommitted changes.  

---

### **5. Recovery from Transaction Failures**  
Failures can occur due to various reasons, and recovery mechanisms ensure the database returns to a consistent state.  

#### **Types of Failures**:  
1. **Transaction Failure**:  
   - Logical errors (e.g., invalid input).  
2. **System Crash**:  
   - Power or hardware failure.  
3. **Disk Failure**:  
   - Data corruption or storage damage.  

#### **Recovery Mechanisms**:  
- **Log-Based Recovery**:  
  - Maintains a log of changes (Undo or Redo) to restore the database.  
- **Checkpoints**:  
  - Saves the current state of the database periodically, reducing the recovery time.  

#### Example:  
- T1 updates A from 10 to 20 → Commits → Crash → Redo ensures A remains 20 after recovery.  

---

### **6. Log-Based Recovery**  
Logs track all transaction operations to recover data after a failure.  
- **Undo Logs**: Reverse uncommitted changes.  
- **Redo Logs**: Reapply committed changes.  

#### Example:  
If a power failure occurs during a transaction:  
- Undo logs restore the database to its state before the transaction.  
- Redo logs ensure committed changes are retained.  

---

### **7. Checkpoints**  
Checkpoints are saved states of the database during operation. During recovery, the system starts from the last checkpoint instead of scanning the entire log.  

#### Example:  
If a checkpoint was created after T1 but before T2:  
- Only transactions after the checkpoint (e.g., T2) need to be rolled back or redone.  

---

### **8. Deadlock Handling**  
A **deadlock** occurs when two or more transactions wait indefinitely for each other’s resources.  

#### **Deadlock Strategies**:  
1. **Prevention**:  
   - Avoid circular waits by setting priorities or ordering resource allocation.  
2. **Detection**:  
   - Use a wait-for graph to identify cycles.  
3. **Resolution**:  
   - Abort one or more transactions to break the cycle.  

#### Example:  
- T1 locks A and waits for B.  
- T2 locks B and waits for A.  
- Deadlock occurs; one transaction must abort.  

---

### **9. Distributed Database**  
A distributed database system stores data across multiple locations but appears unified to users.  

#### **Key Concepts**:  
1. **Distributed Data Storage**:  
   - **Partitioning**: Data is split across locations based on specific criteria (e.g., region).  
   - **Replication**: Data is duplicated across locations for fault tolerance.  

   **Example**:  
   - Indian customers stored on Server A.  
   - US customers stored on Server B.  

2. **Concurrency Control**:  
   - Ensures consistent updates in distributed systems.  
   - **Two-Phase Commit Protocol (2PC)**:  
     - Phase 1: All nodes prepare and agree.  
     - Phase 2: Changes are committed.  
   - **Distributed Locks**: Prevents simultaneous updates to the same data.  

3. **Directory System**:  
   - Tracks metadata about data location and distribution.  
   - Example: A query for a customer from India maps to Server A.

---

