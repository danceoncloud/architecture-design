---
{"dg-publish":true,"permalink":"/data/data-universe/","title":"Data Universe: Principles, Architectures and Modern Solutions"}
---


## Data Categorization and File Formats
### Data Categorization
**Structured Data** (Tables with predefined schema, e.g., RDBMS)
**Semi-Structured Data** (data with predefined schema with schema evolution, JSON, XML, Avro, Parquet, etc.)
**Unstructured Data** (Images, Videos, Audio, PDFs, Raw Text)
### Featured File Formats
**Text-based:** TXT, CSV, JSON, XML, YAML
**Columnar storage formats:** Parquet, ORC
**Binary formats:** Avro, Protobuf, MessagePack
## Data Storage & Processing Taxonomy
### Data-at-Rest 
**RDBMS** (ACID + SQL, vertical scalability)
**NoSQL Databases** (Schema-less, favor availability and scalability over strong consistency)
**NewSQL** (Distributed databases + ACID)

**Data Lake** (Raw storage, massive storage with low cost)
**Data Warehouse** (OLAP-optimized)
**Data Lakehouse** (Raw storage + ACID + SQL)
### Data-in-Motion
**Event Streaming**: Ingest, process and deliver high-velocity event streams.
**API**: Serve or consume data via APIs (synchronous/asynchronous).
**Message Queues**: Decouple producers/consumers with asynchronous messaging.
**Real-Time ETL/Processing**: Transform and enrich data in-flight
**Edge/Device Data Ingestion**: Collect and process data from IoT devices or edge locations.

## Foundational Principles for Guarantees and Trade-Offs on Data-at-Rest
### Theoretical Frameworks for Unavoidable Trade-Offs in Distributed Systems
[[Data/Fundamental Theory/CAP Theorem\|CAP Theorem]] (Consistency, Availability, Partition tolerance)
[[Data/Fundamental Theory/PACELC Theorem\|PACELC Theorem]] (Partition, Availability, Consistency, Else, Latency, Consistency)
### Practical Design Philosophies for Transactions
[[Data/Fundamental Theory/ACID\|ACID]] (Atomicity, Consistency, Isolation, Durability)
[[Data/Fundamental Theory/BASE\|BASE]] (Basically Available, Soft state, Eventually consistent)
### Theory to Practice
[[Data/Purpose-Driven Data Architecture\|Purpose-Driven Data Architecture]]: A Quick Guide to Find the First Component of Data Project
[[Data/Fundamental Mechanisms for ACID and BASE\|Fundamental Mechanisms for ACID and BASE]]
## Feature: Data Security
### Principles: 
- Defense in Depth: use layered security (firewalls, encryption, access controls)to reduce single points of failure.
- Least Privilege: always the minimum access to perform tasks.
- Zero Trust: verify every access request.
### Mechanisms:
- Encryption: in transit and at rest
- Access Control: RBAC and ABAC
### Solution:
**HTTPS**: SSL/TLS in transit
**AWS KMS**: encryption at rest
**AWS IAM/Policy**: access control
>[!INFO] RBAC & ABAC
>**RBAC**: assign permissions to roles (`Admin can delete records`) \
  **ABAC**: define roles using attributes (`IF user.department = "Finance" AND resource.sensitivity = "Low" THEN allow access`)
## Feature: Data Compliance
### Principles: 
- Data Classification: categorize data based on sensitivity level with appropriate protection measures.
- Privacy by Design: embed data protection from the start (GDPR compliance)
### Mechanisms:
- **Data Anonymization**: Irreversible removal of identifiers (exempt from GDPR)
	*Generalization*: replace exact values with ranges (age 25 -> "20-30")
	*Perturbation*: add noise to data (salary 50000 -> 50000 * (0.95, 0.05))
	*Hashing*: hash data with SHA-256 with salt
	*Static Masking*: permanently replace data ("Jone Doe" -> "User_123")
- **Data Pseudonymization**: Reversible replacement (GDPR-compliant with safeguards)
	*Tokenization*: replace data with tokens in a secure vault
	*Dynamic Masking*: make data on-the-fly based on user roles ("123-45-6789" → "--6789")	

> [!NOTE] Regulatory Framework: GDPR, PII, HIPAA
> **Tokenization** and **Pseudonymization** are explicitly recommended by GDPR to reduce risks.
> **Anonymized data** falls outside GDPR scope.
### Solutions:
AWS Compliance Tools, Google Cloud Compliance Controls, Microsoft Compliance Manager
## Feature: Data Governance
### Principles:
- Accountability & Ownership
- Standardization
- Data Provenance & Lineage
- Retention & Disposal
- Data Quality Management
- Audit
### Mechanisms:
- **Ownership**: Assign accountability for datasets
- **Stewardship**: Individuals/teams responsible for data accuracy, compliance, and usability
- **Metadata Management**: Track data lineage, definitions, and usage
- **Data Quality Enforcement**: Validity, completeness, consistency, timeliness
- **Retention & Disposal**: Ingest->Store->Process->Archive->Delete
### Solutions:  
**Data Lineage & Metadata**: Collibra, Alation, AWS Lake Formation
**Quality**: Talend Data Quality, AWS Glue DataBrew
**Retention & Disposal**: AWS S3 Policies, Snowflake Time Travel
## Feature: Data Modeling & Schema Design
### Principles: 
- Normalization vs Denormalization 
- Schema-on-Read vs Schema-on-Write 
- Dimensional Modeling
- Slowly Changing Dimensions
### Mechanisms:
- Star Schema & Snowflake Schema
- Data Vault Modeling
### Solutions:
**Lucidchart**
**Snowflake Schema Builder**
**PowerDesigner**
**ER/Studio**
**Apache Iceberg**
## Feature: Data Integration & Pipelines
### Principles: 
- Idempotence
- Loose Coupling
- Data Freshness
### Mechanisms:
- ETL vs ELT 
- Batch vs Stream Processing 
- Change Data Capture
### Solutions: 
**Apache Spark**
**Apache Airflow**
**AWS Stepfunction**
## Feature: Disaster Recovery & Backup
### Principles: 
- Geographic Distribution
- Recoverability
### Mechanisms:
- RTO/RPO(recovery time/point objectives)
- Cross-Region Replications
- Immutable Backups
### Solutions: 
**AWS Backup**
**Snowflake Fail-Safe**
**Databricks Delta Lake versioning**



































