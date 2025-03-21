---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/architectures/hybrid-network-architecture-between-aws-and-on-premises/"}
---

**Use Case**: Build dedicated, private network connection between on-premises infrastructure and AWS, offering consistent low latency, higher bandwidth reliability, and enhanced security by bypassing the public internet.

**Component**:
[[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/direct-connect\|direct-connect]]  [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/site-to-site-vpn\|site-to-site-vpn]]

## Major Use Cases
#### Direct Connect as Primary + VPN as Backup (Active/Passive)
**benefits**: high availability, cost-effective
**key points**: use **BGP** to advertise routes, assign higher **BGP** priority to Direct Connect routes. 
<br>
#### Direct Connect + VPN for Encryption
**benefits**: combine the speed of Direct Connect with VPN's encryption, meet strict compliance requirements.
**key points**: encrypt data in transit over Direct Connect with IP Sec VPN.
<br>
#### Direct Connect + VPN via Transit Gateway (Scalable Multi-VPC)
**benefits**: simply multi-account/multi-VPC architectures, reduce operational overhead.
**key points**: transit gateway route table propagate routes between VPCs, Direct Connect and VPN. TGW Network Manager for centralized monitoring.
<br>
#### Multi-Region Direct Connect + VPN (Global Resilience)
**benefits**: disaster recovery, geographic redundancy for mission-critical workloads.
**key points**: deploy Direct Connect and VPN to multiples regions, configure **BGP** community tags to prioritize regional routes.
<br>
![Hybrid Network Architecture between AWS and On-Premises.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Hybrid%20Network%20Architecture%20between%20AWS%20and%20On-Premises.png)