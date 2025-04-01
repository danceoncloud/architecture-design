---
{"dg-publish":true,"permalink":"/data/fundamental-theory/pacelc-theorem/"}
---

![PACELC Diagram.png](/img/user/Data/Fundamental%20Theory/PACELC%20Diagram.png)
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

### Examples
**AWS DynamoDB**: PA/EL
**Google Spanner**: PC/EC
**Apache Cassandra**: PA/EL
**CockroachDB**: PC/EC





















