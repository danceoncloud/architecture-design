---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/site-to-site-vpn/","title":"Site-to-Site VPN"}
---

![Site-to-Site VPN.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Atomic-Elements/Site-to-Site%20VPN.png)
## What
AWS Site-to-Site VPN enables secure, encrypted connections between your on-premises network and Amazon VPC (Virtual Private Cloud) over the public internet.

>[!info] Key Concepts
>**VPN tunnel**: an encrypted link between on-premises and AWS VPC.
>**VPN Connection**: a secure connection between your on-premises equipment and your VPCs. Each connection includes **TWO** VPN tunnels for high availability.\
>**Virtual Private Gateway**: VPN endpoint on AWS side of VPN connection, attached to single VPC. only support IPv4. \
>**Transit Gateway**: VPN endpoint on AWS side of VPN connection, used to interconnect multiple VPCs. support IPv4 and IPv6. \
>**Customer Gateway**: virtual representation of On-Premises created in AWS as VPN endpoint.\
>**Customer Gateway Device**: physical device or application on On-Premises side for VPN connection.

### Tunnel Endpoint Replacements
One or both tunnel endpoints could be replace when AWS performs tunnel updates or when you modify your VPN connection.
>[!info] [Endpoint Replacements](https://docs.aws.amazon.com/vpn/latest/s2svpn/endpoint-replacements.html)
>**Customer initiated replacements** may cause the unavailability of both tunnels for most of modifications.
>**AWS initiated replacements** applies to one tunnel at a time, the VPN connection may experience a brief loss of redundancy.
>**Lifecycle Control** can be used to schedule the replacement for better business needs.

### Acceleration of VPN connection with Transit Gateway
- This kind of VPN connection uses AWS Global Accelerator to route traffic from On-Premises to AWS edge location closest to your customer gateway device.
- This connection uses a separate IP address pool for the tunnel endpoint IP, so you must create new connection, instead of modifying existing VPN connection.

### [Route Table and Route Priority](https://docs.aws.amazon.com/vpn/latest/s2svpn/vpn-route-priority.html)
1. A route must be configured to point to virtual private gateway.
2. Tunnel that is available is selected in case of failure of another tunnel.
3. Local route is preferred over propagated routes, no matter longest prefix match.
4. Local route is preferred over propagated routes, for same CIDR.

## When
**Hybrid Cloud Connectivity**: securely extend on-premises data centers to AWS VPCs.
**Disaster Recovery**: establish back VPN tunnels for failover during **AWS Direct Connect** outages.
**Temporary Environments**: secure short-term connections for development/testing.

## Why
**Secure Data Transfer**: encrypt sensitive data over the internet.
**Compliance**: meet regulatory requirements with encrypted tunnels.
**Cost-Effective Connectivity**: avoid upfront costs of AWS Direct Connect.


>[!info] **Virtual Private Gateway** can be used to establish communications between multiple on-premises data centers.
>1. every customer gateway has its unique public IP and BGP ASN.
>2. dynamically routed site-to-site VPN connection from each customer gateway to virtual private gateway
>3. advertise site-specif prefix to virtual private gateway.
>![Site-to-Site VPN for Multiple On-Premises.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Atomic-Elements/Site-to-Site%20VPN%20for%20Multiple%20On-Premises.png)

## Related Services/Resources
[[aws/Networking-Content-Delivery/VPC/Atomic-Elements/direct-connect\|direct-connect]]  

## References
- [Source of information or documentation link]
