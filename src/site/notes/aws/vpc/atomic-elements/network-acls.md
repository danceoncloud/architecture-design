---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/network-acls/"}
---



**STATELESS** firewalls applied at **[[aws/vpc/atomic-elements/subnet\|Subnet]] level**, both inbound and outbound traffic should be allowed.
Ordered Rules are processed from lowest number to highest.
Allows all inbound/outbound by default.
Only one NACLs can be applied to a Subnet at a time.
![Network ACLs.png](/img/user/aws/vpc/png/Network%20ACLs.png)
