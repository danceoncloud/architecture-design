---
{"dg-publish":true,"permalink":"/data/data-foundations/data-storage-and-processing-taxonomy/"}
---


## Data-at-Rest 
### RDBMS
**Purpose**: Store structured data with strict integrity guarantees.
**Key Features**:
- ACID compliance (Atomicity, Consistency, Isolation, Durability).
- Vertical scaling (scale-up via larger servers).
- SQL for complex queries.

**Use Cases**: Banking transactions, ERP systems.
**Examples**: PostgreSQL, Oracle, MySQL.
**Trade-offs**: Limited horizontal scalability, high cost for large datasets.
### NoSQL Databases
**Purpose**: Handle unstructured/semi-structured data at scale.
**Key Features**:
- Schema-less design (flexible data models: document, key-value, graph).
- AP in CAP theorem (prioritize Availability/Partition Tolerance).
 - Horizontal scaling (distributed clusters).

**Use Cases**: Real-time apps (social media), IoT sensor data.
**Examples**: MongoDB (document), Cassandra (wide-column), Redis (key-value).
**Trade-offs**: Eventual consistency, no complex joins.
### NewSQL
**Purpose**: Combine ACID guarantees with distributed scalability.
**Key Features**:
- Distributed architecture + ACID compliance.
 - SQL support with horizontal scaling.
**Use Cases**: High-scale transactional systems (e.g., global e-commerce).
**Examples**: CockroachDB, Google Spanner.
**Trade-offs**: Complexity in cluster management.

### Data Lake
**Purpose**: Store raw, unstructured data or structured data at low cost.
**Key Features**:
- Schema-on-read (flexible ingestion).
- Supports all data types (text, images, logs).
- Built on object storage (e.g., AWS S3).

**Use Cases**: AI/ML training, exploratory analytics.
**Examples**: AWS S3, Azure Data Lake.
**Trade-offs**: Risk of becoming a "data swamp" without governance.
### Data Warehouse
**Purpose**: Optimize for analytical queries (OLAP).
**Key Features**:
- Columnar storage (fast aggregation).
- Schema-on-write (structured for performance).
- Integrates with BI tools (Tableau, Power BI).

**Use Cases**: Business reporting, historical analytics.
**Examples**: Snowflake, Redshift, BigQuery.
**Trade-offs**: Higher storage costs, less flexible for raw data.
## Data-in-Motion
Event Streaming
API
Message Queues
Real-Time ETL/Processing
Edge/Device Data Ingestion




















