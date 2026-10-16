# Architecture

## Required Architecture Inputs

- Behavior and scope: REQUIREMENTS.md, including its fictional-data demo boundary, is authoritative.
- Actors: parent administrators and child sessions; family membership and role come from authoritative records (FR-12.2).
- Domain: families, parents, children, preferences, values, lesson selections, homework, stories, choices, challenges and outcomes.
- State: temporary mutable records with the deletion and expiry policy in NFR-2; reviewed content is separate from mutable family records.
- Integrations: none (OQ-26). Runtime composition uses reviewed local content (FR-10.1).
- Constraints: NFR-1–7; interaction and visual guidance belongs to DESIGN.md. This document specifies responsibilities, not implementation technology or deployment.
- Evidence: ACCEPTANCE.md. No application or implementation evidence exists yet.

## Responsibilities and dependencies

| Responsibility | Owns | Depends on |
| --- | --- | --- |
| Family administration | Membership, child profiles, limits, export, deletion | FR-8.1–8.4, FR-9.6, FR-12.2–12.3 |
| Child policy | Shared values/lessons, version checks, story invalidation | FR-9.1–9.5 |
| Story composition | Five-scene progression, reviewed branches, policy enforcement, retry | Child policy; content catalog; FR-10.1–10.6 |
| Education | Homework validation, selected learning objective, challenges and feedback | Child policy; content catalog; FR-11.1–11.7 |
| Presentation | Parent and child views, accessible state feedback | Authorized domain results; DESIGN.md |
| Lifetime management | Expiry, reset, record/session removal | NFR-2, FR-8.4, FR-12.3 |

## Data invariants

Every mutable child, policy, homework, story and outcome record belongs to exactly one family; child-scoped records also name their child. Parents have explicit membership. A child session names exactly one child. Catalog definitions are not writable through family controls.

A child policy contains a version, selected lesson IDs, value ranking, reading band and challenge setting. A story records its child, policy version, selected educational item/topic (if any), composition seed, scene index and branch state. Challenge state records attempts and its completed/correct/skipped outcome. Credentials are excluded from exports.

State mutations are atomic: validate actor, ownership, bounds, expected version and valid transition before changing anything. Reject stale policy writes; do not merge them. A policy change makes all affected stories unreadable and stale. Concurrent reads must check the current policy version before returning story content. Already displayed content is replaced with the restart state when invalidation is received; previously seen text cannot be retracted from human memory.

## Workflow contracts

- Start: require a valid profile, selected lessons and, for an educational story, one selected item/topic. Produce scene 1 or return a supported-input explanation without partial state.
- Advance: accept only a choice offered by the current scene. Apply it once; return the next reviewed scene. Repeating an identical request returns the original result; a conflicting repeat is rejected.
- Challenge: after scenes 2 and 4, if enabled, accept supported responses, one retry, or skip. Never gate story progress on correctness.
- Read aloud: reuse the same story and challenge state; presentation exposes the parent storytelling controls. No separate content-generation path.
- Remove/expire/reset: revoke affected access and remove dependent mutable records as required by FR-8.4 and NFR-2. Reset then restores fictional fixtures; no deleted user input is restored.

## Open Questions

None for the demo architecture. SECURITY.md OD-001 and OD-002 block a transition to real-family operation, not these demo responsibilities. DQ-1 concerns final branding only.
