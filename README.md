# Scattered Spider – Threat Intelligence Analysis in MISP

## Table of Contents
- [Project Overview](#project-overview)
- [Executive Summary](#executive-summary)
- [Threat Actor Analysis](#threat-actor-analysis)
- [Technical Implementation](#technical-implementation)
- [MISP Configuration & Setup](#misp-configuration--setup)
- [Threat Intelligence Enrichment](#threat-intelligence-enrichment)
- [MITRE ATT&CK Mapping](#mitre-attck-mapping)
- [Key Findings & IOCs](#key-findings--iocs)
- [Conclusion & Defense Recommendations](#conclusion--defense-recommendations)

## Project Overview

**Project:** Real-time Threat Intelligence Analysis of Scattered Spider (UNC3944)  
**Platform:** MISP (Malware Information Sharing Platform)  
**Threat Actor:** Scattered Spider / UNC3944 / Muddled Libra  
**Threat Level:** CRITICAL  
**Date:** December 2025  

## Executive Summary

> **"From Social Engineering to Ransomware: Tracking a Post-MFA Adversary in Real-Time"**

This project demonstrates a comprehensive threat intelligence investigation of Scattered Spider, one of today's most sophisticated cybercriminal groups. Through hands-on analysis in MISP, I transformed raw OSINT into actionable intelligence, creating a living threat profile that enables proactive defense against this identity-focused adversary.

![MISP Dashboard](./images/image%200.jpg)

## Threat Actor Analysis

### Scattered Spider Overview
Scattered Spider is a sophisticated, native English-speaking cybercriminal group that has been actively targeting global enterprises since 2022. The group is highly adept at social engineering, specializing in impersonating IT and help-desk staff to gain initial access. Their primary focus is on exploiting identity systems through techniques like MFA fatigue attacks and SIM swapping to bypass security controls and compromise credentials.

**Key Characteristics:**
- **Native English-speaking operators** aged 16-25
- **Specialization:** Identity system compromise and social engineering
- **Evolution:** From data theft to ransomware affiliate operations
- **Targeting:** Cross-sector attacks with cloud identity focus

## Technical Implementation

### MISP Platform Deployment

#### Step 1: Docker Environment Setup
```bash
# System preparation and Docker installation
sudo apt-get update
```
*Image 1a: System package repository update*

![System Update](./images/image%201a.jpg)

```bash
sudo apt-get install ca-certificates curl
```
*Image 1b: Installing essential security certificates*

![Certificate Installation](./images/IMAMGE%201b.jpg)
![Certificate Installation](./images/image%201c.jpg)
![Certificate Installation](./images/IMAGE%201d.jpg)

#### Step 2: Docker Repository Configuration
```bash
# Adding Docker's official repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian bookworm stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
*Image 2a: Docker repository configuration*

![Docker Repository](./images/IMAGE%202a.jpg)
![Docker Repository](./images/IMAGE%202b.jpg)
![Docker Repository](./images/IMAGE%202C.jpg)



#### Step 3: MISP Deployment
```bash
# Clone MISP docker repository and deploy
git clone https://github.com/MISP/misp-docker-new
cd misp-docker-new/
docker compose up -d
```
*Image 4-8: MISP container deployment process*

![MISP Deployment](./images/IMAGE%203a.jpg)

![MISP Deployment](./images/IMAGE%204.jpg)

![MISP Deployment](./images/image%205.jpg)

![MISP Deployment](./images/IMAGE%206.jpg)

![MISP Deployment](./images/IMAGE%207.jpg)






## MISP Configuration & Setup

### Platform Access & Initialization
**Access URL:** `https://localhost`  
**Credentials:** admin@admin.test / admin

*Image 9: MISP Login Interface*

![MISP Login](./images/IMAGE%209a.jpg)

### Event Creation Process
```markdown
1. Navigate to Events → Add Event
2. Populate metadata: Threat Actor, Distribution Level
3. Submit to generate event UUID
```

*Image 10a-10b: Creating new threat intelligence event*

![Event Creation](./images/image%2010a.jpg)
![Event Creation](./images/image%2010b.jpg)

## Threat Intelligence Enrichment

### Attribute Population & IOC Management

#### Manual Attribute Addition
*Image 11a-11b: Adding structured attributes to the threat event*

![Attribute Addition](./images/image%2011a.jpg)
![Attribute Addition](./images/image%2011b.jpg)
#### Freetext IOC Import
**Capability Demonstrated:** Automated IOC classification and categorization

*Image 13a-13c: Bulk IOC import via freetext tool*

![Freetext Import](./images/image%2013a.jpg)

![Freetext Import](./images/image%2013b.jpg)

![Freetext Import](./images/image%2013c.jpg)

### Intelligence Validation
*Image 14a-14b: IOC validation and categorization review*

![IOC Validation](./images/IMAGE%2014A.jpg)

![IOC Validation](./images/image%2014b.jpg)

## MITRE ATT&CK Mapping

### Strategic TTP Mapping Process

#### Technique Integration
```yaml
Techniques Mapped:
  - T1589.001: Gather Victim Identity Information
  - T1660: Social Engineering
  - T1621: MFA Request Generation
  - T1555.005: Credentials from Password Stores
  - T1021.001: Remote Desktop Protocol
  - T1087: Cloud Account Persistence
  - T1486: Data Encrypted for Impact
```

*Image 18a-18c: MITRE ATT&CK framework integration*

![MITRE Mapping](./images/IMAGE%2018a.jpg)

![MITRE Mapping](./images/image%2018b.jpg)

![MITRE Mapping](./images/image%2018c.jpg)

### Custom Taxonomy Implementation

#### OSINT Classification Tag
```markdown
Tag Created: `osint:malware-patrol`
- Purpose: Source classification and intelligence provenance
- Color-coded for visual identification
- Export-enabled for intelligence sharing
```

*Image 16-17: Custom taxonomy creation and application*

![Custom Taxonomy](./images/image%2016.jpg)

![Custom Taxonomy](./images/image%2016b.jpg)

![Custom Taxonomy](./images/image%2017.jpg)
## Key Findings & IOCs

### Comprehensive Threat Profile
*Image 15a-15b: Complete threat actor profile display*

![Threat Profile](./images/image%2015a.jpg)

![Threat Profile](./images/image%2015b.jpg)

### Critical Indicators Extracted

**IP Addresses:**
```text
185.208.156.251 | 84.200.205.9 | 137.220.43.146
149.248.8.85   | 149.28.41.193 | 146.45.77.214
```

**Malicious Domains:**
```text
complete-sendgrid[.]com
aws-us3-manageprod[.]com  
internal-ssologin[.]com
targetsname-sso[.]com
```

**File Hashes:**
```text
MD5: 1155560e1e4ea8fcce047514a52950859
SHA256: 3ea2d190879c8933363b222c686009b81ba8af9eb6ae3696d2f420e187467f08
```

## Conclusion & Defense Recommendations

### Event Publication & Intelligence Sharing
*Image 20-21: Final event publication and distribution*

![Event Publication](./images/image%2020.jpg)

![Event Publication](./images/image%2021.jpg)

### Strategic Defense Recommendations

1. **Identity-Centric Security**
   - Implement phishing-resistant MFA
   - Monitor for MFA fatigue patterns
   - Enforce strict helpdesk verification

2. **Cloud Environment Hardening**
   - Conditional access policies
   - Legacy authentication protocol restrictions
   - Suspicious API call monitoring

3. **Proactive Threat Hunting**
   - Leverage mapped MITRE techniques
   - Custom detection rules based on IOCs
   - Continuous intelligence feed updates

### Project Impact & Skills Demonstrated

✅ **Threat Intelligence Lifecycle Management**  
✅ **MISP Platform Expertise**  
✅ **IOC Management & Enrichment**  
✅ **MITRE ATT&CK Framework Application**  
✅ **Custom Taxonomy Development**  
✅ **Containerized Security Deployment**  
✅ **Threat Actor Profiling**  
✅ **Intelligence Sharing Protocols**

---

**Tags:** `#ThreatIntelligence` `#MISP` `#SOC` `#ScatteredSpider` `#MITREATTACK` `#CyberSecurity` `#IOC` `#ThreatHunting`

*This project demonstrates practical threat intelligence skills applicable to enterprise security operations, showcasing the complete lifecycle from intelligence collection to actionable defense recommendations.*

---

**Connect with me on GitHub** for more threat intelligence projects and security analysis work.