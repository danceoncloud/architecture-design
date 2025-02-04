---
{"dg-publish":true,"permalink":"/aws/vpc/design-cases/a-simple-public-subnet/"}
---

**User Case**: a simple public subnet allowing traffic with the internet
**Components**: [[aws/vpc/atomic-elements/subnet\|subnet]]  [[aws/vpc/atomic-elements/route-table\|route-table]]  [[aws/vpc/atomic-elements/internet-gateway\|internet-gateway]]

![Public Subnet.png](/img/user/aws/vpc/png/Public%20Subnet.png)

**Security**
Security of EC2 is controlled by [[aws/vpc/atomic-elements/security-group\|security-group]].
Security of Subnet is controlled by [[aws/vpc/atomic-elements/network-acls\|network-acls]].