### Brute Force Attack 

## 🔍 Step 1: Attack Simulation (Failed Login Attempts)

To simulate brute force behavior:

- Performed multiple failed login attempts (3–5 times or more)  
- Used incorrect credentials intentionally  

This generated:
- Authentication failure logs  
- Source IP address tracking  
- Targeted user account data  

---

## 📊 Step 2: Log Analysis Using KQL

### 🔹 Failed Login Analysis

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress, UserPrincipalName
| order by FailedAttempts desc

SigninLogs
| summarize AttemptCount = count() by IPAddress
| order by AttemptCount desc
```

## 🚨 Step 3: Analytics Rule Creation (Brute Force Detection)

Created a scheduled analytics rule in Microsoft Sentinel:

- **Rule Name:** Brute Force Login Detection  
- **Severity:** Medium  
- **Trigger Condition:** Failed login attempts > 5  
- **Run Frequency:** Every 5 minutes  

### MITRE ATT&CK Mapping:
- Credential Access → Brute Force  

This rule automatically detects repeated authentication failures and generates alerts in Microsoft Sentinel.

---

## 🔔 Step 4: Incident Generation & Detection Validation

After triggering failed login attempts:

- Sentinel generated alerts automatically  
- Incidents were created in Microsoft Defender portal  
- Detection rule successfully identified brute force pattern  

### Observed Behavior:
- Multiple failed login attempts from the same IP address  
- Repeated targeting of specific user accounts  
- Time-based clustering of authentication failures  

---

## 🧠 Step 5: SOC Investigation Workflow

Using Microsoft Defender portal:

### Investigation Steps:
- Opened generated incidents  
- Reviewed:
  - Source IP address  
  - Target user account  
  - Number of failed attempts  
  - Time and frequency patterns  

### Findings:
- Consistent failed login pattern from a single IP  
- Targeted authentication attempts on specific user accounts  
- Behavior aligned with brute force attack techniques  

---

## 🧪 Skills Demonstrated

- Microsoft Sentinel deployment  
- SIEM architecture design  
- Log ingestion configuration  
- KQL query development  
- Threat detection engineering  
- Incident analysis and investigation  
- SOC workflow execution  
- Cloud security monitoring  
