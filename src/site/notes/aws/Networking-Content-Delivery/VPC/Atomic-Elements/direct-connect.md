---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/vpc/atomic-elements/direct-connect/","title":"Direct Connect"}
---

## What
AWS Direct Connect links your internal network to an AWS over a standard Ethernet fiber-optic cable through AWS Direct Connect Location. 

>[!info] Key Components: AWS Side
>**Virtual Private Gateway(VGW)**: bridge between On-Premises and private subnet on AWS. attached to single VPC.\
>**Virtual Interface(VIF)**:
>>Public VIF: connect to AWS public services (S3, DynamoDB, etc).\
>>Private VIF: connect to your VPC using private IP address.\
>>Transit VIF: connect to AWS Transit Gateway.
>
>**Direct Connect Gateway**: connect to multiple VPCs of different regions through a single Direct Connect connection.

>[!important] Key Components: AWS Direct Connect
>**Direct Connect Location**: physical facilities to establish dedicated network connection to AWS. \
>**Direct Connection Port**: physical port assigned to your connection, available on 1/10/100/400 Gbps for dedicated connection and 50-500Mbps for hosted connection.\
>**Border Gateway Protocol(BPG)**: dynamic routing protocol used to exchange routes between AWS and On-Premises.\
>**Autonomous System Number(AS Number)**: unique identifier for your network in BGP.
>> *Public AS Number*: assigned by IANA for internet routing. \
>> *Private AS Number*: reserved for internal use and can be used in private BGP configurations. 
>
>**Letter of Authorization(LOA-CFA)**: document provided by AWS to authorize the establishment of connection.\
>**Link Aggregation Group**: combine multiple Direct Connect connections for higher bandwidth and redundancy.\
>**Jumbo Frames**: larger MTU(up to 9001 bytes) for improved network efficiency over direct connect.

>[!example] Key Components: On-Premises Side
>**On-Premises Router/Firewall**: handle traffic between AWS and On-Premises. must support **BGP** for dynamic routing with AWS.

![Direct Connect Summary.png](/img/user/aws/Networking-Content-Delivery/VPC/png/Atomic-Elements/Direct%20Connect%20Summary.png)



## Related Services/Resources
[[aws/Networking-Content-Delivery/VPC/Atomic-Elements/direct-connect-bgp-protocol\|direct-connect-bgp-protocol]]
  
## References
[AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
