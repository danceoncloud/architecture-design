---
{"dg-publish":true,"permalink":"/data/fundamental-theory/index-range-locking/"}
---


Index-range locking is designed to enforce **strict transaction isolation** (e.g., `REPEATABLE READ` or `SERIALIZABLE`) by locking **ranges of index entries** and their **gaps** (empty spaces between existing entries). This prevents:
- **Phantom Reads**: New rows being inserted into a range queried by another transaction.
- **Non-Repeatable Reads**: Existing rows in a range being modified or deleted.

## Key Components
**Range Locks**: Lock a contiguous set of index entries.
**Gap Locks**: Lock the "gaps" between existing index entries to block inserts.
**Next-Key Locks**: A hybrid of a **record lock** (on an index entry) and a **gap lock** (on the preceding gap).
## How It Works
1. **Query Execution**: When a transaction executes a range query (e.g., `SELECT ... WHERE id > 100`), the database:
	Scans the index of matching entries.
	Locks **all index entries** in the range.
	Locks **gaps** between entries to prevent insert.
2. **Lock Modes**: `Shared (S) Locks` for read operations, `Exclusive (X) Locks` for write operations.

> [!success]- Example
> - Transaction A runs `SELECT * FROM employees WHERE salary BETWEEN 5000 AND 10000`.
> - The database locks:
>     - All existing salary entries in `[5000, 10000]` (range locks).
>     - Gaps below 5000 and above 10000 (gap locks) to prevent inserts like `salary = 7500`.

## When is Index-Range Locking Triggered
- **Range Queries**: BETWEEN, <, >, or LIKE 'A%'.
- **Unique Constraints**: Inserts that would violate uniqueness trigger gap locks.
- **Foreign Key Checks**: Locking gaps to prevent violations.

## Challenges and Trade-offs
### Pros:
- **Strong Isolation**: no phantoms.
- **Granular locking**: better concurrency than table locks.
### Cons:
- **Lock Overhead**: Increased memory/CPU for managing many locks.
- **Deadlocks**: Transactions may deadlock if they lock ranges in conflicting orders.
- **Index Dependency**: Requires well-designed indexes; missing indexes lead to table locks.