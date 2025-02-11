---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/gateway-load-balancer/","title":"Gateway Load Balancer"}
---

![Gateway Load Balancer.png](/img/user/aws/vpc/png/atomic-elements/Gateway%20Load%20Balancer.png)

## What
- A managed service for deploying, scaling, and monitoring **third-party virtual appliances** (e.g., firewalls, intrusion detection systems).
- Acts as a gateway to transparently route traffic through appliances for inspection or processing.

>[!info] Key Components
>**Load Balancer**: It listens for all IP packages across all ports and forwards to target group using **GENEVE protocol on port 6081**
>**Target Group**:  Instance or IP address  
>**Listener**: listen for all IP packages across all ports


## When
- **Security Enforcement**: Inline traffic inspection (e.g., malware scanning).
- **Compliance**: Meeting regulatory requirements (e.g., **HIPAA**, **PCI-DSS**).
- **Hybrid Architectures**: Integrating on-premises appliances with AWS workloads.

## Where
- In a **VPC**, using GLB endpoints to redirect traffic flows to GLB
- Supports **cross-account** and **cross-VPC** traffic routing.

## Why
- **Simplified Management**: Automates scaling, availability, and maintenance of appliances.
- **Cost-Effective**: Pay only for the GLB capacity units used.
- **Seamless Integration**: Works with AWS Marketplace appliances (e.g., Check Point, Fortinet) or custom solutions.


## Related Services/Resources
[[aws/vpc/atomic-elements/vpc-endpoint\|vpc-endpoint]]
  
## References
[AWS Gateway Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/gateway/introduction.html)

