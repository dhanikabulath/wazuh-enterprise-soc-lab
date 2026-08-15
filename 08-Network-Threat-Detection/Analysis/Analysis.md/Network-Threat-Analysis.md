# Network Threat Analysis

## Objective

Monitor endpoint network activity and investigate network connections using Sysmon and Wazuh.

## Telemetry

Sysmon network connection monitoring was enabled on the Windows 11 VM.

Network activity generated:

**Sysmon Event ID 3 – Network Connection**

The telemetry was forwarded through the Wazuh agent to the Wazuh SIEM.

## Controlled Reconnaissance

A limited Nmap TCP scan was performed against the Windows VM from the Ubuntu lab environment.

Selected ports included:

21, 22, 23, 25, 53, 80, 135, 139, 443, 445, 3389, 5985, and 8080.

The scan was performed only within the controlled home-lab environment.

## Wazuh Detection

Custom Wazuh Rule 100102 was created to generate an alert from Sysmon Event ID 3 network telemetry.

The rule successfully triggered after fresh network activity was generated.

## Investigation

Network telemetry can provide:

- Source IP and port
- Destination IP and port
- Protocol
- Process responsible for the connection
- User and endpoint context
- Connection direction

This information can be correlated with endpoint, authentication, process, and threat-intelligence telemetry during an investigation.

## Analyst Assessment

A network connection alone does not establish malicious activity.

SOC investigation should consider the destination reputation, process initiating the connection, unusual ports, user context, frequency, related process activity, and other endpoint alerts before escalation.

## Result

The lab successfully demonstrated the collection, forwarding, detection, and investigation of endpoint network connection telemetry using Sysmon and Wazuh.