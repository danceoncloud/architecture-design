---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/register-and-manage-domain-name/","title":"Register and Manage Domain Name"}
---

![Register Domain.png](/img/user/aws/Networking-Content-Delivery/Route%2053/excalidraw/Register%20Domain.png)
## What
Route 53 provides services to register domain name or transfer domain name from other registrar or between AWS accounts.

>[!important] Important to Know
>**[[aws/Networking-Content-Delivery/Route 53/Atomic-Elements/hosted-zone\|hosted-zone]]**: a container for records to map IP addresses to your domain and sub-domains. hosted zone has the same name as the domain.


>[!example] DNS Recursive Lookup
>**Root Name Server**: managed by ICANN to keep records of **TLD name server**, *.com, .org, .fr* \
>**TLD Name Server**: managed by **Registry** to keep records of **Second Level Domain name server**, like *example.com* \
>**Second Level Domain Name Server**: managed by AWS or GoDaddy or other company, for records like *www.example.com* \
>**Registrar**: domain reseller between registrant and **Registry**, is responsable for notifying **Registry** about domain registration/modification.
![DNS Recursive Lookup.png](/img/user/aws/Networking-Content-Delivery/Route%2053/excalidraw/DNS%20Recursive%20Lookup.png)

>[!WARNING] **Domain Lock Status**
> By default, Route 53 enables a **registrar lock** to prevent unauthorized transfers. Keep this enabled unless transferring.
### **Transfer-Specific Considerations**
- **Authorization Code (EPP Code)**: Required for transferring domains between accounts or registrars. AWS automatically generates and manages this, but confirm it’s accessible if needed.
- **AWS Account Ownership**: The domain is tied to the AWS account that registered it. To transfer it to another AWS account:
    - You must **initiate the transfer** from the **source account**.
    - The destination account must accept the transfer.    
- **60-Day Transfer Lock**: AWS imposes a 60-day lock after registration or ownership changes to prevent fraud.


  
## References
[AWS Register and Manage Domains](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar.html)



