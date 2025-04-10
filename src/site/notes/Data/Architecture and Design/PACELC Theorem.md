---
{"dg-publish":true,"permalink":"/data/architecture-and-design/pacelc-theorem/"}
---

![PACELC Diagram.png](/img/user/Data/Architecture%20and%20Design/Diagrams/PACELC%20Diagram.png)
## What
**PACELC** is an extension to CAP Theorem by providing a more comprehensive view of the trade-offs in distributed system. It addresses both scenarios of network partitions and normal operations, completing a nuanced perspective on trade-off between latency and consistency during normal operations, which CAP theorem does not address.

>[!INFO] **Partitioned vs Normal**
>**PAC**: If there is a ** Network Partition**, you must choose between **Availability** and **Consistency** (this is CAP theorem). \
>**ELC**: Else, when the system is running normally (no partition), you must choose between **Latency** and **Consistency**.

> [!important]- CAP Theorem vs PACELC
> **CAP Theorem** focus on trade-offs between ***Consistency*** and ***Availability*** for distributed system during ***Network Partitions***.
> **PACELC** extends this conception by also considering latency trade-offs in ***non-partition*** scenarios.

## Why
**PACELC** is important because it recognizes that distributed systems face important trade-offs even when operating normally without network failures. This framework helps architect to make better-informed decisions about distributed architecture based on their specific requirements for both failure scenarios and day-to-day operations.
## How
### **During Network Partition (P -> A/C):**
aligns with CAP Theorem:
**AP systems**: prioritize availability.
**CAP systems**: prioritize consistency.
### **During Normal Operations (E -> L/C)**
**Low Latency (L)**: relax consistency for faster responses.
**Strong Consistency (C)**: accept higher latency to ensure data accuracy.

## Latency
**Key Metrics to Measure Latency**
- **Average Response Time**: Baseline latency for read/write operations.
- **Tail Latency (e.g., 99th percentile)**: Measures worst-case delays.
- **Time to Consistency**:
    - For AP systems: Time until all replicas converge after a write.
- **Network Latency**:
    - Between nodes (e.g., inter-region vs. intra-region).
- **Coordination Overhead**:
    - Time spent in consensus protocols (e.g., Raft, Paxos) or quorum coordination.    
- **Replication Lag**:
    - Delay in propagating writes to replicas (AP systems).
### Examples
**AWS DynamoDB**: PA/EL
**Google Spanner**: PC/EC
**Apache Cassandra**: PA/EL
**CockroachDB**: PC/EC

### Related Services/Resources
[[Data/Architecture and Design/ACID\|ACID]]
[[Data/Architecture and Design/BASE\|BASE]]
[[Data/Architecture and Design/CAP Theorem\|CAP Theorem]]
[[Data/Architecture and Design/Fundamental Mechanisms for ACID\|Fundamental Mechanisms for ACID]]



















