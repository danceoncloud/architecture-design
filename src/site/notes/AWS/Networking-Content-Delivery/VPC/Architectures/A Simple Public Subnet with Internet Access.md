---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/architectures/a-simple-public-subnet-with-internet-access/"}
---

**Use Case**: a simple public subnet allowing traffic with the internet
**Components**: [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/subnet\|subnet]]  [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/route-table\|route-table]]  [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/internet-gateway\|internet-gateway]]

![Public Subnet.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Public%20Subnet.png)

**Security**
Security of EC2 is controlled by [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/security-group\|security-group]].
Security of Subnet is controlled by [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/network-acls\|network-acls]].