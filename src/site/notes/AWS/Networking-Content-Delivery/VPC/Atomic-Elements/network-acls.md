---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/network-acls/","title":"Network ACLs"}
---



**STATELESS** firewalls applied at **[[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/subnet\|subnet]] level**, both inbound and outbound traffic should be allowed.
Ordered Rules are processed from lowest number to highest.
Allows all inbound/outbound by default.
Only one NACLs can be applied to a Subnet at a time.
![Network ACLs.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Network%20ACLs.png)
