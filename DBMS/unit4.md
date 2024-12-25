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

Serializability ensures that executing transactions concurrently results in the same outcome as executing them one after another in some order (serial schedule). There are two main types of serializability: **Conflict Serializability** and **View Serializability**.

---

### 1. **Conflict Serializability**

- **Definition:** A schedule is conflict-serializable if the conflicts (read-write, write-read, or write-write) between transactions are resolved in such a way that the final result is equivalent to some serial execution of the transactions.
  
- **Conflict:** Occurs when two transactions access the same data item and at least one of the operations is a write.
  - **Examples of Conflicts:**
    - Write-Write conflict: Both transactions write to the same data item.
    - Read-Write conflict: One transaction reads a data item while another writes to it.
    - Write-Read conflict: One transaction writes to a data item, and another reads it.

- **Testing:** To test conflict serializability, we can create a **precedence graph**:
  - Each transaction is represented as a node.
  - Draw a directed edge from one transaction to another if there is a conflict between them (e.g., if transaction T1's write happens before T2's read of the same item).
  - If the graph has no cycles, the schedule is conflict-serializable. If there's a cycle, it is not.

#### Example:
Consider two transactions:

- **T1**: Write(A)
- **T2**: Read(A), Write(B)

The conflict between **T1** and **T2** is a Write-Read conflict. The schedule is conflict-serializable because the conflict can be resolved in an equivalent serial order, either executing T1 before T2 or T2 before T1.

---

### 2. **View Serializability**

- **Definition:** A schedule is view-serializable if the final database state after the transactions execute is equivalent to the state achieved after executing the transactions in some serial order. View serializability is **less strict** than conflict serializability.

Focus:** Unlike conflict serializability, which focuses on conflicts between operations, view serializability focuses on the consistency of the final database state. This means the **reads** and **writes** on the data must be equivalent to what would happen in a serial schedule.

- **Types of Views:**
  1. **Initial Read View:** The data read by a transaction should match the data read in the serial schedule.
  2. **Final Write View:** The final writes of a transaction must match what would happen in the serial schedule.

#### Example:
Consider the schedule:
- **T1**: Write(A)
- **T2**: Read(A), Write(B)

For view serializability, the final state should match what would happen in either serial execution (T1 → T2 or T2 → T1). If the result is the same in both cases, the schedule is view-serializable.

---

### Summary:

- **Conflict Serializability** ensures that conflicts between transactions are resolved in a way that the final result can be achieved by some serial execution of transactions.
**View Serializability** ensures that the database's final state matches what would happen if the transactions were executed in some serial order, but it is more lenient than conflict serializability.
  
Both forms of serializability are used to ensure that concurrent transactions do not lead to inconsistent or incorrect states in the database, but **conflict serializability** is stricter, focusing on specific conflicts between transaction operations.

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
A schedule is **recoverable** if transactions commit only after all dependent transactions (those that read the data written by another transaction) have committed. This ensures that no transaction commits based on uncommitted data from other transactions, maintaining consistency.

#### Why is it important?
If a transaction commits based on data from another transaction that has not yet committed, it can lead to inconsistencies if the first transaction rolls back. Therefore, the dependent transaction must not commit until the data from the preceding transaction is fully committed.

