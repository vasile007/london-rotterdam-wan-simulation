# London–Rotterdam WAN Simulation (Cisco Packet Tracer)

This project is a Cisco Packet Tracer simulation of a secure WAN connection between two sites: **London** and **Rotterdam**.  
The network implements subnetting, dynamic routing (RIPv2), multiple network services (FTP, HTTP, DNS, Email), and a Windows Firewall rule to control FTP traffic.

---

## 1. Network Design & Subnetting (Task 1)

- Given Network ID: **192.168.20.0/24**
- Subnetting method: **FLSM**, with subnets sized for **40 hosts** per side.
- Each subnet uses a **/26 mask**: `255.255.255.192`

### Subnets

1. **Subnet 1 – London LAN**  
   - Network: `192.168.20.0/26`  
   - Network Address: `192.168.20.0`  
   - Usable Host Range: `192.168.20.1 – 192.168.20.62`  
   - Broadcast: `192.168.20.63`

   - **Devices:**
     - PCs **PC1 – PC40**: `192.168.20.3 – 192.168.20.42`  
     - **London Server**: `192.168.20.2`  
     - Default Gateway: `192.168.20.1`  
     - Subnet Mask: `255.255.255.192`

2. **Subnet 2 – Rotterdam LAN**  
   - Network: `192.168.20.64/26`  
   - Network Address: `192.168.20.64`  
   - Usable Host Range: `192.168.20.65 – 192.168.20.126`  
   - Broadcast: `192.168.20.127`

   - **Devices:**
     - PCs **PC41 – PC80**: `192.168.20.67 – 192.168.20.106`  
     - **Rotterdam Server**: `192.168.20.66`  
     - Default Gateway: `192.168.20.65`  
     - Subnet Mask: `255.255.255.192`

3. **Subnet 3 – WAN Link (Router-to-Router)**  
   - Network: `192.168.20.128/26`  
   - Network Address: `192.168.20.128`  
   - Usable Host Range: `192.168.20.129 – 192.168.20.190`  
   - Broadcast: `192.168.20.191`

   - **Devices:**
     - **Router 1 WAN interface**: `192.168.20.129`  
     - **Router 2 WAN interface**: `192.168.20.130`  
     - Subnet Mask: `255.255.255.192`  
     - Default Gateway: N/A (point-to-point link)

---

## 2. Dynamic Routing – RIPv2 (Task 2)

Dynamic routing is implemented using **RIPv2** on both routers to advertise the three networks.

### Router 1 (London) – RIPv2 Configuration

```text
R1(config)# router rip
R1(config-router)# version 2
R1(config-router)# network 192.168.20.128
R1(config-router)# network 192.168.20.0



Router 2 (Rotterdam) – RIPv2 Configuration


R2(config)# router rip
R2(config-router)# version 2
R2(config-router)# network 192.168.20.128
R2(config-router)# network 192.168.20.64

This configuration ensures full reachability between:

London LAN (192.168.20.0/26)

Rotterdam LAN (192.168.20.64/26)

WAN link (192.168.20.128/26)

3. Network Services (Task 3)
3.1 FTP – Rotterdam Server

Location: Rotterdam Server

Service: FTP Server

Credentials:

Username: cisco

Password: cisco

This allows FTP access from client PCs to the Rotterdam server, subject to firewall rules.

3.2 HTTP & DNS – London Server

Location: London Server

Services:

HTTP Server

DNS Server

Domain name: adventureworks.com

The DNS server is configured to resolve the domain adventureworks.com to the appropriate server IPs in the network, allowing HTTP access via hostname instead of just IP addresses.

3.3 Email Server – Rotterdam

Location: Rotterdam Server

Service: Email Server

Domain: adventureworks.com

Email Client Configuration

PC1: client1@adventureworks.com

PC40: client40@adventureworks.com

PC41: client41@adventureworks.com

PC80: client80@adventureworks.com

Each client is configured with:

Proper incoming/outgoing mail server (Rotterdam Email Server)

Correct username and email address

Matching domain adventureworks.com

4. Security – Windows Firewall Rule (Task 3)

A Windows Firewall rule is configured on the Rotterdam Server to:

Block outbound FTP traffic

Protocol: TCP

Port: 21

This demonstrates basic server-side security by preventing the Rotterdam server itself from initiating FTP connections, while still allowing other services such as HTTP, DNS, and Email.

5. Testing & Verification (Task 4)

Connectivity and services are verified using a series of tests:

5.1 ICMP & Traceroute (TRACERT)

tracert from PC1 → PC41

tracert from PC80 → PC40

tracert from Rotterdam Server → London Server

These tests confirm:

Correct routing via RIPv2

Proper WAN connectivity between London and Rotterdam

5.2 HTTP Testing

Browser access from PC1 to the London web server (via IP and/or adventureworks.com)

Browser access from PC80 to the London web server

5.3 FTP Testing

FTP access from PC40 → FTP server (Rotterdam)

FTP access from PC80 → FTP server (Rotterdam)

These tests validate FTP service availability and user authentication with the cisco/cisco credentials.

5.4 Email Testing

Email sent from PC1 → PC41 (client1@adventureworks.com → client41@adventureworks.com)

Screenshot captured on receiving side showing successful delivery.

Email sent from PC80 → PC40 (client80@adventureworks.com → client40@adventureworks.com)

Screenshot captured on receiving side showing successful delivery.

All test results (ping, tracert, HTTP, FTP, Email) are documented with screenshots as part of the project evidence.

6. How to Open the Project

Download the .pkt file from this repository (e.g. Vasile.pkt).

Open Cisco Packet Tracer.

Go to File → Open and select the downloaded .pkt file.

Verify:

IP addressing and subnetting

RIPv2 configurations on both routers

Services on the London and Rotterdam servers

Firewall rule on the Rotterdam server

End-to-end connectivity using the test steps from Task 4.



(Download the project: click on the Vasile.pkt file in this repository and then click “Download raw file” to save it to your device).





