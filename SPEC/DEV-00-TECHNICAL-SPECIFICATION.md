# DEV-00 — SWI Deviation Device Technical Specification

**Version:** 0.1-DRAFT  
**Status:** Specification lock in progress  
**Date:** 2026-11-17  
**Authority:** Not sealed. Not production-authorised.

## 1. Purpose

Define the governance framework, data contracts, classification rules, evidence requirements and adversarial acceptance criteria for Runtime Deviation Intelligence (RDI) applied to devices.

## 2. Architectural Invariants

1. Deviation is measured from what was **authorised**, not from the latest observation.
2. Admission is conditional and scoped, never permanent trust.
3. Detection does not grant permission to repair, modify, isolate or execute.
4. Observation authority, investigation authority and modification authority are distinct permissions.
5. An observed state must never silently become an authorised baseline (baseline poisoning prevention).

## 3. Three States

- `AUTHORISED_BASELINE` — approved reference state (versioned, hashed, approval-bound)
- `OBSERVED_STATE` — current permitted measurement
- `AUTHORISED_TARGET_STATE` — state approved for a specific future change

These are never interchangeable.

## 4. Classification Rules

| Classification | Trigger | Default Response |
|----------------|---------|------------------|
| NORMAL | Fresh, valid observation matches baseline | Continue monitoring |
| DRIFT | Valid observation differs from baseline | Investigate |
| CRITICAL | Defined critical control has deviated | Hold affected operations |
| AUTHORIZED_DEVIATION | Independently validated authorization covers the exact change | Assess new state |
| UNKNOWN | Insufficient information | Do not assume compliance |
| STALE | Evidence outside validity period | Reassess |
| INVALID | Evidence or binding failed validation | Reject affected evidence |

`AUTHORIZED_DEVIATION` requires independent validation of identity, scope, action, validity period and authority. A mere reference to an authorization document is insufficient.

## 5. Evidence Requirements

Every deviation event produces a canonical evidence record containing at minimum:

- event_id, device_id, baseline_id, baseline_version
- control_id, expected_state, observed_state
- observation_method, observation_time
- evidence_hash, evidence_source, freshness_status
- deviation_class, severity
- joe_assessment, alita_assessment
- authority_reference, replay_reference, decision_record

Integrity is provided by SHA-256 manifests. A hash proves integrity of the hashed content, not the truth of the original observation.

## 6. JOE and ALITA Boundaries

**JOE (Human Protection)**  
Detects changes affecting human consent and authority. Identifies actions exceeding approved purpose. Requires human authorization for consequential decisions. No hidden continuous observation.

**ALITA (Hardware Protection)**  
Detects unexpected hardware and runtime changes. Identifies unsafe software-to-hardware interactions. Holds consequential operations when safety cannot be established.

Neither conducts continuous screen observation. Screen observation requires explicit purpose, scope, consent and duration.

## 7. Acceptance Gates (Proposed)

G1 – Baseline creation and versioning  
G2 – Device identity and admission binding  
G3 – Deviation calculation reproducibility  
G4 – Evidence integrity and provenance  
G5 – JOE and ALITA boundary tests  
G6 – Offline / interrupted connectivity  
G7 – Unauthorized execution refusal  
G8 – Replay and tamper resistance  
G9 – Independent implementation review  
G10 – Explicit sealing and authorization decisions

No gate passes merely because another gate passes.

## 8. Explicit Non-Claims

This specification does not claim:
- Production readiness
- Certification against any standard
- Automatic repair capability
- Permanent device trust
- That successful tests equal sealed implementation
