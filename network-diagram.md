# Network Diagram Overview

## Architecture
The network is divided into three main segments:

- **WAN:** The external interface connecting to the Internet.
- **LAN:** The internal network.
  - **Subnet:** `<YOUR_LAN_SUBNET>` (e.g., `192.168.200.0/24`)
  - **Gateway:** `<YOUR_LAN_IP>` (e.g., `192.168.200.2`)
- **DMZ (OPT1):** Isolated for public-facing services.
  - **Subnet:** `<YOUR_DMZ_SUBNET>` (e.g., `192.168.28.1/24`)
  - **Gateway:** `<YOUR_DMZ_IP>` (e.g., `192.168.28.256`)

## Diagram
Below is the network diagram created using [draw.io](https://app.diagrams.net/):

![Network Diagram](../screenshots/NetworkDiagram.jpeg)

## Explanation
- **WAN:** Provides Internet connectivity.
- **LAN:** Hosts internal systems and is secured behind the pfSense firewall.
- **DMZ:** Isolated zone for servers exposed to external traffic, ensuring internal resources are protected.
