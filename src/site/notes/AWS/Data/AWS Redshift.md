---
{"dg-publish":true,"permalink":"/aws/data/aws-redshift/","title":"AWS Redshift"}
---

## What
**Amazon Redshift** is a fully managed, petabyte-scale data warehouse service in the cloud.
- Queries are executed through massively parallel processing on compute nodes.
- Database tables are Columnar typed.
- Data is compressed on storage and uncompressed when loading into RAM, to reduce disk I/O.
- Result caching is enabled by default and cached queries are controlled by Redshift.

> [!NOTE] Core Components:
> **Redshift Serverless**: automatically provision data warehouse capacity and intelligently scales the underlying resources.\
> **Redshift Provisioned cluster**: **a cluster** is a collection of computing resources called ***nodes***. Each cluster can contain one or more databases.\
> **Redshift Spectrum**: a service that allows users to query data on s3 without loading into Redshift data warehouse.\
> **Redshift Managed Storage**: separate storage tier, automatically scale, allow user to size cluster based on computing needs.\
> **Data Backup**:
>> **Snapshots**: manually \
>> **Recovery points**: automatically, every 30 minutes and kept for 24 hours
>
> **Data Shares**: offer live access to data to see the most up-to-date information. for read-only purpose.\
> **Redshift-managed VPC endpoints**: private connection entry powered by AWS Private-Link.\
> **Redshift Processing Units (RPUs)**: resources used to handle worklods.

>[!important]- Node Types: RA3 and DC2
>**RA3**:  separate compute and storage capacity. 
>>RA3 uses SSDs for fast local storage and S3 for longer-term durable storage.
>>launched in VPC.\
>>Data beyond the size of local storage offloads to S3 automatically.\
>>**RA3 provisioned cluster** support Multi-AZ deployments.
>
>**DC2**: compute-intensive with local SSD storage.
>>add more nodes when data grows.
>>best for data < 1TB(compressed).
### Redshift Serverless Cluster
- No Maintenance window.
- Automatic update with control on the release version.
- Minimum of 3 subnets across 3 AZs. for network resilience and flexibility.
- Minimum of 3 free IP addresses in each subnet, if enhanced VPC routing is not enable.

### Redshift Provisioned Cluster
**Leader Node**: each cluster has a leader node. 
- receive queries from client applications 
- parse the queries 
- develop query execution plans
- coordinate parallel execution with compute nodes
- aggregate intermediate results from compute nodes
**Compute Node**: a cluster has one or more compute nodes.
- run query execution plans
- transmit data among themselves
- send to leader node intermediate results

**Performance and Data Loss**
Increase compute nodes can improve execution parallelism.
With at least two compute nodes, data on each node is mirrored on disks of another node to prevent data loss.

## How to Load Data into Redshift 
Use **compression** (e.g., GZIP) and **distribution keys** to optimize storage and query performance.
### COPY command
- Most efficient way to bulk-load data from S3, DynamoDB, or EMR.
- Supports formats like CSV, JSON, Parquet, and Avro.
- Can use manifest files for partitioned data or incremental loads.
### DML tools (Insert/Update/Delete)
- Suitable for small-scale updates or inserts directly via SQL.
- Less efficient for large datasets compared to `COPY`.
### Third-Party ETL Tools:
AWS Glue, AWS Data Pipelines, Apache Kafka, AWS Kinesis Firehose
### Zero-ETL integrations
It's a fully management solution that makes transactional and operational data available in Redshift from multiple sources.
Near real-time analytics with transactional data (e.g., Aurora zero-ETL to Redshift).

> [!NOTE] Components
> **Source Database** is the database where data is replicated into Amazon Redshift.
> **Target Data Warehouse** is the Amazon Redshift provisioned cluster or Redshift Serverless workgroup. \
> **Destination Database** is the database created from zero-ETL integration in the target data warehouse. 

**Source Databases**:
- Amazon Aurora MySQL
- Amazon Aurora PostgreSQL
- Amazon RDS for MySQL
- Amazon DynamoDB
- Applications, such as, Salesforce, SAP, ServiceNow, and Zendesk
**S3 event** can also be ingested into the target table of data warehouse.

## How to Query Data
- Use **workload management (WLM)** to prioritize queries.
- Enable **result caching** for repeated queries to reduce latency.
### SQL Clients
- Use Redshift Query Editor v2, BI tools (Tableau, Power BI), or JDBC/ODBC connections.
### Federated Query
- query data stored in external databases directly with a "virtual" connection to external data sources.
### Redshift Spectrum
**Redshift Spectrum** resides on dedicated Redshift servers independent of your cluster. Allow quering data directly in AWS S3 using external tables.

> [!NOTE]- **Process of Use**:
> 1. configure Redshift cluster and a SQL client that's connected to your cluster.
> 2. create external schema and external table.
> 3. query data in S3.


> [!NOTE]-  **Process of Use with Apache Iceberg Tables**:
> 1. create Iceberg table in AWS Glue Data Catalog using AWS Athena.
> 2. create Redshift cluster or serverless workgroup with IAM role that allow access to your data lake.
> 3. connect to your cluster or workgroup.
> 4. create external schema in Redshift database for specific Data Catalog database that includes Iceberg tables.
> 5. run queries to access Iceberg tables.

### Data Sharing
- Securely share live data across Redshift clusters (even cross-account).
- Avoid data duplication; useful for multi-tenant architectures.

## How to Unload Data
### UNLOAD command
- Export query results to S3 in formats like Parquet, JSON, or CSV.
- Supports **partitioning** (e.g., by date) and **encryption** (SSE-S3, SSE-KMS).













































