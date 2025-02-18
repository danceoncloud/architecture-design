---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/cloud-front/cloud-front-overview/"}
---


## What
CloudFront is a **Content Delivery Network (CDN)** designed to **accelerate content delivery** to end-users globally.

>[!info] Content Delivery
>**Content Origin**:  original location from which CDN gets files to distribute. \
>**Distrubtion**: configuration which defines how CDN delivers the content. \
>**Cache and Edge Location**: Edge Locations are close to user to reduce latency, popular contents are cached on Edge Location to further improve content delivery speed. \
>**Regional Edge Caches**: Larger Cache facilities at Region level, to cache less popular content and offer much larger cache capacity then Edge Location. \
>**TTL**: time-to-live for content in cache, shorter TTL to serve dynamic content and longer to serve the content faster. 

>[!abstract] Content and Server Availability
>**Origin Failover**: composed of primary and secondary origins, Cloud Front fetches from whichever is available. \
>**Origin Shield**: cache layer in front of origin, consolidates queries for the same object to single query to origin server. \
>**Cache-Control Header**: offers **Stale-if-error** and **Stale-while-revalidate** to improve content availability in the cache. \
>**Connection Time**: increase for origins that is slow to response. \
>**Keep Alive Settings**: enable to keep persistent connection alive and to reduce overhead to establish new connection. \
>**ALB as Origin and Lambda@Edge**: route traffics to available origins or customize behaviors/responses through Lambda functions. 

>[!warning] Security
>**Access Control and Authentication**: Signed URLs, Signed Cookies, Origin Access Identity, Origin Access Control, Geo Restriction \
>**Encryption and HTTPs**: HTTPs configuration, SSL/TLS certification, Field-Level encryption \
>**Network Protection**: AWS WAF Integration, AWS Shield Integration, Custom Headers \
>**Access Control at Edge**: Lambda@Edge, Cloudfront Functions \
>**Logging, Monitoring and Compliance**: Real-Time logs, Cloudwatch Integration, Compliance Certifications

## Related Services/Resources
- [[aws/Networking-Content-Delivery/CloudFront/Content Delivery\|Content Delivery]]
- [[aws/Networking-Content-Delivery/CloudFront/Content and Server Availability\|Content and Server Availability]]

## References
[AWS CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)