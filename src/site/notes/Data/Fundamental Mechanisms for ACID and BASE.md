---
{"dg-publish":true,"permalink":"/data/fundamental-mechanisms-for-acid-and-base/"}
---


## ACID Compliance
### Atomicity:
**[[Data/Fundamental Theory/Transaction Boundary\|Transaction Boundary]]**
**[[Data/Fundamental Theory/Write-Ahead Logging\|Write-Ahead Logging]]**
**[[Data/Fundamental Theory/Two-Phase Commit (2PC)\|Two-Phase Commit (2PC)]]**
**[[Data/Fundamental Theory/Compensating Transactions (Sagas)\|Compensating Transactions (Sagas)]]**

### Isolation
**Isolation Level** is the guarantee offered by different solutions and **Locking Mechanism** is how the guarantee is achieved.

**Isolation Levels and Anomaly Prevention**

| **Isolation Level**        | **Dirty Reads** | **Non-Repeatable Reads** | **Phantom Reads** | **Write Skew** |
| -------------------------- | --------------- | ------------------------ | ----------------- | -------------- |
| **Read Uncommitted**       | ❌ Allowed       | ❌ Allowed                | ❌ Allowed         | ❌ Allowed      |
| **Read Committed**         | ✅ Prevented     | ❌ Allowed                | ❌ Allowed         | ❌ Allowed      |
| **Repeatable Read**        | ✅ Prevented     | ✅ Prevented              | ❌ Allowed         | ❌ Allowed      |
| **Snapshot Isolation**     | ✅ Prevented     | ✅ Prevented              | ❌ Allowed*        | ❌ Allowed      |
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
**[[Data/Fundamental Theory/Two-Phase Locking (2PL)\|Two-Phase Locking (2PL)]]**
**[[Data/Fundamental Theory/Index-Range Locking\|Index-Range Locking]]**

`Optimistic`: detect and resolve conflicts at commit time, no upfront locking, ideal for low-conflict, read-heavy systems like OLAP.
**[[Data/Fundamental Theory/Optimistic Concurrency Control (OCC)\|Optimistic Concurrency Control (OCC)]]**
**[[Data/Fundamental Theory/Timestamp Ordering\|Timestamp Ordering]]**

`Multiversion`: non-locking, balance concurrency and consistency.
**[[Data/Fundamental Theory/Multi-Version Concurrency Control (MVCC)\|Multi-Version Concurrency Control (MVCC)]]**
**[[Data/Fundamental Theory/Serializable Snapshot Isolation (SSI)\|Serializable Snapshot Isolation (SSI)]]**

### Durability
**[[Data/Fundamental Theory/Write-Ahead Logging\|Write-Ahead Logging]]**

> [!important]- Complete Solution: WAL + `fsync` + Check pointing + Check summing
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

## BASE Compliance
### Scalability and Availability
#### Replication
**Leader-Follower (Primary-Secondary)**
> [!info]- Details
> - One node designated as leader for writes
> - Followers replicate data from leader
> - Examples: MongoDB replica sets, PostgreSQL streaming replication, MySQL replication

**Multi-Leader**
> [!info]- Details
> - Multiple nodes can accept writes
> - Each leader replicates to other leaders and its followers
> - Examples: CockroachDB, some MySQL and PostgreSQL configurations

**Leaderless/Peer-to-Peer**
> [!info]- Details
> - Any node can accept writes
> - Consistency often managed via quorum writes and vector clocks
> - Examples: Cassandra, Amazon Dynamo, Riak

**Consensus-Based**
> [!info]- Details
> - Uses algorithms like Raft or Paxos to achieve agreement
> - Typically requires majority agreement for writes
> - Examples: etcd, Zookeeper, Consul
#### Partition/Sharding
**Range Partitioning**
> [!info]- Details
> - Data divided based on ranges of a key value
> - Example: Users A-M on Server 1, N-Z on Server 2

**Hash Partitioning**
> [!info]- Details
> - Apply hash function to the partition key to determine placement
> - Distributes data more evenly
> - May complicate range queries
> - Example: hash(user_id) % 4 determines server placement

**Consistent Hashing**
> [!info]- Details
> - Special hash technique that minimizes data redistribution when adding/removing nodes
> - Used in many NoSQL databases and distributed caches

**Directory-Based Partitioning**
> [!info]- Details
> - Maintains a lookup table mapping keys to partitions
> - More flexible but adds lookup overhead

**Composite Partitioning**
> [!info]- Details
> - Combines multiple strategies (e.g., hash + range)
> - Used in sophisticated systems like Cassandra (compound partition keys)

#### Node Failure Handling
**Hinted Handoff**
- When a node is down, another node temporarily stores its writes as "hints"
- When the failed node recovers, hints are forwarded to catch it up
- Ensures writes aren't lost when destination nodes are temporarily unavailable
- Helps maintain eventual consistency when nodes recover
### Consistency
**Strong Consistency**:
- Two-phase commit (2PC)
- Three-phase commit (3PC)
- State machine replication
- Leader election
- Sharding with consistent hashing
- Lease-based coordination

**Eventual Consistency**:
- Sloppy quorums
- Gossip protocols 
- Vector clocks/version vectors
- Read repair
- Hinted handoff 
- Last-Write-Wins conflict resolution
- CRDTs (Conflict-free Replicated Data Types)
- Anti-entropy processes
- Merkle trees for synchronization

> [!warning]
> - Some mechanisms (e.g., leases, sharding) can appear in both CP/AP systems depending on implementation.
> - Systems often blend CP/AP traits (e.g., CockroachDB is CP but scales like AP).
### Related Services/Resources
[[Data/Fundamental Theory/ACID\|ACID]]
[[Data/Fundamental Theory/BASE\|BASE]]
[[Data/Fundamental Theory/CAP Theorem\|CAP Theorem]]
[[Data/Fundamental Theory/PACELC Theorem\|PACELC Theorem]]









