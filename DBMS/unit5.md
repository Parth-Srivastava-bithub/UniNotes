```bash
Unit 5
│
├── Lock
│   ├── Binary Lock
│   │   ├── Rules Every Transaction Must Follow (4 Rules)
│   │   └── Example
│   ├── Shared Locks
│   │   ├── Process
│   │   └── Example
│   ├── Why Read/Write Locks Are Also Known As Shared Locks
│   ├── Rules to Follow (6 Rules)
│   ├── Conversion Lock
│   └── Two-Phase Locking
│       ├── Basic 2PL
│       ├── Conservative 2PL
│       ├── Strict 2PL
│       └── Rigorous 2PL
├── Concurrency Control Based on Timestamp Ordering
│   ├── Timestamps
│   ├── Timestamp Ordering Algorithm
│   │   ├── Key Features
│   │   ├── Difference from 2PL
│   │   ├── read_TS(X)
│   │   ├── Formula
│   │   └── write_TS(X)
│   ├── How to Ensure Serializability
│   │   ├── Advantages
│   │   └── Disadvantages
│   ├── Basic Timestamp Ordering (TO)
│   │   ├── Steps
│   │   ├── Write Item(X) Operation Checks
│   │   └── Read Item(X) Operation Checks
│   ├── Strict Timestamp Ordering (TO)
│   │   └── Steps
│   ├── Thomas Write Rule
│   └── Multiversion Concurrency Control Technique
│       ├── Key Features
│       │   └── Multiple Version
│       ├── Advantages
│       └── Drawbacks
├── Multiversion Technique Based on Timestamp Ordering
│   ├── Key Concepts
│   │   ├── Version of X
│   │   │   ├── Value
│   │   │   ├── Write
│   │   │   └── Read
├── Rules of Serializability
│   ├── Write Operation (write_item(X))
│   │   ├── Check for Conflicts
│   │   │   ├── If Conflicts
│   │   │   └── If No Conflicts
│   │   └── Examples
│   ├── Read Operation (read_item(X))
│   │   ├── Find Latest Suitable Version
│   │   └── Read the Value and Update read_TS
├── Multiversion Two-Phase Locking MVP2PL Using Certified Locks
│   ├── Key Components
│   │   ├── Locks Used
│   │   │   ├── Read Lock
│   │   │   ├── Write Lock
│   │   │   └── Certify Lock
│   │   ├── Version Management
│   │   └── Phases
│   │       ├── Growing Phase
│   │       └── Shrinking Phase
│   ├── Two Versions of Each Item
│   │   ├── Committed Version
│   │   └── Uncommitted Version
│   ├── Steps in MVP2PL
│   │   ├── Write Lock
│   │   ├── Commit Phase
│   │   ├── Replace the Old Version
│   │   └── Release Locks
│   ├── Advantages
│   │   ├── Concurrent Reads
│   │   └── Avoid Cascading Aborts
├── Validation Concurrency Control Technique
│   ├── How It Works
│   │   ├── Read Phase
│   │   ├── Validation Phase
│   │   └── Write Phase
│   ├── Validation Rules
│   │   ├── Condition 1
│   │   └── Condition 2
│   ├── Phantom Phenomenon
│   │   └── Example
│   ├── Timestamp Protocol to Avoid Phantom Phenomenon
│   │   ├── Assign Timestamps
│   │   │   ├── Read Operations
│   │   │   └── Write Operations
│   │   ├── Range Queries to Avoid Phantoms
│   │   │   ├── Handle Range of Queries
│   │   │   └── Ensuring Serializability
├── How Validation Differs from 2PL Validation (Optimistic Concurrency Control)
│   ├── Approach
│   ├── Phases
│   │   ├── Validation Phase
│   │   ├── Growing Phase
│   │   └── Shrinking Phase
│   ├── Performance
│   ├── Key Differences
│   └── Overall Table Difference
├── Recovery from Concurrent Transactions
│   ├── Transaction Log
│   ├── Undo/Redo
│   ├── Before and After Images
├── Transaction States
│   ├── Committed
│   ├── Active
│   ├── Aborted
│   ├── Recovery Protocol
│   │   ├── Write Ahead Logging
│   │   └── Checkpoints
├── Two-Phase Commit Protocol
│   ├── Prepare Phase
│   └── Commit/Abort Phase
├── Recovery Procedure
│   ├── Identify Transactions to Undo-Redo
│   │   ├── Undo Phase
│   │   └── Redo Phase
├── Multiple Granularity Lock
│   ├── Tradeoffs in Granularity
│   │   ├── Fine Granularity
│   │   └── Coarse Granularity
│   ├── Lower Overhead, Fewer Items Mean
│   └── Choosing the Right Granularity
├── Multiple Granularity Level Locking Problem with Basic Locking
│   └── 2PL Protocol Level
```
# Lock

#### Binary Lock
A binary lock can have only two states: locked or unlocked. It is used to ensure mutual exclusion in database systems.

#### Rules Every Transaction Must Follow (4 Rules)
1. **Acquire Lock Before Access**: A transaction must acquire a lock on the data item before reading or writing it.
2. **Hold Lock Until Done**: The transaction must hold the lock until it has finished using the data item.
3. **Release Lock After Access**: The transaction should release the lock after it has completed its operations on the data item.
4. **No Reacquisition**: A transaction cannot reacquire a lock that it has already released.

#### Example
Consider two transactions, T1 and T2, both trying to update a bank account balance:
- T1 acquires the lock on the balance and updates it.
- T2 waits until T1 releases the lock.
- Once T1 releases the lock, T2 can then acquire it and proceed with its update. 

This ensures that both transactions do not interfere with each other, maintaining data consistency.
### Shared Locks

#### Process
A **shared lock** allows multiple transactions to read a data item simultaneously but prevents any transaction from writing to it until all shared locks are released.

#### Example
- **Transaction T1** acquires a shared lock on a data item to read it.
- **Transaction T2** also acquires a shared lock on the same data item to read it.
- Neither T1 nor T2 can write to the data item until both release their shared locks, ensuring no data inconsistency occurs due to concurrent reads.

