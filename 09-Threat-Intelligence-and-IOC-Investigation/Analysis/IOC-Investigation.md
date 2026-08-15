# IOC Investigation

## Objective

Enrich external indicators of compromise and determine whether they appear within monitored Wazuh telemetry.

## IOC 1 – Domain

**Indicator:** testsafebrowsing.appspot.com  
**Type:** Domain

### Threat Intelligence

VirusTotal enrichment showed 2 security vendors flagging the test domain as malicious.

Vendor detections were treated as threat-intelligence context rather than independent proof of compromise.

### Internal Hunt

The domain was searched across Wazuh telemetry.

**Result:** 0 matches.

### Assessment

No evidence was identified showing that the monitored environment communicated with or referenced the domain during the searched period.

---

## IOC 2 – SHA-256

**Indicator:**

`275a021bbfb6489e54d471899f7db9d1663fc695ec2fe2a2c4538aabf651fd0f`

**Type:** SHA-256  
**Context:** EICAR anti-malware test file

### Threat Intelligence

VirusTotal reported 65 security vendor detections for the hash.

### Internal Hunt

The SHA-256 indicator was searched across Wazuh telemetry.

**Result:** 0 matches.

### Assessment

The external reputation indicated that the hash was strongly recognized by security products, but no corresponding evidence was present in the Wazuh data searched during this investigation.

## Final Analyst Verdict

```text
Domain IOC
VirusTotal: 2 detections
Wazuh:      0 matches

SHA-256 IOC
VirusTotal: 65 detections
Wazuh:      0 matches

Disposition:
No evidence of internal exposure identified.