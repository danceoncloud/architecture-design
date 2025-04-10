---
{"dg-publish":true,"permalink":"/data/fundamental-theory/quorum/"}
---


## What
A **Quorum** is a minimum number of nodes in a distributed system that must participate in an operation to ensure **consistency** and **fault tolerance**. It's a foundational concept for balancing **consistency** and **availability**.

## Why
**Consistency**: Ensure all nodes agree on the state of the system.
**Fault Tolerance**: Allow the system to operate even if some nodes fail.
**Avoid Split-Brain**: Prevent conflicting decisions in partitioned network.

## How
### Strick Quorum
**Write Quorum (W)**: minimum nodes that must acknowledge a write.
**Read Quorum (R)**: minimum nodes that must respond to a read.
**Total Replicas (N)**: total number of nodes.

For strong consistency, the system enforces: **W+R > N**. This ensures that read and write operations **overlap**, guaranteeing that reads always see the latest written value.

### Sloppy Quorum
**Sloppy Quorum** relaxes strict quorum rules to prioritize **availability** over immediate consistency.
- **Node Selection**: if home nodes are down, writes/reads use **any available nodes**.
- **Consistency**: temporary inconsistency is allowed (e.g., resolved later via hinted handoff).

## When
**Strict Quorum**:
    - Critical systems needing strong consistency (e.g., financial transactions, leader election).
**Sloppy Quorum**:
    - Systems prioritizing availability (e.g., social media, IoT sensor networks).
