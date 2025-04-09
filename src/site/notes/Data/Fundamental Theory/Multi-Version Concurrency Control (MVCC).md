---
{"dg-publish":true,"permalink":"/data/fundamental-theory/multi-version-concurrency-control-mvcc/"}
---


**Multi-Version Concurrency Control** is a used to enable ***high concurrency without*** blocking reads or writes. It achieves this by maintaining **multiple versions of data** and allowing transactions to operate on a consistent snapshot of the database.

### Key Concepts of MVCC
#### Data Versioning
- When a row is updated, the database creates **a new version** of the row instead of overwriting it.
- Older versions of the row are retained temporarily so that ongoing transactions can continue to see the version that was current when they started.
#### Transaction Snapshots
Each transaction "sees" a **consistent snapshot** of the database as of the start of the transaction.
#### No Blocking
Readers don't block writers, and writers don't block readers.

### Why to Use MVCC
**High Concurrency**: Enable many reads/writes to proceed in parallel.
**Consistency**: Transactions see a logical snapshot of the database.
**Avoid Locking Overhead**: No need for heavy **row/table locks** in most cases.
**Support ACID Isolation Levels**: Used in **Repeatable Read** and **Serializable** isolation levels.

## When to use MVCC
**Analytics Workloads**: Long-running queries need consistent snapshots.
**High-Read Systems**: reads outnumber writes, e.g., e-commerce platforms.
**Mixed Workloads**: Systems with both OLTP and OLAP needs (e.g., SaaS applications).

## Temporary vs Persistent Snapshots
The persistence of snapshots in MVCC depends on the implementation and the cleanup policies.
**Temporary Snapshots**: serve active transactions, then discard.
**Persistent Snapshots**: enable time-travel queries, backups, or audit trails.

### Challenges
**Storage Overhead**: Multiple versions of data consumes space.
**Version Cleanup**: Manage "garbage collection" for old versions.
**Isolation Level Limitation**: MVCC alone guarantees high concurrency, but isolation level determines which anomalies slip through.
**Performance in Write-Heavy Workload**: Frequent versioning can slow down updates.
































