---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/architectures/a-simple-public-subnet-with-internet-access/"}
---

**Use Case**: a simple public subnet allowing traffic with the internet
**Components**: [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/subnet\|subnet]]  [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/route-table\|route-table]]  [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/internet-gateway\|internet-gateway]]

![Public Subnet.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Public%20Subnet.png)

**Security**
Security of EC2 is controlled by [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/security-group\|security-group]].
Security of Subnet is controlled by [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/network-acls\|network-acls]].