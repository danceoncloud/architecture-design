---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/internet-gateway/","title":"Internet Gateway","tags":["internet-gateway"]}
---

<br>

It is a VPC component that allows communication between VPC and the internet.

It allows traffic to/from internet.

Instance always has private IP address and it must have [[AWS/Networking-Content-Delivery/VPC/Atomic-Elements/public-ipv4-address\|public-ipv4-address]] (static or dynamic) to enable communication over the internet.

Internet Gateway applied Network Address Translate(NAT) between private and public/elastic ip address.

Outgoing traffics coming from NAT Gateway does not need NAT at IGW, since it's already done by NAT Gateway.

![Internet Gateway and NAT.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/Internet%20Gateway%20and%20NAT.png)