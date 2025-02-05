---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/vpc-peering/"}
---


Allows private one-to-one communications between VPCs through AWS global backbone network.

VPCs can reside in different AWS regions or from different AWS accounts.

Using [[aws/vpc/atomic-elements/route-table\|route-table]] and [[aws/vpc/atomic-elements/security-group\|security-group]]  for traffic flow.


![VPC Peering.png](/img/user/aws/vpc/png/VPC%20Peering.png)


**Non-transitive**

If **VPC A is peered with VPC B, and VPC B is peered with VPC C**, **VPC A cannot talk to VPC C** without dedicated vpc peering connection.