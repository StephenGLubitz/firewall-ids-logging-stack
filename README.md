# firewall-ids-logging-stack
A home-lab project building a firewall + IDS + centralized logging/SIEM stack for monitoring and securing a small network.
# Firewall + IDS + Logging Stack Lab

## 📌 Summary
This project builds a home-lab security stack that combines a **firewall**, an **Intrusion Detection System (IDS)**, and **centralized logging / SIEM**.  
The goal is to design and document a realistic monitoring setup for a small network: seeing traffic, detecting suspicious activity, and having a single place to review security events.

This lab is a foundation for learning **network defense**, **visibility**, and **blue-team operations**.

---

## 🖥️ Environment

**Planned lab components:**

- **Firewall:**
  - pfSense / OPNsense / iptables-based firewall

- **IDS / IPS:**
  - Suricata / Snort (running on the firewall or a separate sensor)

- **Logging / SIEM:**
  - Wazuh / Elastic Stack / Graylog (choose one to start)

- **Endpoints:**
  - 1× Linux server
  - Optional: 1× Windows VM
  - Optional: 1× “attacker” machine (Kali, etc.)

- **Virtualization:**
  - VirtualBox / Proxmox / VMware (whichever I’m using)

---

## 🎯 Objectives

By the end of this project, I want to:

- Route lab traffic through a dedicated firewall
- Deploy an IDS to monitor network traffic and raise alerts
- Forward logs from firewall + hosts to a central logging/SIEM system
- Create at least a few **detection examples** (e.g., port scans, brute-force attempts)
- View, filter, and interpret security events in one place
- Document the architecture and configuration clearly enough that someone else could reproduce it

---

## 🧭 Architecture Overview (Planned)

> *(This section will be updated once the final design is chosen.)*

**Initial idea:**

- Internet → Firewall VM → Internal lab network
- IDS running:
  - either on the firewall
  - or on a span/mirror port in the internal segment
- Logging/SIEM server receiving:
  - firewall logs
  - IDS alerts
  - OS logs from Linux/Windows

I will add:

- A simple **network diagram**
- IP ranges and interfaces
- Which traffic each component sees

---

## 🧱 Component Setup

### 1. Firewall

To document:

- OS / platform (pfSense, OPNsense, etc.)
- Interface layout (WAN, LAN, optional DMZ)
- Rules created:
  - default policy
  - allowed services (SSH, HTTP, DNS, etc.)
- NAT configuration (if applicable)
- Any basic hardening done

---

### 2. IDS (Intrusion Detection System)

To document:

- IDS choice (Suricata / Snort)
- How it receives traffic (SPAN port / bridge / on-firewall)
- Rule set used (Emerging Threats, etc.)
- Example rules of interest
- How alerts are sent (local log, syslog to SIEM, etc.)

---

### 3. Logging / SIEM

To document:

- Platform (Wazuh, Elastic Stack, Graylog, etc.)
- Log sources:
  - firewall logs
  - IDS alerts
  - Linux server logs
  - (optionally) Windows Event Logs
- Indexes / data streams
- Basic dashboards or saved searches
- Any detection rules or alerts configured

---

## 🧪 Example Use Cases (Planned)

I plan to simulate and document at least a few of these:

- **Port scan** from attacker → internal host
- **SSH brute-force** attempts against a Linux server
- **Blocked connection** by firewall rule
- Optional: suspicious DNS or HTTP traffic

For each scenario, I will capture:

- What actually happened
- How it appeared in:
  - firewall logs
  - IDS alerts
  - SIEM / dashboards
- Screenshots with short explanations

---

## ✅ Verification

How I’ll verify the stack is working:

- Confirm all hosts route through the firewall
- Confirm IDS sees the same traffic the firewall sees (or at least key segments)
- Confirm logs from all components arrive at the SIEM
- Run a port scan / brute-force test and see:
  - firewall rule hits
  - IDS alerts
  - events in SIEM

This section will include commands, screenshots, and notes.

---

## 📚 Lessons Learned

After the initial build, I’ll note:

- What was surprisingly hard
- What concepts clicked
- Any trade-offs between complexity vs visibility
- What I would do differently in a production environment

---

## 🚀 Next Improvements

Potential future expansions:

- Add TLS inspection (if appropriate)
- Add IPS (blocking) mode instead of pure IDS
- Add more segmenting (e.g., DMZ, separate VLANs)
- Create custom IDS rules
- Automate log queries or alerting
- Integrate with incident-response workflows

---

## 📌 Status

This repository is currently a **planned / in-progress lab**.  
Content will be added as the firewall, IDS, and logging stack are built and tested.
