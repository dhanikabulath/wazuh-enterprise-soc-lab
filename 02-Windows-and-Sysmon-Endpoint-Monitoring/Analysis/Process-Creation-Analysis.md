# Process Creation Analysis

## Event

Sysmon Event ID 1 records process creation activity on the Windows endpoint.

A controlled PowerShell process was executed:

`powershell.exe -Command "whoami; hostname"`

## Detection

Wazuh successfully ingested the Sysmon event from `CLIENT01` and generated:

- Rule ID: 67027
- Description: A process was created.
- Severity: Level 3

## Analysis

The event demonstrated that Wazuh could provide visibility into processes executed on the monitored endpoint.

Process and command-line information can be used by SOC analysts to identify suspicious PowerShell execution and investigate parent-child process relationships.

## Result

Process creation telemetry was successfully generated, collected, detected, and investigated through Wazuh.