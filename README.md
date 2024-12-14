# Network Setup and Security Guide for Remote Non-Profits (All Open Source & Free Tools)

This comprehensive guide provides a roadmap for fully remote non-profit organizations to set up and secure their networks using only free and open-source tools. It covers fundamental concepts, essential services, best practices, and strategies to protect sensitive data, ensuring a secure and sustainable digital environment that supports your mission.

---

## Table of Contents

- [Introduction](#introduction)  
- [Guiding Principles](#guiding-principles)  
- [Foundational Concepts](#foundational-concepts)  
  - [Zero-Trust Security](#zero-trust-security)  
  - [Open-Source First](#open-source-first)  
- [Architecture Overview](#architecture-overview)  
  - [VPN and Secure Remote Access](#vpn-and-secure-remote-access)  
  - [Cloud and On-Premise Hosting Considerations](#cloud-and-on-premise-hosting-considerations)  
  - [Identity and Access Management (IAM)](#identity-and-access-management-iam)  
  - [Network Segmentation](#network-segmentation)  
  - [Encrypted Communication](#encrypted-communication)  
- [Tools Summary](#tools-summary)  
- [Step-by-Step Setup](#step-by-step-setup)  
  - [VPN Setup](#vpn-setup)  
  - [File Sharing and Collaboration](#file-sharing-and-collaboration)  
  - [Secure Communication and Email](#secure-communication-and-email)  
  - [Identity and Access Management Setup](#identity-and-access-management-setup)  
  - [Encrypted Communication Implementation](#encrypted-communication-implementation)  
  - [Password Management](#password-management)  
- [Network Segmentation Details](#network-segmentation-details)  
- [Endpoint Security and Device Management](#endpoint-security-and-device-management)  
- [Monitoring, Logging, and Analysis](#monitoring-logging-and-analysis)  
- [Security Monitoring and Incident Response](#security-monitoring-and-incident-response)  
- [User Education and Awareness](#user-education-and-awareness)  
- [Continuous Improvement](#continuous-improvement)  
- [Automated Security Updates and Patch Management](#automated-security-updates-and-patch-management)  
- [Data Backup and Recovery](#data-backup-and-recovery)  
- [Cloud Security and Hardening](#cloud-security-and-hardening)  
- [Third-Party Risk Management](#third-party-risk-management)  
- [Compliance and Legal Considerations](#compliance-and-legal-considerations)  
- [Physical Security](#physical-security)  
- [Testing Your Security Posture](#testing-your-security-posture)  
- [Security Metrics and Reporting](#security-metrics-and-reporting)  
- [Additional Recommendations and Advanced Topics](#additional-recommendations-and-advanced-topics)  
- [Additional Resources](#additional-resources)  
- [Contributing](#contributing)  
- [Conclusion](#conclusion)  

---

## Introduction

Fully remote non-profits face unique cybersecurity challenges: distributed staff, limited budgets, and the need to safeguard donor information, financial data, and internal communications. This guide empowers you to build a strong security foundation using only open-source, free-to-use tools, ensuring cost-effective, transparent, and community-vetted solutions.


## Guiding Principles

- **Risk-Based Focus:** Identify and protect your most sensitive assets first.  
- **Simplicity & Accessibility:** Choose widely supported, user-friendly tools.  
- **Scalability & Flexibility:** Implement solutions that evolve with your organization.  
- **Transparency & Trust:** Use open-source tools for verifiable security and community support.  
- **Continuous Improvement:** Reassess and refine security measures regularly.


## Foundational Concepts

### Zero-Trust Security

Adopt a mindset where no user, device, or network is implicitly trusted. Every request to access sensitive resources should be authenticated, authorized, and encrypted.

### Open-Source First

Open-source tools provide transparency, community-driven development, and lower costs. By using open-source software, you can:

- Verify security through public code reviews.  
- Avoid vendor lock-in.  
- Benefit from large, active communities that provide ongoing support and improvements.


## Architecture Overview

A secure remote environment for your non-profit can be built with these core components:

### VPN and Secure Remote Access

- **WireGuard or OpenVPN:** These open-source VPNs create encrypted tunnels for staff to securely access internal resources over public networks.

### Cloud and On-Premise Hosting Considerations

You can host services on open-source-friendly cloud providers (or on-premise if feasible):

- Consider reputable providers that offer virtual machines (Linux-based) for hosting your chosen open-source tools.
- Always encrypt data in transit (TLS) and at rest.

### Identity and Access Management (IAM)

Centralize identity control and authentication:

- **Keycloak** or **FreeIPA:** Open-source IAM solutions that support Single Sign-On (SSO) and multi-factor authentication (MFA).

### Network Segmentation

Divide your network into zones to limit the impact of a breach:

- Use firewalls and VLANs to separate public-facing services from internal resources and sensitive data stores.

### Encrypted Communication

Ensure all communication channels are encrypted end-to-end where possible:

- **Signal:** Secure messaging, voice, and video.  
- **OpenPGP:** Standard for email encryption.


## Tools Summary

| Tool                                         | Function                                         |
|----------------------------------------------|--------------------------------------------------|
| **WireGuard/OpenVPN**                        | VPN for secure remote access                     |
| **Nextcloud**                                | Secure file sharing & collaboration              |
| **Mattermost**                               | Team communication (chat, channels, file sharing)|
| **Keycloak/FreeIPA**                         | IAM, SSO, MFA                                    |
| **Signal**                                    | Encrypted messaging & calling                    |
| **OpenPGP (GnuPG)**                          | Email/file encryption                            |
| **Mail-in-a-Box or Modoboa**                 | Self-hosted email server & security hardening    |
| **Bitwarden (Self-Hosted)**                  | Password management                              |
| **Wazuh**                                    | Open-source SIEM and endpoint security           |
| **OpenVAS (Greenbone Community Edition)**     | Vulnerability scanning                           |
| **Renovate**                                 | Automated dependency updates                     |
| **Ansible/Puppet/Chef**                      | Configuration & patch management                 |
| **BorgBackup or Restic**                     | Encrypted backups                                |
| **MeshCentral**                              | Open source remote device management             |


## Step-by-Step Setup

### VPN Setup

1. **Choose a VPN:**  
   - **WireGuard:** Modern, lightweight, high-performance.  
   - **OpenVPN:** Mature, flexible, widely supported.

2. **Deploy the VPN Server:**  
   - Run on a Linux-based VM.  
   - Harden by disabling unnecessary services and applying updates regularly.

3. **Client Profiles:**  
   - Generate unique keys for each user.  
   - Distribute configs securely (e.g., via encrypted email or a secure portal in Nextcloud).

4. **Mandatory Use:**  
   - Require VPN use for all internal systems, ensuring encrypted access for staff.

### File Sharing and Collaboration

1. **Nextcloud Setup:**  
   - Install Nextcloud on a secure server or VM.  
   - Enable end-to-end encryption and two-factor authentication.  
   - Store sensitive documents here rather than on staff laptops.

2. **Mattermost for Communication:**  
   - Host Mattermost on a secure VM behind your VPN.  
   - Integrate with Keycloak for SSO.  
   - Use private channels for sensitive discussions.

### Secure Communication and Email

1. **Encrypted Email Server:**  
   - Deploy **Mail-in-a-Box** or **Modoboa** for a self-hosted, open-source email solution.  
   - Configure DNS records (SPF, DKIM, DMARC) to prevent spoofing.

2. **Email Encryption (OpenPGP):**  
   - Train staff to use GnuPG for encrypting sensitive emails.  
   - Integrate with Thunderbird (Enigmail or native OpenPGP support) for user-friendliness.

3. **Messaging via Signal:**  
   - Encourage Signal for sensitive one-to-one and group communications.  
   - Avoid SMS or unencrypted chat tools.

### Identity and Access Management Setup

1. **Keycloak or FreeIPA:**  
   - Centralize user accounts and roles.  
   - Provide SSO, reducing password fatigue.  
   - Enforce MFA with TOTP-based authenticators (e.g., FreeOTP or andOTP).

2. **Role-Based Access Control (RBAC):**  
   - Define roles (e.g., Admin, Finance, Volunteer) and assign only necessary permissions.  
   - Regularly audit user roles and offboard departed staff promptly.

### Encrypted Communication Implementation

1. **Force TLS Everywhere:**  
   - Use Let’s Encrypt for free TLS certificates on all web services (Nextcloud, Mattermost, Keycloak).

2. **SSH / SFTP:**  
   - Use SSH for remote administration. Disable Telnet and FTP.  
   - Require key-based authentication over passwords for admin access.

### Password Management

1. **Bitwarden (Self-Hosted):**  
   - Deploy a self-hosted Bitwarden server for password storage.  
   - Enforce strong, unique passwords and encourage password sharing through secure vaults.  
   - Enable 2FA for password vault access.


## Network Segmentation Details

1. **Define Zones:**  
   - **Public Zone:** Minimal internet-facing services (e.g., email server interfaces).  
   - **Internal Zone:** Systems accessible only via VPN (Nextcloud, Mattermost).  
   - **Restricted Zone:** Sensitive services (IAM, financial data) locked down to specific roles.

2. **Use Firewalls and VLANs:**  
   - Apply the principle of least privilege: only allow necessary traffic between zones.  
   - Keep the restricted zone isolated and accessible only after strict authentication.

3. **Regular Reviews:**  
   - Periodically review firewall rules and VLAN assignments as your organization evolves.


## Endpoint Security and Device Management

1. **Device Baselines:**  
   - Enforce full-disk encryption (e.g., LUKS for Linux) on staff laptops.  
   - Require OS-level security patches, antivirus (e.g., ClamAV), and firewall enabled by default.

2. **Open Source Endpoint Management:**  
   - Use **MeshCentral** for remote device management and monitoring.  
   - Ensure devices meet security standards before granting VPN access.

3. **Personal vs. Work Devices:**  
   - Strongly encourage using dedicated work devices for staff handling sensitive data.  
   - If personal devices must be used, ensure strict security policies apply.


## Monitoring, Logging, and Analysis

1. **SIEM with Wazuh:**  
   - Deploy Wazuh to collect logs from servers, VPN, IAM, and endpoints.  
   - Configure rules for detecting suspicious behavior.

2. **Dashboards & Alerts:**  
   - Set up dashboards for critical events (failed logins, unusual network activity).  
   - Configure email or Mattermost alerts for critical security events.


## Security Monitoring and Incident Response

1. **Incident Response Plan (IRP):**  
   - Follow frameworks like [NIST SP 800-61r2].  
   - Define communication channels, escalation paths, and clear roles for handling incidents.

2. **Vulnerability Scanning with OpenVAS:**  
   - Run regular scans to detect missing patches and misconfigurations.  
   - Remediate findings promptly and record improvements over time.

3. **Regular Drills:**  
   - Conduct tabletop exercises to ensure your team is prepared for real incidents.


## User Education and Awareness

1. **Training:**  
   - Offer basic cybersecurity training for all staff (phishing, password hygiene, identifying suspicious behavior).  
   - Provide ongoing education with simple guides and periodic security newsletters.

2. **Policy Accessibility:**  
   - Keep security policies in Nextcloud, accessible and easy to understand.  
   - Encourage staff to ask questions and clarify doubts.

3. **Reporting Culture:**  
   - Incentivize staff to report suspicious incidents promptly, without fear of blame.



## Continuous Improvement

1. **Scheduled Reviews:**  
   - Quarterly or annual security audits to update policies, tools, and configurations.

2. **Stay Informed:**  
   - Subscribe to open-source security mailing lists, RSS feeds, and non-profit tech communities.

3. **Community Engagement:**  
   - Participate in open-source forums and non-profit security groups to share experiences and stay current.


## Automated Security Updates and Patch Management

1. **OS & Application Patches:**  
   - Configure unattended-upgrades or similar tools for automatic patching of Linux servers.  
   - Use Ansible or Puppet to apply consistent security patches across multiple hosts.

2. **Dependency Management with Renovate:**  
   - Automate dependency updates for web applications or tools you maintain.  
   - Review changes before production deployment to ensure stability.


## Data Backup and Recovery

1. **Regular Backups:**  
   - Use **BorgBackup** or **Restic** for encrypted, incremental backups of critical data.  
   - Perform daily incremental and weekly full backups.

2. **Off-Site Storage:**  
   - Store backups off-site or in a different cloud region. Encrypt them before upload.

3. **Disaster Recovery Drills:**  
   - Test restore procedures regularly to ensure reliability and resilience against ransomware and data loss.


## Cloud Security and Hardening

1. **Least Privilege Cloud Roles:**  
   - Assign minimal IAM roles in the cloud environment. Restrict access to production servers.

2. **Encryption:**  
   - Always enable TLS for data in transit and use native encryption options for data at rest (e.g., LUKS or cloud-based encryption keys).

3. **Secure Configurations:**  
   - Regularly review firewall rules, security groups, and access logs in the cloud.

4. **Monitoring:**  
   - Send cloud logs to Wazuh for centralized alerting and incident response.


## Third-Party Risk Management

1. **Vendor Security Checks:**  
   - When using external open-source solutions or cloud services, review their documentation, security track record, and community reputation.

2. **License Review:**  
   - Ensure all tools comply with open-source licenses that align with your organization’s values and requirements.


## Compliance and Legal Considerations

1. **Identify Applicable Regulations:**  
   - Understand data protection regulations relevant to your jurisdiction (e.g., GDPR for EU data).

2. **Implement Controls:**  
   - Align policies with recognized frameworks (CIS Controls, NIST CSF) for guidance and compliance.

3. **Documentation:**  
   - Keep records of compliance efforts, configuration changes, and security incidents for auditing purposes.


## Physical Security

1. **Device Protection:**  
   - If there is an office or data center presence, lock servers in secure cabinets.  
   - Use cable locks for laptops and secure destruction methods (e.g., wiping or shredding disks) when decommissioning hardware.

2. **Environmental Protections:**  
   - Keep backups in safe locations, protected from fire, flooding, or theft.


## Testing Your Security Posture

1. **Tabletop Exercises:**  
   - Simulate phishing attacks or system breaches to test staff responses and IRP effectiveness.

2. **Ongoing Improvement:**  
   - Refine incident response plans based on lessons learned.


## Security Metrics and Reporting

1. **Key Metrics:**  
   - Track metrics such as patching timeframes, incident response times, and vulnerability counts.

2. **Regular Reporting:**  
   - Provide summaries to stakeholders (board members, donors) to demonstrate ongoing improvements and accountability.

3. **Data-Driven Adjustments:**  
   - Use metrics to prioritize where to invest time and resources (e.g., more training if phishing attempts are frequent).


## Additional Recommendations and Advanced Topics

- **Infrastructure as Code (IaC):**  
  - Use Terraform or Ansible to define and deploy secure configurations repeatedly and reliably.
  
- **Container Security:**  
  - If using containers (Docker, Kubernetes), adopt scanning tools (Trivy, Anchore) for open-source images.
  
- **Micro-Segmentation:**  
  - Consider advanced identity-based segmentation for critical services as you grow.


## Additional Resources

- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)  
- [CIS Controls](https://www.cisecurity.org/controls/)  
- [Open Source Security Foundation (OpenSSF)](https://openssf.org/)  
- [OWASP](https://owasp.org/) for Web Application Security  
- [GnuPG](https://gnupg.org/) for encryption guidance  
- [EFF Surveillance Self-Defense](https://ssd.eff.org/) for user-friendly security instructions

## Contributing

This guide thrives on community input. If you have suggestions, improvements, or additional tools to recommend, please submit a pull request or open an issue in the repository hosting this document.

## Conclusion

By following these recommendations and leveraging free, open-source tools, your fully remote non-profit can establish a robust and cost-effective cybersecurity posture. Encourage continuous learning, adapt to emerging threats, and foster a security-conscious culture within your team. With the right mindset and resources, you can protect your organization, its donors, and the communities you serve.

---

**Disclaimer:** This document is provided for informational purposes only. No security measure is foolproof. Consult with cybersecurity professionals as needed and continuously adapt to new threats and challenges.
