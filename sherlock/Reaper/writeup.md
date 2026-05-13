# Sherlock: Reaper

## Overview

Network forensics challenge — analyze a packet capture in Wireshark.

## Protocol Reference

| Protocol | Description |
|----------|-------------|
| NBNS | NetBIOS Name Service — translates human-readable names to IP addresses (similar to DNS) |
| IGMP | Internet Group Management Protocol — used for multicast group management |
| ICMP | Internet Control Message Protocol — used for diagnostics and error reporting |
| ARP | Address Resolution Protocol — maps IP addresses to MAC addresses |
| MDNS | Multicast DNS — resolves hostnames on small networks without a DNS server |
| SSDP | Simple Service Discovery Protocol — allows networked devices to discover each other |

## DHCP Flow

1. Client broadcasts a **DHCP Discover** to find a DHCP server
2. DHCP server responds with a **DHCP Offer** (proposed IP address)
3. Client accepts with a **DHCP Request** (broadcast)
4. DHCP server confirms with a **DHCP Ack**
