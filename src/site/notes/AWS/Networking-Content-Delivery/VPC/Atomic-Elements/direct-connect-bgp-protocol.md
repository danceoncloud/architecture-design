---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/direct-connect-bgp-protocol/","title":"Direct Connect BGP Protocol"}
---

## What
**Border Gateway Protocol** is routing protocol for establishing and maintaining the exchange of network path information to determine how traffic flows between AWS and On-Premises.

>[!info] Key Components
>**Autonomous System Number**: identify your network and AWS.
>>AWS uses by default 64512 from range of 64512-65534. 
>
>**BGP Peer IPs**: used to establish BGP session between AWS and On-Prem (for example AWS: 169.254.255.1, On-Prem: 169.254.255.1). \
>**BGP Communities Tags**: control route propagation. to all regions or to specific region, etc. \
>**Equal-Cost Multi-Path (ECMP)**: allows multiple paths with same cost (BGP attributes) to be used simultaneously for load balancing. \
>**AS_PATH**: Autonomous System Path Length, represents the sequence of ASNs a route traverses, shorter paths are preferred. \
>**Multi-Exit Discriminator (MED)**: is a BGP attribute that influences route preference between different entry points, lower values are preferred.
## How and Why
**Public VIF with 8x00 and 9x00**: public VIFs connect to AWS public services that are global, so AWS uses 8x00 and 9x00 to control geographic propagation of public IP routes.
![Direct Connect BGP Public Tags Assignment.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Direct%20Connect%20BGP%20Public%20Tags%20Assignment.png)


**Private/Transit VIF with 7x00**: routes through these interface are already region-bound, so tags are used for load balancing, failover or traffic engineering.
>[!info] Understanding 7x00
>BGP community tags of 7224:7100/7200/7300 are configured at On-Prem router to influence traffic path originating from AWS.
>1. configure at On-Premise
>2. advertise to AWS router
>3. AWS choose traffic path according to received tags, 7300 is most preferred and 7100 is least preferred.

### Route Path Engineering

1. **Longest Prefix length** is evaluated at first by AWS to choose route path for outbound traffics.
2. **BGP Local Preference** is recommended way for equal length of prefix.
3. **BGP AS Path Prepending** is used if prefix length and local preference are the same.
4. **Multi-Exit Discriminator (MED)** can be used if prefix length, local preference and AS_PATH are the same.
5. **Equal-cost Multi-path (ECMP)** is used to across multiple transit or private virtual interface when prefixes have the same AS_PATH length and BGP attributes.

**Load Balancing (Active/Active)**, **Failover (Active/Passive)** and **Route Filtering** can be achieved with these features.
![Direct Connect BGP Private Tags Assignment.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Direct%20Connect%20BGP%20Private%20Tags%20Assignment.png)














