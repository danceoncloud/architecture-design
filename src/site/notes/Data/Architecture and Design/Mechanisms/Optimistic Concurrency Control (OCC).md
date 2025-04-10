---
{"dg-publish":true,"permalink":"/data/architecture-and-design/mechanisms/optimistic-concurrency-control-occ/"}
---


**Optimistic Concurrency Control** allows multiple transactions to proceed **without locking resources**, assuming conflicts are rare. Instead of preventing conflicts upfront, OCC detects and resolves them at **commit phase**.

## How does OCC Work
1. **Read Phase**:
	- Transactions read data and make modifications in a **private workspace (no locks held)**.
	- Track which data items are read and modified.
2. **Validation (Commit) Phase**
	- Before committing, the system checks if any conflicts occurred since the transaction started.
	- If no conflicts -> Commit the changes.
	- If conflicts -> Abort, roll back and optionally retry.
3. **Write Phase (if validated)**
	- Apply the transaction's changes.

## Key Features
**No Locks During Execution**: Reduce blocking and boosts throughput.
**Conflict Detection at Commit**: Uses techniques like:
- **Version Stamps**: Track data versions.
- **Timestamp Ordering**: Compare transaction timestamps to detect write-write conflicts.
- **Diff Checks**: Compare initial and current data states.

## Pros vs Cons
| **Pros**                                     | **Cons**                                                   |
| -------------------------------------------- | ---------------------------------------------------------- |
| High concurrency (no locks).                 | Aborts/retries if conflicts are frequent.                  |
| Low overhead (ideal for read-heavy systems). | Validation phase adds latency.                             |
| Simplifies distributed transactions.         | Requires explicit conflict resolution (e.g., retry logic). |
