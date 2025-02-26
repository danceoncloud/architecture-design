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
2. private subnet: has no direct route to [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/internet-gateway\|internet-gateway]]; requires [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/nat-gateway\|nat-gateway]] for public internet
3. VPN-only subnet: has route to [[aws/Networking-Content-Delivery/VPC/excalidraw/Atomic-Elements/Site-to-Site VPN\|Site-to-Site VPN]] through [[virtual private gateway\|virtual private gateway]]
4. Isolated subnet: has no route to outside of its vpc.


#### **Public Subnet**


![Public Subnet.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Public%20Subnet.png)
#### **Private Subnet**
![Private Subnet.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Private%20Subnet.png)