---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/private-link/","title":"Private Link"}
---

![Private Link.png](/img/user/aws/vpc/png/atomic-elements/Private%20Link.png)
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
- for cross-region access, choose [[aws/vpc/atomic-elements/vpc-peering\|vpc-peering]], [[aws/vpc/atomic-elements/transit-gateway-peering\|transit-gateway-peering]], or deploy service to multiple regions.

## Why
- **Enhanced Security**: Traffic stays within the AWS network, reducing DDoS/sniffing risks.  
- **Simplified Architecture**: No need for NAT gateways/public IPs.  
- **Cost Savings**: Reduces data transfer costs (no public internet traffic).  
- **Compliance**: Meets private connectivity requirements for finance/healthcare industries.

## Related Services/Resources
[[aws/vpc/atomic-elements/network-load-balancer\|network-load-balancer]] 
[[aws/vpc/atomic-elements/gateway-load-balancer\|gateway-load-balancer]]



## References
- [AWS Private Link](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html)
