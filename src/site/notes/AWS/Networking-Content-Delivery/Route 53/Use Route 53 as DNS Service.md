---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/use-route-53-as-dns-service/","title":"Use Route 53 as DNS Service"}
---

## What
when using Route 53 as DNS service, route 53 will route internet traffics to your website by translating domain name to IP address, or privately between VPCs.

>[!info] Important
>**[[AWS/Networking-Content-Delivery/Route 53/Atomic-Elements/hosted-zone\|hosted-zone]]**: a container for records to map IP addresses to your domain and sub-domains. hosted zone has the same name as the domain.
>**[[AWS/Networking-Content-Delivery/Route 53/Atomic-Elements/routing-policy\|routing-policy]]**: determine how Route 53 responses to queries \
>**[[AWS/Networking-Content-Delivery/Route 53/DNSSEC Trust Chain\|aws/Networking-Content-Delivery/Route 53/DNSSEC Trust Chain]]**: validate Route 53 responses \
>**public hosted zone**: internet-facing \
>**private hosted zone**: used inside VPC \
>**Alias Record**: Route 53-specific record type for AWS resources \
>**CNAME Record**: standard record for non-AWS domain, or a sub-domain alias

>[!example] DNS Recursive Lookup
>**Root Name Server**: managed by ICANN to keep records of **TLD name server**, *.com, .org, .fr* \
>**TLD Name Server**: managed by **Registry** to keep records of **Second Level Domain name server**, like *example.com* \
>**Second Level Domain Name Server**: managed by AWS or GoDaddy or other company, for records like *www.example.com* \
>**Registrar**: domain reseller between registrant and **Registry**, is responsable for notifying **Registry** about domain registration/modification.
![DNS Recursive Lookup.png](/img/user/AWS/Networking-Content-Delivery/Route%2053/excalidraw/DNS%20Recursive%20Lookup.png)


>[!info]- Public Hosted Zone
>- Used for public DNS resolution (internet-facing)
>- Key considerations:
>>- One domain can have only one public hosted zone
>>- Can be accessed from anywhere on the internet
>>- Cannot resolve private/internal resources directly
>>- Supports all Route 53 routing policies

>[!info]- Private Hosted Zone
>- Used for internal DNS resolution within VPCs
>- Key considerations:
>>    - Must be associated with specific VPCs
>>    - Can only be accessed from associated VPCs
>>    - Can have overlapping domain names
>>    - DNS records only resolve within associated VPCs
>>    - Limited support for routing policies (no geolocation or latency-based)

>[!warning]- DNSSEC
>- Protects against DNS spoofing/cache poisoning
>- Verifies DNS responses are authentic
>- Ensures data integrity
>- Only available for **public hosted zones**

## References
[AWS Use Route53 as DNS Service](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring.html)
