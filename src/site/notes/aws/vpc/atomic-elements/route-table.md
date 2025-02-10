---
{"dg-publish":true,"permalink":"/aws/vpc/atomic-elements/route-table/","title":"Route Table"}
---



## A route table contains a set of rules, called _routes_, that determine where network traffic from your subnet or gateway is directed.

- Destination: the range of ip address you want to reach
- Target: through which to send traffic to destination

#### Types
- subnet route table
- gateway route table: [[aws/vpc/atomic-elements/internet-gateway\|internet-gateway]] or virtual private gateway
- transit gateway route table: [[aws/vpc/atomic-elements/transit-gateway\|transit-gateway]]
- local gateway route table: outposts local gateway