# Threat model

## Scope and assets

Model the fictional-family workflows in REQUIREMENTS.md, with the responsibilities in ARCHITECTURE.md. Protect parent administration, family boundaries, story-policy integrity, safe educational content and deletion semantics. Real child information and public operation are outside the demo and remain gated by OD-001/OD-002.

Inputs from a browser are untrusted. Authoritative family records and reviewed content are separate trust domains. Parent privileges do not authorize catalog changes or safety overrides. Potential actors include a child attempting parent actions, another fixture family, malformed input and an accidental operator error. Demo-only data and credentials reduce impact; they do not make authorization irrelevant.

## Findings, decisions and coverage

All findings below are design analysis, not observed vulnerabilities. “Specified” means a mitigation decision exists; no implementation has been tested.

| ID | Finding / impact | Decision and mitigation | Status / evidence |
| --- | --- | --- | --- |
| TF-01 | Child or forged role gains parent control | Enforce authoritative roles, scoped child sessions and parent sign-in for administration; fixture login is not real parent proof. SC-01, SC-07. | Specified; AC-02. Real verification depends on OD-002. |
| TF-02 | Another family reads or changes records | Apply ownership checks to reads, writes, exports and deletions. SC-01. | Specified; AC-03. |
| TF-03 | Input becomes executable content or unsupported guidance | Accept only bounded formats/catalog entries; render accepted content as data; reject before mutation. SC-02, SC-04. | Specified; AC-04, AC-10, AC-11. |
| TF-04 | Stale policy or replay exposes an unselected lesson or duplicates progress | Version-check policy and story reads; invalidate affected stories; atomic, idempotent transitions. SC-03. | Specified; AC-06, AC-08, AC-09. |
| TF-05 | Unsafe or inaccurate educational content reaches a child | Reviewed fragments and answer keys, arithmetic validation, no fact overrides, safe failure. SC-04. | Specified; AC-05, AC-10, AC-12–14. |
| TF-06 | Deleted records remain accessible or exported credentials leak | Enforce deletion/session cascades, memory lifetime and export exclusions. SC-06. | Specified; AC-15. |
| TF-07 | Unbounded work or creation makes demo unusable | Enforce stated capacities before mutation and preserve prior state on rejection. SC-08. | Specified; AC-17, AC-18. |
| TF-08 | Demo is mistaken for a compliant service for real children | Persistent fictional-data label; no integrations; real onboarding gated by SC-09. | Production decision DEFERRED under OD-001/OD-002; AC-01, AC-16, AC-21. Only real-family operation is blocked. |

## Residual limitations

Local operation is not an assurance against an operator who controls the machine. Synthetic credentials cannot establish real parenthood. Entering real personal information violates the demo scope; input checks cannot guarantee that arbitrary text contains no personal information. Already viewed text cannot be erased from a person's memory. These limitations must not be advertised as solved security properties.

## Decision dependencies

No independent threat decision remains open for the fictional-data demo. TF-08's production decision is owned by SECURITY.md OD-001/OD-002; do not duplicate or silently close it here. Revisit affected findings whenever roles, integrations, storage, content generation or data scope changes. Evidence remains unverified until the corresponding AC scenarios run against an implementation.
