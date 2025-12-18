# Proof-of-Game (PoG) — Ruleset Identification

This document defines the role and governance of the `rulesetId`
used by the Proof-of-Game (PoG) protocol.

The ruleset identifier establishes a strict consensus domain
for behavioral evaluation.

---

## Purpose

The Proof-of-Game protocol allows multiple evaluation strategies,
event subsets, and behavioral constraints to coexist.

The `rulesetId` explicitly identifies the exact set of rules
used by the Uniqueness Engine (UE) to evaluate a session.

EvaluationResults produced under different rulesets
MUST NOT be compared or combined.

---

## Definition

A **Ruleset** is a complete and immutable definition of:

- accepted event types and versions
- canonicalization parameters
- evaluation logic and thresholds
- uniqueness block construction rules
- any additional constraints affecting EvaluationResult

The `rulesetId` uniquely identifies such a definition.

---

## Properties of `rulesetId`

A valid `rulesetId` MUST be:

- globally unique
- deterministic
- immutable once published
- explicitly included in all EvaluationResults and Attestations

---

## Format

The internal representation of `rulesetId` is implementation-defined.

However, it SHOULD be derived from:

- a human-readable ruleset name
- a version identifier
- a cryptographic hash of the ruleset definition

Example (illustrative):

```text
pog:v1:mouse_move_only@sha256:3a9f...e21c
````

This example is non-normative.

---

## Inclusion in Evaluation and Attestation

* Every EvaluationResult MUST include `rulesetId`.
* Every Attestation MUST bind signatures to a specific `rulesetId`.
* On-chain verification MUST reject attestations
  with unsupported or unknown `rulesetId` values.

---

## Governance and Evolution

Rulesets are governed explicitly.

* Introducing a new ruleset does NOT modify existing rulesets.
* Existing rulesets MUST remain valid and verifiable.
* Deprecated rulesets MAY be rejected for new mints,
  but MUST remain interpretable for historical verification.

Ruleset changes MUST NOT be implicit.

---

## Relationship to Protocol Version

The PoG protocol version and `rulesetId` serve different purposes:

* Protocol version defines wire format and consensus mechanics.
* Ruleset defines evaluation semantics.

Multiple rulesets MAY coexist under the same protocol version.

---

## Security Considerations

Failure to correctly bind EvaluationResults to a `rulesetId`
can result in silent consensus divergence.

All UE nodes participating in a quorum MUST:

* agree on the ruleset definition
* produce identical results for the same Canonical Behavior

---

## Design Principle

> Evaluation rules must be explicit, immutable, and identifiable.

The `rulesetId` mechanism ensures that behavioral uniqueness
is always evaluated within a clearly defined consensus domain.

---

End of document.
