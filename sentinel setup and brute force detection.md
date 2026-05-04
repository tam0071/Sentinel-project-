# Microsoft Sentinel SOC Lab – SIEM Deployment & Brute Force Detection

## Project Overview
This project demonstrates a hands-on implementation of a Security Information and Event Management (SIEM) solution using Microsoft Sentinel. The lab simulates real-world SOC operations including log ingestion, threat detection, and brute force attack monitoring in a cloud environment.

The system is integrated with Microsoft Entra ID (Azure Active Directory) to collect authentication logs and detect suspicious login activity using KQL (Kusto Query Language).

This lab reflects real SOC workflows used by cloud security engineers and SOC analysts.

---

## Objectives
- Deploy a SIEM environment using Microsoft Sentinel  
- Connect Microsoft Entra ID for log ingestion  
- Analyze authentication logs in real time  
- Detect brute force login attempts using KQL  
- Create analytics rules for automated alerting  
- Simulate attacker behavior through failed login attempts  
- Validate detection through incident generation  

---

## Lab Architecture
- **Cloud Platform:** Microsoft Azure  
- **SIEM Tool:** Microsoft Sentinel  
- **Identity Source:** Microsoft Entra ID  
- **Log Source:** Sign-in Logs + Audit Logs  
- **Query Language:** KQL (Kusto Query Language)  
- **Investigation Tool:** Microsoft Defender Portal  

---

## ⚙️ Step 1: Log Analytics Workspace Setup

- Created a Log Analytics Workspace in Azure  
- Configured Sentinel on top of the workspace  
- Defined workspace for centralized log storage and analysis  

This workspace acts as the core ingestion point for all security logs.

---

## 🔗 Step 2: Microsoft Sentinel Deployment

- Enabled Microsoft Sentinel on the Log Analytics Workspace  
- Connected Sentinel to the Azure environment  
- Established SIEM layer for monitoring and detection  

Sentinel acts as the central platform for detection, investigation, and response.

---

## 🔐 Step 3: Microsoft Entra ID Integration

- Connected Microsoft Entra ID to Sentinel  
- Enabled:
  - Sign-in Logs  
  - Audit Logs  

These logs provide visibility into:
- Authentication attempts  
- Failed login activity  
- User identity behavior  

> ⚠️ Diagnostic settings must be enabled or logs will not flow into Sentinel.

---

## ⚠️ Step 4: Diagnostic Settings Configuration

- Configured diagnostic settings in Entra ID  
- Routed logs to Log Analytics Workspace  
- Selected:
  - Sign-in logs  
  - Audit logs  

This step is critical for enabling detection visibility inside Sentinel.

---

## 💰 Step 5: Cost Awareness

- Disabled logs after testing to avoid unnecessary Azure charges  
- Prevented continuous log ingestion costs  

---

## 🔍 Step 6: Attack Simulation (Failed Login Attempts)

To simulate brute force behavior:

- Performed multiple failed login attempts (3–5 times or more)  
- Used incorrect credentials intentionally  

This generated:
- Authentication failure logs  
- Source IP address tracking  
- Targeted user account data  

---

## 📊 Step 7: Log Analysis Using KQL

### 🔹 Failed Login Analysis
```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress, UserPrincipalName
| order by FailedAttempts desc
