---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/cloud-front/content-delivery/"}
---


![Content Delivery Diagram.png](/img/user/aws/Networking-Content-Delivery/CloudFront/Content%20Delivery%20Diagram.png)
## What
CloudFront is used to deliver contents globally with optimal user experience and customized control on query process.

Core Elements/Services:
1. **Content Origin**: AWS S3, Elastic Load Balancer, API Gateway, Mediastore Container, Mediapackage Container, Mediapackage V2 Endpoints, VPC Origins.
2. **Distribution**: configuration on how CloudFront access to and get content from Origin, may have **any combination of Up To 25 origins** per distribution.
3. **Edge Location**: also called Points-of-Presence, are global data centers managed by AWS, cache storage is small.
4. **Regional Edge Caches**: a secondary cache layer with larger cache size.
5. **Origin Shield**: last cache layer in front of Origin, created in the same or closest region to origin.

### What can be done through Distribution Configuration
1. Enable usage of Origin Shield
2. Configure routing pattern for different origins
3. HTTP/HTTPS behavior: allow, refuse, redirect with chosen actions to be allowed
4. Configure trusted authorization with signed URL/cookies
5. Enable Amazon WAF

>[!warning] Signed URL/Cookies
>1. Content owner create a pair of public/private key, upload public key to cloudfront to configure trust key group
>2. User must authenticate to obtain signed URL or cookies encrypted by private key.
>3. Content owner offers application that can respond to authenticated user with signed URL or cookies

![Distribution Configuration.png](/img/user/aws/Networking-Content-Delivery/CloudFront/Distribution%20Configuration.png)

  
## References
[AWS CloudFront Content Delivery](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-working-with.html)
