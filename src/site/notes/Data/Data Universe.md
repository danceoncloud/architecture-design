---
{"dg-publish":true,"permalink":"/data/data-universe/","title":"Data Universe"}
---

## Data Storage Paradigms
 **RDBMS** (Relational Database Management System)
 **NoSQL Databases** (Key-Value Stores, Document Stores, Columnar DBs, Graph DBs, etc.)
 **NewSQL** (Databases with RDBMS features but distributed and scalable, e.g., CockroachDB)

 **Data Lake** (Stores raw, unstructured, and structured data)
 **Data Warehouse** (Structured, optimized for analytics)
 **Data Lakehouse** (Hybrid of Data Lake & Data Warehouse)

## Data Categorization
**Structured Data** (Tables with predefined schema, e.g., RDBMS)
**Semi-Structured Data** (JSON, XML, Avro, Parquet, etc.)
**Unstructured Data** (Images, Videos, Audio, PDFs, Raw Text)

## File Formats
**Text-based:** TXT, CSV, JSON, XML, YAML
**Columnar storage formats:** Parquet, ORC
**Binary formats:** Avro, Protobuf, MessagePack

## Fundamental Principles
### [[Data/Fundamental Theory/ACID\|ACID]] (Atomicity, Consistency, Isolation, Durability)
### BASE (Basically Available, Soft state, Eventually consistent)
### [[Data/Fundamental Theory/CAP Theorem\|CAP Theorem]] (Consistency, Availability, Partition tolerance)
### PACELC Theorem (Partition, Availability, Consistency, Else, Latency, Consistency)
### Data Architecture Design: Balancing ACID, CAP, BASE, and PACELC

## Feature: Data Security
#### Principles: 
- Defense in Depth
- Least Privilege
- Zero Trust
#### Mechanisms:
- Encryption: in transit and at rest
- Access Control: RBAC and ABAC
#### Solution:
***HTTPS***: SSL/TLS in transit
***AWS KMS***: encryption at rest
***AWS IAM/Policy***: access control
>[!INFO] RBAC & ABAC
>**RBAC**: assign permissions to roles (`Admin can delete records`) \
  **ABAC**: define roles using attributes (`IF user.department = "Finance" AND resource.sensitivity = "Low" THEN allow access`)

## Feature: Data Privacy and Compliance
#### Principles: 
- Data Minimization
- Purpose Limitation
- Privacy by Design
#### Mechanisms:
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
#### Solutions:
***AWS Payment Cryptography***
## Feature: Data Governance
#### Principles:
- Single Source of Truth
- Data Quality Management
- Accountability
#### Mechanisms:
- **Ownership**: Assign accountability for datasets
- **Stewardship**: Individuals/teams responsible for data accuracy, compliance, and usability
- **Metadata Management**: Track data lineage, definitions, and usage
- **Data Quality Enforcement**: Validity, completeness, consistency, timeliness
- **Lifecycle Management**: Ingest->Store->Process->Archive->Delete
#### Solutions:  
***Ownership***: Collibra, Alation
***Stewardship***: AWS Lake Formation
***Metadata***: AWS Glue Data Catalog, Apache Atlas
***Quality***: Talend Data Quality, AWS Glue DataBrew
***Lifecycle***: AWS S3 Policies, Snowflake Time Travel

## Feature: Data Modeling & Schema Design
#### Principles: 
- Normalization vs Denormalization 
- Schema-on-Read vs Schema-on-Write 
- Dimensional Modeling
- Slowly Changing Dimensions
#### Mechanisms:
- Star Schema & Snowflake Schema
- Data Vault Modeling
#### Solutions:
***Lucidchart***
***Snowflake Schema Builder***
***PowerDesigner***
***ER/Studio***
***Apache Iceberg***
## Feature: Data Integration & Pipelines
#### Principles: 
- Idempotence
- Loose Coupling
- Data Freshness
#### Mechanisms:
- ETL vs ELT 
- Batch vs Stream Processing 
- Change Data Capture
#### Solutions: 
***Apache Spark***
***Apache Airflow***
***AWS Stepfunction***

## Feature: Disaster Recovery & Backup
#### Principles: 
- Geographic Distribution
- Recoverability
#### Mechanisms:
- RTO/RPO(recovery time/point objectives)
- Cross-Region Replications
- Immutable Backups
#### Solutions: 
***AWS Backup***
***Snowflake Fail-Safe***
***Databricks Delta Lake versioning***



































