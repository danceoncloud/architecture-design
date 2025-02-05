---
{"dg-publish":true,"permalink":"/aws/vpc/design-cases/a-simple-private-subnet-with-ec-2-and-rds/"}
---

**Use Case**: a simple private subnet with AWS services inside talking to each other. 
**Components**: [[aws/vpc/atomic-elements/subnet\|subnet]]  [[aws/vpc/atomic-elements/route-table\|route-table]] 


![Private Subnet.png](/img/user/aws/vpc/png/Private%20Subnet.png)
**Security**
Security of EC2 is controlled by [[aws/vpc/atomic-elements/security-group\|security-group]].
Security of Subnet is controlled by [[aws/vpc/atomic-elements/network-acls\|network-acls]].

