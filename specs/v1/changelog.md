# Proof-of-Game (PoG) — Changelog

This changelog records **protocol-level changes** to the Proof-of-Game (PoG)
specification.

It follows a chronological, versioned history.
Editorial changes that do not affect consensus semantics MAY be omitted.

---

## [v1.0-draft] — Initial Specification

**Status:** Draft  
**Category:** Standards Track

### Added

- Initial Proof-of-Game (PoG) protocol specification.
- Formal definitions of:
  - Agent, Action, Event, Behavior, Session
  - Canonical Behavior and Uniqueness Blocks
  - Uniqueness Engine (UE) and Attestation model
- Normative event model with binary encoding.
- Canonicalization pipeline:
  - stable time ordering
  - exact duplicate removal
  - fixed-rate downsampling (25 Hz, last-in-frame)
- Minimum session viability requirement (≥ 500 canonical frames).
- Deterministic EvaluationResult definition.
- Global network difficulty model for mint eligibility.
- Quorum-signed Attestation format.
- Strict on-chain verification rules.

### Out of Scope

- Delta-encoded input events.
- Additional event types beyond `mouse_move`.
- Human verification or identity guarantees.
- Tokenomics, incentives, or economic policy.
- SDK, UE, or smart contract implementations.

### Security Notes

- UE canonicalization is consensus-critical.
- On-chain logic relies exclusively on Attestation objects.
- Identical canonical behavior MUST yield identical EvaluationResult.

---

## Versioning Policy

- Patch versions (v1.0.x) MAY include:
  - clarifications
  - editorial fixes
  - non-normative additions

- Minor or major versions MUST NOT alter:
  - canonicalization rules
  - event semantics
  - evaluation determinism

Such changes require a new protocol version.

---

End of changelog.
