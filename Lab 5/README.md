

🧠 Overview
- This lab demonstrates how to divide a large network (10.0.0.0/24) into smaller subnetworks for better IP address management and traffic segmentation.
- Multiple switches and PCs are grouped into subnetted ranges, with a single router providing inter-subnet routing.

🧱 Topology Structure
- 1 Router (Router0) with multiple FastEthernet interfaces
- 4 Switches (Switch0, Switch1, Switch2, Switch3)
- 8 PCs:
  - PC0, PC1 in Subnet A
  - PC2, PC3 in Subnet B
  - PC4, PC5 in Subnet C
  - PC6, PC7 in Subnet D

🌐 IP Addressing
| Device   | Interface | IP Address    | Network         |
|----------|-----------|---------------|-----------------|
| Router0  | Fa0/0     | 10.0.0.1      | 10.0.0.0/26     |
| Router0  | Fa1/0     | 10.0.0.65     | 10.0.0.64/26    |
| Router0  | Fa4/0     | 10.0.0.129    | 10.0.0.128/26   |
| Router0  | Fa5/0     | 10.0.0.193    | 10.0.0.192/26   |
| PC0      | Fa0       | 10.0.0.2      | 10.0.0.0/26     |
| PC1      | Fa0       | 10.0.0.3      | 10.0.0.0/26     |
| PC2      | Fa0       | 10.0.0.66     | 10.0.0.64/26    |
| PC3      | Fa0       | 10.0.0.67     | 10.0.0.64/26    |
| PC4      | Fa0       | 10.0.0.130    | 10.0.0.128/26   |
| PC5      | Fa0       | 10.0.0.131    | 10.0.0.128/26   |
| PC6      | Fa0       | 10.0.0.194    | 10.0.0.192/26   |
| PC7      | Fa0       | 10.0.0.195    | 10.0.0.192/26   |

🔧 Configuration Steps
- Place the router, switches, and PCs as per the topology structure.
- Connect each pair of PCs to a switch.
- Connect each switch to a dedicated interface on the router.
- Assign the IP addresses to all PCs and router interfaces as per the table above.
- Set the default gateway on each PC according to its subnet:
  - Subnet A → Gateway: 10.0.0.1
  - Subnet B → Gateway: 10.0.0.65
  - Subnet C → Gateway: 10.0.0.129
  - Subnet D → Gateway: 10.0.0.193
- Ping between different subnets to ensure inter-subnet communication is working.
