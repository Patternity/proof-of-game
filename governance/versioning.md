# Proof-of-Game (PoG) — Versioning and Governance

This document defines the versioning and governance rules
for the Proof-of-Game (PoG) protocol specification.

---

## Scope

This governance applies to:
- protocol specifications
- RFC-style documents
- consensus-critical rules

It does NOT apply to:
- SDKs
- Uniqueness Engine (UE) implementations
- smart contracts
- client applications

---

## Versioning Scheme

PoG follows a **semantic protocol versioning** model:

```

vMAJOR.MINOR.PATCH

```

### MAJOR

Incremented when:
- canonicalization rules change
- event semantics change
- determinism guarantees change
- consensus assumptions change

A MAJOR version defines a **new protocol**.

---

### MINOR

Incremented when:
- new event types are introduced
- new optional fields are added
- protocol is extended without altering existing semantics

MINOR versions MUST be backward-compatible within the same MAJOR version.

---

### PATCH

Incremented when:
- clarifications are added
- editorial errors are fixed
- non-normative text is updated

PATCH versions MUST NOT affect consensus behavior.

---

## Immutability Rule

Once a protocol version is published:

- Its semantics are **immutable**.
- No normative rules may be altered retroactively.
- Corrections affecting consensus require a new version.

Historical specifications MUST remain accessible.

---

## Canonical Specification

For each protocol version, a single document is designated as canonical:

```

/specs/vX/pog-vX.md

```

RFC representations MUST be identical in content.

---

## Change Process

1. Proposed changes are documented as drafts.
2. Consensus impact is explicitly evaluated.
3. Version increment is determined according to this policy.
4. A new specification is published.

There is no implicit or automatic upgrade path.

---

## Authority and Maintenance

The Proof-of-Game protocol is maintained by the **Patternity** organization.

Final authority over protocol changes rests with the maintainers,
acting in the interest of determinism, clarity, and long-term stability.

---

## Design Principle

> Stability is a feature.

Protocol evolution MUST prioritize:
- reproducibility
- determinism
- minimalism
- explicitness

---

End of document.

