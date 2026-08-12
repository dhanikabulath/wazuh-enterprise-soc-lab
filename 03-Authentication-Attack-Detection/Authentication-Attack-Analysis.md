# Authentication Attack Analysis

## Scenario

Multiple failed authentication attempts were generated against the local `SOC-Test` account on `CLIENT01`.

## Evidence

Windows recorded the failed authentication activity using Security Event ID 4625.

The events were forwarded to Wazuh, where repeated failures were correlated.

## Detection

Wazuh generated:

- Rule ID: 60204
- Description: Multiple login failures
- Total observed hits: 9

## Analyst Assessment

The repeated authentication failures represented a pattern consistent with attempted credential guessing.

Individual authentication failures may have limited significance in isolation. Correlation of repeated failures provides stronger evidence of potentially suspicious authentication activity.

The analyst can use the target account, timestamps, source information, logon type, and failure status to determine the scope and origin of the activity.

## Conclusion

Wazuh successfully detected and correlated repeated Windows authentication failures, demonstrating centralized authentication monitoring and detection of suspicious login behaviour.