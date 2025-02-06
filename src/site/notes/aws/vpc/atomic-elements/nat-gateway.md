---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/nat-gateway/"}
---

NAT gateway allows internet access from private subnet.

They ONLY allow **outgoing** requests and responses of these requests.

only for IPv4 traffic.

Private IP of instance will be replaced by Elastic IP of NAT device.

#NAT_Gateway
AWS-managed Network Address Translate service.
NAT gateway is created in availability zone.
#### Public NAT Gateway

![NAT Gateway.png](/img/user/aws/vpc/png/atomic-elements/NAT%20Gateway.png)


#NAT_Instance
User-managed Network Address Translate service on EC2.
Not recommended except for cost saving and non-critical usage.