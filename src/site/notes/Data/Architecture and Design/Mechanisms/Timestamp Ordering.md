---
{"dg-publish":true,"permalink":"/data/architecture-and-design/mechanisms/timestamp-ordering/"}
---


## What
**Timestamp Ordering** is used to enforce **isolation** by ensuring serializability based on **unique timestamps** of each transaction.

## Key Concepts and How
1. **Timestamps**:
	- Each transaction receives a **unique timestamp T** when it starts
	- Transactions are ordered by these timestamps to simulate **a serial execution sequence**.
2. **Data Item Metadata**:
	- **Read Timestamp (R-TS)**: The latest timestamp of a transaction that read the data item.
	- **Write Timestamp (W-TS)**: The latest timestamp of a transaction that wrote the data item.
3. **Rules for Operations**:
	- **Read Operation**:
		If the transaction's timestamp T < W-TS of the data item, the read is invalid (data was modified by a later transaction) and the transaction is **aborted**
		Otherwise, the read proceeds, and R-TS is updated to the max of its current value and T.
	- **Write Operation**:
		If T < R-TS of the data item, the write is invalid (a later transaction already read the data, modify the data may cause inconsistency), the transaction is **aborted**.
		If T < W-TS of the data item, the write is invalid (a later transaction already wrote the data), the transaction is **aborted**.
		Otherwise, the write proceeds, and W-TS is updated to T.

## How does a Transaction get its Timestamp
### Single-Node Database
Timestamps are generated locally using:
**Monotonic Counters**: a simple counter increments for each transaction.
**System Clock**: the local machine's clock provides timestamps.
**Hybrid Logical Clocks**: combines physical time with a logical counter to handle clock skew.

### Distributed Systems
In distributed systems, timestamp generation must account for **clock synchronization** and **global ordering**.
**Centralized Timestamp Authority**: A dedicated service assigns timestamps to all transactions.
- **pros**: guarantee globally unique, strictly ordered timestamps.
- **cons**: single point of failure, latency for coordination.

**Logical Clocks (Decentralized)**: **Lamport Clocks** or **Vector Clocks** generate timestamps based on event ordering, not physical time.
- Each node maintains a counter incremented on events.
- Timestamps are tuples like `[counter, node_id]`
- **pros**: no clock sync needed, decentralized.
- **cons**: no real-time guarantees.

**Hybrid Logical Clocks (HLC)**: Combien **physical clock time**(from local system clock) with a **logical counter** to handle clock skew.
Timestamps are of the form `[max(physical_time, last_HLC), counter]`.
- **pros**: maintain causality while staying close to physical time.
- **cons**: overhead for counter synchronization.

**TrueTime**: Use **synchronized atomic clocks and GPS** to bound clock uncertainty. Google Spanner uses this method.
**pros**: enable strict serializability with near-global time.
**cons**: requires specialized hardware, add latency.

**Decentralized Hybrid Approaches**: Systems like **YugabyteDB** or **TiDB** use a hybrid of local clocks and coordination protocols (e.g., Raft/Paxos) to agree on timestamps for ranges of data.

## Variations: BTO, MVTO and Thomas Write Rule
**Basic Timestamp Ordering (BTO)**: the protocol described above, which may lead to many aborts.
**Multiversion Timestamp Ordering (MVTO)**: maintain multiple versions of each data item to reduce aborts.
- When a transaction write data, it creates a new version.
- When reading, the transaction accesses the most recent version with a timestamp less than its own.
**Thomas Write Rule**: An optimization that reduces unnecessary aborts.
If T > W-TS, but the transaction is writing the same value, the write can be ignored rather than causing an abort.

## Strengths and Limitations
**Strengths**:
Prevent deadlocks by design.
Guarantee serializability.
Simple conceptual model.

**Limitations**:
Can lead to frequent transaction aborts and restart in high-contention scenarios.
Timestamp management adds overhead.
Long-running transactions may repeatedly abort due to conflicts with shorter transactions.

