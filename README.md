# London–Rotterdam WAN Simulation (Cisco Packet Tracer)

This project presents a complete Cisco Packet Tracer simulation of a Wide Area Network (WAN)
connecting two sites: **London** and **Rotterdam**.

The purpose of this project is to demonstrate practical networking skills including:
- IP addressing and **FLSM subnetting**
- **Dynamic routing using RIPv2**
- Configuration of core **network services** (FTP, HTTP, DNS, Email)
- Basic **security implementation** using Windows Firewall
- End-to-end **testing and verification** of connectivity and services

---

## Network Overview

The network is based on the address space **192.168.20.0/24** and is subnetted using
**Fixed Length Subnet Masking (FLSM)** to support **40 hosts per LAN**.

A subnet mask of **/26 (255.255.255.192)** is used, providing:
- 64 IP addresses per subnet
- 62 usable host addresses
- Sufficient capacity for current requirements

The network consists of:
- One LAN at the London site
- One LAN at the Rotterdam site
- One WAN subnet connecting the two routers

---

## IP Addressing & Subnetting

### Subnet Allocation

- **London LAN:** `192.168.20.0/26`
- **Rotterdam LAN:** `192.168.20.64/26`
- **WAN Link:** `192.168.20.128/26`

All end devices and network interfaces are manually assigned IP addresses according
to the subnet they belong to, with routers acting as default gateways for each LAN.

---

## Dynamic Routing (RIPv2)

Dynamic routing is implemented using **RIPv2** on both routers.
RIPv2 allows automatic exchange of routing information between the London and Rotterdam sites,
ensuring full connectivity without the need for static routes.

RIPv2 is chosen because:
- It supports classless routing
- It is simple to configure
- It is suitable for small to medium-sized networks

---

## Network Services

### FTP Service
An FTP server is configured on the **Rotterdam Server**.
This service allows authenticated file access from client PCs using the following credentials:
- Username: `cisco`
- Password: `cisco`

### HTTP & DNS Services
The **London Server** hosts both HTTP and DNS services.
DNS is configured with the domain name **adventureworks.com**, allowing clients to access
the web server using a hostname instead of an IP address.

### Email Service
An email server is configured on the **Rotterdam Server** using the domain
**adventureworks.com**.

Email clients are configured on selected PCs, each with a unique email address.
Successful send and receive operations confirm correct email server configuration.

---

## Security Configuration

A **Windows Firewall rule** is implemented on the Rotterdam Server to enhance security.
The rule blocks **outbound FTP traffic (TCP port 21)** initiated by the server itself.

This demonstrates basic server-side security control while still allowing
other services such as HTTP, DNS, and Email to function normally.

---

## Testing & Verification

The network is fully tested to ensure correct configuration and functionality.

Testing includes:
- ICMP ping tests to verify basic connectivity
- TRACERT tests to verify correct routing paths
- HTTP testing using a web browser
- FTP login and file access testing
- Email send and receive testing

All tests confirm:
- Correct IP addressing
- Proper operation of RIPv2 routing
- Availability of configured services
- End-to-end connectivity between London and Rotterdam

---

## Project Files

- **Vasile.pkt** – Cisco Packet Tracer simulation file
- **README.md** – Project documentation
- **Screenshot files (.png)** – Visual evidence of configuration and testing

---

## How to Open the Project

1. Download the `.pkt` file from this repository
2. Open **Cisco Packet Tracer**
3. Load the project file
4. Verify IP addressing, routing, services, and security configuration
5. Repeat the test procedures described above






# London–Rotterdam WAN Simulation (Cisco Packet Tracer)

This repository contains a Cisco Packet Tracer project demonstrating a secure WAN
connection between London and Rotterdam using subnetting, RIPv2, and multiple services.

---

## Network Topology
![Topology](topology-overview.png)

---

## Firewall – FTP Block (Rotterdam Server)
![Firewall](firewall-ftp-block.png)

---

## TRACERT Tests
![PC1 to PC41](tracert-pc1-pc41.png)
![PC80 to PC40](tracert-pc80-pc40.png)
![Server to Server](tracert-rotterdam-london.png)

---

## HTTP Test
![HTTP PC1](http-pc1.png)

---

## FTP Tests
![FTP PC40](ftp-pc40.png)
![FTP PC80](ftp-pc80.png)

---

## Email Tests
![Email PC41](email-pc41.png)
![Email PC40](email-pc40.png)