#### Example:
- **T1** updates data item **A**.
- **T2** reads **A** (dependent on **T1**'s update).
  
If **T2** commits before **T1** commits, **T2** is relying on uncommitted changes, which could be rolled back, leaving **T2** with invalid data. The correct behavior is for **T1** to commit before **T2** does.

---

### **5. Recovery from Transaction Failures**  
Failures can occur during transaction processing, and recovery mechanisms are essential to ensure the database returns to a consistent state. Recovery is needed in situations like transaction failure, system crash, or disk failure.

#### **Types of Failures**:
1. **Transaction Failure**:
   - Caused by logical errors such as incorrect inputs, violating constraints, or deadlocks.
   
2. **System Crash**:
   - Due to power outages, hardware malfunctions, or software bugs, which can cause the system to stop unexpectedly.
   
3. **Disk Failure**:
   - Corruption or damage to the storage medium that can lead to data loss.

#### **Recovery Mechanisms**:
- **Log-Based Recovery**:
  - A log is maintained to track all the changes made by transactions. This log is used to either **Undo** or **Redo** changes depending on whether a transaction is committed or not.
  
- **Checkpoints**:
  - Periodic snapshots of the database's state. When recovery is required, the system can start from the most recent checkpoint, reducing the time spent recovering from the logs.

#### Example:
- **T1** updates **A** from 10 to 20 and commits. 
- The system crashes after commit. During recovery, **Redo** ensures that **A** remains 20 after recovery, restoring the system to its consistent state.

---

### **6. Log-Based Recovery**  
Log-based recovery is the foundation of many database recovery systems. The log records every operation that changes the state of the database, including the start, commit, and rollback of transactions, as well as all data modifications.

#### Types of Logs:
- **Undo Logs**:
  - Tracks operations of uncommitted transactions. If a transaction fails, the changes made by that transaction are undone, restoring the database to its state before the transaction.
  
- **Redo Logs**:
  - Records committed transactions. If a crash happens after a commit, the redo log ensures that the changes made by the transaction are reapplied during recovery, even if they weren't fully written to disk at the time of the crash.

#### Example:
- If a power failure occurs during **T1**'s transaction:
  - The **Undo Logs** ensure any changes made by **T1** are reversed if it did not commit.
  - The **Redo Logs** ensure that the changes from transactions that were committed before the failure are applied, ensuring the database reflects all committed changes.

---

### **7. Checkpoints**  
A checkpoint is a mechanism to save the database’s state at a particular point in time. Checkpoints are critical for reducing the time it takes to recover from a failure. Instead of scanning the entire transaction log, recovery can start from the last checkpoint.

#### **Checkpoint Process**:
- The system periodically writes a snapshot of its current state (including all modified data) to stable storage.
- During recovery, the system does not need to go through all logs. Instead, it starts from the last checkpoint and processes only the transactions that occurred after that point.

#### Example:
- If a checkpoint occurs after **T1** but before **T2**:
  - During recovery, only transactions that occurred after the checkpoint (e.g., **T2**) need to be redone or undone, minimizing the recovery time compared to scanning the full transaction log.

---

### **8. Deadlock Handling**  
A **deadlock** occurs when two or more transactions are in a state of waiting for each other’s resources, causing them to be stuck indefinitely. Deadlock management is essential for preventing the system from becoming unresponsive.

#### **Deadlock Strategies**:
1. **Prevention**:
   - Deadlock is avoided by ensuring that one or more of the necessary conditions for deadlock do not hold:
     - **No circular wait**: Transactions must request all resources at once or in a specific order to prevent circular dependencies.
   
2. **Detection**:
   - The system uses a **wait-for graph**, where nodes represent transactions, and directed edges represent the wait-for relationship (a transaction waits for another to release a resource). A cycle in the graph indicates a deadlock.
   
3. **Resolution**:
   - When a deadlock is detected, the system must resolve it by aborting one or more transactions to break the cycle and release resources.

#### Example:
- **T1** locks **A** and waits for **B**.
- **T2** locks **B** and waits for **A**.
  
This results in a deadlock, and one of the transactions must be aborted to resolve it.

---

### **9. Distributed Database**  
A **distributed database** is a collection of databases distributed across multiple sites, which are managed and accessed in a way that makes them appear as a single unified system. This architecture offers advantages in terms of availability, fault tolerance, and scalability.

#### **Key Concepts**:
1. **Distributed Data Storage**:
   - **Partitioning**: Data is divided and stored across different locations based on specific criteria such as data type or region.
     - Example: **Indian customers** are stored on **Server A**, while **US customers** are stored on **Server B**.
   - **Replication**: Data is duplicated across multiple locations to provide fault tolerance and improve access speed. If one site fails, data is still available from another.
   
2. **Concurrency Control**:
   - Ensures consistency of data even when multiple transactions are accessing and modifying data stored in different locations.
   - **Two-Phase Commit Protocol (2PC)**: A protocol used to ensure that all nodes in a distributed system agree on a transaction commit or rollback. It consists of two phases:
     - **Phase 1**: All nodes prepare and agree to commit.
     - **Phase 2**: After the agreement, changes are committed to all nodes.
   - **Distributed Locks**: Used to ensure that only one transaction can access and modify a data item at a time across different sites.

3. **Directory System**:
   - Keeps track of the metadata about where data is stored in the distributed system.
   - For example, when querying for customer data from India, the system uses the directory to map the query to **Server A**, where the data is stored.

#### Example:
- **Customer Data**:
  - **India-based customers**: Stored on **Server A**.
  - **US-based customers**: Stored on **Server B**.
  - When a query for an Indian customer is received, the system uses the directory to direct the query to **Server A**, ensuring efficient data access.
