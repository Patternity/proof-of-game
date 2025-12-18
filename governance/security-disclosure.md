# Proof-of-Game (PoG) — Security Disclosure Process

This document defines the responsible disclosure process
for security-related issues affecting the Proof-of-Game (PoG) protocol.

It complements the Security Policy and Security Model documents.

---

## Purpose

The purpose of this document is to ensure that
security-relevant issues are disclosed in a way that:

- avoids unnecessary public disruption
- allows maintainers to assess consensus impact
- preserves protocol stability and trust

This process applies to **protocol-level issues**, not implementation bugs.

---

## What Should Be Disclosed

Security disclosure applies to findings that may affect:

- consensus determinism
- canonicalization correctness
- evaluation consistency
- ruleset or protocol ambiguity
- UE quorum or attestation trust assumptions

Pure editorial issues or clarifications
SHOULD be handled through the normal change process.

---

## How to Disclose

Security issues MUST be reported **privately**.

At this stage, reporters SHOULD:
- contact repository maintainers directly via GitHub, or
- use GitHub Security Advisories (if enabled)

Public issues or discussions MUST NOT be opened
prior to private review.

---

## Review Process

Upon receiving a disclosure:

1. Maintainers acknowledge receipt.
2. The issue is assessed for:
   - consensus impact
   - security severity
   - need for protocol clarification or revision
3. A resolution path is determined.

Not all disclosures result in protocol changes.

---

## Disclosure Timeline

There is no fixed disclosure timeline.

If a protocol change is required:
- the issue will be addressed in a future version
- the change will be documented in the changelog
- prior protocol versions remain immutable

Public disclosure MAY occur after resolution,
at the discretion of the maintainers.

---

## Reporter Recognition

Reporters MAY be acknowledged in:
- release notes
- changelog entries
- governance records

There are currently no bug bounties associated
with the Proof-of-Game protocol.

---

## Non-Goals

This disclosure process does NOT:
- guarantee mitigation of all risks
- provide response-time SLAs
- define legal or contractual obligations

Its purpose is coordination, not enforcement.

---

## Design Principle

> Protocol security issues require coordination, not publicity.

Responsible disclosure protects both the protocol
and its participants.

---

End of document.
