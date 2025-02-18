---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/cloud-front/content-and-server-availability/"}
---

> [!info] Content Availability Facilities:
>**Edge Locations (Points-of-Presence)**: These cache content close to users globally, reducing latency and improving availability even if the origin server experiences issues \
>**Regional Edge Caches**: The secondary cache layer with larger storage capacity that sits between edge locations and origins \
>**Origin Shield**: The last cache layer directly in front of the origin, reducing load on the origin server 

- Edge Locations and Regional Edge caches are managed by AWS, transparent for content owner and content requesters.
- Origin Shield can be enabled by creator of distribution and the closest region to Origin server should be chosen.


>[!important] Content Availability Configuration:
>**Cache Policy**: Control **what** is cached and **how long** it stays cached
>>TTL Settings: **Min TTL, Max TTL, Default TTL** \
>>Cache Key Composition: **Headers** in cache key, **Query strings**, **Cookies** 
>
>**Origin Query Policy**: Control what informations is **forward to** Origin when CloudFront needs to fetch content 
>>Headers Forwarded \
>>Query Strings Forwarded \
>>Cookies Forwarded
>
>**Origin Response Headers**: influence caching
>>Overides: `Cache-Control: max-age=3600` from the origin takes precedence over the Cache Policy’s TTL.
>>Revalidation: CloudFront sends `If-Modified-Since` requests if the cached object is stale.

![Content Cache.png](/img/user/aws/Networking-Content-Delivery/CloudFront/Content%20Cache.png)



> [!example] Origin Server Availability
> **Origin failover**: Configure origin groups with a primary and secondary origin; if the primary fails, CloudFront automatically routes requests to the secondary \
> **Multiple origins**: Up to 25 origins per distribution allows for redundancy and load balancing \
> **Health checks**: CloudFront can be configured to check origin health and route accordingly \
> **AWS Shield/WAF integration**: Protects origins from DDoS attacks and malicious traffic \
> **Elastic Load Balancing**: When using ELB as an origin, it distributes traffic across multiple instances
  
## References
[AWS CloudFront Caching and Availability](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html)
