---
{"dg-publish":true,"permalink":"/data/fundamental-theory/two-phase-commit-2-pc/"}
---


**Two-Phase Commit** is a distributed protocol used to ensure **atomicity** and **consistency** across multiple notes or services in a transaction. It's critical for coordinating commits in distributed systems where a single transaction spans multiple databases, services or nodes.

## How Two-Phase Commit (2PC) Works
### Phase 1: Prepare (Voting)
A **coordinator** (transaction manager) sends a `PREPARE` message to all participants (nodes/services) in the transaction.
Each participant:
- performs the transaction locally (but does not commit).
- writes changes to a permanent log (to ensure recovery if a crash occurs). 
- responses **YES** (if ready to commit) or **NO** (if an error occurs).

### Phase 2: Commit/Rollback (Decision)
**If all participants vote "YES"**:
- the coordinator send a `COMMIT` command to all participants.
- participants finalize the transaction and release locks.

**if any participants votes "NO"**:
- the coordinator sends a `ROLLBACK` command.
- participants undo changes using their logs.
## Why 2PC is Used
**Atomicity in Distributed Systems**: ensures all nodes commit or rollback as a single unit.
**Consistency Guarantees**: prevents partial updates.
**Recovery Support**: allows participants to recover from failures with logs.

## When to use 2PC
**Scenario 1**: when multiple nodes need to maintain the same data state.
**Scenario 2**: when multiple services or systems are triggered by a single transaction. payment processing + inventory update + order management.

## Limitations & Challenges
**Blocking Problem**:
If the coordinator crashes after sending `PREPARE` but before sending `COMMIT`, participants are stuck in a "prepared" state until the coordinator recovers.

**Latency Overhead**:
Multiple round-trip messages between coordinator and participants.

**Scalability Issues**:
Not idea for high-throughput systems.

**Single Point of Failure**:
The crash of coordinator can stall the entire system.
## Alternative to 2PC
**SAGA Pattern**
**Optimistic Concurrency Control (OCC)**
**Eventual Consistency**
