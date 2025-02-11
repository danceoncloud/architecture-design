---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/application-load-balancer/","title":"Application Load Balancer"}
---

![Application Load Balancer.png](/img/user/aws/vpc/png/atomic-elements/Application%20Load%20Balancer.png)
## What
- routing **HTTP and HTTPS** traffic to multiple targets, such as EC2 instances, containers, and IP addresses, based on advanced routing rules.

>[!info] Key Components
   >**Load Balancer**: single point of contact for clients
   > **Target Group**:  routes requests to one or more registered targets  
   > **Listener**: checks for connection requests from clients using the port and protocol and determines how to route requests to registered targets. 

## When
- ALB is used when you need advanced routing capabilities like **host-based**, **path-based**, or **query string routing**, and need to manage traffic for HTTP/HTTPS applications. 
- It is ideal for microservices, containerized applications, and serverless architectures

## Where
- ALB is deployed in **AWS regions** within **VPCs**, routing traffic to resources in private or public subnets across multiple availability zones.

## Why
- To achieve **high availability**, **fault tolerance**, **scalability**, and **flexible routing** in web applications.


## Related Services/Resources
- AWS Web Application Firewall 

## References

- [AWS Application Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)




```mermaid

flowchart LR
 %% ===== Security & Public Traffic =====
	Users["Users (Public Internet)"] -- HTTPS --> WAF["AWS WAF (DDoS/OWASP Protection)"]
	WAF --> Internet-facing-ALB["Internet-facing ALB\n(SSL Termination, Redirect HTTP→HTTPS)"]

  %% ===== Host-Based Routing =====
	Internet-facing-ALB -->|"Host: api.example.com"| APIRoute
	Internet-facing-ALB -->|"Host: app.example.com"| AppRoute

 %% ===== API Route (api.example.com) =====
  subgraph API Routing
    APIRoute -->|"/v1/*"| Cognito["Cognito (Auth)"]
    Cognito -->|Authenticated| EC2-API["EC2 (API Servers)\n- Auto Scaling\n- Health Checks"]
    APIRoute -->|"Path: /health"| Lambda-Health["Lambda (Health Check)\n- Fixed Response: 200 OK"]
  end
```
