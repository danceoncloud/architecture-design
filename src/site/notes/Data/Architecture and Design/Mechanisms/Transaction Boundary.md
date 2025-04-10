---
{"dg-publish":true,"permalink":"/data/architecture-and-design/mechanisms/transaction-boundary/"}
---


**Transaction Boundary** refers to a system's ability to explicitly define the **start and end of a transaction**, this is critical for the "all-or-nothing" guarantee of atomicity.

### Key Components of Transaction Boundaries
1. **Begin/Start**: mark the start of a transaction.
2. **Operations**: add all actions within the boundary.
3. **Commit**: finalize the transaction, making the changes permanent.
4. **Rollback**: abort the transaction, undoing all changes.

### How Systems Support Transaction Boundaries
#### Explicit Transaction Control
**SQL Databases**
Use ***BEGIN, COMMIT and ROLLBACK*** statements.

**NoSQL Databases**
Use ***Session-Based*** transactions.

**NewSQL**
Support distributed transactions via protocols like ***2PC***.

#### Implicit Transactions (Auto-Commit)
- **Single-statement** transactions auto-commit.
- Atomicity is limited to **individual operations** unless explicitly grouped.

| **System**       | **Atomicity Support**                                   | **Transaction Boundary Syntax**                                   |
| ---------------- | ------------------------------------------------------- | ----------------------------------------------------------------- |
| **PostgreSQL**   | Full (multi-statement transactions).                    | `BEGIN; ... COMMIT/ROLLBACK;`                                     |
| **MongoDB**      | Single-document (implicit), multi-document (explicit).  | `session.startTransaction(); ... session.commit()`.               |
| **Redis**        | Limited (MULTI/EXEC for batch commands, not full ACID). | `MULTI; ... EXEC;` (queues commands, no rollback).                |
| **Apache Kafka** | Distributed (transactional producers with 2PC).         | `initTransaction()`, `beginTransaction()`, `commitTransaction()`. |
