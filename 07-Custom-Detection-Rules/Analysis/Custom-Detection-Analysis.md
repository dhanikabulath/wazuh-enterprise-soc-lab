# Custom Detection Analysis

## Objective

Develop and validate custom Wazuh detection logic using Sysmon process creation telemetry.

## Detection 1 – Controlled PowerShell Activity

A PowerShell process containing the unique `SOCLabDetection` marker was generated on the Windows endpoint.

Sysmon recorded the activity as Event ID 1.

Custom Wazuh Rule 100100 successfully identified the command and generated a Level 8 alert.

## Detection 2 – Encoded PowerShell

A harmless PowerShell command was Base64 encoded and executed using the `-EncodedCommand` parameter.

Custom Wazuh Rule 100101 detected the encoded PowerShell execution and generated a Level 10 alert.

## MITRE ATT&CK

The activity was mapped to:

**T1059.001 – PowerShell**

## Analyst Assessment

Encoded PowerShell activity warrants additional investigation because command encoding can be used to obscure execution content.

An analyst should review:

- Full command line
- Parent process
- User account
- Endpoint
- Execution time
- Related network activity
- Subsequent child processes

The presence of encoded PowerShell alone does not establish malicious activity, so surrounding telemetry should be reviewed before escalation.

## Result

Both custom detection rules successfully triggered against their intended test conditions, demonstrating the ability to create, validate, and investigate custom Wazuh detections.