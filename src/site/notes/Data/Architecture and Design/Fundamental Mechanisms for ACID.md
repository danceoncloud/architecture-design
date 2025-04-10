---
{"dg-publish":true,"permalink":"/data/architecture-and-design/fundamental-mechanisms-for-acid/"}
---


## Atomicity
**[[Data/Architecture and Design/Mechanisms/Transaction Boundary\|Transaction Boundary]]**
**[[Data/Architecture and Design/Mechanisms/Write-Ahead Logging\|Write-Ahead Logging]]**
**[[Data/Architecture and Design/Mechanisms/Two-Phase Commit (2PC)\|Two-Phase Commit (2PC)]]**
**[[Data/Architecture and Design/Mechanisms/Compensating Transactions (Sagas)\|Compensating Transactions (Sagas)]]**

## Isolation
**Isolation Level** is the guarantee offered by different solutions,
**Locking Mechanism** is how the guarantee is achieved.

| **Isolation Level**        | **Dirty Reads** | **Non-Repeatable Reads** | **Phantom Reads** | **Write Skew** |
| -------------------------- | --------------- | ------------------------ | ----------------- | -------------- |
| **Read Uncommitted**       | ❌ Allowed       | ❌ Allowed                | ❌ Allowed         | ❌ Allowed      |
| **Read Committed**         | ✅ Prevented     | ❌ Allowed                | ❌ Allowed         | ❌ Allowed      |
| **Repeatable Read**        | ✅ Prevented     | ✅ Prevented              | ❌ Allowed         | ❌ Allowed      |
| **Snapshot Isolation**     | ✅ Prevented     | ✅ Prevented              | ❌ Allowed         | ❌ Allowed      |
| **Serializable**           | ✅ Prevented     | ✅ Prevented              | ✅ Prevented       | ✅ Prevented    |
| **Strict Serializability** | ✅ Prevented     | ✅ Prevented              | ✅ Prevented       | ✅ Prevented    |

> [!success]- Lock Granularity: Concurrency vs Locking Overhead
> Locks are the fundamental building blocks that help implementing isolation by controlling access to shared data.
> **Field-Level Locks**: Lock individual field in a table, highest concurrency but maximum overhead. \
> **Row-Level Locks**: Lock individual rows within a table, provides good concurrency for OLTP workloads. \
> **Table-Level Locks**: Lock entire table, used for operations like `ALTER TABLE`, `TRUNCATE`. \
> **Predicate Locks**: Lock ranges of data matching certain conditions. used to prevent phantom reads. \
> **Index-Level Locks**: Lock portions of indexes rather than data itself. can be more efficient for certain query patterns.

`Pessimistic`: prevent conflicts via upfront locking, optimal for high-conflict systems like OLTP.
**[[Data/Architecture and Design/Mechanisms/Two-Phase Locking (2PL)\|Two-Phase Locking (2PL)]]**
**[[Data/Architecture and Design/Mechanisms/Index-Range Locking\|Index-Range Locking]]**

`Optimistic`: detect and resolve conflicts at commit time, no upfront locking, ideal for low-conflict, read-heavy systems like OLAP.
**[[Data/Architecture and Design/Mechanisms/Optimistic Concurrency Control (OCC)\|Optimistic Concurrency Control (OCC)]]**
**[[Data/Architecture and Design/Mechanisms/Timestamp Ordering\|Timestamp Ordering]]**

`Multiversion`: non-locking, balance concurrency and consistency.
**[[Data/Architecture and Design/Mechanisms/Multi-Version Concurrency Control (MVCC)\|Multi-Version Concurrency Control (MVCC)]]**
**[[Data/Architecture and Design/Mechanisms/Serializable Snapshot Isolation (SSI)\|Serializable Snapshot Isolation (SSI)]]**

## Durability
**[[Data/Architecture and Design/Mechanisms/Write-Ahead Logging\|Write-Ahead Logging]]**

> [!important]- Complete Solution: WAL + `fsync` + Check pointing + Checksumming
> **`fsync`** is a system call that forces the operating system to flush all modified data for a file to the physical storage device.
>>- Without fsync, data might remain in OS buffers/cache and not be physically written to disk
>>- The OS acknowledges write completion only after data is physically on disk 
>
> **Check pointing**: reduce recovery time by periodically creating a snapshot of the data base and truncate WAL.
>>  - A checkpoint write all dirty pages(modified data) to disk.
>>  - After a crash, recovery starts from the last checkpoint instead of the entire log.
>
> **Check summing**: validate checksums during recovery or reads.
>> - Compute checksums for log entries and data pages.
>> - Validate checksums during recovery or reads.
### Consistency
**Consistency** is primarily enforced through the combination of AID, Schema Constraints and Transaction Design where:
- **Schema Constraint** as the primary enforcers of structural consistency,
- **AID** enable transactions to safely apply these constraints,
- **Transaction Design** bridges the gap between structural rules and business logic.

### Related Services/Resources
[[Data/Architecture and Design/ACID\|ACID]]
[[Data/Architecture and Design/BASE\|BASE]]
[[Data/Architecture and Design/CAP Theorem\|CAP Theorem]]
[[Data/Architecture and Design/PACELC Theorem\|PACELC Theorem]]