#### Why Read/Write Locks Are Also Known as Shared Locks
Read/write locks are called **shared locks** because they allow concurrent reading by multiple transactions, sharing the data for read operations while preventing write access to maintain data integrity.

#### Rules to Follow (6 Rules)
1. **Multiple Read Access**: Many transactions can hold shared locks on a data item simultaneously.
2. **No Write Access with Shared Lock**: A data item cannot be written to when a shared lock is held.
3. **Upgrade Restriction**: A shared lock cannot be upgraded to an exclusive lock if another transaction already holds a shared lock.
4. **Downgrade Allowed**: An exclusive lock can be downgraded to a shared lock.
5. **Precedence for Exclusive Locks**: If an exclusive lock request is pending, no new shared locks are granted.
6. **Release Before Writing**: A shared lock must be released before a transaction can request an exclusive lock to write the data.

These rules ensure that shared locks help maintain a balance between concurrency and data consistency

# Conversion Lock

A **conversion lock** allows a transaction holding a shared lock on a data item to convert it to an exclusive lock, provided no other transactions hold a shared lock on the same item.

#### Process
1. A transaction holds a **shared lock** on a data item.
2. It decides to perform a write operation and requests to **convert** the shared lock to an **exclusive lock**.
3. The conversion is granted if no other transactions hold shared locks on that data item at the time of the request.

#### Example
- **Transaction T1** has a shared lock on a data item (reading it).
- T1 decides to update the data item and requests an exclusive lock.
- If no other transaction holds a shared lock, T1's shared lock is converted to an exclusive lock, allowing the update.

#### Importance
Conversion locks improve efficiency by allowing a transaction to escalate its lock type without releasing and reacquiring locks, reducing the chances of deadlocks and maintaining consistency

# Two Phase Locking (2PL)

**Two Phase Locking** is a concurrency control method that ensures transactions are executed in two distinct phases: the **growing phase** (acquiring locks) and the **shrinking phase** (releasing locks).

#### Basic 2PL
- **Growing Phase**: The transaction acquires all the locks it needs but cannot release any.
- **Shrinking Phase**: Once it releases a lock, it cannot acquire any more locks.
- Ensures **serializability** but may lead to **deadlocks**.

#### Conservative 2PL
- Acquires all the required locks before the transaction starts.
- **Deadlock-free**, as it prevents the transaction from waiting for locks.
- May result in **reduced concurrency** because it may hold locks longer than necessary.

#### Strict 2PL
- All locks are held until the transaction **commits or aborts**.
- Provides **cascadeless schedules** by preventing intermediate state exposure.
- **Reduces concurrency** but enhances **recoverability**.

#### Rigorous 2PL
- Similar to strict 2PL, but all locks (both shared and exclusive) are held until the transaction commits.
- Ensures **serializability** and **recoverability**, and prevents **cascading rollbacks**.
- **Lowest concurrency** among the 2PL variations, but the safest in terms of consistency and recovery

# Concurrency Control Based on Timestamp Ordering

**Timestamp Ordering (TO)** is a concurrency control mechanism used in databases to ensure the serializability of transactions by ordering their operations based on timestamps. This approach eliminates the need for locks, thus preventing deadlocks.

## Timestamps
- Each transaction **T** is assigned a unique **timestamp** \(\text{TS}(T)\) when it starts, usually based on the system clock or a logical counter.
- The timestamp represents the transaction’s order relative to others in the system.
- There are two types of timestamps for each data item **X**:
  - **read_TS(X)**: The largest timestamp of any transaction that has successfully read **X**.
  - **write_TS(X)**: The largest timestamp of any transaction that has successfully written **X**.

#### The Timestamp Ordering Algorithm
The algorithm ensures that transactions are executed in a way that their operations are ordered according to their timestamps:

1. **Read Operation** \(\text{read}(X)\):
   - If \(\text{TS}(T) < \text{write\_TS}(X)\), the read operation is rejected, and **T** is aborted because a more recent transaction has already written to **X**.
   - Otherwise, the read operation is allowed, and \(\text{read\_TS}(X)\) is updated to \(\max(\text{read\_TS}(X), \text{TS}(T))\).

2. **Write Operation** \(\text{write}(X)\):
   - If \(\text{TS}(T) < \text{read\_TS}(X)\), the write operation is rejected, and **T** is aborted because a more recent transaction has read **X**.
   - If \(\text{TS}(T) < \text{write\_TS}(X)\), the write operation is rejected for similar reasons, and **T** is aborted.
   - Otherwise, the write operation is allowed, and \(\text{write\_TS}(X)\) is updated to \(\text{TS}(T)\).

#### Key Features
- **Non-Blocking**: Transactions do not have to wait; they are either allowed to proceed or are aborted.
- **Deadlock-Free**: Since no locks are used, there is no possibility of deadlocks.
- **Preemptive Abortion**: Transactions that violate the timestamp order are aborted and restarted with new timestamps, ensuring the correct order of operations.

#### Difference From 2PL
- **No Locks**: Unlike Two-Phase Locking (2PL), TO doesn’t use locks, which eliminates the chance of deadlocks.
- **Immediate Conflict Resolution**: In TO, conflicts are resolved immediately by aborting the conflicting transaction, whereas in 2PL, transactions may wait for locks, potentially causing deadlocks.
- **Higher Abort Rate**: TO may result in more transaction abortions than 2PL, especially in high-conflict scenarios.

#### `read_TS(X)` and `write_TS(X)`
- **`read_TS(X)`**: Tracks the most recent transaction that has read the data item **X**.
  - Formula: \(\text{read\_TS}(X) = \max(\text{TS}(T), \text{read\_TS}(X))\).
- **`write_TS(X)`**: Tracks the most recent transaction that has written to the data item **X**.
  - Formula: \(\text{write\_TS}(X) = \max(\text{TS}(T), \text{write\_TS}(X))\).


# Ensuring Serializability

**Serializability** is the concept in database concurrency control that ensures the result of executing transactions concurrently is the same as if the transactions were executed serially (one after the other).

#### Methods to Ensure Serializability

