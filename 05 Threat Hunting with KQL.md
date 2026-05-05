# Microsoft Sentinel Lab 4: Threat Hunting with KQL

## Overview
This lab focuses on proactive threat hunting using KQL (Kusto Query Language) in Microsoft Sentinel. Instead of relying solely on alerts, this exercise demonstrates how SOC analysts identify suspicious behavior directly from log data.

---

## Objectives
- Perform proactive threat hunting using KQL
- Identify failed login patterns
- Detect high-frequency login attempts
- Investigate suspicious IP activity
- Understand attacker behavior patterns

---

## Step 1: Access Logs in Microsoft Sentinel

Navigate to:

Microsoft Sentinel → Select Workspace → Logs

---

## Step 2: Detect Failed Login Attempts

### KQL Query
```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by IPAddress, UserPrincipalName
| order by FailedAttempts desc
```

## Step 3: Detect High Login Attempt Volume

### KQL Query
```kql
SigninLogs
| summarize AttemptCount = count() by IPAddress
| order by AttemptCount desc
```


## Step 4: Detect Impossible Travel Activity
```kql
SigninLogs
| project UserPrincipalName, IPAddress, Location, TimeGenerated
| order by UserPrincipalName, TimeGenerated asc
```

## Step 5: Threat Hunting Analysis

During analysis, investigate:

Suspicious IP addresses
Repeated failed login attempts
Targeted user accounts
Time-based patterns of activity
Geographic anomalies

## Step 6: Investigation Questions
Is the IP address known or suspicious?
Is a specific user being targeted?
Are login attempts happening in rapid succession?
Does the behavior match brute force patterns?

## Key Takeaways
Threat hunting is proactive, not reactive.
KQL enables deep visibility into log data.
Not all anomalies indicate attacks, but pattern analysis is critical.
Identifying suspicious behavior early reduces risk.
