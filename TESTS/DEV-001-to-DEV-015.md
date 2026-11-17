# Device Deviation Acceptance Tests (DEV-001 – DEV-015)

**Status:** Specification only. Not yet implemented or sealed.

| Test ID | Scenario | Expected Result |
|---------|----------|-----------------|
| DEV-001 | Device matches baseline | NORMAL |
| DEV-002 | Unauthorized OS configuration change | DRIFT |
| DEV-003 | Hardware identity mismatch | CRITICAL / HOLD |
| DEV-004 | Admission credential invalid | INVALID |
| DEV-005 | Observation permission revoked | UNKNOWN / HOLD affected observation |
| DEV-006 | Evidence older than validity period | STALE |
| DEV-007 | Approved software update | AUTHORIZED_DEVIATION |
| DEV-008 | Unapproved workflow execution | CRITICAL / HOLD |
| DEV-009 | Mesh connection interruption | OFFLINE / UNKNOWN |
| DEV-010 | Device attempts unauthorized execution | REFUSE |
| DEV-011 | Baseline modified without approval | INVALID |
| DEV-012 | Evidence hash mismatch | INVALID |
| DEV-013 | Device recovers after deviation | REVALIDATION REQUIRED |
| DEV-014 | JOE authorization boundary violated | REFUSE |
| DEV-015 | ALITA hardware safety boundary violated | HOLD |

## Required Adversarial Cases

- Replaying old healthy device evidence
- Replacing an accepted baseline without authorization
- Falsifying device identity
- Disconnecting from the mesh to avoid reporting
- Changing device time to manipulate evidence freshness
- Reusing one device's admission credential on another device
- Manipulating deviation percentages by excluding unknown controls
- Treating an approved change as blanket permission
- Treating successful CI execution as proof of implementation

Each test must preserve command, raw output, exit code, environment, source hashes, fixture hashes and SHA-256 integrity manifest.
