**Static Routing between Three LANs using Routers and Switches**

## 🧠 Overview
- This lab demonstrates communication between three different LANs using three routers connected via serial links.
- Each LAN includes a switch and two end devices (PCs). Static routing is configured on each router to enable full connectivity between all networks.

## 🧱 Topology Structure
- 3 Routers (Router0, Router1, Router2) connected via Serial links
- 3 Switches (Switch0, Switch1, Switch2)
- 6 PCs:
  - PC0 and PC1 on Network A (10.1.2.0/24)
  - PC2 and PC3 on Network B (20.1.2.0/24)
  - PC4 and PC5 on Network C (30.1.2.0/24)

## 🌐 IP Addressing
| Device   | Interface | IP Address  | Network       |
|----------|-----------|-------------|---------------|
| Router0  | Fa0/0     | 10.1.2.1    | 10.1.2.0/24   |
| Router0  | Se2/0     | 200.1.2.1   | 200.1.2.0/30  |
| Router1  | Fa0/0     | 20.1.2.1    | 20.1.2.0/24   |
| Router1  | Se2/0     | 200.1.2.2   | 200.1.2.0/30  |
| Router1  | Se3/0     | 201.1.2.1   | 201.1.2.0/30  |
| Router2  | Fa0/0     | 30.1.2.1    | 30.1.2.0/24   |
| Router2  | Se2/0     | 201.1.2.2   | 201.1.2.0/30  |
| PC0      | Fa0       | 10.1.2.2    | 10.1.2.0/24   |
| PC1      | Fa0       | 10.1.2.3    | 10.1.2.0/24   |
| PC2      | Fa0       | 20.1.2.2    | 20.1.2.0/24   |
| PC3      | Fa0       | 20.1.2.3    | 20.1.2.0/24   |
| PC4      | Fa0       | 30.1.2.2    | 30.1.2.0/24   |
| PC5      | Fa0       | 30.1.2.3    | 30.1.2.0/24   |

## 🔧 Configuration Steps
- Place all the devices mentioned in the topology structure.
- Connect them using the suitable wires (Ethernet and Serial cables).
- Assign the IP addresses for the PCs.
- Assign the IP addresses for the router interfaces.
- Set the default gateway on each PC:
  - PC0, PC1: 10.1.2.1
  - PC2, PC3: 20.1.2.1
  - PC4, PC5: 30.1.2.1
- Configure static routing on all routers:
  - On Router0:
    - Network: 20.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 200.1.2.2
  
    - Network: 30.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 200.1.2.2

  - On Router1:
    - Network: 10.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 200.1.2.1

    - Network: 30.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 201.1.2.2

  - On Router2:
    - Network: 10.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 201.1.2.1

    - Network: 20.1.2.0
    - Mask: 255.255.255.0
    - Next Hop: 201.1.2.1
- Send packets across the network to verify connectivity between all PCs.

