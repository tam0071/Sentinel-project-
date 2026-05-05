# Microsoft Sentinel Lab 2: Investigating Failed Login Attacks

## Overview
This lab demonstrates detection and investigation of failed authentication attempts using Microsoft Sentinel and Microsoft Defender. It simulates a real-world SOC scenario where repeated login failures are analyzed to identify potential brute force attacks.

The lab validates how analytics rules generate alerts and how incidents are investigated within the Defender portal.

---

## Objectives
- Enable log ingestion from Microsoft Entra ID
- Simulate failed login attempts
- Validate analytics rule detection
- Investigate incidents in Microsoft Defender
- Identify brute force attack patterns

---

## Environment
- Platform: Microsoft Azure  
- SIEM: Microsoft Sentinel  
- Identity Source: Microsoft Entra ID  
- Investigation Tool: Microsoft Defender Portal  
- Data Sources: Sign-in Logs, Audit Logs  

---

## Step 1: Enable Data Connectors

1. Navigate to Microsoft Sentinel  
2. Go to **Configuration > Data Connectors**  
3. Select **Microsoft Entra ID**  
4. Enable:
   - Sign-in Logs  
   - Audit Logs  
5. Apply changes  

---

## Step 2: Simulate Failed Login Activity

- Use a test account  
- Perform multiple failed login attempts (≥ 5)  
- Enter incorrect credentials intentionally  

---

## Step 3: Verify Analytics Rule

Ensure the following rule is enabled:

- Rule Name: **Brute Force Login Detection**  
- Trigger: Failed login attempts > 5  
- Frequency: Every 5 minutes  

---

## Step 4: KQL Log Analysis

### Failed Login Detection

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress, UserPrincipalName
| order by FailedAttempts desc
```
## High Volume Log In Attempts

```kql
SigninLogs
| summarize AttemptCount = count() by IPAddress
| where AttemptCount > 10
| order by AttemptCount desc
```
## Step 5: Validate Detection in Defender Portal

1. Go to **Microsoft Defender Portal**
2. Navigate to:  
   **Investigation & Response > Incidents**
3. Open a generated incident

---

## Step 6: Incident Analysis

### Review
- Source IP Address  
- Target User Account  
- Number of Failed Attempts  
- Timestamp and frequency  

### Indicators
- Multiple failed attempts from one IP  
- Repeated targeting of a user  
- High-frequency login attempts  

---

## Step 7: Detection Validation

- Alerts triggered automatically by Microsoft Sentinel  
- Incidents generated in Microsoft Defender portal  
- Detection aligns with simulated attack activity  

---

## Step 8: Security Interpretation

Observed activity indicates brute force behavior:

- High authentication failure rate  
- Repeated login attempts from same IP  
- Credential guessing pattern  

### Recommended Actions

- Block malicious IP  
- Reset user credentials  
- Enforce Multi-Factor Authentication (MFA)  
- Monitor for continued suspicious activity  

---

## Optional: Azure CLI Commands

```bash
# List Log Analytics Workspaces
az monitor log-analytics workspace list --output table

# View diagnostic settings
az monitor diagnostic-settings list --resource <resource-id>
```
