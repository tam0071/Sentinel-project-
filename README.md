# Microsoft Sentinel SOC Labs – Complete Project Series

---

These labs are designed to reflect how real SOC analysts and cloud security engineers operate using Microsoft Sentinel and Microsoft Defender in Azure environments.

---

## Project Goals

- Build a functional SIEM environment using Microsoft Sentinel  
- Ingest and analyze authentication logs from Microsoft Entra ID  
- Detect brute force attacks and suspicious login behavior  
- Perform SOC-style incident investigation and triage  
- Create custom detection rules for privilege escalation scenarios  
- Develop threat hunting skills using KQL (Kusto Query Language)  
- Understand real-world cloud security monitoring workflows  

---

## Lab Series Structure

### Lab 1: Microsoft Sentinel SIEM Deployment & Brute Force Detection
- Created Log Analytics Workspace  
- Enabled Microsoft Sentinel  
- Integrated Microsoft Entra ID logs  
- Simulated failed login attempts  
- Built brute force detection rule using KQL  
- Generated alerts and incidents  

**Key Focus:** SIEM setup, log ingestion, authentication monitoring  

---

### Lab 2: Investigating Failed Login Attacks (SOC Analyst Workflow)
- Enabled sign-in and audit logs via Defender portal  
- Simulated failed login attack behavior  
- Investigated incidents in Microsoft Defender  
- Analyzed IP addresses, users, and login patterns  
- Validated detection accuracy  

**Key Focus:** Incident investigation, alert validation, SOC triage  

---

### Lab 3: SOC Incident Investigation & Response
- Opened and analyzed Sentinel incidents  
- Reviewed attack scope (IP, user, timestamps)  
- Used KQL queries for validation  
- Classified incidents (In Progress workflow)  
- Defined response actions  

**Key Focus:** Incident response, SOC investigation lifecycle  

---

### Lab 4: Threat Hunting with KQL
- Performed proactive threat hunting  
- Identified high-volume login attempts  
- Analyzed failed sign-in patterns  
- Explored impossible travel scenarios  
- Investigated suspicious IP behavior  

**Key Focus:** Threat hunting, behavioral analysis, KQL mastery  

---

## Technologies Used

- Microsoft Sentinel (SIEM/SOAR)
- Microsoft Defender Portal
- Microsoft Entra ID (Azure AD)
- Kusto Query Language (KQL)
- Azure Log Analytics Workspace
- Azure CLI (optional validation)

---

## Security Concepts Covered

- Brute Force Attacks  
- Credential Stuffing  
- Privilege Escalation  
- Account Takeover Detection  
- Suspicious Authentication Patterns  
- Impossible Travel Detection  
- Cloud Identity Monitoring  

---

## Skills Demonstrated

- SIEM deployment and configuration  
- Log ingestion and normalization  
- KQL query development and optimization  
- SOC incident investigation workflow    
- Cloud security monitoring and response  
- Security analytics and behavioral analysis  

---
