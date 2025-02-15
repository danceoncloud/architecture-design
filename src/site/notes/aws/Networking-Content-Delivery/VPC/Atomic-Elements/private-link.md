---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/private-link/","title":"Private Link"}
---

![Private Link.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Atomic-Elements/Private%20Link.png)
# AWS Private-Link

## What
PrivateLink enables private connectivity across VPCs, accounts, and regions **without traversing the public internet, VPN, or Direct Connect**.
In Reality, we refer to following services backed by private link.



> [!info] Key Components:
>- **Endpoints (Consumer side)**: 
>>- Interface endpoint 
>>- Gateway Endpoint: ONLY for S3 and DynamoDB access, and **Private Link is NOT used**
>>- Gateway Load Balancer Endpoint
>- **Endpoint services (Provider side)**: 
>>- Network Load Balancer
>>- Gateway Load Balancer



## When
- Securely access third-party services (avoid public exposure).  
- Share internal services across accounts (e.g., data lake query APIs).  
- Access AWS services in hybrid cloud setups (e.g., S3, DynamoDB).

## Where
- both endpoints and endpoint services should be in the same AWS region.
- for cross-region access, choose [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/vpc-peering\|vpc-peering]], [[aws/Networking-Content-Delivery/VPC/Atomic-Elements/transit-gateway-peering\|transit-gateway-peering]], or deploy service to multiple regions.

## Why
- **Enhanced Security**: Traffic stays within the AWS network, reducing DDoS/sniffing risks.  
- **Simplified Architecture**: No need for NAT gateways/public IPs.  
- **Cost Savings**: Reduces data transfer costs (no public internet traffic).  
- **Compliance**: Meets private connectivity requirements for finance/healthcare industries.

## Related Services/Resources
[[aws/Networking-Content-Delivery/VPC/Atomic-Elements/network-load-balancer\|network-load-balancer]] 
[[aws/Networking-Content-Delivery/VPC/Atomic-Elements/gateway-load-balancer\|gateway-load-balancer]]



## References
- [AWS Private Link](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)