1. **Two-Phase Locking (2PL)**:
   - Transactions are divided into two phases: acquiring locks (growing phase) and releasing locks (shrinking phase).
   - Ensures conflict serializability.

2. **Timestamp Ordering (TO)**:
   - Transactions are ordered based on timestamps to ensure that conflicting operations occur in a serial order.

3. **Serialization Graph Testing**:
   - A graph-based method that ensures no cycles in the graph of transactions, maintaining serializability.

4. **Optimistic Concurrency Control**:
   - Transactions execute without restrictions and are validated at the end to ensure serializability.

#### Advantages of Serializability

- **Data Integrity**: Prevents anomalies and maintains the consistency of the database.
- **Predictability**: Ensures that the concurrent execution of transactions produces a correct result.
- **Isolation**: Provides isolation of transactions, which is crucial for maintaining data accuracy.

#### Disadvantages of Serializability

- **Overhead**: Mechanisms to ensure serializability (like locking) can introduce significant overhead.
- **Reduced Concurrency**: Strict serializability can limit the parallelism of transactions, reducing system throughput.
- **Potential Deadlocks**: In methods like 2PL, deadlocks can occur, necessitating deadlock detection and resolution mechanisms.
- **Higher Abort Rates**: In timestamp ordering, conflicts can lead to higher transaction abortion rates.

# Basic Timestamp Ordering (TO)

**Timestamp Ordering (TO)** ensures serializability by ordering transactions based on their timestamps. It checks the order of operations to maintain consistency.

#### Steps

1. Each transaction **T** is assigned a unique **timestamp** \(\text{TS}(T)\) when it starts.
2. For each data item **X**, two timestamps are maintained:
   - **read_TS(X)**: The latest timestamp of any transaction that successfully read **X**.
   - **write_TS(X)**: The latest timestamp of any transaction that successfully wrote **X**.

#### Whenever a Transaction **T** Issues a `write_item(X)` Operation, the Following is Checked:

1. **If \(\text{TS}(T) < \text{read\_TS}(X)\)**:
   - **T** is **aborted** because **X** has already been read by a newer transaction. 
   - **T** is restarted with a new timestamp.

2. **If \(\text{TS}(T) < \text{write\_TS}(X)\)**:
   - **T** is **aborted** because a newer transaction has already written **X**.
   - **T** is restarted with a new timestamp.

3. **Otherwise**:
   - The write operation is allowed.
   - \(\text{write\_TS}(X)\) is updated to \(\text{TS}(T)\).

#### Whenever a Transaction **T** Issues a `read_item(X)` Operation, the Following is Checked:

1. **If \(\text{TS}(T) < \text{write\_TS}(X)\)**:
   - **T** is **aborted** because **X** has already been written by a newer transaction.
   - **T** is restarted with a new timestamp.

2. **Otherwise**:
   - The read operation is allowed.
   - \(\text{read\_TS}(X)\) is updated to \(\max(\text{read\_TS}(X), \text{TS}(T))\).

These checks ensure that transactions are executed in a way that their operations are consistent with their timestamps, maintaining the correct serial order

# Strict Timestamp Ordering (TO)

Strict Timestamp Ordering (STO) is a stricter version of the basic Timestamp Ordering that ensures serializability while also preventing certain anomalies by adding additional constraints to the transaction execution.

### Steps

1. **Assign Timestamp**: Each transaction **T** is assigned a unique timestamp \(\text{TS}(T)\) when it starts.

2. **Maintain Timestamps for Data Items**:
   - **read_TS(X)**: The largest timestamp of any transaction that has read **X**.
   - **write_TS(X)**: The largest timestamp of any transaction that has written **X**.

3. **When a Transaction **T** Issues a `write_item(X)` Operation**:
   - **If \(\text{TS}(T) < \text{read\_TS}(X)\)**: 
     - **T** is aborted because a newer transaction has already read **X**.
   - **If \(\text{TS}(T) < \text{write\_TS}(X)\)**: 
     - **T** is aborted because a newer transaction has already written **X**.
   - **Otherwise**: 
     - The write operation is allowed.
     - \(\text{write\_TS}(X)\) is updated to \(\text{TS}(T)\).

4. **When a Transaction **T** Issues a `read_item(X)` Operation**:
   - **If \(\text{TS}(T) < \text{write\_TS}(X)\)**:
     - **T** is aborted because a newer transaction has already written **X**.
   - **Otherwise**: 
     - The read operation is allowed.
     - \(\text{read\_TS}(X)\) is updated to \(\max(\text{read\_TS}(X), \text{TS}(T))\).

Strict Timestamp Ordering adds the additional rule that a transaction will be aborted if it attempts to read or write an item that has already been accessed by a transaction with a higher timestamp, further restricting concurrent operations to avoid conflicts

# Thomas Write Rule

The **Thomas Write Rule** is a concurrency control protocol used in database systems, specifically in the context of **two-phase locking** (2PL) or **timestamp ordering** (TO) schemes. The rule aims to maintain **serializability** by ensuring that transactions are executed in a way that prevents conflicting operations.

### Key Idea:
- The Thomas Write Rule says that **write operations** in a transaction are allowed **only if** there is no later transaction that has already written to the same data item or will write to it in the future. It allows for **cascading aborts** but avoids **non-serializable schedules**.

### Rule:
If a transaction **T1** writes a data item **X**, and a subsequent transaction **T2** writes **X** as well, **T1**'s write will be ignored if **T2** has a later timestamp, provided **T2**'s transaction commits successfully.

### Example:
Consider two transactions:

1. **T1** writes **X** at time **TS(T1)**.
2. **T2** writes **X** at time **TS(T2)**, where **TS(T2) > TS(T1)**.

Under the Thomas Write Rule:
- **T1**'s write to **X** will be ignored if **T2**'s timestamp is later.
- The rule helps avoid unnecessary writes and ensures consistency in a transaction processing system.

In summary, the **Thomas Write Rule** is a mechanism to prevent **overwriting** by ensuring that a transaction’s write operation is only valid if no conflicting writes have been made by other transactions after it

# Multiversion Concurrency Control (MVCC)

