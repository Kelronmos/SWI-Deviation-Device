# SWI-Deviation-Device

**Status:** Specification and foundation stage  
**Default posture:** `PROVEN=NO` · `SEALED=NO` · `PRODUCTION_AUTHORIZED=NO`

Runtime Deviation Intelligence (RDI) for devices — the first reference implementation of SWI Deviation Governance.

## Core Principle

> A device being admitted yesterday does not establish that it remains trustworthy today.

Admission is a recorded state at a particular time. Continued trust requires fresh, scoped and verifiable evidence.

## Three Non-Interchangeable States

| State | Meaning |
|-------|---------|
| `AUTHORISED_BASELINE` | The approved reference state |
| `OBSERVED_STATE` | What the permitted observer actually measured |
| `AUTHORISED_TARGET_STATE` | The state approved for a specific future change |

An observed state must never silently become its authorised baseline.

## Classification Set

| Classification | Meaning |
|----------------|---------|
| `NORMAL` | Valid, fresh observation matches baseline |
| `DRIFT` | Valid observation differs from baseline |
| `CRITICAL` | A defined critical control has deviated |
| `AUTHORIZED_DEVIATION` | A separate, validated authorization covers the exact change |
| `UNKNOWN` | State cannot be established |
| `STALE` | Evidence is outside its freshness limit |
| `INVALID` | Evidence or observation fails validation |

## Repository Structure

```text
SWI-Deviation-Device/
├── SPEC/
│   └── DEV-00-TECHNICAL-SPECIFICATION.md
├── ARCHITECTURE/
│   ├── AUTHORITY-BOUNDARIES.md
│   └── DEVICE-EVIDENCE-MODEL.md
├── SCHEMAS/
│   ├── device-baseline.schema.json
│   ├── device-observation.schema.json
│   └── deviation-evidence.schema.json
├── TESTS/
│   ├── DEV-001-to-DEV-015.md
│   └── adversarial/
├── IMPLEMENTATION/
│   └── baseline-registry/
└── EVIDENCE/
```

## Protective Responsibilities

- **JOE** — Protects humans from unsafe autonomous decisions, manipulation and unintended consequences.
- **ALITA** — Protects hardware from unsafe software and autonomous processes.

Neither independently grants universal execution authority.

## Current Scope

This repository implements the **device-first** reference path of SWI Deviation.  
It does not modify or replace existing SWI governing-spine repositories.

Android Prototype remains a separate integration target.
