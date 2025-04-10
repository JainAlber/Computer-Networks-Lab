**Basic Inter-Network Communication using Routers and Switches**

## 🧠 Overview
- This lab demonstrates a simple network topology involving two separate LANs interconnected via routers. 
- Each LAN includes a switch and end devices (PCs), and IP routing is configured between the two networks to enable communication across subnets.

## 🧱 Topology Structure
- 2 Routers (Router0 and Router1) connected via a Serial link
- 2 Switches (Switch0 and Switch1)
- 4 PCs:
  - PC0 and PC1 on Network A (10.1.2.0/24)
  - PC2 and PC3 on Network B (20.1.2.0/24)

## 🌐 IP Addressing

| Device   | Interface | IP Address  | Network       |
|----------|-----------|-------------|---------------|
| Router0  | Fa0/0     | 10.1.2.1    | 10.1.2.0/24   |
| Router0  | Se2/0     | 200.1.2.1   | 200.1.2.0/24  |
| Router1  | Fa0/0     | 20.1.2.1    | 20.1.2.0/24   |
| Router1  | Se2/0     | 200.1.2.2   | 200.1.2.0/24  |
| PC0      | Fa0       | 10.1.2.2    | 10.1.2.0/24   |
| PC1      | Fa0       | 10.1.2.3    | 10.1.2.0/24   |
| PC2      | Fa0       | 20.1.2.2    | 20.1.2.0/24   |
| PC3      | Fa0       | 20.1.2.3    | 20.1.2.0/24   |

🔧 Configuration Steps
- Place all the devices mentioned in the topology structure.
- Connect them using the suitable wires (Ethernet and Serial cables).
- Assign the IP addresses for the PCs.
- Assign the IP addresses for the router interfaces.
- Set the default gateway on each PC:
  - PC0 and PC1: 10.1.2.1
  - PC2 and PC3: 20.1.2.1
- Configure static routing on both routers:
  - On Router0:
    - Network:	20.1.2.0
    - Mask:	255.255.255.0
    - Next Hop:	200.1.2.2
  - On Router1:
    - Network:	10.1.2.0
    - Mask:	255.255.255.0
    - Next Hop:	200.1.2.1
- Send packets across the network to verify connectivity.
