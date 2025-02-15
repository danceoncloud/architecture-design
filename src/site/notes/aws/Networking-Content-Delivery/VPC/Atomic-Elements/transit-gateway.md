---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/transit-gateway/","title":"Transit Gateway"}
---


central hub routing traffic between VPCs, VPN connections and AWS Direct Connect connections.

**Attachement**: both a source and a destination of traffic. could be VPCs, AWS Direct Connect Gateway, another TGW through peering, VPN
**Transit Gateway Route Table**: route traffics coming from associated attachment to destination CIDR through target Attachment.
for example: requests from VPC A arrive at transit gateway through attachment A, then go to 10.20.0.0/16 through Attachment B.

**Association**: associate this route table with attachment in order to configure routes for  traffics originating from this attachment .

**Route Propagation**: automatically add route to route table and update in case of changement. 

![Transit Gateway.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Atomic-Elements/Transit%20Gateway.png)