# Task-3
Networking Basics commands for DevOps
# Networking Commands Practice – 19-Jan-2026

## Overview

Today, I practiced various networking commands and Linux tools to understand network configuration, diagnostics, and connectivity in a Linux (CentOS) environment. These commands help in monitoring, troubleshooting, and managing networks effectively.

## Commands Practiced

### 1. Check IP Address

```
ip addr show
ifconfig
```

* Used to view IP addresses assigned to network interfaces.
* Helps verify network connectivity and interface configuration.

### 2. Check Network Connectivity

```
ping <IP/Hostname>
```

* Used to test connectivity between local machine and another host.
* Example:

```
ping 8.8.8.8
ping google.com
```

### 3. Check Routing Table

```
route -n
ip route show
```

* Displays the system's routing table.
* Helps understand how packets are routed to different networks.

### 4. Check Open Ports

```
netstat -tuln
ss -tuln
```

* Displays listening TCP/UDP ports.
* Useful for verifying services and firewall rules.

### 5. DNS Resolution

```
nslookup <domain>
dig <domain>
```

* Used to check DNS resolution and troubleshoot domain name issues.

### 6. Traceroute

```
traceroute <IP/Hostname>
```

* Traces the path packets take to reach a destination.
* Helps identify network latency or routing issues.

### 7. Check Active Network Connections

```
nmcli device status
```

* Displays the status of all network interfaces.
* Helps in managing network connections on Linux.

### 8. Firewall Status

```
sudo firewall-cmd --state
sudo firewall-cmd --list-all
```

* Checks firewall rules and active zones.
* Ensures network security and proper access control.

## Summary

* Learned to view IP addresses and network interfaces.
* Practiced testing connectivity and DNS resolution.
* Explored routing tables, ports, and traceroute for diagnostics.
* Checked firewall configuration to manage access.
* Gained hands-on experience in networking troubleshooting commands on CentOS.
