---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/atomic-elements/hosted-zone/","title":"Hosted Zone"}
---

## What
A **hosted zone** in AWS Route 53 is a **container for DNS records** that define how a domain name resolves to IP addresses or AWS resources.

**Type of Records**:

| **Record Type** | **Purpose** | **Example** | **Created By** |
|---------------|-------------|------------|--------------|
| **NS (Name Server)** | Lists authoritative name servers for the domain | `example.com. NS ns-123.awsdns-01.net.` | ✅ Auto |
| **SOA (Start of Authority)** | Metadata about the hosted zone (primary NS, refresh time) | `example.com. SOA ns-123.awsdns-01.net.` | ✅ Auto |
| **A (Address Record)** | Maps a domain to an IPv4 address | `example.com. A 192.0.2.44` | 🔹 Manual |
| **AAAA (IPv6 Address)** | Maps a domain to an IPv6 address | `example.com. AAAA 2001:db8::ff00:42:8329` | 🔹 Manual |
| **CNAME (Canonical Name)** | Creates an alias from one domain to another | `www.example.com. CNAME example.com.` | 🔹 Manual |
| **MX (Mail Exchange)** | Specifies mail servers for email routing | `example.com. MX 10 mail.example.com.` | 🔹 Manual |
| **TXT (Text Record)** | Stores verification data (SPF, DKIM, ownership verification) | `example.com. TXT "v=spf1 include:_spf.google.com ~all"` | 🔹 Manual |
| **ALIAS (AWS-Specific)** | Maps domain to AWS resources (CloudFront, S3, ELB) | `example.com. ALIAS d111111abcdef8.cloudfront.net.` | 🔹 Manual |


```
example.com.  NS  
ns-123.awsdns-01.net.  
ns-456.awsdns-02.org.  
ns-789.awsdns-03.co.uk.  
ns-101.awsdns-04.com.  

example.com.  SOA  
ns-123.awsdns-01.net. hostmaster.awsdns.com. 2024021301 7200 900 1209600 86400  

example.com.  A  
192.0.2.44  

www.example.com.  CNAME  
example.com.  

example.com.  MX  
10 mail.example.com.  

example.com.  TXT  
"v=spf1 include:_spf.google.com ~all"  
```
## When
- Managing DNS for an existing domain
- Routing traffic to AWS services
- Creating subdomains
- Hybrid DNS resolution (Private Hosted Zone)

### Types of hosted zones:
1. Public hosted zones
    - For domains accessible from the internet
    - Used for public-facing websites and applications
2. Private hosted zones
    - For internal DNS resolution within VPCs
    - Not accessible from the public internet
    - Used for internal applications/services


## Related Services/Resources
[[aws/Networking-Content-Delivery/Route 53/Route 53 Overview\|Route 53 Overview]]
  
## References
- [Source of information or documentation link]