**Multiversion Concurrency Control (MVCC)** is a database concurrency control technique that allows multiple versions of a data item to exist concurrently. This technique helps ensure that transactions can read data without waiting for other transactions to release locks, which significantly improves performance and concurrency in database systems.

### Key Features

- **Multiple Versions**: MVCC maintains multiple versions of data items, allowing transactions to access the most recent version of the data they need without affecting others.
- **Snapshot Isolation**: Each transaction sees a snapshot of the database as it was when the transaction started. Transactions do not block each other because they operate on different versions of the data.
- **Read-Write and Write-Write Conflict Handling**: Read operations do not block other transactions, and write operations ensure consistency by maintaining different versions of the data.
- **Timestamps or Transaction IDs**: Data versions are typically managed using timestamps or transaction IDs to determine which version of the data is valid at a given time.

### Advantages

- **Improved Concurrency**: Multiple transactions can access different versions of data concurrently without causing conflicts, which increases throughput and reduces transaction wait times.
- **Non-blocking Reads**: Since readers do not block writers and vice versa, read operations can proceed without waiting for locks to be released.
- **No Deadlock**: MVCC eliminates the possibility of deadlock because transactions do not have to wait for other transactions to release locks.
- **Increased Throughput**: Since the database can handle more transactions simultaneously, it improves overall system throughput.

### Drawbacks

- **Space Overhead**: Storing multiple versions of data can consume more disk space, especially when the database has many versions of each data item.
- **Complexity**: Managing multiple versions of data can add complexity to the database management system (DBMS) and its transaction management logic.
- **Garbage Collection**: Old, obsolete versions of data need to be periodically cleaned up, which can add extra overhead for the database system (known as garbage collection).
- **Write Skew**: In some cases, MVCC might not handle certain conflicts between concurrent writes as effectively as locking mechanisms, leading to potential consistency issues in complex scenarios.

In summary, MVCC offers a powerful technique for handling concurrency by allowing multiple versions of data, but it comes with some challenges like space overhead and complexity

# Multiversion Technique Based on Timestamp Ordering

Multiversion Concurrency Control (MVCC) based on **timestamp ordering** is a technique where each data item can have multiple versions, and the versioning is managed using timestamps to ensure consistency and serializability. In this method, transactions are assigned timestamps when they begin, and the system uses these timestamps to order operations.

### Key Concepts

1. **Version of X**:  
   Each data item (X) in the database may have multiple versions, and the version is managed based on transaction timestamps. Versions are created whenever there is a write operation.

   - **Value**:  
     The **value** refers to the actual content of the data item in its current version. Every time a transaction writes to an item, a new version of that data item is created, and the value of the data item is updated.
   
   - **Write**:  
     A **write** operation creates a new version of the data item and updates its value. Each version is associated with a timestamp, and the write timestamp (often denoted as **TS(T)**) is the timestamp of the transaction that wrote it.
     
     - **Rule for writes**: If a transaction with a later timestamp tries to write a data item, its write is ignored if there exists a conflicting transaction that has already written to that data item.
   
   - **Read**:  
     A **read** operation in the timestamp-based MVCC system allows a transaction to read the latest committed version of a data item that existed at the time the transaction began. It uses the timestamp of the transaction to decide which version of the data item is valid for the transaction.
     
     - **Rule for reads**: If a transaction **T1** reads a data item **X**, it will read the most recent version of **X** that was committed before **T1**'s timestamp. If **T1** is trying to read a version created by a transaction that conflicts with its timestamp, the read operation might be blocked or result in an error, depending on the system design.

### Summary of Key Features

- **Multiple Versions of Data**: A data item can have several versions, each associated with a write timestamp.
- **Timestamps**: Each transaction has a timestamp, which is used to order operations and determine the correct version of a data item for each transaction.
- **Consistency**: Timestamp ordering ensures that transactions read the data as it was at the time they started, preventing issues such as "dirty reads" and helping ensure serializability.

By leveraging timestamp ordering, this version-based MVCC technique provides high concurrency and avoids locking, but still ensures consistency across multiple transactions

# Rules of Serializability

Serializability is a fundamental concept in database systems to ensure the correctness of concurrent transactions. It ensures that the results of executing transactions concurrently are the same as if they were executed one after another in some sequential order.

### Write Operation (write_item(X))

When a transaction **T** tries to write to a data item **X**, the system checks for conflicts with other transactions that might be attempting to modify or access the same item.

1. **When T tries to write to a data item X:**
   - The system checks whether any other transaction has already written to **X** in such a way that would create a conflict.
   
2. **Check for conflicts:**
   - **If conflicts**:
     - Conflicts can arise if another transaction **T2** has either:
       - A conflicting write operation on **X** with **T** (write-write conflict).
       - A conflicting read operation on **X** after **T**'s write (write-read conflict).
     - **Solution**: In this case, the system ensures serializability by preventing one of the transactions from proceeding. This might involve aborting the conflicting transaction or delaying the execution to resolve the conflict. In timestamp-based protocols, conflicts are checked against timestamps to enforce the order of operations.
   
   - **If no conflicts**:
     - If no conflicts are found, **T** is allowed to write **X** without interruption. The system then updates the version of **X** with the new value and assigns a timestamp to the write operation.
     - The **write_TS(X)** is updated with **T**'s timestamp.

#### Example for Write Operation:
- Transaction **T1** writes to **X** and **T2** also tries to write to **X**. If **T1** has an earlier timestamp than **T2**, **T2**'s write will be ignored if **T1** is the valid one, according to the serializability rules.

### Read Operation (read_item(X))

When a transaction **T** tries to read a data item **X**, it needs to access the most recent version of **X** that is consistent with its own transaction timeline.

1. **Find the latest suitable version:**
   - The system checks all versions of **X** and determines which version was the most recent and consistent with the transaction's timestamp. The version that was committed before **T** started is the one that should be read. This ensures **snapshot isolation**.
   
2. **Read the value and update `read_TS`:**
   - After determining the correct version of **X**, **T** reads the value.
   - The **read_TS(X)** is updated to **max(read_TS(X), TS(T))**, where **TS(T)** is the timestamp of transaction **T**. This ensures that the read operation reflects the most up-to-date snapshot as of the time **T** started.

