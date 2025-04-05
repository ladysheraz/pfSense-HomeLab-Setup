# pfSense Configuration Guide

## Overview
This guide documents the configuration of WAN, LAN, and DMZ (OPT1) interfaces along with DHCP and firewall/NAT settings. All non-default values and sensitive IP addresses have been obfuscated.

## Configuring the LAN Interface
- **Assigned IP:** `<YOUR_LAN_IP>` (e.g., `192.168.200.1`)
- **Subnet:** `/24`
- **DHCP Settings:**
  - DHCP Range: Begins at `<YOUR_DHCP_START>` (e.g., `192.168.101.24`)
  - Ensure static IPs for critical devices are reserved outside this range.

## Configuring the DMZ (OPT1) Interface
- **Assigned IP:** `<YOUR_DMZ_IP>` (e.g., `192.168.28.2`)
- **Subnet:** `/24`
- **Purpose:** To isolate public-facing services from the internal LAN.
- **Optional DHCP:** If enabled, use a range from `<YOUR_DMZ_DHCP_START>` to `<YOUR_DMZ_DHCP_END>`.

## Firewall and NAT Rules
- **Firewall Rules:** Custom rules are created to allow necessary traffic between WAN, LAN, and DMZ, while ensuring proper segmentation.
- **NAT Configuration:** Set up to allow external access without exposing the internal network.

## Additional Settings
- **Certificate Management:** Self-signed certificates are used initially; ensure to replace them with valid certificates in production.
- **Backup & Restore:** Regular exports of the pfSense configuration are stored in the `config` folder (with sensitive data removed).

## Challenges and Resolutions
- **IP Conflicts:** Adjusted default settings to avoid conflicts.
- **Certificate Warnings:** Managed through safe acceptance and replacement.
- **Rule Tuning:** Iterative testing to optimize security policies.
