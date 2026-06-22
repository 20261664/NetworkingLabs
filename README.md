# DHCP and DNS Packet Tracer Lab Report

## 1. Title

**Implementation of a Small LAN with DHCP and DNS Services in Cisco Packet Tracer**

---

## 2. Objective

To design and configure a small local area network (LAN) using Cisco Packet Tracer that includes:

* A router acting as the default gateway
* A switch for local connectivity
* End devices (PCs)
* A DNS server for name resolution
* Static and dynamic IP addressing

The goal is to enable successful communication between devices using both IP addresses and domain names.

---

## 3. Network Topology

```
                +-------------------+
                |     Router        |
                | 192.168.1.1       |
                +---------+---------+
                          |
                          |
                +---------+---------+
                |      Switch        |
                +----+----+----+-----+
                     |    |    |
                     |    |    |
                 PC1  PC2  DNS Server

PC1: 192.168.1.10
PC2: 192.168.1.11
DNS Server: 192.168.1.2
```

---

## 4. Device Configuration

### 4.1 Router Configuration

The router was configured as the default gateway for the network.

```
enable
configure terminal
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
```

---

### 4.2 Switch Configuration

* Switch was used for Layer 2 connectivity only.
* No additional configuration was required.
* All ports were active and connected using copper straight-through cables.

---

### 4.3 DNS Server Configuration

The server was assigned a static IP address:

* IP Address: 192.168.1.2
* Subnet Mask: 255.255.255.0
* Default Gateway: 192.168.1.1

DNS Service Configuration:

* DNS Service: ON
* A Records added:

| Domain Name | IP Address   |
| ----------- | ------------ |
| pc1.local   | 192.168.1.10 |
| pc2.local   | 192.168.1.11 |

---

### 4.4 PC Configuration

Each PC was initially configured with static IP addresses.

Example:

* PC1: 192.168.1.10 /24
* PC2: 192.168.1.11 /24
* Default Gateway: 192.168.1.1
* DNS Server: 192.168.1.2

---

## 5. Implementation Steps

1. Placed router, switch, server, and PCs in Packet Tracer workspace.
2. Connected devices using copper straight-through cables.
3. Configured router interface with IP address and enabled it using `no shutdown`.
4. Assigned static IP address to DNS server.
5. Enabled DNS service and created A records.
6. Configured PCs with static IP addresses and DNS server IP.
7. Tested connectivity using ping and DNS resolution.

---

## 6. Testing and Results

### 6.1 Connectivity Test (IP-based)

Command executed on PC:

```
ping 192.168.1.2
```

Result:

* Successful reply from DNS server

---

### 6.2 DNS Resolution Test

Command executed on PC:

```
ping pc1.local
```

Result:

* Successful resolution of domain name to IP address
* ICMP packets successfully received from PC1

---

## 7. Issues Encountered and Fixes

### Issue 1: DNS resolution failure

* Cause: DNS server IP was not configured on PCs
* Fix: Manually set DNS server IP (192.168.1.2) in PC configuration

### Issue 2: Initial port connection issues

* Cause: Incorrect switch module ports (100FX fiber ports used)
* Fix: Installed FastEthernet module (PM-Fe) and used RJ-45 ports

---

## 8. Conclusion

The LAN was successfully implemented and tested using Cisco Packet Tracer. Devices were able to communicate using both IP addresses and domain names. DNS resolution worked correctly after proper configuration of DNS server settings on all PCs.

This lab demonstrated:

* Basic LAN design
* IP addressing
* DNS configuration and resolution
* Troubleshooting network connectivity issues

---

## 9. Key Learning Outcomes

* Understanding of DNS A records and name resolution
* Importance of correct DNS server configuration on clients
* Differences between fiber and copper switch ports
* Practical troubleshooting of network issues
