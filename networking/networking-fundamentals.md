# Networking Fundamentals

## The Goal: What "Enough" Looks Like

You do not need to be a full network engineer to succeed in DevOps. You have reached "enough" networking knowledge when:

- You understand how devices on a network acquire an IP address.
- You can set up subnets and explain CIDR ranges from memory.
- You can debug routing and firewall issues using tools like `ping`, `ip route`, and `nc`.
- You understand VLANs and why they are used to isolate traffic.
- You feel comfortable designing and troubleshooting cloud VPCs (AWS) or VNets (Azure).

---

## Core Concepts

### IP Addresses & The Hierarchy

Every device needs an address to communicate. In modern infrastructure, you primarily deal with **IPv4** (though IPv6 is growing).

- **Structure:** Four octets separated by dots (e.g., `192.168.1.15`).
- **Public vs. Private:**
    - **Public IPs:** Routable on the global internet. Unique worldwide.
    - **Private IPs:** Reserved for internal networks (Home, Office, Cloud VPCs). They are not routable on the internet.
    - _Memorize these Private Ranges:_
        - `10.0.0.0/8` (Common in large enterprise/cloud)
        - `172.16.0.0/12` (Common in Docker/Containers)
        - `192.168.0.0/16` (Common in Home networks)

### Subnetting & CIDR

Subnetting splits a large network into smaller, manageable pieces. We use **CIDR (Classless Inter-Domain Routing)** notation to define the size.

- **The Notation:** An IP followed by a slash and a number (e.g., `10.0.0.0/24`). The number represents the "network bits" that are fixed.
- **Common Sizes to Know:**
    - `/32` = 1 IP (Used to target a single specific host).
    - `/24` = 256 IPs (Standard size for a LAN subnet).
    - `/16` = 65,536 IPs (Used for a large VPC).
    - `/0` = `0.0.0.0/0` (Represents "Anywhere" or "The entire internet").

### Routing & Gateways

- **The Default Gateway:** When a host wants to send a packet to an IP _outside_ its own subnet, it sends it here. This is usually your router.
- **Routing Table:** A map on your device that tells it: "If the destination is X, send the packet to gateway Y."
- **NAT (Network Address Translation):** This allows multiple private devices (like your laptop and phone) to share a single Public IP provided by your ISP.

### DNS (Domain Name System)

- Computers speak in numbers (IPs); humans speak in names (`google.com`).
- DNS is the phonebook that translates the Name to the IP.
- If you can `ping 8.8.8.8` but cannot `ping google.com`, your internet works, but your DNS is broken.

---

## Security Boundaries

In DevOps, networking is often synonymous with **Security**.

### Firewalls & Security Groups

- **Stateful (Security Groups):** If you allow a request _out_, the response is automatically allowed _in_. (Most Cloud Firewalls).
- **Stateless (NACLs):** You must explicitly allow traffic in both directions.
- **The Golden Rule:** Block everything by default; allow only what is necessary.

### Ports

A port allows a single IP address to run multiple services.

- **Port 22:** SSH (Remote Linux access)
- **Port 80/443:** HTTP/HTTPS (Web traffic)
- **Port 3389:** RDP (Remote Windows access)
- **Port 53:** DNS

---

## The Toolkit: Debugging Commands

When connectivity fails, use this hierarchy of commands to isolate the problem.

|**Layer**|**Question**|**Command (Linux)**|
|---|---|---|
|**IP Config**|Do I have an IP address?|`ip a`|
|**Routing**|Do I know where to send packets?|`ip route`|
|**Connectivity**|Can I reach the gateway/destination?|`ping <ip_address>`|
|**Path**|Where is the packet getting lost?|`traceroute <ip_address>`|
|**Ports**|Is the application listening/blocked?|`nc -zv <ip> <port>` or `telnet <ip> <port>`|
|**DNS**|Can I resolve the name?|`dig <domain>` or `nslookup <domain>`|
|**Listening**|What ports are open on _my_ machine?|`ss -tulpn` or `netstat -tulpn`|
