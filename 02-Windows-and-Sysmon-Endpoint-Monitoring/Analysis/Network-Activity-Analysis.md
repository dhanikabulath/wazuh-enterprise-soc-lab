# Network Activity Analysis

## Objective

The lab also evaluated whether the current native Sysmon configuration captured network connection telemetry.

## Observation

Test network activity was generated from the Windows endpoint. However, Sysmon Event ID 3 was not observed with the current configuration.

The observed Sysmon telemetry primarily included:

- Event ID 1 – Process Creation
- Event ID 5 – Process Termination

## Finding

Sysmon network connection monitoring depends on the active Sysmon configuration. The current configuration provided process-level visibility but did not produce Event ID 3 during testing.

Network telemetry collection can be enabled and tuned in a future detection-engineering exercise.

## Result

The test demonstrated an important monitoring principle: telemetry availability depends on endpoint logging configuration, and analysts should validate data sources before relying on them for detection.