#### Example for Read Operation:
- Transaction **T1** starts at timestamp **TS(T1)** and reads **X**. If **X** was written by **T2** after **TS(T1)**, **T1** will read the value that existed before **T1**'s start time (ensuring no "dirty reads").
- If **T1** reads **X** after **T2** has written to it, it will check that **X**'s version matches **T2**'s timestamp and the appropriate version is read.

### Summary of the Rules

1. **Write Operation**:
   - A **write** operation checks for conflicts with other transactions (write-write or write-read conflicts). If there are conflicts, the transaction may be aborted or delayed. If no conflicts exist, the transaction writes the data item and updates its version with a timestamp.

2. **Read Operation**:
   - A **read** operation checks for the most recent committed version of the data item, according to the transaction's timestamp. The read timestamp is updated to reflect the most recent transaction that accessed the data item.

In conclusion, serializability ensures that transactions are executed in a way that maintains consistency and correctness. By following the rules of write and read operations, conflicts are resolved, and transactions can proceed without violating the consistency of the database system

# Multiversion Two-Phase Locking (MVP2PL) Using Certified Locks

Multiversion Two-Phase Locking (MVP2PL) is a concurrency control protocol that combines the features of multiversion concurrency control and two-phase locking. In MVP2PL, the system allows multiple versions of data items, but also applies two-phase locking to ensure serializability. The certified lock mechanism is used to guarantee the correctness of operations in concurrent environments.

### Key Components

1. **Locks Used**:
   
   MVP2PL uses multiple types of locks to manage concurrency, including:
   
   - **Read Lock**:
     - A **read lock** is used when a transaction wants to read a data item. Multiple transactions can hold read locks on the same item simultaneously, allowing them to read the data concurrently. However, a read lock is incompatible with a write lock on the same data item, meaning a transaction cannot write to a data item if any transaction has a read lock on it.
     
   - **Write Lock**:
     - A **write lock** is used when a transaction wants to modify a data item. Write locks are exclusive, meaning that only one transaction can hold a write lock on a data item at any time. If any transaction holds a write lock on an item, no other transaction can read or write to that item until the write lock is released.
     
   - **Certify Lock**:
     - A **certify lock** is used in the MVP2PL protocol to ensure that the transaction is eligible for committing based on its conflict with other transactions. A certified transaction is guaranteed to not violate serializability when it commits. Before a transaction is allowed to commit, it must acquire a certify lock to ensure that no conflicts have been detected during its execution.
     - The certify lock acts as a final check to ensure that the transaction is safe to commit without violating the rules of serializability or consistency.

### Summary of Key Components in MVP2PL Using Certified Locks

1. **Read Lock**: Allows multiple transactions to read the same data item but prevents writing.
2. **Write Lock**: Allows a transaction to write to a data item, preventing other transactions from reading or writing to it.
3. **Certify Lock**: Ensures that a transaction is eligible to commit by checking for conflicts, ensuring that serializability is preserved when the transaction commits.

The MVP2PL protocol, with the addition of certified locks, ensures that transactions can execute concurrently while maintaining data consistency and serializability. It allows multiple versions of data to coexist, and the use of locks ensures that the transactions interact in a way that guarantees correctness

# Version Management in Database Systems

Version management is a technique used to handle concurrency in database systems. It allows multiple versions of data items to exist at the same time, which can be read or written by different transactions. This approach helps improve transaction throughput and allows for better isolation in multiversion concurrency control systems.

### Phases of Version Management

1. **Growing Phase**:
   - The **growing phase** refers to the period during which a transaction can acquire locks and modify data. During this phase, transactions may read and write data, but no locks can be released. It represents the part of the transaction's execution where it is expanding or "growing" in terms of accessing and modifying data items.
   
2. **Shrinking Phase**:
   - The **shrinking phase** starts when a transaction begins to release locks and can no longer acquire any new locks. In this phase, the transaction is typically finishing up and is preparing for commit. The shrinking phase ensures that once a transaction has finished modifying data, it will not continue to make further changes or acquire new locks that could conflict with other transactions.
   
### Two Versions of Each Item

1. **Committed Version**:
   - The **committed version** of a data item is the version that has been successfully written to the database and committed. This version is considered the "official" version and is visible to all transactions that start after the commit. Committed versions are stored permanently in the database after a transaction completes successfully.
   
2. **Uncommitted Version**:
   - The **uncommitted version** of a data item is a temporary version created during a transaction's execution. It represents a tentative or intermediate state of the data item. Uncommitted versions are only visible to the transaction that created them, and they are discarded if the transaction fails (rollbacks) or aborted. If the transaction commits, the uncommitted version becomes the committed version.

### Summary

- **Growing Phase**: Transaction expands by acquiring locks and performing operations.
- **Shrinking Phase**: Transaction releases locks and prepares for commit.
- **Committed Version**: The final, permanent version of a data item after a transaction is successfully committed.
- **Uncommitted Version**: A temporary version of a data item created by a transaction, which is only visible to the transaction and may be discarded if the transaction aborts.

Version management helps achieve **high concurrency** by allowing multiple versions of data to be manipulated simultaneously. This technique helps avoid conflicts and increases the performance of the database system

# Steps in MVP2PL (Multiversion Two-Phase Locking)

Multiversion Two-Phase Locking (MVP2PL) is a concurrency control protocol that combines multiversioning and two-phase locking. It aims to increase concurrency by allowing multiple versions of data while ensuring serializability through locking.

### Steps in MVP2PL

1. **Write a Lock**:
   - Before a transaction can write to a data item, it must acquire a **write lock**. This lock ensures exclusive access to the data item for the transaction, preventing other transactions from reading or writing to the same item until the lock is released.

2. **Commit Phase**:
   - Once a transaction finishes its operations and is ready to commit, it enters the **commit phase**. During this phase, it checks if it can safely commit based on its interactions with other transactions, ensuring serializability. It must acquire a **certify lock** to verify that no conflicts exist and it is safe to commit.

