---
{"dg-publish":true,"permalink":"/data/fundamental-theory/serializable-snapshot-isolation-ssi/"}
---


**SSI** is a concurrency control mechanism that combines the benefits of **Snapshot Isolation (SI)** -- high concurrency and non-blocking read with guarantees of true **serializable isolation**. It ensures that the outcome of concurrent transactions is equivalent to some ***serial execution*** of those transactions.

## How SSI Works
1. **Snapshot Isolation (Baseline)**:
	- Each transaction operates on a consistent snapshot of the database as of its start time.
	- Reads are non-blocking, and writes create new versions of data (via [[Data/Fundamental Theory/Multi-Version Concurrency Control (MVCC)\|Multi-Version Concurrency Control (MVCC)]]).
2. **Conflict Detection (Key Addition in SSI)**:
	- SSI tracks dependencies between transactions to detect **serialization conflicts** that could lead to anomalies.
	- It monitors:
		- **Read-Write Conflicts**: One transaction reads data, and another modifies it.
		- **Write-Write Conflicts** Two transactions modify the same data.
	- A **serialization graph** is maintained, where nodes represent transactions and edges represent dependencies.
	- If the graph contains a cycle, SSI aborts one or more transactions to break the cycle, ensuring a serializable outcome.

## Why Use SSI
**True Serializability**: Guarantees the strictest isolation level without the overhead of 2-Phase Locking.
**High Concurrency**: Non-blocking reads similar to **SI** and minimized locking.
**Simple for Developers**: No need for manual `SELECT FOR UPDATE` or row-level locks.
## Problems SSI Solves (That SI Doesn't)
### Write Skew
***Issue***: Two transactions read overlapping data, make disjoint updates, and violate a global constraint.
***SSI Fix***: Detect overlapping read and write sets to abort one transaction.
### Phantom Read
***Issue***: A transaction re-runs a query and sees new rows inserted by other transactions.
***SSI Fix***: Tracks predicates and blocks phantoms via dependency checks.

## When Use SSI
**Critical Transaction** Banking, inventory, booking system.
**Complex Workload**: Queries with predicates needing phantom prevention.
**Dev simplicity**: Avoid manual locking in code.

### Challenges
**Higher Abort Rates**: Transactions are aborted if cycles are detected.
**Performance Overhead**: Tracking dependencies adds CPU/memory cost.