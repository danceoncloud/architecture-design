---
{"dg-publish":true,"permalink":"/data/theory/acid/","title":"ACID"}
---

## What
in the contexte of databases and data storage system, a **transaction** is any operation that is treated as a single unit of work, which either completes fully or does not complete at all, and leaves the storage system in a consistent state.

Data bases and storage systems that support ACID are **transactional system**.

> [!NOTE] Four Properties
> **Atomicity**: all statements in a transaction(to read, write, update or delete data) are treated as a single unit. Either all statements complete or none of them are accepted, rollback will be applied to finished statements to bring system to original state.
> 
> **Consistency**: ensure that transactions only make changes to tables in predefined, predictable ways. it also guarantees that database transitions from one valid state to another and that transaction must satisfy defined database constraints.
> 
> **Isolation**: concurrent transactions will not interfere with or affect one other. Each request can occur as though they were occurring one by one. Isolation level can vary based on Read Uncommitted, Read Committed, Repeatable Read, Serializable. 
> 
> **Durability**: ensures that changes to the data will be saved, even in system failure.
## Why
**ACID Transaction** ensures highest possible data reliability and integrity.

## How
### **Traditional Databases (RDBMS)**: Full ACID compliance
RDBMS like **PostgreSQL, MySQL and SQL Server** are designed for OLTP(Online Transactional Processing) and natively enforce ACID.
- **Priority**: All four ACID properties equally.
- **Mechanisms**: WAL, row-level locking, strict serializability.
- **Trade-off**: Sacrifices scalability for strict consistency (optimized for OLTP).

### **Data Warehouse**: Partial or Modified ACID
Systems like **Snowflake, AWS Redshift, Google BigQuery, Azure Synapse Analytics** prioritize analytics(OLAP) over transactional workloads. Techniques like **snapshot isolation** or **multi-version concurrency control** to ensure atomicity and consistency for bulk operations. Data warehouse often use ***eventual consistency***, instead of full transactional consistency. 
- **Priority**: Atomicity and durability for bulk operations, with relaxed isolation (e.g., snapshot isolation).
- **Mechanisms**: MVCC, time-travel, immutable snapshots.
- **Trade-off**: Prioritizes read performance and concurrency for analytics over strict transactional isolation.

### **Data Lakehouse**: ACID via metadata layers
Platforms like **Databricks Delta Lake, Apache Iceberg and Apache Hudi** add ACID guarantees to object storage using transaction logs and atomic commits.
- **Priority**: Atomicity and durability for large-scale data writes (often append-heavy workloads).
- **Mechanisms**: Transaction logs (e.g., Delta Lake’s `_delta_log`), optimistic concurrency control, and schema enforcement.
- **Trade-off**: trade write performance for ACID guarantee and additional features like time travel and schema evolution.

### **NoSQL databases**: ACID supports in progress
MongoDB (4.0+): multi-document ACID transactions.
DynamoDB: ACID compliance on single-item by default, multi-item transactions require use of ***TransactWriteIteams API***.
Neo4J: full ACID support.


> [!important] Data Lake
> Data lake itself is a storage-centric platform for massive storage with low cost. 
> Services like HDFS, AWS S3, Google Cloud Storage and Azure Data Lake Storage Gen2 are popular options. \
> By using technologies like Apache Iceberg, Databricks Delta Table or Apache Hudi, data lake can be transformed to data lakehouse with ACID supports.

## Storage and Compute
### **Storage-Compute Separation**:
Snowflake, AWS Redshift Spectrum, Google BigQuery, Azure Synapse Analytics, Databricks Lakehouse
- Independent scaling of storage and compute resources
- Pay-for-use compute model
- Multiple compute clusters can access the same data concurrently
- Storage costs typically lower

### **Integrated Storage-Compute**:
AWS Redshift(DC2 nodes), Teradata, Oracle Exadata
- Potentially lower latency for some workloads
- Predictable performance characteristics
- Sometimes simpler management
- Often better for specific workload patterns

### Related Services/Resources
[[Data/Theory/CAP Theorem\|CAP Theorem]]
