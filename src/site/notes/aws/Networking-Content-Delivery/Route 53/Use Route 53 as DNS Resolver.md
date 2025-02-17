---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/use-route-53-as-dns-resolver/","title":"Use Route 53 as DNS Resolver"}
---


## What
- **Route 53 Resolver** is a virtual service that responds recursively to DNS queries between VPCs, on-premises and the internet (via Inbound/outbound endpoints).
- Route 53 Resolver is VPC level, all subnets share the same VPC resolver. 


>[!info] Key Components/Services
>**Inbound Endpoint**: forward DNS queries from On-Premises Resolver to your Route 53 resolver via this endpoint.
>**Outbound Endpoint**: forward DNS queries from your VPCs to your On-Premises DNS resolver or other Resolver. via this endpoint

>[!warning] Attention!
>Post-Creation of Outbound Endpoint:
>**private IP of subnet** will be used as Source IP when traffic leaves subnet and pass through outbound endpoint, so check followings:
>>Security Group of outbound endpoint: allow **UDP/TCP port 53 outbound** \
>>Network ACLs of Subnet: allow UDP/TCP port 53 for outbound, allow on-premises DNS server ip for inbound \
>>Subnet Route Table pointing to VPN or Direct Connect virtual interface \
>>On-Premises Firewall/Security Configuration


![Route 53 Resolver-Outbound.png](/img/user/aws/Networking-Content-Delivery/Route%2053/excalidraw/Route%2053%20Resolver-Outbound.png)
## When and Why

| **Scenario**                             | **Use Route 53 Resolver?** | **Why?**                                          |
| ---------------------------------------- | -------------------------- | ------------------------------------------------- |
| Default AWS VPC DNS resolution           | ✅ Yes                      | Built-in for resolving public & private domains.  |
| Hybrid cloud DNS (on-prem <-> AWS)       | ✅ Yes                      | Supports inbound & outbound DNS forwarding.       |
| Multi-VPC private hosted zone resolution | ✅ Yes                      | Enables DNS without requiring VPC peering.        |
| Forwarding DNS queries to custom servers | ✅ Yes                      | Custom rules for domain-based forwarding.         |
| Centralized DNS logging & monitoring     | ✅ Yes                      | Supports query logging for security & compliance. |

## Where
**Route 53 resolver** is created in VPC, at VPC+2 IP address. 
A minimum of 2 subnets are required to assure availability and avoid traffics bottleneck, since the traffics can use any subnet to reach the endpoint.
  
## References
[AWS Route 53 Resolver](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html)
