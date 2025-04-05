# pfSense HomeLab Setup Documentation

## Overview
This repository documents the configuration and deployment of my pfSense firewall in my SOC homelab. The project demonstrates the setup of a segmented network with three zones: WAN, LAN, and DMZ (OPT1). It highlights the step-by-step process, challenges encountered, and the lessons learned while configuring the firewall to support a realistic SOC environment.

## Network Architecture
The network is divided into three primary segments:

- **WAN:** Connects to the Internet.
- **LAN:** Internal network used by trusted devices.
  - **Subnet:** `192.168.--.--/24`
  - **Gateway (pfSense LAN IP):** `192.168.--.--`
  - **Example Devices:** Windows 10 (`192.168.---.--`), Kali Linux (`192.168.---.--`)
- **DMZ (OPT1):** Isolated subnet for public-facing services.
  - **Subnet:** `192.168.--.-/24`
  - **Gateway (pfSense DMZ IP):** `192.168.--.--`

### Network Diagram
![Network Diagram](./screenshots/network-diagram.png)

## Configuration Steps

### 1. Accessing the pfSense Dashboard
- **Initial Access:** The default IP was `https://192.168.1.1` (pre-configuration).
- **Current Access:** After reconfiguring the LAN interface, access via `https://192.168.--.--`.

### 2. Configuring the LAN Interface
- **Assigned IP:** `192.168.--.-` with a `/24` subnet mask.
- **DHCP Configuration:**
  - **DHCP Range:** Configured to start at `192.168.--.--` to avoid conflicts with static IPs.
  - **Static Reservations:** Existing devices like the Windows 10 and Kali Linux systems have fixed IPs.

### 3. Configuring the DMZ (OPT1) Interface
- **Assigned IP:** `192.168.--.-` with a `/24` subnet mask.
- **Purpose:** To isolate public-facing services from the internal LAN.
- **DHCP Settings:** (Optional) Can be configured with a range such as `192.168.--.--` to `192.168.--.--` if required.

### 4. Firewall & NAT Rules
- **Firewall Rules:** Implemented rules to control and restrict traffic between WAN, LAN, and DMZ.
- **NAT Configuration:** Set up for proper translation between the WAN and internal subnets.

### 5. Additional Settings
- **Certificate Management:** Handled self-signed certificate warnings by accepting the certificate after confirming its validity.
- **Backup & Restore:** Configuration files are regularly exported and saved in the `/configs` directory (with sensitive data removed).

## Screenshots
- **Dashboard Overview:** ![Dashboard Overview](./screenshots/dashboard.png)
- **LAN Configuration Screen:** ![LAN Config](./screenshots/lan-config.png)
- **DMZ (OPT1) Configuration Screen:** ![DMZ Config](./screenshots/dmz-config.png)

## Challenges & Resolutions
- **IP Conflicts:** Resolved by changing the default LAN IP from `192.168.1.1` to `192.168.--.--` and adjusting the DHCP range.
- **Certificate Warnings:** Managed by learning how to safely bypass self-signed certificate warnings in browsers.
- **Firewall Rules Tuning:** Iterative testing was required to ensure proper traffic segregation among LAN, DMZ, and WAN.

## Lessons Learned
- **Network Segmentation:** Isolating different network zones enhances security.
- **Documentation:** Maintaining detailed documentation simplifies troubleshooting and future expansions.
- **Continuous Improvement:** Regular reviews of firewall and NAT rules are critical as new security challenges emerge.

## Future Enhancements
- **Integration with Monitoring Tools:** Plans to integrate Suricata, Zeek, and Graylog for comprehensive network monitoring.
- **Automation:** Developing scripts for automated backups and configuration checks.
- **Extended Security Measures:** Further refinement of firewall rules and NAT configurations based on emerging threat intelligence.

## Repository Structure

