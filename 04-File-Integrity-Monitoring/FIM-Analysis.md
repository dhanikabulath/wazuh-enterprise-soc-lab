# File Integrity Monitoring Analysis

## Scenario

A dedicated directory on `CLIENT01` was configured for real-time Wazuh File Integrity Monitoring.

Controlled file creation, modification, and deletion operations were performed.

## Detection

Wazuh generated:

- Rule 554 – File added to the system
- Rule 550 – Integrity checksum changed
- Rule 553 – File deleted

## Analysis

The modification generated a Level 7 alert, demonstrating that Wazuh can identify integrity changes to monitored files.

FIM provides SOC analysts with visibility into unexpected changes to sensitive files and directories.

## Result

Wazuh successfully detected the complete file lifecycle: creation, modification, and deletion.