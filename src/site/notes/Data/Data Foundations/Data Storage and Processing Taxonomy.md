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
### Event Streaming
**Purpose**: Process high-velocity data in real time.
**Key Features**:
- Persistent, ordered event logs.
- Scalable consumers/producers.

**Use Cases**: Fraud detection, live dashboards.
**Examples**: Apache Kafka, AWS Kinesis.
**Trade-offs**: Requires stream-processing frameworks (e.g., Flink).
### API
**Purpose**: Expose or consume data programmatically.
**Key Features**:
 - REST (stateless), GraphQL (flexible queries), gRPC (high-performance).
- Sync/async communication.

**Use Cases**: Microservices, third-party integrations.
**Examples**: Express.js (REST), Apollo (GraphQL).
**Trade-offs**: Latency in synchronous APIs.
### Message Queues
**Purpose**: Decouple systems with asynchronous communication.
**Key Features**:
- Guaranteed delivery, fault tolerance.
- Pub/sub or point-to-point models.

**Use Cases**: Order processing, workload distribution.
**Examples**: RabbitMQ, Amazon SQS.
**Trade-offs**: Message ordering challenges.
### Real-Time ETL/Processing
**Purpose**: Transform data in transit (before storage).
**Key Features**:
- Stream processing (windowing, aggregations).
- Low-latency transformations.

**Use Cases**: Enriching clickstream data, fraud alerts.
**Examples**: Apache Spark Streaming, AWS Glue Streaming.
**Trade-offs**: Complexity in state management.
### Edge/Device Data Ingestion
**Purpose**: Collect data from distributed sources (IoT, mobile).
**Key Features**:
- Lightweight protocols (MQTT, CoAP).
- Local preprocessing (edge computing).

**Use Cases**: Smart factories, connected vehicles.
**Examples**: AWS IoT Core, Azure IoT Hub.
**Trade-offs**: Bandwidth/latency constraints.



















