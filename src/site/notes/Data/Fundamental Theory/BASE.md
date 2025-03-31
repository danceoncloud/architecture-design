---
{"dg-publish":true,"permalink":"/data/fundamental-theory/base/"}
---


## What
**BASE (Basically Available, Soft state, Eventually consistent)** is a design philosophy for distributed systems that prioritize **scalability and availability** over immediate consistency. It is the antithesis of ACID and is widely used in NoSQL, micro services and global-scale applications.

>[!INFO] **Core Principles**
>**Basically Available**: The system ***always*** responds to requests, even with degraded or stale data. \
>**Soft State**: Data may change over time **without** immediate updates (no strict consistency). \
>**Eventually Consistent**: All replicas converge to consistency **after some time** (seconds/minutes).
## Why
**Trade-offs (CAP Theorem Alignment)**:
**AP Systems (Availability + Partition Tolerance)**: BASE is the default model for systems like Cassandra, DynamoDB, etc.
**Sacrifice strong consistency** for:
- Higher throughput (1M writes/sec in Cassandra)
- Lower latency (no cross-node coordination)
- Fault tolerance (keeps working during network splits)
## How
**Conflict Resolution**:
- ***Last-Write-Wins(LWW)***: Timestamps decide the "true" state.
- ***Vector Clocks***: Track causal dependencies (DynamoDB).
**Read Repair**: Fix inconsistencies during reads (Cassandra).
**Hinted Handoff**: Store writes temporarily during node failures.
## When
**BASE** is the backbone of highly scalable, fault-tolerant systems where "perfect" consistency is less important than availability.
- **High Scalability**: Systems requiring 100K+ TPS (Transactions Per Second) (e.g., Uber surge pricing).
- **Global Availability**: Apps with users across regions (e.g., Netflix recommendations).
- **Temporary Inconsistency**: Features where stale data is acceptable (e.g., product reviews).
### Use Cases
- **Netflix**: Uses Cassandra for viewing history (eventually consistent across devices).
- **Uber**: DynamoDB for ride metadata (high writes, tunable consistency).
- **Twitter**: Redis for timelines (cached, eventually consistent).
## Challenges of BASE
**Stale Reads**: users may see outdated data.
**Conflict Handling**: concurrent updates can diverge
**Complex Dubugging**: Tracing causality in eventual consistency is hard.

### Related Services/Resources
[[Data/Fundamental Theory/ACID\|ACID]]
[[Data/Fundamental Theory/CAP Theorem\|CAP Theorem]]










