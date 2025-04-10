---
{"dg-publish":true,"permalink":"/data/data-categorization/"}
---


## Structured Data 
**Definition**:
Data organized into a predefined schema, typically stored in **tables** with rows and columns.

**Characteristics**:
- **Schema-on-Write**: require a fixed schema before ingestion.
- **Relational**: relationships between tables (e.g., foreign keys).
- **SQL Optimized**: optimized for SQL queries.

**Examples**:
- RDBMS tables (e.g., PostgreSQL)
- CSV files with header
- Excel spreadsheet

**Storage Solutions**:
- RDBMS: PostgreSQL
- Data Warehouse: Snowflake, Redshift
- Data Lake: AWS S3, Google Cloud Storage

**Use Cases**:
- Transactional Systems (banking, inventory)
- Reporting and BI dashboards
## Semi-Structured Data
**Definition**:
Data with partial organization, often self-describing via tags, metadata, or nested hierarchies.
**Characteristics**:
- **Schema-on-Read**: Schema is applied when data is read, not enforced during ingestion.
- **Flexible**: Mixes structured and unstructured elements.
**Examples**:
- JSON, XML, YAML
- Avro, Parquet (columnar formats with embedded metadata)
**Storage Solutions**:
- NoSQL Databases: MongoDB, DynamoDB
- Data Lake: AWS S3, Azure Data Lake
**Use Cases**:
- Web APIs
- IoT sensor data
## Unstructured Data
**Definition**:
Data with no predefined schema or organization.

**Characteristics**:
- **No Fixed Format**: require parsing (e.g., NLP for text, computer vision for images).
- **High Volume**: often the largest data type in modern systems.

**Examples**:
- Text: Emails, social media posts, PDFs
- Media: photos, videos, audio files
- Raw logs: server logs, clickstreams

**Storage Solutions**:
**Data Lake**: AWS S3, Hadoop HDFS

**Use Cases**:
- AI/ML training
- Content Management Systems
### Featured File Formats
**Text-based:** TXT, CSV, JSON, XML, YAML
**Columnar storage formats:** Parquet, ORC
**Binary formats:** Avro, Protobuf, MessagePack