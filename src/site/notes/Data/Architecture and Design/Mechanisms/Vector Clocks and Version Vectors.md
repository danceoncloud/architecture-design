---
{"dg-publish":true,"permalink":"/data/architecture-and-design/mechanisms/vector-clocks-and-version-vectors/"}
---


## What
Both **vector clocks** and **version vectors** are used in distributed systems to track causality and detect conflicts.

## How
### Vector Clocks
**Vector Clocks** are used to track causal relationships between **events** across nodes.
- Each node maintains a vector of counters, one per node.
- When a node performs an event, it increments its own counter.
- vectors are attached to messages, recipients merge vectors to infer causal ordering.
#### Conflict Detection
If two vectors are **incomparable** (neither is entirely greater than the other), the events are concurrent.
- Example:
    - Node A: `[A:2, B:1]`
    - Node B: `[A:1, B:2]`  
        → **Conflict** (concurrent updates).

### Version Vectors
**Version Vectors** track version history of **specific objects** to detect conflicting updates.
- Each object has a version vector (e.g., `{A:3, B:2}`) where entries represent node-specific update counts.
- When a node updates the object, it increments its own counter in the version vector.

#### Conflict Detection
- Compare two version vectors for the same object:
    - If one is **strictly greater** in all entries, it is newer.
    - If **incomparable**, updates are concurrent (conflict).
- Example:
    - Replica 1: `{A:2, B:1}`
    - Replica 2: `{A:1, B:2}`  
        → **Conflict** (neither is newer).

#### Conflict Resolution
- **Vector Clocks**: Systems like Dynamo return all conflicting versions to the application for resolution (e.g., merging user profiles).
- **Version Vectors**: Systems like Riak store conflicting "siblings" and let the application resolve them (e.g., picking the latest timestamp).