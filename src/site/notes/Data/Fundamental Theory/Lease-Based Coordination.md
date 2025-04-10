---
{"dg-publish":true,"permalink":"/data/fundamental-theory/lease-based-coordination/"}
---


## What
**LBC** is a distributed system mechanism that use **time-bound permissions** (lease) to manage access to shared resources or roles across nodes. It ensures safety and liveness by preventing conflicting actions while allowing graceful recovery from failures.

## How
1. **Lease Granting**
	- A coordinator (e.g., ZooKeeper, etcd) grants a lease to a node for a specific duration (e.g., 10 seconds).
2. **Lease Renewal**
	- The node must **periodically renew** its lease before it expires.
	- If the node is healthy, it sends renewal requests to the coordinator.
3. **Lease Expiration**
	- If the node crashes or is partitioned, it cannot renew the lease.
	- After expiration, the coordinator revokes the lease, freeing the resource/role for others.
4. **Failover**
	- Another node can acquire the lease and take over as the new leader.

## When
**Leader Election**:
Ensures only one leader exists at a time.

**Distributed Locks**:
Locks are held only while the lease is active (e.g., prevent concurrent write).

**Caching/Data Access**:
Nodes hold leases to serve cached data, avoiding stale reads.

## Why
**Split-Brain Prevention**: only one node holds lease at a time.
**Automatic Recovery**: expired leases trigger failover without manual intervention.
**Low Overhead**: lightweight compared to consensus protocols like Paxos/Raft.

## Challenges
**Clock Synchronization**:
Leases rely on loosely synchronized clocks (e.g., using NTP).
**Lease Duration**:
- Too short: excessive renewal traffic.
- Too long: delayed failure detection.
**Network Partitions**:
A partitioned node may still act as leader until its lease expires.