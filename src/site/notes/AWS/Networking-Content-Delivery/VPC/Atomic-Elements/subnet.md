---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/subnet/","title":"Subnet"}
---

## A subnet is a range of IP addresses in your VPC.

One subnet resides in a single Available Zone, one AZ can have multiple subnets.

### Subnet Sizing

IPv4 CIDR block size for a subnet is between /28 netmask and /16 netmask.
The first 4 ip address and the last IP address in each subnet are reserved by AWS.

### Subnet types:
1. public subnet: has direct route to internet gateway
2. private subnet: has no direct route to [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/internet-gateway\|internet-gateway]]; requires [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/nat-gateway\|nat-gateway]] for public internet
3. VPN-only subnet: has route to [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/site-to-site-vpn\|site-to-site-vpn]] through virtual private gateway
4. Isolated subnet: has no route to outside of its vpc.


#### **Public Subnet**


![Public Subnet.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Public%20Subnet.png)
#### **Private Subnet**
![Private Subnet.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Private%20Subnet.png)