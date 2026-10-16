# Decision record

## Authority and scope

The initial scan found only REQUIREMENTS.md: 25 open entries and three unknown required inputs. REQUIREMENT_TEMPLATE.md was excluded as requested. The previously unnumbered inputs received owning IDs OQ-26–28; the country discussion added OQ-29. Original OQ ownership remains REQUIREMENTS.md; resolved entries were removed from its Open Questions section and their values applied to its requirements.

The user initially requested an interview one question at a time, then explicitly replaced that process with: “please answer the rest of the questions as you see fit, jsut to save time, this is a demo.” The assistant's decisions below are authorized demo defaults, not answers attributed to the user. No further interview is pending. The later design/logo request requires explicit markers for unsupported facts and inferences; DQ-1 preserves those markers.

## Ordered decisions

Foundational scope and privacy decisions come first, followed by access, data, lesson policy and detailed workflows. RESOLVED means applied to specifications, not implemented or tested. Every remaining open decision is explicitly DEFERRED under its owning file's ID; each blocks only the work named below.

1. **OQ-1 — RESOLVED — user.** Ages 6–12 inclusive. Coverage: FR-8.1.
2. **OQ-28 — RESOLVED for demo — user + assistant.** User: United States, all EU member countries and Ukraine; GDPR and applicable US privacy/child-data laws. Assistant: applicable Ukrainian law plus GDPR-style product protections for Ukraine; fictional-data demo only. Production review remains OD-001/OD-002. Coverage: Required Requirement Inputs; NFR-1.
3. **OD-001 — DEFERRED — assistant.** Production jurisdiction/data-flow mapping and privacy readiness. Owner: SECURITY.md. Blocks real-family operation only; closure criteria are in the owning entry. Coverage: SECURITY.md; TF-08; AC-21.
4. **OD-002 — DEFERRED — assistant.** Real parent verification and consent process. Owner: SECURITY.md. Depends on OD-001 and future production identity design; blocks real-family onboarding only. Coverage: SECURITY.md; TF-01; TF-08; AC-21.
5. **OQ-29 — RESOLVED — assistant.** English interface and content for the demo; language keys support later translation without promising additional languages. Coverage: FR-12.1.
6. **OQ-26 — RESOLVED — assistant.** No external services. Compose stories at runtime from reviewed local templates; live AI, email, analytics, advertising, payments and school integrations are outside the demo. Coverage: Required Requirement Inputs; FR-10.1.
7. **OQ-27 — RESOLVED — assistant.** Fixture-parent username/password sign-in and authoritative sessions. Parents start child-scoped sessions; returning to administration requires parent sign-in. Coverage: FR-12.2.
8. **OQ-8 — RESOLVED for demo — assistant.** Derive roles and family membership from fixture records; enforce ownership on every operation. Fictional data, minimal profile fields, review/export/deletion and bounded memory lifetime. Real parenthood is not verified; see OD-002. Coverage: FR-8.2; FR-12.2–12.3; NFR-1–2.
9. **OQ-21 — RESOLVED — assistant.** Parents add unused fictional parent fixtures and catalog-based child profiles; parents can remove members, but not the last parent. Removal cascades to affected records and access. Coverage: FR-8.4.
10. **OQ-22 — RESOLVED — assistant.** One to four parents and zero to eight children per family; seed two parents and three children. Whole-family deletion remains available. Coverage: FR-8.1; FR-8.4.
11. **OQ-2 — RESOLVED — assistant.** Parent selects catalog alias/avatar, age, up to three interests and one optional wish. Children may change only allowed interest/wish tags. No real identifying information. Coverage: FR-8.2.
12. **OQ-3 — RESOLVED — assistant.** Age band controls reading complexity/challenge difficulty; interests/wishes affect settings and characters, never lesson eligibility or facts. Coverage: FR-8.3.
13. **OQ-23 — RESOLVED — assistant.** Use reviewed lesson/value catalogs and exclude sexual content, graphic violence, hate, humiliation, coercion, dangerous instructions, requests for secrets/contact details and medical/legal advice. Coverage: FR-9.2; FR-10.5.
14. **OQ-24 — RESOLVED — assistant.** Reject unsafe/unsupported guidance before storage or generation. Give parents safe alternatives and children a neutral ask-a-parent message; never echo rejected text to children. Coverage: FR-10.6.
15. **OQ-25 — RESOLVED — assistant.** Use kindness, honesty, perseverance, cooperation, curiosity and respect tags; values rank selected lessons. Observable modeled actions and reflection questions demonstrate alignment. Coverage: FR-9.1–9.2.
16. **OQ-13 — RESOLVED — assistant.** Equal parent administrators share one versioned child policy. Reject stale saves; require reload and explicit resubmission, without silent merge or parent priority. Coverage: FR-9.4.
17. **OQ-5 — RESOLVED — assistant.** Six named catalog lessons; each models an observable, age-appropriate, non-coercive action and a related reflection question. Coverage: FR-9.1–9.2.
18. **OQ-9 — RESOLVED — assistant.** Create a child profile and explicitly select at least one lesson before starting. No default selection; empty selection blocks start with setup guidance. Coverage: FR-9.3.
19. **OQ-10 — RESOLVED — assistant.** Lesson/value changes make all affected saved and in-progress stories stale and unreadable. Show restart guidance; new stories use the new policy. Coverage: FR-9.5.
20. **OQ-11 — RESOLVED — assistant.** Parents control reading band, challenges, story lifecycle, educational input, preferences, outcomes, exports and deletion; children cannot change parent controls. Coverage: FR-9.6.
21. **OQ-4 — RESOLVED — assistant.** Start Story generates the first of five scenes; compose the next scene after each choice using reviewed local fragments. Coverage: FR-10.1.
22. **OQ-6 — RESOLVED — assistant.** Scenes 1–4 present two choices; each changes branch state and leads to a reviewed continuation. Scene 5 concludes. Coverage: FR-10.2.
23. **OQ-7 — RESOLVED — assistant.** Preserve valid content/state on failure; offer Retry and Return to family screen. Retry is idempotent; no unchecked fallback. Coverage: FR-10.3.
24. **OQ-12 — RESOLVED — assistant.** Parent reads large text aloud and operates pause, repeat scene, next choice and restart. Parent selects the spoken choice; do not capture audio. Coverage: FR-10.4.
25. **OQ-14 — RESOLVED — assistant.** Up to 200 characters of fictional homework using bounded integer arithmetic or reviewed reading/nature IDs; select arithmetic, reading comprehension or nature. No files or links. Coverage: FR-11.1.
26. **OQ-15 — RESOLVED — assistant.** Parent explicitly selects one homework item or subject/topic for an educational story; normal stories can omit educational input. Coverage: FR-11.2.
27. **OQ-16 — RESOLVED — assistant.** Educational content supplies learning objectives; lessons/values guide character behavior. Facts and safety take precedence; unsupported combinations fail. Coverage: FR-11.3.
28. **OQ-17 — RESOLVED — assistant.** Require a learning objective, reviewed explanation, expected answer and age mapping; compute arithmetic and validate reviewed keys. Do not claim proven learning outcomes. Coverage: FR-11.4; AC-12.
29. **OQ-18 — RESOLVED — assistant.** Three-option multiple choice, true/false, integer arithmetic and optional unrecorded parent-led spoken reflection. Coverage: FR-11.5.
30. **OQ-19 — RESOLVED — assistant.** When enabled, challenges occur after scenes 2 and 4 before the next choice. Answer, retry once or skip; correctness never blocks progress. Coverage: FR-11.6.
31. **OQ-20 — RESOLVED — assistant.** Accept choices or bounded integers, give encouraging feedback/explanation and reveal the answer after a second incorrect attempt. Store outcome flags, not speech; no grades or competitive rewards. Coverage: FR-11.7.
32. **DQ-1 — DEFERRED — assistant.** Final brand adoption; existing brand guidelines are UNKNOWN. Demo unicorn identity is an explicitly labeled ASSUMPTION. Owner: DESIGN.md. Blocks final branded release only; the demo mark/tokens are selected and usable. Coverage: DESIGN.md; logo.svg; AC-20.

