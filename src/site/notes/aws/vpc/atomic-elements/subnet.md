---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/subnet/"}
---

## A subnet is a range of IP addresses in your VPC.

One subnet resides in a single Available Zone, one AZ can have multiple subnets.

### Subnet Sizing

IPv4 CIDR block size for a subnet is between /28 netmask and /16 netmask.
The first 4 ip address and the last IP address in each subnet are reserved by AWS.

### Subnet types:
1. public subnet: has direct route to internet gateway
2. private subnet: has no direct route to [[aws/vpc/atomic-elements/internet-gateway\|internet-gateway]]; requires [[aws/vpc/atomic-elements/nat-gateway\|nat-gateway]] for public internet
3. VPN-only subnet: has route to [[aws/vpc/atomic-elements/Site-to-Site VPN\|Site-to-Site VPN]] through [[virtual private gateway\|virtual private gateway]]
4. Isolated subnet: has no route to outside of its vpc.


#### **Public Subnet**


![Public Subnet.png](/img/user/aws/vpc/png/Public%20Subnet.png)
#### **Private Subnet**
![Private Subnet.png](/img/user/aws/vpc/png/Private%20Subnet.png)