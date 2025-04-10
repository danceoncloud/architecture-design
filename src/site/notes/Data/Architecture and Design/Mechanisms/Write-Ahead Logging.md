---
{"dg-publish":true,"permalink":"/data/architecture-and-design/mechanisms/write-ahead-logging/"}
---


Write-Ahead Logging is a method where all changes to a database are logged to a persistent storage medium **before** the actual data is modified. This log is used to recover the database to a consistent state after crashes of failures.

### Key Mechanisms
#### Order of Operations:
1. Write transaction details, including the **before** and **after** state of data, to a sequential WAL file.
2. Apply changes to the main files (tables, indexes).

#### Log Structure:
**Transaction ID**
**Operation Type (CRUD)**
**Data Changes** (old and new values for rollback/redo)
**Commit/Abort Marker**

### Purpose of WAL
**Atomicity**:
If a transaction fails midway, the WAL provides the information needed to **undo** incomplete changes.

**Durability**:
Once a transaction is logged, it survives database system crashes. During recovery, the log is used to redo committed transactions not yet applied to the databases.

**Concurrency and Performance**:
**Sequential WAL writes** are faster then random I/O to the main database files.
Supports **Multi-Version Concurrency Control (MVCC)**, as logs track historical versions of data.

