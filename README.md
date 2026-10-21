
# 🛡️ SOC Capstone Project
## Threat Detection & Incident Response Using Wireshark, pfSense and Wazuh

![SOC](https://img.shields.io/badge/Security-SOC%20Analysis-0078D4)
![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-blue)
![Wireshark](https://img.shields.io/badge/Network-Wireshark-1679A7)
![pfSense](https://img.shields.io/badge/Firewall-pfSense-orange)
![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-purple)
![Status](https://img.shields.io/badge/Project-Completed-success)

**Analyst:** Qhubekani Luphahla  
**Role:** Security Operations Centre (SOC) Analyst  
**Organisation:** Barclays Telco (Capstone Case Study)  
**Cohort:** April 2026  
**Project Date:** June 2026  
**Project Type:** Cybersecurity | Blue Team | Incident Response

---

## 📌 1. Project Overview

This project demonstrates a practical Security Operations Centre (SOC) investigation involving network reconnaissance, port scanning, SSH brute-force activity, security event monitoring, and incident containment.

The investigation was conducted within a simulated Barclays Telco network environment using Kali Linux, Ubuntu Server, pfSense, Wireshark, and Wazuh SIEM.

The objective was to investigate suspicious network activity, identify potential cyber threats, correlate evidence from multiple security tools, and implement defensive controls.

The project demonstrates the importance of combining network-level visibility, endpoint monitoring, and firewall enforcement in a defence-in-depth security architecture.

### Key Project Highlights

- Simulated network reconnaissance and SSH brute-force activity.
- Analysed network packets using Wireshark.
- Investigated firewall logs and access rules using pfSense.
- Monitored endpoint security events using Wazuh SIEM.
- Correlated network and endpoint evidence.
- Identified suspicious authentication attempts.
- Implemented a firewall blocking rule.
- Verified containment through connection testing and firewall logs.
- Documented incident findings and security recommendations.

> **Disclaimer:** All attack simulations were conducted as part of an educational cybersecurity laboratory. This project does not document an attack against Barclays' real infrastructure.

---

## 🎯 2. Problem Statement

Organisations face persistent cybersecurity threats involving unauthorised network reconnaissance, exposed services, and password-based attacks.

Without effective security monitoring and incident response capabilities, attackers may identify vulnerable systems and attempt to gain unauthorised access.

In this capstone scenario, suspicious activity was directed toward an internal Ubuntu server.

The activity included:

1. ICMP-based network discovery.
2. TCP port scanning.
3. Identification of an exposed SSH service.
4. Repeated SSH authentication attempts.
5. Automated password-guessing behaviour.

The SOC investigation focused on detecting these activities, validating the evidence, assessing the threat, and containing the suspicious source.

---

## 🎯 3. Project Objectives

The primary objectives were to:

- Investigate suspicious traffic targeting an Ubuntu server.
- Detect reconnaissance and network scanning behaviour.
- Identify SSH brute-force indicators.
- Analyse packet captures using Wireshark.
- Review firewall activity through pfSense.
- Monitor authentication events using Wazuh SIEM.
- Correlate evidence across security monitoring tools.
- Implement network-level containment.
- Validate the effectiveness of firewall restrictions.
- Produce a professional SOC incident investigation report.

---

## 🏗️ 4. Lab Environment and Architecture

The project used a simulated network environment with an attacking host, a firewall, a monitored Ubuntu endpoint, and a centralised SIEM platform.

### Lab Components

| Component | Role | Reported IP Address |
|---|---|---|
| Kali Linux | Simulated attacker | 192.168.1.100 |
| Ubuntu Server | Monitored target endpoint | 192.168.2.101 |
| Wazuh Server | Centralised SIEM | 192.168.1.101 |
| pfSense Firewall | Network security gateway | 192.168.1.1 / 10.0.2.15 |

**Note:** The source report contains inconsistent IP references between its topology, findings, and incident assessment. These addresses are taken from the topology and must be verified against the final lab configuration.

### Conceptual Security Architecture

```text
       SIMULATED ATTACK ENVIRONMENT
                    |
              Kali Linux
          Reconnaissance / SSH
                    |
                    v
             pfSense Firewall
          Traffic Filtering & Logs
                    |
                    v
              Ubuntu Server
             Monitored Endpoint
                    |
              Security Events
                    |
                    v
                Wazuh SIEM
          Centralised Monitoring

       Wireshark captures and analyses
          relevant network traffic
```

The environment supports investigation across multiple security layers.

---

## 🛠️ 5. Tools and Technologies

| Tool | Purpose |
|---|---|
| Kali Linux | Simulated adversarial activity |
| Nmap | Network discovery and port scanning |
| Hydra | Simulated SSH password-guessing attempts |
| Wireshark | Packet capture and network traffic analysis |
| pfSense | Firewall monitoring, access control, and containment |
| Wazuh SIEM | Centralised security event monitoring |
| Ubuntu Server | Monitored target system |
| SSH | Targeted remote administration service |

### Technical Skills Demonstrated

- Network traffic analysis
- TCP/IP and ICMP protocol analysis
- Network reconnaissance detection
- SSH authentication monitoring
- SIEM alert investigation
- Firewall log analysis
- Threat identification and triage
- Incident evidence correlation
- Network-level threat containment
- Security reporting and documentation

---

## 🔍 6. Investigation Methodology

The investigation followed a structured workflow involving network monitoring, attack simulation, evidence collection, analysis, and containment.

### Phase 1 — Environment Verification

The first phase focused on confirming the laboratory network configuration and endpoint connectivity.

Activities included:

- Reviewing network interfaces.
- Confirming assigned IP addresses.
- Checking connectivity between systems.
- Reviewing the monitored Ubuntu endpoint.
- Confirming Wazuh agent availability.

**Outcome:** The investigation environment and monitoring components were reviewed before analysing suspicious activity.

### Phase 2 — Network Traffic Monitoring

Wireshark was used to inspect network traffic and identify abnormal communication patterns.

The investigation examined:

- DNS traffic.
- ICMP packets.
- TCP connection attempts.
- SSH traffic on TCP port 22.
- Changes in traffic frequency.

Example Wireshark display filters:

**ICMP traffic from the reported Kali address**

```wireshark
ip.addr == 192.168.1.100 && icmp
```

**SSH traffic**

```wireshark
tcp.port == 22
```

**DNS traffic**

```wireshark
dns
```

These filters supported the identification of reconnaissance and authentication-related traffic.

### Phase 3 — Network Reconnaissance Analysis

The simulated attacker used network discovery and scanning techniques.

The report documents:

- ICMP Echo Requests.
- Sequential host discovery.
- TCP service probing.
- Identification of SSH on TCP port 22.

Wireshark analysis identified structured scanning behaviour that differed from baseline traffic.

**Finding:** Network traffic patterns were consistent with automated reconnaissance and service discovery.

### Phase 4 — SSH Brute-Force Investigation

The simulation progressed from network reconnaissance to repeated SSH authentication attempts.

Hydra was used in the laboratory to simulate password-guessing activity.

The investigation identified:

- Repeated SSH connection attempts.
- Failed authentication events.
- Rapidly recurring authentication activity.
- Targeted usernames reported as `trial` and `telnetuser`.

**Finding:** The authentication activity was consistent with automated SSH brute-force behaviour.

The report does not establish that the attacker successfully authenticated or gained control of the Ubuntu server.

### Phase 5 — Wazuh SIEM Investigation

Wazuh was used to monitor endpoint events and investigate authentication activity.

The report documents:

- An active Wazuh agent.
- Agent ID `005`.
- Endpoint hostname `SOC_3_BARCLAYS`.
- Ubuntu 24.04.4 LTS.
- Failed SSH authentication events.
- High-severity security alerts.

Wazuh provided endpoint-level evidence supporting the network investigation.

**Finding:** Endpoint authentication telemetry corroborated the suspicious SSH activity identified during network analysis.

### Phase 6 — pfSense Firewall Analysis

pfSense was used to investigate network access and enforce containment.

The report describes:

1. Reviewing firewall logs.
2. Identifying traffic associated with the suspicious source.
3. Creating an alias named `Suspicious Hosts`.
4. Adding the suspicious address to the alias.
5. Implementing a WAN firewall block rule.
6. Reviewing subsequent firewall events.

**Finding:** The firewall logs showed blocked traffic following the containment change.

### Phase 7 — Containment Verification

After the firewall rule was implemented, additional connection tests were performed.

The report states that:

- Follow-up connections timed out.
- Firewall logs recorded dropped packets.
- The configured rule restricted the suspicious source.

**Outcome:** Network-level containment was demonstrated for the tested traffic path.

---

## 🚨 7. Incident Timeline

The report records the following investigation milestones:

| Time | Activity | Evidence |
|---|---|---|
| 15:03 | Network architecture and endpoint verification | Ubuntu terminal |
| 15:23 | Wazuh agent status verification | Wazuh dashboard |
| 15:45 | Baseline traffic inspection | Wireshark |
| 15:55 | ICMP connectivity validation | Packet capture |
| 16:09 | Port probing and SSH service identification | Nmap output |
| 16:25 | Firewall log and traffic-blocking verification | pfSense logs |

These timestamps reflect the documented investigation timeline. The report does not provide a separate timestamp for every SSH authentication attempt.

---

## 📊 8. Summary of Security Findings

### Finding 1 — Network Reconnaissance

**Detection Tool:** Wireshark  
**Activity:** ICMP-based network discovery

The investigation identified sequential ICMP Echo Requests targeting multiple network addresses.

**Security Significance:** Systematic network discovery can indicate preparation for further attacks.

### Finding 2 — SSH Service Discovery

**Detection Tools:** Nmap and Wireshark  
**Target Service:** SSH, TCP port 22

The simulation identified SSH as an accessible service.

**Security Significance:** Exposed remote administration services can become targets for password-based attacks.

### Finding 3 — Repeated Authentication Failures

**Detection Tool:** Wazuh SIEM  
**Activity:** SSH password-guessing attempts

Endpoint logs showed repeated failed authentication events.

**Security Significance:** Repeated authentication failures associated with automated attempts may indicate a brute-force attack.

### Finding 4 — Firewall Containment

**Detection and Control Tool:** pfSense  
**Action:** Source-based traffic restriction

A firewall alias and blocking rule were implemented.

**Security Significance:** Network controls can reduce exposure by preventing unwanted connections from reaching protected services.

---

## 🧠 9. Incident Assessment

| Assessment Area | Finding |
|---|---|
| Threat Category | Network reconnaissance and SSH brute-force attempt |
| Target | Ubuntu Server |
| Target Service | SSH / TCP 22 |
| Network Indicators | ICMP scanning and TCP connection activity |
| Endpoint Indicators | Repeated SSH authentication failures |
| Monitoring Tools | Wireshark, Wazuh and pfSense |
| Containment | pfSense firewall block rule |
| Incident Classification | Malicious simulated activity |
| Confirmed Compromise | Not established in the report |

### Analytical Conclusion

The observed sequence progressed from host discovery to service scanning and repeated SSH authentication attempts.

The combination of network packet evidence, firewall records, and endpoint authentication events supported the conclusion that the activity was deliberate and automated.

The investigation demonstrates the value of correlating multiple evidence sources rather than relying on a single security alert.

---

## 🛡️ 10. MITRE ATT&CK Mapping

The documented activity can be related to the following MITRE ATT&CK techniques:

| Technique | MITRE ID | Project Evidence |
|---|---|---|
| Network Service Discovery | T1046 | Network scanning and SSH service identification |
| Brute Force | T1110 | Repeated automated SSH authentication attempts |

These mappings provide a standardised way to describe the simulated adversarial behaviour.

**MITRE References:**

- [T1046 — Network Service Discovery](https://attack.mitre.org/techniques/T1046/)
- [T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)

---

## 🔐 11. Security Recommendations

The investigation identified opportunities to strengthen the security posture of the monitored environment.

### 1. Strengthen SSH Authentication

- Enforce SSH key-based authentication.
- Disable password authentication where operationally appropriate.
- Restrict privileged remote access.
- Review unnecessary exposed services.

### 2. Implement Automated Brute-Force Protection

Deploy Fail2ban or an equivalent control to detect and restrict repeated failed authentication attempts.

### 3. Improve Firewall Access Control

- Apply least-privilege firewall rules.
- Restrict direct management access from untrusted networks.
- Use a secure VPN or controlled jump host where appropriate.
- Review and validate firewall rules regularly.

### 4. Strengthen Security Monitoring

- Maintain active Wazuh endpoint agents.
- Review authentication alerts.
- Correlate network and host security events.
- Monitor repeated login failures and suspicious source activity.

### 5. Improve Incident Response Readiness

- Document incident escalation procedures.
- Maintain evidence records.
- Validate containment effectiveness.
- Review lessons learned after security incidents.

These recommendations are proposed improvements and are not claimed as fully implemented.

---

## ⚙️ 12. Installation and Lab Requirements

This repository documents an investigation rather than providing a deployable software application.

To reproduce a similar educational laboratory, the following components are required:

### Prerequisites

- A virtualisation platform capable of hosting multiple virtual machines.
- Kali Linux.
- Ubuntu Server.
- pfSense.
- Wazuh server and endpoint agent.
- Wireshark.
- Nmap.
- Hydra for authorised laboratory simulation.
- An isolated and appropriately configured virtual network.

### General Setup Workflow

1. Create the virtual machines.
2. Configure isolated virtual network segments.
3. Deploy pfSense as the firewall gateway.
4. Configure the Ubuntu target endpoint.
5. Deploy the Wazuh server.
6. Install and register the Wazuh agent on Ubuntu.
7. Confirm network connectivity and monitoring.
8. Configure Wireshark capture access.
9. Establish baseline network traffic.
10. Conduct authorised security simulations.
11. Review collected logs and packet captures.
12. Implement and validate defensive firewall controls.

The exact VM resources, network adapter settings, routing configuration, and installation commands were not provided in the report and should be documented separately for full reproducibility.

All simulations must be limited to systems and networks you own or are explicitly authorised to test.

---

## 📖 13. How to Use This Repository

This repository is designed for cybersecurity learners, SOC analysts, and recruiters interested in practical Blue Team investigations.

### Step 1 — Clone the Repository

```bash
git clone https://github.com/<your-username>/<repository-name>.git
```

### Step 2 — Open the Project

```bash
cd <repository-name>
```

### Step 3 — Review the Investigation Report

Read the SOC capstone report to understand:

- The incident scenario.
- The laboratory architecture.
- The investigation timeline.
- The evidence collected.
- The security findings.
- The containment actions.
- The final recommendations.

### Step 4 — Examine Supporting Evidence

Where supporting screenshots or evidence files are available, review:

- Wireshark packet captures.
- Nmap scan results.
- Wazuh security alerts.
- pfSense firewall logs.
- Containment verification records.

### Step 5 — Understand the SOC Workflow

Follow the investigation sequence:

**Detect → Investigate → Correlate → Assess → Contain → Verify → Report**

This workflow demonstrates how multiple defensive security technologies can support a structured incident investigation.

---

## 🎓 14. Skills and Learning Outcomes

Through this capstone project, I developed and demonstrated practical skills in:

### Security Operations

- SOC monitoring and incident investigation.
- Security event analysis.
- Threat detection and triage.
- Incident assessment and reporting.

### Network Security

- TCP/IP and ICMP analysis.
- Network traffic inspection.
- Port scanning detection.
- Firewall access control.
- Network-based containment.

### SIEM and Endpoint Monitoring

- Wazuh agent monitoring.
- Authentication event analysis.
- Security alert investigation.
- Network and endpoint evidence correlation.

### Incident Response

- Identification of suspicious activity.
- Evidence-based incident classification.
- Containment planning and execution.
- Verification of defensive actions.
- Documentation of findings and recommendations.

---

## 📈 15. Project Outcomes

The documented investigation achieved the following:

| Objective | Documented Outcome |
|---|---|
| Network monitoring | Traffic inspected using Wireshark |
| Reconnaissance detection | ICMP scanning and service discovery identified |
| SSH attack investigation | Repeated authentication failures analysed |
| Endpoint monitoring | Wazuh agent and alerts reviewed |
| Firewall investigation | pfSense logs examined |
| Incident containment | Blocking rule implemented |
| Containment validation | Connection timeouts and dropped packets reported |
| Reporting | SOC investigation report completed |

### Key Takeaway

Effective incident detection and response depend on combining visibility from different layers of the network.

Wireshark supported packet-level investigation, Wazuh provided endpoint security telemetry, and pfSense enabled network-level containment.

Together, these technologies demonstrated a practical defence-in-depth approach to investigating and responding to simulated cyber threats.

---

## 🚀 16. Future Improvements

Potential enhancements to this project include:

- Developing custom Wazuh detection rules.
- Introducing automated alert enrichment.
- Expanding SIEM dashboards.
- Testing additional authorised attack scenarios.
- Adding a documented incident severity matrix.
- Creating detailed incident response playbooks.
- Mapping additional validated activity to MITRE ATT&CK.
- Adding packet capture samples and sanitised event logs.
- Measuring detection and containment response times.

These improvements are proposed future work rather than completed project features.

---

## 🤝 17. Contributions

This repository forms part of my individual cybersecurity learning and professional portfolio.

Constructive suggestions are welcome, particularly concerning:

- SOC investigation techniques.
- Detection engineering.
- Wazuh alert analysis.
- Firewall security.
- Incident response methodology.
- Technical documentation.

To contribute:

1. Open a GitHub issue describing the suggested improvement.
2. Explain the technical or security benefit.
3. Provide relevant documentation or evidence.
4. Submit a pull request if repository contributions are enabled.

Please do not upload credentials, confidential logs, sensitive network information, or unauthorised attack data.

---

## 📚 18. References

- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [THC Hydra](https://github.com/vanhauser-thc/thc-hydra)
- [Ubuntu OpenSSH Documentation](https://ubuntu.com/server/docs/how-to/security/openssh-server/)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [NIST SP 800-61 Rev. 3](https://doi.org/10.6028/NIST.SP.800-61r3)

---

## 👨‍💻 19. About the Author

**Qhubekani Luphahla**  
**Cybersecurity | SOC Analysis | Network Security | GRC**

I am developing my cybersecurity expertise through practical security operations, network defence, incident response, and governance, risk and compliance projects.

My interests include:

- Security Operations Centre (SOC) Analysis
- Threat Detection and Incident Response
- Network Security Monitoring
- SIEM Technologies
- Vulnerability Assessment
- Governance, Risk and Compliance
- Cybersecurity Risk Management

This project demonstrates my ability to investigate suspicious activity, interpret security evidence, and apply defensive controls within a simulated enterprise network.

 
**LinkedIn:** www.linkedin.com/in/qhubekani-luphahla

---

## ⚠️ Disclaimer

This project was conducted for educational and cybersecurity training purposes in a simulated laboratory environment.

The tools, techniques, findings, and containment actions are documented solely to demonstrate authorised security investigation and defensive cybersecurity practices.

No unauthorised testing or access to real Barclays infrastructure is claimed.

---

**Developed by Qhubekani Luphahla | SOC Analyst Portfolio | 2026**
