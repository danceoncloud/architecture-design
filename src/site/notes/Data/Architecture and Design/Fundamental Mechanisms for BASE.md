---
{"dg-publish":true,"permalink":"/data/architecture-and-design/fundamental-mechanisms-for-base/"}
---


## Scalability and Availability
### Replication
**Leader-Follower (Primary-Secondary)**
> [!example]- Details
> - One node designated as leader for writes
> - Followers replicate data from leader
> - Examples: MongoDB replica sets, PostgreSQL streaming replication, MySQL replication

**Multi-Leader**
> [!info]- Details
> - Multiple nodes can accept writes
> - Each leader replicates to other leaders and its followers
> - Examples: CockroachDB, some MySQL and PostgreSQL configurations
> - Attention: require conflict detection/resolution in systems like Cassandra.

**Leaderless/Peer-to-Peer**
> [!example]- Details
> - Any node can accept writes
> - Consistency often managed via quorum writes and vector clocks
> - Examples: Cassandra, Amazon Dynamo, Riak

**Consensus-Based**
> [!info]- Details
> - Uses algorithms like Raft or Paxos to achieve agreement
> - Typically requires majority agreement for writes
> - Examples: etcd, Zookeeper, Consul
### Partition/Sharding
**Range Partitioning**
> [!example]- Details
> - Data divided based on ranges of a key value
> - Example: Users A-M on Server 1, N-Z on Server 2

**Hash Partitioning**
> [!info]- Details
> - Apply hash function to the partition key to determine placement
> - Distributes data more evenly
> - May complicate range queries
> - Example: hash(user_id) % 4 determines server placement

**Consistent Hashing**
> [!example]- Details
> - Special hash technique that minimizes data redistribution when adding/removing nodes
> - Used in many NoSQL databases and distributed caches

**Directory-Based Partitioning**
> [!info]- Details
> - Maintains a lookup table mapping keys to partitions
> - More flexible but adds lookup overhead

**Composite Partitioning**
> [!example]- Details
> - Combines multiple strategies (e.g., hash + range)
> - Used in sophisticated systems like Cassandra (compound partition keys)

**Hinted Handoff**

> [!info]- Details
> - When a node is down, another node temporarily stores its writes as "hints"
> - When the failed node recovers, hints are forwarded to catch it up
> - Ensures writes aren't lost when destination nodes are temporarily unavailable
> - Helps maintain eventual consistency when nodes recover

## Consistency
[[Data/Architecture and Design/Mechanisms/Quorum\|Quorum]]: Balancing between Consistency and Availability.

**Strong Consistency**:
- [[Data/Architecture and Design/Mechanisms/Two-Phase Commit (2PC)\|Two-Phase Commit (2PC)]]
- [[Data/Architecture and Design/Mechanisms/State Machine Replication\|State Machine Replication]]
- [[Data/Architecture and Design/Mechanisms/Lease-Based Coordination\|Lease-Based Coordination]]

**Eventual Consistency**:
- [[Data/Architecture and Design/Mechanisms/Vector Clocks and Version Vectors\|Vector Clocks and Version Vectors]]
- [[Data/Architecture and Design/Mechanisms/Last-Write-Wins (LWW)\|Last-Write-Wins (LWW)]]
- [[Data/Architecture and Design/Mechanisms/Gossip protocols\|Gossip protocols]]

## Related Services/Resources
[[Data/Architecture and Design/ACID\|ACID]]
[[Data/Architecture and Design/BASE\|BASE]]
[[Data/Architecture and Design/CAP Theorem\|CAP Theorem]]
[[Data/Architecture and Design/PACELC Theorem\|PACELC Theorem]]









