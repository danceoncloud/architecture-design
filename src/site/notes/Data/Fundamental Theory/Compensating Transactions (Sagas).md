---
{"dg-publish":true,"permalink":"/data/fundamental-theory/compensating-transactions-sagas/"}
---


A **Compensating Transaction**, often referred to as a **SAGA**, is a design pattern used in distributed systems to manage long-running, multi-step transactions. A **SAGA** is a sequence of smaller, loosely coupled transactions (steps). Each step has a corresponding **compensating action** that undoes its effect if the SAGA fails at any point.


## How SAGAs Work
**Forward Operations**
Execute a series of steps (e.g., reserve inventory, charge payment, schedule shipping).

**Compensation Actions**
If any step fails, the SAGA triggers **compensating transaction in reverse order** (e.g., cancel inventory  reservation, refund payment, cancel scheduled shipping.)

## Types of SAGAs
### Choreography-Based SAGAs:
**Decentralized**: Each step emits events to trigger the next action or compensation.
**Pros**: Flexible, no central coordinator.
**Cons**: Complex to debug.

### Orchestration-Based SAGAs**:
**Centralized**: A coordinator manages the workflow.
**Pros**: Centralized logic, easier to track.
**Cons**: Single point of failure.

## Why Use SAGAs
**Scalability**: No long-lived locks, so high throughput can be supported.
**Fault Tolerance**: Compensations handle partial failures.
**Decentralized Control**: Works in a systems without a global transaction manager. 

## Limitations & Challenges
**Compensation Complexity**: Designing idempotent, reversible compensating actions can be challenging.
**Eventual Consistency**: Temporary inconsistencies may exist until compensations complete.
**Debugging**: Tracing SAGA's flow across services/events is dificult.




































