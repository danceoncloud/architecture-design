---
{"dg-publish":true,"permalink":"/data/fundamental-theory/state-machine-replication/","tags":["strong_consistency"]}
---



## What
**SMR** is a fundamental technique in distributed systems that enables multiple servers to maintain identical copies of data and process logic, providing fault tolerance and consistency.

>[!INFO] Core Concept
>The central idea is to model a system as a deterministic state machine where:
>> - The system has a well-defined initial state. 
>> - It processes commands in sequence. 
>> - Each command deterministically transitions the system from one state to the next. 
>> - All replicas processing the same commands in the same order will reach the same state. 

## How
**Step 1: Command Logging**:
All client requests (commands) are logged in a **replicated log**.

**Step 2: Consensus on Log Order**:
Replicas use a **consensus algorithm** (e.g., Paxos, Raft) to agree on the order of commands in the log.
- A **Leader** proposes the order,
- Followers vote to accept/reject the proposal.
- Once a majority agrees, the command is **committed** to the log.

**Step 3: Applying Commands**:
Each replica **applies the commands** from the log **in the agreed order** to its local state machine.

**Step 4: Handling Failures**:
**Leader Failure**: A new leader is elected and the log is repaired if gaps exist.
**Follower Failure**: The failed replica catches up by replaying the log once it recovers.

## Pros and Cons
**Pros**:
- Strong consistency guarantees
- Automatic fault tolerance
- Simplified application development
**Cons**:
- Performance cost of consensus
- Choose consistency over availability during network partitions