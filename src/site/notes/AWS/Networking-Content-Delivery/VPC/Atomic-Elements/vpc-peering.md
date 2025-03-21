---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/vpc-peering/","title":"VPC Peering"}
---



Allows private one-to-one communications between VPCs through AWS global backbone network.

VPCs can reside in different AWS regions or from different AWS accounts.

Using [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/route-table\|route-table]] and [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/security-group\|security-group]]  for traffic flow.


![VPC Peering.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/VPC%20Peering.png)


**Non-transitive**

If **VPC A is peered with VPC B, and VPC B is peered with VPC C**, **VPC A cannot talk to VPC C** without dedicated vpc peering connection.