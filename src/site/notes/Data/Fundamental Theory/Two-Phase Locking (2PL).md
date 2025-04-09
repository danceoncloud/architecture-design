---
{"dg-publish":true,"permalink":"/data/fundamental-theory/two-phase-locking-2-pl/"}
---


**Two-Phase Locking** is a concurrency control protocol to ensure **serializable transaction schedules**. It enforces strict rules for acquiring and releasing locks, ensuring consistency and preventing anomalies and lost updates.

## Types of Locks in 2PL
### Shared Lock (S-Lock):
For **Read** operations.
Multiple transactions can hold shared locks on the same data.
### Exclusive Lock (X-Lock):
For **Write** operations.
Only one transaction can hold an exclusive lock on a data item.

## How does 2PL Work
### Growing Phase (Locking Acquisition):
- A transaction acquires all the **locks** (read/write) it needs ***before accessing data***.
- Once a lock is acquired, the transaction **cannot release it** until the next phase.
### Shrinking Phase (Lock Release):
- After the transaction completes its operations, it starts releasing locks.
- Once a lock is released, the transaction **cannot acquire new locks**.
### Conflict Rules
- Two transactions cannot hold conflicting locks (e.g., one holds X-Lock, the other wants X-Lock).
- If a lock is unavailable, the transaction **waits (blocked)** until the lock is release.

## Why Use 2PL
**Serializable Schedules**: Guarantee transactions are executed as if they run sequentially.
**Prevent Concurrency Anomalies**: 
- No dirty read 
- No lost updates (no concurrent write to the same data)

## Challenges
**Deadlocks**:
- Transactions can block each other in a cycle.
- Requires deadlock detection(timeouts, cycle checks) or prevention (transaction ordering).
**Reduced Concurrency**:
Locks block other transactions, limiting throughput.
**Overhead**:
Managing locks consume memory and CPU.

