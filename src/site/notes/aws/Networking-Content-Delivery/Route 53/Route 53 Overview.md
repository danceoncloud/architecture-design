---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/route-53-overview/","title":"Route 53 Overview"}
---

## What
Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service.


## When
>[!info] Main Functions as DNS service
>**Register Domain Names**: map domain name with IP addresses \
>**Route Internet Traffic to Resources for your Domain**: connect browser with your website/application \
>**Check the Health of your Resources**: verify the reach-ability, availability and functionality of your services 

>[!info] Other Features other than DNS
>**Route 53 Resolver**: responds recursively to DNS queries from AWS resources \
>**Route 53 Resolver on Outposts**: offer DNS resolution between on-premises environments and AWS cloud resources. \
>**Route 53 Resolver Firewall**: protect your recursive DNS queries within the Route 53 Resolver \
>**Traffic Flow**: easy-to-use and cost-effective global traffic management \
>**Route 53 Profiles**: apply and manage DNS-related Route 53 configurations across many VPCs and in different AWS account.


## Where
- Route 53 operates Globally across AWS's worldwide network.
- Integrates with AWS services (CloudFront, S3) and external endpoints.

## Why
- **High Availability**: Ensures minimal downtime with automated failover.
- **Advanced Routing Policies**:
	- _Latency-based_: Directs traffic to the lowest-latency region.
    - _Geolocation_: Routes users based on location.
    - _Weighted_: Distributes traffic across multiple endpoints.


## References
- [AWS Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)

