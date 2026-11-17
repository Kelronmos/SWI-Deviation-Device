# Device Evidence Model

## Evidence Lifecycle

`OBSERVED → RECORDED → HASHED → VALIDATED → CLASSIFIED → REVIEWED → SEALED`

Sealing does not imply the implementation is proven or production-authorized.

## Canonical Evidence Fields

| Field | Purpose |
|-------|---------|
| event_id | Unique event reference |
| device_id | Bound device identity |
| baseline_id | Reference baseline |
| baseline_version | Exact version evaluated |
| control_id | Requirement being assessed |
| expected_state | Approved expectation |
| observed_state | Actual observation |
| observation_method | How the result was obtained |
| observation_time | Timestamp |
| evidence_hash | Integrity verification |
| evidence_source | Provenance |
| freshness_status | Current, stale or unknown |
| deviation_class | Classification |
| severity | Consequence assessment |
| joe_assessment | Human-protection assessment |
| alita_assessment | Hardware-protection assessment |
| authority_reference | Applicable permission record |
| replay_reference | Reproduction information |
| decision_record | Subsequent governed response |

## Integrity Rules

- SHA-256 evidence integrity manifests required
- Source, test and fixture hashes where applicable
- Immutable or tamper-evident event history
- Explicit clock source and time-confidence information
- Original evidence preservation
- Reproducible deviation calculations
- Separate assessment and authorization records

A hash proves integrity of the hashed content, not the truth of the original observation.
