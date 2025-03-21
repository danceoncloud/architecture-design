---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/nat-gateway/","title":"Nat Gateway"}
---

NAT gateway allows internet access from private subnet, through internet gateway.

They ONLY allow **outgoing** requests and responses of these requests.

only for IPv4 traffic.

Private IP of instance will be replaced by Elastic IP of NAT device.

#NAT_Gateway
AWS-managed Network Address Translate service.
NAT gateway is created in availability zone.
#### Public NAT Gateway

![NAT Gateway.png](/img/user/AWS/Networking-Content-Delivery/VPC/png/Atomic-Elements/NAT%20Gateway.png)


#NAT_Instance
User-managed Network Address Translate service on EC2.
Not recommended except for cost saving and non-critical usage.