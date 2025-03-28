---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/network-load-balancer/","title":"Network Load Balancer"}
---

![Network Load Balancer.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Network%20Load%20Balancer.png)

## What
- A **Layer 4 (Transport Layer)** load balancer that distributes **TCP, UDP, and TLS** traffic across multiple targets (EC2, IPs, Lambda).
- Designed for **high throughput** and **millisecond latency**. 
- Supports **zonal failover** and **Private Link** for secure service exposure.

> [!info] Key Components:
    >**Load Balancer**: single point of contact for clients 
    >**Listener**: check connection requests and forwards to target group  
    >**Target Group**: route requests to one or more targets

## When
- When your application needs to handle **millions of requests per second**.
- When **low-latency** connections and **static IP addresses** are required.
- When exposing services **via AWS [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/private-link\|private-link]]**.

## Where
- In an **AWS VPC** across **multiple Availability Zones (AZs)**.
- Supports **on-premises** connections via AWS Direct Connect or VPN.

## Why
- **Resilience:** Automatic failover across **Availability Zones**.
- **Static IP Support:** Ensures a fixed **public or private IP** for clients.
- **AWS PrivateLink Integration:** Allows exposing services securely.

## Related Services/Resources
- [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/private-link\|private-link]]
- direct-connect
- site-to-site-vpn

## References
- [AWS Network Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-monitoring.html)

