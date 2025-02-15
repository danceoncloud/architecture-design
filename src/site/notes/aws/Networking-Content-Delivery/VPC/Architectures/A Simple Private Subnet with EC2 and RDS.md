---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/architectures/a-simple-private-subnet-with-ec-2-and-rds/"}
---

**Use Case**: a simple private subnet with AWS services inside talking to each other. 
**Components**: [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/subnet\|subnet]]  [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/route-table\|route-table]] 


![Private Subnet.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Private%20Subnet.png)
**Security**
Security of EC2 is controlled by [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/security-group\|security-group]].
Security of Subnet is controlled by [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/network-acls\|network-acls]].

