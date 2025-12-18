# Proof-of-Game (PoG) — Security Model

This document defines the security model and threat assumptions
of the Proof-of-Game (PoG) protocol.

It describes what PoG explicitly guarantees, what it does not,
and which components are security- and consensus-critical.

---

## Scope

This security model applies to:

- protocol specifications
- Uniqueness Engine (UE) behavior
- Attestation and quorum model
- on-chain verification assumptions

It does NOT apply to:
- SDK or client-side security
- game-specific logic
- economic incentives or tokenomics
- user identity or privacy guarantees

---

## Security Goals

The primary security goals of PoG are:

1. **Determinism**
   Identical canonical behavior MUST produce identical EvaluationResults.

2. **Explicit Trust Boundaries**
   All trust assumptions are explicit and verifiable.

3. **Consensus Safety**
   On-chain verification relies solely on Attestations,
   not on raw behavior or UE internals.

4. **Replay and Ambiguity Resistance**
   Canonicalization prevents ambiguity, smoothing, or reinterpretation.

---

## Threat Model Overview

PoG assumes an adversarial environment where:

- Agents may be automated or adversarial
- Clients may emit malformed or malicious events
- UE nodes may fail, diverge, or collude
- Network conditions may be unreliable or adversarial

PoG is designed to remain correct under these conditions,
within its explicitly stated guarantees.

---

## Trusted Components

### Uniqueness Engine (UE)

UE is a **consensus-critical off-chain component**.

Security assumptions:
- UE implementations follow the published specification
- Canonicalization and evaluation are deterministic
- UE nodes participating in a quorum agree on ruleset semantics

UE is trusted to:
- correctly canonicalize events
- correctly compute EvaluationResults
- sign Attestations honestly

UE is NOT trusted to:
- infer missing data
- repair malformed behavior
- judge intent or identity

---

### UE Quorum

The UE quorum model mitigates risks of:

- unilateral control
- single-node compromise
- accidental divergence

Security properties:
- No single UE node can unilaterally authorize minting
- On-chain verification enforces quorum thresholds
- Quorum configuration is explicit and auditable

The quorum model does NOT prevent:
- collusion by a quorum majority
- coordinated malicious behavior

---

## Untrusted Components

### Agent and Client

Agents and clients are considered **fully untrusted**.

They may:
- emit malformed or adversarial events
- attempt replay or spam
- simulate arbitrary behavior

PoG defends against these by:
- strict event validation
- soft rejection of invalid events
- canonicalization without inference

---

### Network and Transport

Network transport is assumed to be unreliable and adversarial.

PoG makes no assumptions about:
- packet ordering
- latency
- delivery guarantees

All ordering and validation are enforced at the UE level.

---

## On-Chain Verification Model

The blockchain layer:

MUST:
- verify Attestation signatures
- verify quorum thresholds
- verify TTL and single-use
- verify protocol version and rulesetId compatibility

MUST NOT:
- process raw events
- recompute behavior
- reinterpret EvaluationResults
- apply heuristics or inference

The Attestation object is the sole source of truth on-chain.

---

## Non-Goals and Explicit Non-Guarantees

PoG explicitly does NOT guarantee:

- human origin of behavior
- resistance to automation or AI agents
- global agent uniqueness
- fairness, usefulness, or intent of behavior
- privacy or anonymity guarantees
- protection against Sybil attacks
- economic value preservation

These concerns are intentionally out of scope.

---

## Attack Classes and Mitigations

### Event Injection and Malformed Input

Mitigation:
- strict event validation
- soft rejection
- no repair or inference

---

### Replay and Smoothing Attacks

Mitigation:
- canonicalization
- duplicate removal
- fixed-rate downsampling
- last-in-frame selection

---

### UE Divergence

Mitigation:
- deterministic specification
- rulesetId binding
- quorum-signed Attestations

---

### Silent Semantic Changes

Mitigation:
- immutable protocol versions
- explicit ruleset identification
- governance-controlled evolution

---

## Residual Risks

The following risks remain by design:

- collusion of quorum majority
- economic manipulation external to protocol
- emergent behaviors not anticipated by rulesets

PoG prioritizes explicitness over attempting to eliminate all risk.

---

## Design Principle

> Security through explicit rules, not hidden heuristics.

PoG treats behavior as data,
canonicalization as consensus,
and attestations as authority.

---

End of document.
