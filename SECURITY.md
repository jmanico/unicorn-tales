# Security specification

## Secure-Coding Inputs

- Scope: fictional-data demonstration; no real-family onboarding or production compliance claim (REQUIREMENTS.md).
- Roles and ownership: FR-8.4 and FR-12.2; parents administer their family, children access their own permitted operations.
- Input policy: catalog selections and bounded educational formats in FR-8.2, FR-9.1 and FR-11.1.
- Content policy: reviewed generation, safety rejection and educational correctness in FR-10.1–10.6 and FR-11.3–11.7.
- Data lifetime and external access: NFR-1–3; no integrations, persistent mutable records or content logs.
- Verification: ACCEPTANCE.md. ACTIVE below means a complete normative rule, not implemented or verified protection.

## Secure-coding rules

| ID / status | Scope and required behavior | Dependencies | Evidence |
| --- | --- | --- | --- |
| SC-01 — ACTIVE | Every family operation must derive actor role and membership from authoritative records and reject unauthorized or cross-family access without mutation. Child operations must remain child-scoped. | FR-8.4, FR-12.2 | AC-02, AC-03 |
| SC-02 — ACTIVE | Validate every accepted field against the catalog, type, size, capacity and educational bounds in requirements; reject unsupported input before storage or generation. Treat user input as data, never executable content. | FR-8.2, FR-9.1, FR-10.6, FR-11.1, NFR-7 | AC-04, AC-11, AC-17 |
| SC-03 — ACTIVE | Every story read and transition must honor current policy, accepted version and branch state. Preserve state on failure; prevent duplicate side effects. | FR-9.4–9.5, FR-10.2–10.3, NFR-6 | AC-06, AC-08, AC-09 |
| SC-04 — ACTIVE | Emit only reviewed safe content and valid educational explanations; unsafe or unsupported combinations must fail before presentation. Parent values cannot override safety or facts. | FR-9.2, FR-10.5–10.6, FR-11.3–11.4 | AC-05, AC-10, AC-12 |
| SC-05 — ACTIVE | Enforce the fictional-data, no-integration and no-content-log boundary; do not describe a demo acknowledgment as verified parental consent. | FR-12.3, NFR-1, NFR-3 | AC-01, AC-16 |
| SC-06 — ACTIVE | Honor review/export/removal and all expiry/reset cascades; exclude credentials from exports and remove affected session access. | FR-8.4, FR-9.6, FR-12.2–12.3, NFR-2 | AC-03, AC-15 |
| SC-07 — ACTIVE | Preserve required access boundaries when switching between parent and child workflows; administrative return requires parent sign-in. Demo credentials establish a fixture role only. | Required Requirement Inputs; FR-12.2 | AC-02 |
| SC-08 — ACTIVE | Bound request work and records by the specified capacities; enforce limits before mutation and return a clear failure. | NFR-5–7 | AC-17, AC-18 |
| SC-09 — BLOCKED | Real-child-data operation cannot be enabled until jurisdiction-specific obligations and verifiable parental consent are resolved, specified and verified. This future rule is incomplete and must not be represented as ACTIVE. | OD-001, OD-002 | AC-21 |

No formerly blocked rule has been promoted on the strength of a documentation change. All ACTIVE demo rules have resolved specification dependencies; implementation verification remains outstanding.

## Open decisions

- **OD-001 — DEFERRED: production privacy readiness.** Owner: product owner with qualified privacy review. Resolve the applicable US federal/state, EU/member-state and Ukrainian obligations; data purposes and lawful bases; required notices, rights handling, retention and transfer arrangements; and any required impact assessment. Preserve the user's US, EU and Ukraine scope. GDPR-style protections for Ukraine are a chosen product baseline, not a claim of legal equivalence. Exit: an approved jurisdiction/data-flow mapping and testable production requirements. Blocks real-family data collection and public real-family release only. Does not block fictional-data demo work. Dependencies: OQ-28, actual production data flows. Update REQUIREMENTS.md, this file, TF-08 and AC-21 when resolved.
- **OD-002 — DEFERRED: real parent verification and consent.** Owner: product owner with privacy and engineering review. Select and validate the actual verification/consent process, evidence, revocation and family membership recovery rules. Fixture usernames/passwords are not real parent verification. Exit: a documented process appropriate to the jurisdictions and data uses from OD-001, with positive, negative and withdrawal acceptance scenarios. Blocks real-family onboarding only. Dependencies: OD-001 and a future production identity design. Update FR-12.2–12.3, SC-07, SC-09, TF-01, TF-08 and AC-21 when resolved.

For SC-09 to become ACTIVE, close both OD entries, replace the gate with complete production obligations, and update dependent specifications and coverage. A completed demo does not close either entry.

## Legal source notes

These sources establish why production review remains necessary; they do not constitute a full compliance assessment. Reviewed for this specification on 2026-10-16.

- Covered US services directed to children under 13 have COPPA obligations including parental notice/consent and parental rights. See the [FTC compliance plan](https://www.ftc.gov/business-guidance/resources/childrens-online-privacy-protection-rule-six-step-compliance-plan-your-business) and [2025 rule changes](https://www.ftc.gov/news-events/news/press-releases/2025/01/ftc-finalizes-changes-childrens-privacy-rule-limiting-companies-ability-monetize-kids-data). Applicable state requirements still need the OD-001 review.
- For consent-based online services offered directly to children, GDPR child-consent thresholds vary between 13 and 16 by member state. See the [European Commission guidance](https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/legal-grounds-processing-data/are-there-any-specific-safeguards-data-about-children_en). The demo age range does not remove the need to establish an appropriate lawful basis and parental safeguards for real operation.
- Ukraine has its own [Law on Protection of Personal Data](https://zakon.rada.gov.ua/laws/show/en/2297-17/ed20250614/parast10). This reference identifies the law, not a completed analysis of its current requirements; OD-001 retains that work.
