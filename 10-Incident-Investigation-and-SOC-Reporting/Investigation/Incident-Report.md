# SOC Incident Report

## Incident Summary

A Wazuh Level 10 alert was generated after an encoded PowerShell command executed on the monitored Windows 11 VM.

The activity triggered custom Wazuh Rule 100101 and was mapped to MITRE ATT&CK T1059.001 – PowerShell.

## Alert Details

| Field | Finding |
|---|---|
| Detection | Encoded PowerShell execution |
| Wazuh Rule | 100101 |
| Rule Level | 10 |
| Sysmon Event | Event ID 1 |
| MITRE ATT&CK | T1059.001 |
| Initial Severity | High |
| Status | Investigated |

## Process Investigation

Sysmon process telemetry confirmed execution of `powershell.exe`.

The command line contained:

`-EncodedCommand`

Process, command-line, user, and endpoint context were reviewed to determine whether additional suspicious activity occurred.

## Network Investigation

Sysmon Event ID 3 telemetry was searched around the incident timestamp.

No network connections associated with the PowerShell process were identified during the investigated time window.

## Scope Assessment

No evidence was identified indicating:

- PowerShell-related network communication
- Command-and-control activity
- Additional malicious process execution
- Lateral movement
- Follow-on compromise

## MITRE ATT&CK

**T1059.001 – Command and Scripting Interpreter: PowerShell**

The technique mapping reflects the observed execution method. ATT&CK mapping alone does not establish malicious intent.

## Analyst Assessment

The encoded PowerShell execution was successfully detected by the custom Wazuh rule.

Because the command was intentionally executed as part of an authorized SOC lab and the investigation identified no evidence of malicious follow-on activity, the detection is classified as a true positive with benign context.

## Final Disposition

**Detection Accuracy:** True Positive  
**Activity Classification:** Authorized / Benign Test Activity  
**Evidence of Compromise:** None identified  
**Final Status:** Closed

## Analyst Recommendation

No containment or eradication action is required for this controlled test.

In a production environment, unexpected encoded PowerShell execution should be investigated using process lineage, command-line content, user context, network connections, related endpoint alerts, and threat-intelligence evidence before determining the appropriate response.