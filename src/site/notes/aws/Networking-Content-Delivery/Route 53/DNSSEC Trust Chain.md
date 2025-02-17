---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/dnssec-trust-chain/","title":"DNSSEC Trust Chain"}
---

![DNSSEC Trust Chain.png](/img/user/aws/Networking-Content-Delivery/Route%2053/excalidraw/DNSSEC%20Trust%20Chain.png)
## What
The DNSSEC (DNS Security Extensions) trust chain is a hierarchical cryptographic system that **validates the authenticity and integrity of DNS responses** by linking digital signatures from the root DNS zone down to your domain. It ensures DNS data (e.g., IP addresses) cannot be tampered with or forged.

>[!info] Key Type/Records
>| Key Type / Record                     | Description                                                                                      |
| ------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **KSK (Key Signing Key)**             | Signs the ZSK, ensuring integrity.                                                               |
| **ZSK (Zone Signing Key)**            | Signs actual DNS records to validate them.                                                       |
| **DS (Delegation Signer) Record**     | Hash of child zone’s KSK, stored in the parent zone to create a chain of trust.                  |
| **RRSIG (Resource Record Signature)** | Digital signature attached to DNS records, proving authenticity and integrity.                          |
| **Trust Anchor** | Preconfigured root public key in resolvers. Starts the validation process. |
| **Chain of Trust**                    | Root zone is the trust anchor, and each parent zone signs its child zone to maintain validation. |
| **Validation**                        | DNS resolvers verify records by checking signatures and following the chain from the root down.  |


## References
[AWS Route 53 DNSSEC signing](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring-dnssec.html)