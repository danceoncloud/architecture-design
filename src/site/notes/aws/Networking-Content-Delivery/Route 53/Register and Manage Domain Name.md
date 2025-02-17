---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/register-and-manage-domain-name/","title":"Register and Manage Domain Name"}
---

![Register Domain.png](/img/user/aws/Networking-Content-Delivery/Route%2053/excalidraw/Register%20Domain.png)
## What
Route 53 provides services to register domain name or transfer domain name from other registrar or between AWS accounts.


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