## Preserved user answer record

- OQ-1: “6-12”. Applied unchanged.
- OQ-28 initial: “global”. Superseded, not current scope.
- OQ-28 correction: “change the countries to US or EUROPEAN countries, and account for GDPR”.
- OQ-28 clarification: “we want all EU countires and Ukrain which will be part of the EU soon anyways *grin*”. Recorded as US + all EU members + Ukraine; Ukraine's inclusion does not depend on future membership.
- OQ-28 US clarification: “US needs to follow US privacy and child data law”. Preserved; GDPR is not treated as a replacement for US law.
- Remaining answers: delegated to the assistant by the quoted demo instruction above. The pending question about Ukraine's product privacy baseline was resolved by the assistant, not by an additional user answer.

## Applied artifacts and dependencies

REQUIREMENTS.md owns all behavior and workflows. DESIGN.md and logo.svg provide the requested demo visual identity. ARCHITECTURE.md describes responsibilities and state invariants. SECURITY.md owns complete demo rules and the deferred production decisions; THREAT_MODEL.md links findings to those rules. ACCEPTANCE.md maps all functional/non-functional requirements to scenarios and distinguishes document checks from runtime tests.

No existing BLOCKED rules or OD findings were present in the initial repository. SC-09 is a newly explicit production gate and remains BLOCKED by OD-001/OD-002. None of its dependencies were silently treated as complete. DQ-1 is independent of demo implementation and production privacy work.
