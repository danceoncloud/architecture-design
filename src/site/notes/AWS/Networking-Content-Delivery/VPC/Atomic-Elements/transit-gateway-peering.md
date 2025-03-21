---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/transit-gateway-peering/","title":"Transit Gateway Peering"}
---

Transit Gateway Peering is used to connect transit gateway in **different regions**.

**Components**:
[[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/transit-gateway\|transit-gateway]] 

Things to remember: 
1. Create dedicated route table and associate with Peering attachment, add **Static Route** pointing to the other side of TGW.
2. add **Static Route** to route table of VPC attachment pointing to the other side of TGW.

![Transit Gateway Peering.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Transit%20Gateway%20Peering.png)