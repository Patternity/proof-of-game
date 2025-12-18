# Proof-of-Game (PoG) — Uniqueness Engine Quorum

This document describes the **quorum model** for the Uniqueness Engine (UE)
used by the Proof-of-Game (PoG) protocol.

It defines governance-level rules for UE participation and attestation signing.
It does NOT define canonicalization or evaluation semantics.

---

## Purpose

The Uniqueness Engine (UE) is a consensus-critical off-chain component
responsible for:

- canonicalizing behavioral event streams
- evaluating behavioral uniqueness
- producing deterministic EvaluationResults
- issuing Attestations

To prevent centralization and unilateral control,
PoG supports a **quorum-based UE model**.

---

## Quorum Concept

An Attestation is considered valid only if it is signed by
a sufficient number of independent UE nodes.

This threshold is defined as:

```

N-of-M

```

Where:
- `M` is the total number of active UE nodes
- `N` is the minimum number of signatures required

---

## Initial Deployment

For early or experimental deployments:

- `M = 1`
- `N = 1`

This configuration is explicitly allowed and
does NOT violate the PoG protocol.

The quorum model exists to enable future decentralization
without protocol changes.

---

## Quorum Evolution

The quorum parameters (`N`, `M`) MAY be updated over time via governance.

Such updates:
- MUST NOT alter protocol semantics
- MUST NOT affect canonicalization or evaluation
- MUST be explicitly reflected in Attestation metadata

---

## Independence Requirement

UE nodes participating in a quorum SHOULD be:

- operated by independent entities
- geographically and administratively separated
- running independently built UE implementations (where possible)

This reduces correlated failure and collusion risk.

---

## Signature Model

- Each UE node signs the full Attestation object.
- Signatures are collected into `signatures[]`.
- The on-chain verifier checks:
  - signature validity
  - signer authorization
  - quorum threshold satisfaction

The blockchain layer MUST NOT interpret or compare EvaluationResults.

---

## Trust Assumptions

PoG does NOT attempt to eliminate trust entirely.

Instead, it:
- makes trust explicit
- distributes it across multiple UE operators
- allows verification of quorum compliance on-chain

---

## Non-Goals

The UE quorum model does NOT:
- guarantee honesty of all UE nodes
- prevent collusion by a quorum majority
- define UE operator incentives or slashing

These concerns are explicitly out of scope.

---

## Design Principle

> Off-chain computation, on-chain verifiable authority.

The UE quorum model ensures that no single entity
unilaterally controls mint eligibility decisions.

---

End of document.

