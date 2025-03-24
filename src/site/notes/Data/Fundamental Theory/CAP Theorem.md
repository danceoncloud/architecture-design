---
{"dg-publish":true,"permalink":"/data/fundamental-theory/cap-theorem/","title":"CAP Theorem"}
---

### What
**CAP Theorem** states that in a distributed system, you can only guarantee two out of three properties at the same time:
1. **Consistency**: all nodes see the same data at the same time
2. **Availability**: every request receives a response, even during failure
3. **Partition Tolerance**: the system continues operating despite network partitions

> [!NOTE] Key Implications:
> Partitions are inevitable in distributed system, so you must choose between C and A.
> Trade-offs are not permanent, systems can prioritize different properties under normal vs. partitioned conditions.

### How
| **System Type** | **Prioritizes**            | **Example Systems**                   | **Use Case**                         |
| --------------- | -------------------------- | ------------------------------------- | ------------------------------------ |
| **CP**          | Consistency + Partition    | MongoDB, Redis (cluster mode), HBase  | Banking, financial systems           |
| **AP**          | Availability + Partition   | Cassandra, DynamoDB, S3               | Social media, IoT, high-traffic apps |
| **CA**          | Consistency + Availability | Single-node RDBMS (PostgreSQL, MySQL) | Non-distributed legacy systems       |

### CAP vs ACID
- **ACID** focuses on **transactional guarantees** (e.g., atomicity, isolation) within a single system.
- **CAP** addresses **distributed system trade-offs** (e.g., consistency vs. availability).
- **Overlap**: Strict ACID compliance in distributed systems (e.g., global consistency) often requires sacrificing availability (CP systems).

### Why It Matters for ACID:
- Distributed databases (e.g., CockroachDB, Google Spanner) use techniques like **atomic clocks** or **Paxos/Raft consensus** to achieve both ACID and partition tolerance (CP).
- Data warehouses/lakehouses (AP or CP) often relax consistency for scalability (e.g., Snowflake’s eventual consistency for queries).


### CAP with AWS Redshift, Snowflake, Databricks
|**System**|**ACID Focus**|**CAP Classification**|**Reasoning**|
|---|---|---|---|
|**AWS Redshift**|Bulk operations with relaxed isolation|CP|Prioritizes consistency during partitions; availability may drop.|
|**Snowflake**|Full ACID for DML/ELT|CP|Strong consistency with partition tolerance; availability is managed via retries.|
|**Databricks (Delta Lake)**|ACID via metadata/transaction logs|CP|Consistency enforced through atomic commits; S3 provides partition tolerance.|
### Why CP?
- **Analytics Workloads**: All three systems prioritize **consistency** to ensure accurate query results, even if it means temporary unavailability during partitions.
- **Storage Layer**: Dependence on distributed storage (S3, Azure Blob) ensures partition tolerance.
- **Trade-offs**:
    - Availability is often managed through retries or transient failures (e.g., Snowflake’s auto-resume).
    - Strict consistency is critical for reporting, compliance, and data integrity in analytics.

### Related Services/Resources
[[Data/Fundamental Theory/ACID\|ACID]]









