---
{"dg-publish":true,"permalink":"/aws/networking-content-delivery/route-53/atomic-elements/routing-policy/","title":"Route Policy"}
---

These routing policies apply to **all Route 53 usage**, specifically for **DNS records** in **public hosted zones**.

| **Routing Policy**    | **Use Case**                                                                              |
| --------------------- | ----------------------------------------------------------------------------------------- |
| **Simple**            | For a single resource (e.g., web server)                                                  |
| **Failover**          | For active-passive failover (one resource is backup for another)                          |
| **Geolocation**       | Routes traffic based on the location of users                                             |
| **Geoproximity**      | Routes traffic based on resource location and optionally shifts traffic between locations |
| **Latency**           | Routes traffic to the region with the best latency (multiple AWS regions)                 |
| **IP-based**          | Routes traffic based on user IP addresses                                                 |
| **Multivalue Answer** | Responds with up to 8 healthy random records                                              |
| **Weighted**          | Routes traffic in specified proportions across multiple resources                         |

### Failover Routing
![Failover Routing.png](/img/user/AWS/Networking-Content-Delivery/Route%2053/excalidraw/Failover%20Routing.png)

### Multivalue Answer Policy
Route 53 can response to DNS query with up to 8 records(IP addresses) for the same domain or sub-domain name, to improve availability of services.

| **Record Type** | **Name**     | **Value (IP address)** | **Routing Policy**        | **Health Check**       |
|-----------------|--------------|------------------------|---------------------------|------------------------|
| A               | example.com  | 192.0.2.1              | Multivalue Answer         | Yes (healthy)          |
| A               | example.com  | 192.0.2.2              | Multivalue Answer         | Yes (healthy)          |
| A               | example.com  | 192.0.2.3              | Multivalue Answer         | No (unhealthy)         |
| A               | example.com  | 192.0.2.4              | Multivalue Answer         | Yes (healthy)          |

## Weighted Policy
- higher weight will receive more requests
- traffics are split and sent proportionally 
- same domain can have multiple records with different weights for loading balancing

In this example:
- Route 53 will route **70%** of the traffic to `192.0.2.1` and **30%** to `192.0.2.2`.

| **Record Type** | **Name**    | **Value (IP address)** | **Weight** | **Health Check** |
| --------------- | ----------- | ---------------------- | ---------- | ---------------- |
| A               | example.com | 192.0.2.1              | 70         | Yes (healthy)    |
| A               | example.com | 192.0.2.2              | 30         | Yes (healthy)    |


## IP-based Policy
- route traffics to different destination according to source IP address
- for better security and access control

| **Record Type** | **Name**    | **Value (IP address)** | **Source IP Range** | **Routing Policy** |
| --------------- | ----------- | ---------------------- | ------------------- | ------------------ |
| A               | example.com | 192.0.2.1              | 192.0.2.0/24        | IP-based Routing   |
| A               | example.com | 198.51.100.1           | 198.51.100.0/24     | IP-based Routing   |
