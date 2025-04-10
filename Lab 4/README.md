**Dynamic Routing with RIP in a Triangle Topology**

🧠 Overview
- This lab demonstrates a fault-tolerant triangle network topology using RIP (Routing Information Protocol) for dynamic routing.
- Three routers form a redundant path between two LANs. RIP is used to automatically exchange routing information and maintain connectivity even in case of a link failure.

🧱 Topology Structure
- 3 Routers (Router0, Router1, Router2) connected in a triangle with Serial links
- 2 PCs:
  - PC0 on Network A (10.0.0.0/24)
  - PC1 on Network B (11.0.0.0/24)

🌐 IP Addressing
| Device   | Interface | IP Address  | Network       |
|----------|-----------|-------------|---------------|
| Router0  | Fa0/0     | 10.0.0.1    | 10.0.0.0/24   |
| Router0  | Se2/0     | 199.0.0.1   | 199.0.0.0/30  |
| Router0  | Se3/0     | 0.0.0.1     | 0.0.0.0/30    |
| Router1  | Fa0/0     | 11.0.0.1    | 11.0.0.0/24   |
| Router1  | Se2/0     | 200.0.0.1   | 200.0.0.0/30  |
| Router1  | Se3/0     | 0.0.0.2     | 0.0.0.0/30    |
| Router2  | Se2/0     | 199.0.0.2   | 199.0.0.0/30  |
| Router2  | Se3/0     | 200.0.0.2   | 200.0.0.0/30  |
| PC0      | Fa0       | 10.0.0.2    | 10.0.0.0/24   |
| PC1      | Fa0       | 11.0.0.2    | 11.0.0.0/24   |

🔧 Configuration Steps
- Place all the devices mentioned in the topology structure.
- Connect them using suitable cables (Ethernet for PCs, Serial for router-to-router links).
- Assign the IP addresses to all interfaces as per the table above.
- Set the default gateway on each PC:
  - PC0 → 10.0.0.1
  - PC1 → 11.0.0.1
- Enable RIP routing on all routers and advertise the directly connected networks.
  - Router0 Configuration:
    - Add networks: 10.0.0.0, 199.0.0.0, 0.0.0.0
  - Router1 Configuration:
    - Add networks: 11.0.0.0, 200.0.0.0, 0.0.0.0
  - Router2 Configuration:
    - Add networks: 199.0.0.0, 200.0.0.0
- Finally, verify connectivity using the ping tool on PC0 and PC1.
- Optionally test redundancy by shutting down one serial link and ensuring packets are rerouted dynamically.