3. **Replace the Old Version**:
   - After committing, the transaction replaces the old version of the data item with its updated version. This change is reflected in the committed version of the item, making it visible to future transactions.

4. **Release Locks**:
   - Once the transaction has committed and updated the data, it releases all the locks (including the write lock and certify lock). This allows other transactions to access the data items it was using, enabling continued concurrency.

### Advantages of MVP2PL

1. **Concurrent Reads**:
   - MVP2PL allows **multiple transactions** to read different versions of a data item simultaneously. This increases concurrency by allowing read-only transactions to proceed without waiting for write locks, which are exclusive.

2. **Avoid Cascading Aborts**:
   - By maintaining multiple versions of data and using a strict certification process, MVP2PL avoids **cascading aborts** (where one transaction's failure causes others to roll back). Since each transaction works with versions of data, conflicts are managed more effectively, reducing the need for rollback propagation.

### Summary

- **Write Lock**: Transaction locks the data before writing.
- **Commit Phase**: Ensures that the transaction is safe to commit and doesn't cause conflicts.
- **Replace Old Version**: Updates the committed version with the new data.
- **Release Locks**: Frees up locks after the transaction is committed.
- **Advantages**:
  - **Concurrent Reads**: Improves performance by allowing multiple read operations.
  - **Avoid Cascading Aborts**: Reduces the impact of transaction failures by isolating their effects

 # Validation Concurrency Control Technique

The **Validation Concurrency Control Technique** is a method used in database systems to manage concurrent transactions while ensuring consistency and serializability. It works by validating the transactions before they are committed to ensure that they do not violate serializability.

### How it Works

The validation technique divides each transaction into three phases: **Read Phase**, **Validation Phase**, and **Write Phase**.

### 1. **Read Phase**:
   - During the **Read Phase**, a transaction reads the data it requires for processing. It doesn't modify the database yet. The transaction just collects information and starts executing based on the initial values of the data items.
   - The transaction is allowed to read data freely and can even perform operations like computations. However, it does not interact with other transactions during this phase (no conflicting operations).

### 2. **Validation Phase**:
   - After the read phase, the **Validation Phase** begins. This phase checks if the transaction can safely commit.
   - It involves verifying that the transaction does not conflict with other transactions. In essence, the system checks whether the transaction would result in any violations of serializability based on the data it has read or modified.
   - The system checks for **conflicts** with other transactions that have been validated, ensuring the transaction adheres to the required consistency rules.

### 3. **Write Phase**:
   - If the transaction passes the validation checks, it proceeds to the **Write Phase**, where it writes the changes to the database and commits the transaction.
   - During this phase, the system ensures that no conflicts with other transactions are introduced and that all changes are permanent.

### Validation Rules

There are specific conditions to be checked during the **Validation Phase**. These rules ensure that transactions meet the consistency and isolation properties of serializability.

#### Condition 1:
   - The transaction must not have any **conflicts** with other transactions that have already been validated and are in the **write phase**. If any conflict is detected, the transaction must be aborted or rolled back.
   
#### Condition 2:
   - The transaction must **not violate serializability**. Specifically, it checks that the transaction's actions can be ordered in a way that would allow the transaction to run in isolation without affecting the results of other transactions.

### Summary

- **Read Phase**: The transaction reads the necessary data but does not modify it.
- **Validation Phase**: Checks whether the transaction can commit by ensuring it does not conflict with other transactions.
- **Write Phase**: The transaction writes its changes to the database if it passes the validation phase.
  
### Validation Rules:
- **Condition 1**: No conflict with already validated transactions.
- **Condition 2**: Ensures serializability and consistency of the transactions.

This approach ensures **higher concurrency** by allowing transactions to execute without locking resources, but it requires careful validation to prevent conflicts when committing changes

# Phantom Phenomenon

The **Phantom Phenomenon** occurs in databases when a transaction reads a set of rows based on a certain condition, but during the transaction's execution, new rows that match the condition are inserted by other transactions. This results in the transaction seeing a different set of rows when it re-executes the same query, creating a "phantom" effect.

### Example

Consider a scenario where a transaction **T1** is executing and it queries a list of employees who have a salary greater than $50,000:

```sql
SELECT * FROM Employees WHERE Salary > 50000;
```

- Transaction **T1** finds 10 employees meeting this condition.
- Before **T1** finishes, another transaction **T2** inserts 5 new employees whose salaries are above $50,000.

When **T1** executes the same query again (possibly in a loop or for a second time during its execution), it may now find 15 employees, even though **T1** has not made any changes to the data. The newly inserted rows, which weren't there during the initial execution of the query, now appear as "phantoms."

### Conclusion

The phantom phenomenon occurs when the data returned by a query changes during the course of a transaction due to concurrent insertions or deletions by other transactions. This is typically handled by **Serializable isolation level** or using **range locks** to prevent such changes during a transaction's execution

# Timestamp Protocol that Avoids Phantom Phenomena

The **Timestamp Protocol** helps in managing concurrent transactions in a way that avoids phenomena like **phantoms** by using timestamps to order transactions and ensuring that operations are performed in a serializable manner. The protocol ensures that transactions that could lead to the phantom phenomenon are prevented through careful management of read and write operations.

### How it Works

#### 1. **Assign Timestamps**:
   - Each transaction is assigned a unique **timestamp** when it begins. The timestamp defines the global order of transactions, which determines the order in which operations are allowed to proceed.
   - This helps to ensure that all transactions are executed in a serializable order, preventing conflicts such as phantoms, where data changes mid-transaction.

##### **Read Operations**:
   - When a transaction performs a **read operation**, it checks the timestamp of the data item it wants to access. The transaction can read the item only if the item's timestamp is **greater than or equal** to the transaction's timestamp.
   - This ensures that the transaction reads the most recent committed version of the data and avoids accessing "phantom" data that may be added later by other transactions.

##### **Write Operations**:
   - When a transaction performs a **write operation**, it can write to a data item only if no other transaction has already read or written to that data item with a timestamp greater than the current transaction's timestamp.
   - This prevents a transaction from writing to data that could conflict with or create new "phantoms" in the data set, ensuring that all write operations are performed in the correct order.

#### 2. **Range Queries to Avoid Phantoms**:

   To handle the phantom phenomenon that occurs during range queries (where transactions may encounter new data that fits the query condition during their execution), the timestamp protocol uses additional measures.

##### **To Handle a Range of Queries**:
   - When a transaction performs a range query (e.g., `SELECT * FROM Employees WHERE Salary BETWEEN 50000 AND 70000`), it locks the range of data it is querying to prevent new data from being inserted into this range during the execution of the query.
   - The timestamp of the transaction is used to ensure that no new data can be added within this range that would change the results of the query, effectively avoiding the phantom problem.

##### **Ensuring Serializability**:
   - The timestamp protocol guarantees **serializability** by ensuring that all transactions operate in a globally ordered manner based on timestamps. This ensures that there are no conflicts between transactions, such as new data being added while a transaction is still running, which could cause a phantom phenomenon.
   - The protocol ensures that if transactions are executed serially (one after the other), the outcome will be the same as if they were executed concurrently, which is the essence of serializability.

### Summary

- **Assign Timestamps**: Every transaction gets a unique timestamp, which is used to determine the order of execution.
- **Read Operations**: A transaction reads a data item only if the item's timestamp is greater than or equal to the transaction’s timestamp.
- **Write Operations**: A transaction writes a data item only if no other transaction has read or written to it with a greater timestamp.
- **Range Queries to Avoid Phantoms**: For range queries, the protocol locks the range of data and ensures no new data can be inserted within the range during the query execution.
- **Ensuring Serializability**: The protocol ensures that all transactions execute in a serializable order to avoid conflicts and phantom phenomena.

By using timestamps and validating operations based on transaction order, the **Timestamp Protocol** effectively avoids phantom phenomena and ensures the serializability of transactions

# Validation vs 2PL (Optimistic Concurrency Control)

### Approach

- **Validation (Optimistic Concurrency Control)**: Assumes that conflicts will be rare and transactions will mostly commit without issues. Transactions are executed in three phases: Read, Validation, and Write. Validation occurs at the end before committing, where conflicts are checked, and only non-conflicting transactions are allowed to commit.
  
- **2PL (Two-Phase Locking)**: Ensures serializability by using locks. It has two phases:
  - **Growing Phase**: A transaction can acquire locks but cannot release any.
  - **Shrinking Phase**: After releasing a lock, no more locks can be acquired.

### Phases

- **Validation Phase** (in Optimistic Concurrency Control):
  - Occurs at the end of the transaction.
  - The system checks if the transaction can commit by validating whether there were conflicts with other concurrent transactions.
  - If conflicts are detected (e.g., conflicting reads or writes), the transaction is rolled back.
  
- **Growing Phase** (in 2PL):
  - During this phase, a transaction can acquire locks but cannot release any locks.
  
- **Shrinking Phase** (in 2PL):
  - After the transaction starts releasing locks, it cannot acquire any more locks. This phase ensures that once a transaction releases a lock, no conflicting actions can occur in other transactions.

### Performance

- **Validation**:
  - **Higher throughput** because transactions can proceed in parallel without waiting for locks.
  - **Reduced contention** for resources as transactions don't have to wait for lock acquisitions and releases.
  - Can result in more **abort/rollbacks** during validation if conflicts are detected.

- **2PL**:
  - Can have **lower throughput** due to waiting for locks, especially in high-contention environments.
  - **Fewer rollbacks** as transactions are guaranteed serializability through locks.
  - Potential **deadlocks** may arise if there are cyclic dependencies in lock acquisition.

### Key Difference

| Aspect               | **Validation (Optimistic Concurrency Control)** | **2PL (Two-Phase Locking)**            |
|----------------------|--------------------------------------------------|----------------------------------------|
| **Concurrency Model** | Optimistic, assuming few conflicts              | Pessimistic, using locks to prevent conflicts |
| **Phases**           | Read, Validation, Write                         | Growing, Shrinking                     |
| **Conflict Detection** | Performed during validation phase               | Locks are held to prevent conflicts in real-time |
| **Deadlocks**        | Less likely, but transactions may be rolled back | Deadlocks are possible when cyclic dependencies occur |
| **Throughput**       | Generally higher (fewer waits for resources)    | Can be lower due to lock contention    |
| **Rollback**         | More frequent rollbacks during validation if conflicts are detected | Fewer rollbacks (locks prevent most conflicts) |

### Summary

- **Validation** is optimistic, allowing transactions to run without locks and only validating them at commit time, which can improve performance in low-contention environments.
- **2PL** is pessimistic, locking data before a transaction begins and ensuring consistency throughout, but it can cause delays due to lock contention and deadlocks.

The choice between the two depends on the workload: **Validation** works best when conflicts are rare, while **2PL** is suitable for systems where data consistency is critical and conflicts are frequent

# Recovery from Concurrent Transactions

### Transaction Log

A **Transaction Log** is a critical component in database recovery, which records all the actions (transactions) that are performed on the database. It helps ensure that, in case of a failure, the system can restore the database to a consistent state by replaying or undoing certain transactions. The log contains details like:
- Transaction IDs
- Operation types (insert, update, delete)
- Data values before and after the operation (before-image and after-image)

### Undo/Redo

- **Undo**: Used to revert a transaction that was partially completed. If a transaction failed after making some changes, the system will use the **Undo** operation to roll back any modifications made by that transaction, returning the database to its state before the transaction began.
- **Redo**: Used to apply changes from transactions that have been committed but not yet written to the database due to a crash. After recovery, **Redo** will reapply these changes to ensure that committed transactions are correctly reflected in the database.

### Before and After Images

- **Before Image**: The data value of an item **before** it was modified by a transaction. It's stored to allow undoing changes in case of a failure.
- **After Image**: The data value of an item **after** the transaction has been performed. It's stored for the redo process, allowing a system to reapply changes if needed.

### Process

1. **Transaction starts**: The transaction is logged.
2. **Before Image**: A copy of the data before the transaction modifies it is logged.
3. **Operation (insert/update/delete)**: The operation is performed on the database.
4. **After Image**: A copy of the data after the operation is logged.
5. **Commit**: The transaction is marked as complete in the log.
6. **Crash Recovery**: 
   - **Undo** all uncommitted transactions.
   - **Redo** all committed transactions that weren't fully written to the database.

### Summary

- **Transaction Log** tracks all database changes.
- **Undo/Redo** operations are used for rollback and recovery after failures.
- **Before/After Images** ensure that the original and modified data are available to properly handle recovery

# Transaction States

### Committed
A transaction is in the **committed** state when it has successfully completed all its operations and has been permanently saved to the database. After committing, the transaction can no longer be rolled back, and its changes are visible to other transactions.

### Active
A transaction is in the **active** state when it is in progress and has not yet been completed (committed or aborted). During this state, the transaction can execute its operations, and it may involve multiple changes to the database.

### Aborted
A transaction is in the **aborted** state when it has encountered an error or a failure and has been rolled back. All changes made by the transaction are undone, and the database is returned to the state before the transaction began.

# Recovery Protocol

### Write-Ahead Logging (WAL)
**Write-Ahead Logging (WAL)** is a recovery protocol that ensures that any changes made to the database are first written to a transaction log before they are applied to the database itself. This guarantees that, in the event of a failure, the system can recover by using the log to undo or redo transactions as needed.

### Checkpoints
A **checkpoint** is a mechanism used to minimize recovery time by periodically saving the state of the database. During a checkpoint, the system writes all modified data from the memory to the disk and records a special entry in the transaction log. If a failure occurs, the system can start recovery from the last checkpoint instead of from the beginning of the log

# Two-Phase Commit Protocol

### Prepare Phase
In the **Prepare Phase**, the coordinator (the transaction manager) sends a **prepare** message to all participants (databases or servers) in the distributed transaction. The participants then check whether they can commit the transaction based on their local conditions (e.g., if all operations were successful and there are no errors). Each participant responds with either a **commit** or **abort** message:
- **Commit**: If the participant is ready to commit.
- **Abort**: If there is any issue, and the participant cannot commit the transaction.

### Commit/Abort Phase
After receiving the responses from all participants:
- If **all participants** send a **commit** message, the coordinator sends a **commit** signal to all participants, instructing them to commit the transaction.
- If **any participant** sends an **abort** message, the coordinator sends an **abort** signal to all participants, instructing them to roll back the transaction.

In the event of a failure, the coordinator or participants can recover using logs, ensuring that the transaction either commits successfully or is completely rolled back (atomicity)

# Recovery Procedure

### Identify Transactions to Undo-Redo
In a recovery process, the system first identifies which transactions need to be **undone** or **redone**. This is typically done by examining the **transaction log** that records the state of each transaction at different stages (before and after images, commit/abort signals). Based on this, the system can determine:
- **Transactions to Undo**: Transactions that were active or aborted before a crash and need to be rolled back.
- **Transactions to Redo**: Transactions that were committed but not fully written to the database and need to be reapplied.

### Undo Phase
The **Undo Phase** is responsible for rolling back the changes made by transactions that were **not committed** before the crash or failure. The steps include:
- Scanning the transaction log from the last checkpoint or failure point.
- Reversing the changes made by **incomplete** transactions using the **before image** of the data (before changes).
- Ensuring the database is restored to its state before the uncommitted transactions started.

### Redo Phase
The **Redo Phase** ensures that all **committed** transactions that were not yet written to the database are reapplied. The steps include:
- Reapplying changes from **committed transactions** using the **after image** of the data (after changes).
- Ensuring that the database reflects all successful, committed transactions, even if the changes were not fully written to disk before the failure.

By following these phases, the recovery procedure ensures that the database remains consistent, and no committed changes are lost while uncommitted changes are properly discarded


# Multiple Granularity Lock

### Tradeoffs in Granularity

#### Fine Granularity
**Fine Granularity** refers to locking very small data items, such as individual rows or even specific fields within a record. The key advantages and tradeoffs include:
- **Advantages**: It allows for more concurrency, as different transactions can access different parts of the data simultaneously.
- **Disadvantages**: It requires managing many locks, which can introduce overhead and decrease performance due to the need for frequent lock acquisitions and releases.

#### Coarse Granularity
**Coarse Granularity** refers to locking larger data units, such as entire tables or database files. The advantages and tradeoffs include:
- **Advantages**: Lower overhead due to fewer locks being held, reducing the cost of lock management.
- **Disadvantages**: Less concurrency, as locking a large unit may block other transactions from accessing unrelated parts of the data.

#### Lower Overhead, Fewer Items Mean
When fewer items are locked (coarse granularity), the overhead of lock management is reduced because fewer locks need to be created, maintained, and released. However, this sacrifices concurrency, as transactions may be forced to wait for the entire data unit to become available.

#### Choosing the Right Granularity
The choice between fine and coarse granularity depends on the application’s needs:
- **Fine Granularity**: Preferred for high-concurrency systems where many transactions operate on different parts of the data.
- **Coarse Granularity**: Better for environments with lower concurrency requirements where minimizing overhead is a priority.

### Multiple Granularity Level Locking Problem with Basic Locking

In basic locking schemes (like 2PL), the locks are typically applied uniformly across all levels of granularity. However, with **multiple granularity locking**, a single transaction may hold locks at different levels of granularity (e.g., both row-level and table-level locks). This can lead to problems like:
- **Deadlocks**: When multiple transactions acquire locks at different granularities, it increases the potential for cyclic dependencies between transactions.
- **Locking Hierarchy Violations**: If transactions acquire locks in a non-hierarchical order, it can lead to inconsistent or conflicting states.

### 2PL Protocol Level
To handle these issues, the **2PL (Two-Phase Locking) Protocol** ensures that transactions follow a lock acquisition and release protocol:
- **Growing Phase**: A transaction can acquire locks but cannot release them.
- **Shrinking Phase**: After releasing a lock, the transaction cannot acquire any new locks.
This approach ensures serializability and prevents conflicting locks at different granularities by enforcing a structured and orderly lock acquisition and release sequence
