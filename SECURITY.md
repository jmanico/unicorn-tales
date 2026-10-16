# Security specification

## Secure-Coding Inputs

**Priority: kids privacy is top concern.**

**Inputs read:** `REQUIREMENTS.md`, `DESIGN.md`, `ARCHITECTURE.md`, the supplied security note, the previous `SECURITY.md`, and `ACCEPTANCE.md` for existing verification references. No required input document is missing. Previous security rules preserve identifiers and coverage; they do not establish project facts or override the authoritative documents.

[REQUIREMENTS.md](REQUIREMENTS.md) owns behavior and scope; [DESIGN.md](DESIGN.md) owns interaction and frontend constraints; [ARCHITECTURE.md](ARCHITECTURE.md) owns component responsibilities and records technology inputs. An architecture proposal is not a confirmed implementation choice. The existing security obligations are retained below with their legacy identifiers. These documents describe an unimplemented system, not verified protections.

- **Users and operation** — Adult-operated, English-language, local demonstration for ages 6–12 using fictional families. Parents administer their family; a parent starts a session scoped to one child. No real-family onboarding. REQUIREMENTS.md: Scope and decision authority; FR-8.1; FR-12.2–12.3.
- **Surfaces and stack** — Browser web demo; Node.js and React.js are documented inputs, but their versions are UNKNOWN. React Native is an input for an unconfirmed mobile surface; its applicability is TO BE DECIDED. Separate server framework, language/build tooling, host OS and test-machine details are UNKNOWN. ARCHITECTURE.md: Required Architecture Inputs; AQ-1–3.
- **Architecture** — Hexagonal architecture is requested. Family/policy and story/education domain responsibilities are SUPPORTED. Built-in HTTP, JSON commands/queries, opaque cookie sessions, serialized memory commits and server-sent invalidation are PROPOSED; their contracts remain TO BE DECIDED under AQ-2, AQ-4 and AQ-5.
- **Identity and authority** — Fixture usernames/passwords authenticate on the server; server records determine role and family membership for every read/write. Child access cannot grant parent authority; administrative return requires parent sign-in. Credential storage/verification details and session/request defenses are UNKNOWN. Demo credentials and acknowledgment do not verify real parenthood or provide legal consent. REQUIREMENTS.md: Required Requirement Inputs; FR-12.2–12.3.
- **Data minimization and content** — Catalog alias/avatar, age in years and bounded interest/wish tags; no requested real names, birth dates, email, location, photos, health information or school identifiers. Homework is supported plain text up to 200 characters. Reviewed local templates and answer keys supply content; rejected text and spoken reflections are not retained. REQUIREMENTS.md: FR-8.2, FR-9.1, FR-10.1, FR-10.4–10.6, FR-11.1–11.7.
- **Lifetime and disclosure** — Mutable state stays in server memory. Purge at the earlier of 30 minutes without an authenticated family request or two hours from fixture creation, and on the required deletion/reset/shutdown paths. No database, browser storage, backups, service-worker cache or disk logs; API responses use `Cache-Control: no-store`. Exports exclude credentials. The idle-refresh predicate and disconnected-reader policy remain TO BE DECIDED. REQUIREMENTS.md: FR-8.4, FR-9.6, FR-12.2–12.3, NFR-2; ARCHITECTURE.md: AQ-4–5.
- **Network and integrations** — UI/API only at `http://127.0.0.1:3000`; bind only to `127.0.0.1` and reject unexpected Host/Origin headers. No public hosting, remote proxy, external APIs, live AI, analytics, advertising, tracking SDKs, remote assets or content logs. REQUIREMENTS.md: Scope and decision authority; NFR-1–3. DESIGN.md: Typography; Do's and Don'ts.
- **Production privacy** — Intended markets remain the US, all EU member countries and Ukraine. Production obligations, real-parent verification and consent are unresolved under [OD-001](#od-001) and [OD-002](#od-002). This file makes no legal-compliance claim.
- **Verification** — [ACCEPTANCE.md](ACCEPTANCE.md) supplies existing scenarios. Runtime checks are NOT RUN because no application is implemented. Documentation checks cannot establish runtime security.

## Selected Manicode Prompts

Corpus root: `/Users/jmanico/Dropbox/github/aegis/secure-coding-knowledge`. All `content/...` paths below are relative to that root. The manifests, prompt scopes, source records and resolver paths were inspected on 2026-10-16. A corpus version label or dependency include is not evidence that this project uses that version.

**Direct SELECTED packs: none. Eligible transitive packs: none.** A direct selection requires authoritative project evidence for both the technology and its version scope. A transitive pack requires an eligible selected composition and applicable guidance; resolving a candidate does not select its parents. Missing facts are UNKNOWN; unresolved choices or scope conflicts are TO BE DECIDED.

- **`js/nodejs/26`** — BLOCKED; not selected. Node.js is confirmed, version UNKNOWN. ARCHITECTURE.md: Required Architecture Inputs; AQ-3. [OD-003](#od-003).
- **`js/react-native/0.87`** — BLOCKED; not selected. React Native version UNKNOWN; mobile scope TO BE DECIDED against the browser-only demo. ARCHITECTURE.md: AQ-1, AQ-3. [OD-003](#od-003), [OD-005](#od-005).
- **`js/fastify/5.12`** — BLOCKED; not selected. Fastify adoption/version UNKNOWN; built-in HTTP is only proposed. ARCHITECTURE.md: server-framework input; AQ-2–3. [OD-003](#od-003), [OD-004](#od-004).
- **`jvm/android-sdk/37`** — BLOCKED; not selected. No confirmed Android surface, SDK or Kotlin version. Native applicability TO BE DECIDED. ARCHITECTURE.md: AQ-1, AQ-3. [OD-005](#od-005).
- **`swift/ios-sdk/27`** — BLOCKED; not selected. No confirmed iOS surface, SDK or Swift version. Native applicability TO BE DECIDED. ARCHITECTURE.md: AQ-1, AQ-3. [OD-005](#od-005).
- **`policy/open-policy-agent/1.20`** — BLOCKED; not selected. A family-policy domain does not establish OPA use. Engine adoption/version UNKNOWN. ARCHITECTURE.md: Components and flows. [OD-006](#od-006).
- **`js/zod/4`** — BLOCKED; not selected. Required validation does not establish a validation library. Zod adoption/version UNKNOWN. ARCHITECTURE.md: AQ-3; REQUIREMENTS.md: FR-10.6, FR-11.1. [OD-006](#od-006).
- **`js/prisma/7.10`** — NOT APPLICABLE to this demo; not selected. REQUIREMENTS.md NFR-2 explicitly excludes a database; ARCHITECTURE.md specifies memory-only mutable state. Prisma is not a way to satisfy this persistence contract. Reconsider only after an authoritative scope change, not as an unresolved demo dependency.
- **`infra/dockerfile/1`** — BLOCKED; not selected. Container use, Dockerfile syntax and builder/platform details are UNKNOWN. Local operation alone neither confirms nor excludes containers. ARCHITECTURE.md: runtime/deployment input; AQ-3. [OD-006](#od-006).

The shared preamble resolves separately to `content/preamble.md`. It is the composition prerequisite and supplies process instructions about scope, preserving protections, conflicts and verification. It is not a versioned pack and contains no substantive authorization, retention, session or content-safety control that could establish the missing rule evidence below.

The resolver returned these dependency-first orders. `P` means `content/preamble.md`; every other entry is a pack ID whose prompt path is listed in the inventory. These are inspected candidate compositions, not adopted project policy:

- **Node.js** — P → `js/javascript/ES2026` → `js/nodejs/26`
- **React Native** — P → `js/javascript/ES2026` → `js/react/19` → `js/typescript/7` → `js/react-native/0.87`
- **Fastify** — P → `js/javascript/ES2026` → `js/nodejs/24` → `js/typescript/7` → `js/fastify/5.12`
- **Android SDK** — P → `jvm/kotlin/2.4` → `jvm/android-sdk/37`
- **iOS SDK** — P → `swift/swift/6.4` → `swift/ios-sdk/27`
- **Open Policy Agent** — P → `policy/open-policy-agent/1.20`
- **Zod** — P → `js/javascript/ES2026` → `js/typescript/7` → `js/zod/4`
- **Prisma** — P → `js/javascript/ES2026` → `js/nodejs/24` → `js/typescript/7` → `js/prisma/7.10`
- **Dockerfile** — P → `infra/dockerfile/1`

Each manifest at `content/<pack-ID>/manifest.json` resolves its `prompt` and `sources` fields to the following existing files. “Parent” means transitive within the candidate compositions above, not independently selected. None of these versioned files is eligible rule evidence for this project yet.

- **`js/nodejs/26` — direct** — prompt: `content/js/nodejs/26/prompt.md`; sources: `content/js/nodejs/26/sources.md`
- **`js/react-native/0.87` — direct** — prompt: `content/js/react-native/0.87/prompt.md`; sources: `content/js/react-native/0.87/sources.md`
- **`js/fastify/5.12` — direct** — prompt: `content/js/fastify/5.12/prompt.md`; sources: `content/js/fastify/5.12/sources.md`
- **`jvm/android-sdk/37` — direct** — prompt: `content/jvm/android-sdk/37/prompt.md`; sources: `content/jvm/android-sdk/37/sources.md`
- **`swift/ios-sdk/27` — direct** — prompt: `content/swift/ios-sdk/27/prompt.md`; sources: `content/swift/ios-sdk/27/sources.md`
- **`policy/open-policy-agent/1.20` — direct** — prompt: `content/policy/open-policy-agent/1.20/prompt.md`; sources: `content/policy/open-policy-agent/1.20/sources.md`
- **`js/zod/4` — direct** — prompt: `content/js/zod/4/prompt.md`; sources: `content/js/zod/4/sources.md`
- **`js/prisma/7.10` — direct** — prompt: `content/js/prisma/7.10/prompt.md`; sources: `content/js/prisma/7.10/sources.md`
- **`infra/dockerfile/1` — direct** — prompt: `content/infra/dockerfile/1/prompt.md`; sources: `content/infra/dockerfile/1/sources.md`
- **`js/javascript/ES2026` — parent** — prompt: `content/js/javascript/ES2026/prompt.md`; sources: `content/js/javascript/ES2026/sources.md`
- **`js/react/19` — parent** — prompt: `content/js/react/19/prompt.md`; sources: `content/js/react/19/sources.md`
- **`js/typescript/7` — parent** — prompt: `content/js/typescript/7/prompt.md`; sources: `content/js/typescript/7/sources.md`
- **`js/nodejs/24` — parent** — prompt: `content/js/nodejs/24/prompt.md`; sources: `content/js/nodejs/24/sources.md`
- **`jvm/kotlin/2.4` — parent** — prompt: `content/jvm/kotlin/2.4/prompt.md`; sources: `content/jvm/kotlin/2.4/sources.md`
- **`swift/swift/6.4` — parent** — prompt: `content/swift/swift/6.4/prompt.md`; sources: `content/swift/swift/6.4/sources.md`

React.js being confirmed does not select the inherited React 19 pack while its version is UNKNOWN. Fastify and Prisma resolve Node.js 24, not the separate Node.js 26 candidate. These manifest choices do not prove a compatible project stack or authorize replacing a baseline. No combined composition has been selected. Supporting source records describe corpus research; they do not confirm project adoption or constitute fresh upstream verification.

## Secure-Coding Rules

Canonical IDs use three digits; **SC-01 through SC-09 remain valid legacy aliases for SC-001 through SC-009**, respectively, so existing ACCEPTANCE.md and THREAT_MODEL.md references retain their meaning.

There are **no ACTIVE entries** under the required evidence standard. The earlier ACTIVE labels on SC-01–08 are replaced with BLOCKED because eligible substantive prompt evidence is missing, with additional implementation decisions identified below. **Every established REQUIREMENTS.md obligation remains binding.** BLOCKED does not authorize omitting privacy, isolation, validation, deletion or other required behavior.

The coverage descriptions below retain requirement traceability and are not implementation instructions. Before promotion, an entry needs confirmed applicability, a confirmed enforcement point, precise project and eligible prompt/preamble evidence that actually supports its control, and pass/fail verification. A resolved file or generic preamble citation alone is insufficient. All verification below is NOT RUN.

<a id="sc-001"></a>

**SC-001 — Family authorization**

- **Legacy ID:** SC-01 — family authorization.
- **Status:** BLOCKED.
- **Coverage:** Server-derived roles and memberships; family/child scope for reads, mutations, exports and deletion; rejection without unauthorized disclosure or mutation.
- **Enforcement:** Server authorization and family/policy ownership are required responsibilities; concrete session/application adapter contracts remain proposed.
- **Evidence:** REQUIREMENTS.md FR-8.4, FR-9.6, FR-12.2; ARCHITECTURE.md Components and flows, family/policy domain. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004).
- **Verification:** AC-02, AC-03 and AC-07. PASS only when permitted operations succeed and forged roles, cross-family IDs and child attempts at parent operations disclose no unauthorized records and change no state; otherwise FAIL.

<a id="sc-002"></a>

**SC-002 — Input and output boundaries**

- **Legacy ID:** SC-02 — input and output boundaries.
- **Status:** BLOCKED.
- **Coverage:** Required catalog, type, size, age, educational and capacity validation; inert handling of accepted input; rejection before storage/generation and non-retention of rejected text.
- **Enforcement:** Confirmed family/policy and story/education domain validation responsibilities; concrete transport parsing, rendering and validation-library choices are not confirmed.
- **Evidence:** REQUIREMENTS.md FR-8.1–8.3, FR-9.1, FR-10.6, FR-11.1, FR-11.5, NFR-7; DESIGN.md Components, field and homework patterns; ARCHITECTURE.md Components and flows. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004); [OD-006](#od-006) only if Zod is adopted.
- **Verification:** AC-04, AC-10, AC-11 and AC-17. PASS only when supported boundary values work, invalid types/IDs/limits are rejected without mutation, and input cannot execute or expose rejected text through either reader; otherwise FAIL.

<a id="sc-003"></a>

**SC-003 — Policy and progression integrity**

- **Legacy ID:** SC-03 — policy and progression integrity.
- **Status:** BLOCKED.
- **Coverage:** Current policy/version/branch enforcement; rejection of stale, out-of-order and conflicting duplicate mutations; idempotent retries and preservation of valid state on generation failure. Disconnected-reader behavior remains unresolved.
- **Enforcement:** Confirmed policy and story-domain invariants; serialized commits and invalidation delivery are proposed. Disconnected-reader behavior is unresolved.
- **Evidence:** REQUIREMENTS.md FR-9.4–9.5, FR-10.2–10.3, NFR-6; DESIGN.md Components, shared settings and story patterns; ARCHITECTURE.md persistence/consistency and invalidation proposals, AQ-4–5. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004), [OD-008](#od-008).
- **Verification:** AC-06, AC-08 and AC-09. PASS only when stale policies cannot serve content, invalid/replayed transitions cannot corrupt or duplicate state, and forced generation failure preserves valid progress. Full reader verification also requires the pass/fail disconnected-state scenario from OD-008; unresolved or failed checks prevent promotion.

<a id="sc-004"></a>

**SC-004 — Reviewed content and educational integrity**

- **Legacy ID:** SC-04 — reviewed content and educational integrity.
- **Status:** BLOCKED.
- **Coverage:** Reviewed local content and parent-selected lessons; safety and educational facts take priority over values; rejection of unsupported combinations and no capture of spoken reflections.
- **Enforcement:** Confirmed story/education domain and reviewed-content responsibilities; adapter realization remains proposed.
- **Evidence:** REQUIREMENTS.md FR-9.1–9.3, FR-10.1, FR-10.4–10.6, FR-11.3–11.7; ARCHITECTURE.md Components and flows. Eligible substantive prompt: NONE; available candidate packs must not be represented as evidence of child-content review.
- **Dependency:** [OD-003](#od-003), including control-specific source adequacy rather than version confirmation alone.
- **Verification:** AC-05, AC-10 and AC-12–14. PASS only when every reachable reviewed combination obeys the content policy, lesson selection and answer checks, unsupported combinations fail safely, and no spoken response is captured; otherwise FAIL.

<a id="sc-005"></a>

**SC-005 — Fictional-data and local-only privacy boundary**

- **Legacy ID:** SC-05 — fictional-data and local-only privacy boundary.
- **Status:** BLOCKED.
- **Coverage:** Fictional families, minimal profiles, loopback-only access and Host/Origin boundary; no integrations, tracking, remote assets or content logs; demo acknowledgment distinct from verified parental consent.
- **Enforcement:** Confirmed fixture/profile, local HTTP, asset and interface boundaries; concrete HTTP defense placement remains proposed.
- **Evidence:** REQUIREMENTS.md FR-8.1–8.2, FR-12.3, NFR-1, NFR-3; DESIGN.md Layout, Typography, Do's and Don'ts; ARCHITECTURE.md Required Architecture Inputs. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004). Real-family scope remains separately blocked by [OD-001](#od-001) and [OD-002](#od-002).
- **Verification:** AC-01, AC-04 and AC-16. PASS only when the fixture-only notice is persistent, disallowed profile fields are rejected, binding/Host/Origin checks enforce the local boundary, and observed traffic/assets/logging contain no prohibited external connection, tracker or content log; otherwise FAIL.

<a id="sc-006"></a>

**SC-006 — Lifetime, export and deletion**

- **Legacy ID:** SC-06 — lifetime, export and deletion.
- **Status:** BLOCKED.
- **Coverage:** Memory-only data, sessions and metadata; fixed expiry/removal/reset/shutdown cascades; authorized parent review/export without credentials; no-store API responses and absence of prohibited persistence.
- **Enforcement:** Server-memory ownership, export exclusions and removal cascades are confirmed requirements; memory/lifetime adapter and idle-refresh contract remain partly defined.
- **Evidence:** REQUIREMENTS.md FR-8.4, FR-9.6, FR-12.2–12.3, NFR-2; DESIGN.md Components, review/delete/reset; ARCHITECTURE.md memory/lifetime responsibility, lifetime/removal flow, AQ-4. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004), [OD-007](#od-007).
- **Verification:** AC-03 and AC-15. PASS only when export omits credentials, removal/reset/expiry revoke all affected access and records, both lifetime bounds purge with a controlled clock, API responses carry no-store, and no mutable state survives through prohibited persistence. OD-007 must define the idle-refresh cases before this verification is complete; any counterexample is FAIL.

<a id="sc-007"></a>

**SC-007 — Parent/child session separation**

- **Legacy ID:** SC-07 — parent/child session separation.
- **Status:** BLOCKED.
- **Coverage:** Parent-started single-child sessions without administrative authority; parent sign-in for administrative return; fixture identity restricted to a demo role.
- **Enforcement:** Server fixture authentication and parent/child authority separation are confirmed; credential handling, session transport and lifecycle mechanisms remain undecided.
- **Evidence:** REQUIREMENTS.md Required Requirement Inputs, FR-12.2–12.3; ARCHITECTURE.md proposed authentication handling, AQ-4. Eligible substantive prompt: NONE.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004); real-parent verification remains [OD-002](#od-002).
- **Verification:** AC-02 and AC-03. PASS only when child mode cannot reuse administrative authority or select another child, parent return requires sign-in, and removed-member access is revoked; otherwise FAIL. Session-defense cases depend on OD-004 and are not claimed complete.

<a id="sc-008"></a>

**SC-008 — Capacity and bounded work**

- **Legacy ID:** SC-08 — capacity and bounded work.
- **Status:** BLOCKED.
- **Coverage:** Family/member/homework/story capacities checked before mutation, with clear rejection and no silent eviction. Request-work limits remain unresolved.
- **Enforcement:** Confirmed family and story/homework capacity checks. Request-work limits and concrete HTTP enforcement remain UNKNOWN under OD-004; no numeric limits are invented here.
- **Evidence:** REQUIREMENTS.md NFR-6–7; ARCHITECTURE.md Components and flows. Eligible substantive prompt: NONE. NFR-5/AC-18 remains the separate responsiveness requirement, not evidence of denial-of-service protection.
- **Dependency:** [OD-003](#od-003), [OD-004](#od-004).
- **Verification:** AC-17. PASS only when each permitted boundary succeeds and one-over-limit, invalid and unauthorized creations fail clearly without changing existing state; otherwise FAIL. Request-work verification remains incomplete until OD-004 defines its limits and checks.

<a id="sc-009"></a>

**SC-009 — Production privacy gate**

- **Legacy ID:** SC-09 — production privacy gate.
- **Status:** BLOCKED.
- **Coverage:** Real-family onboarding and child-data collection gated on completed production privacy and verification/consent decisions. Future production obligations and enforcement remain unresolved.
- **Enforcement:** Current scope excludes real-family operation. Future onboarding, identity and data-flow enforcement points are TO BE DECIDED.
- **Evidence:** REQUIREMENTS.md Required Requirement Inputs, Scope and decision authority, FR-12.3, NFR-1; ARCHITECTURE.md final production gate. Eligible substantive production prompt/source mapping: NONE.
- **Dependency:** [OD-001](#od-001), [OD-002](#od-002), then applicable production-source selection under [OD-003](#od-003).
- **Verification:** AC-21. PASS for future release only after both production decisions close, complete obligations replace this incomplete gate, and derived positive, negative and withdrawal scenarios pass. An open dependency or demo acknowledgment is insufficient; otherwise FAIL. Demo completion does not promote this entry.

## Open Security Decisions

Owners below are **UNKNOWN**: the authoritative inputs do not assign a person to these security decisions. Existing OD-001 and OD-002 remain stable production gates. Closing a decision requires recorded evidence and re-auditing the affected rules; it does not automatically make any rule ACTIVE.

### OD-001

**Production privacy readiness — DEFERRED; outcome TO BE DECIDED.** Owner: UNKNOWN. Actual production data flows and the applicable jurisdiction-specific obligations remain UNKNOWN. Preserve the US, all EU member countries and Ukraine scope, including the selected GDPR-style product baseline for Ukraine without treating it as a substitute for Ukrainian law.

Resolve purposes, legal bases, notices, rights handling, retention, transfers and any required impact assessment through qualified review. Exit: an approved jurisdiction/data-flow mapping and testable production requirements with supporting sources. Depends on actual production scope; blocks real-family collection and public real-family release, not fictional-data demo work. Preserve dependent OQ-28, SC-009/SC-09 and AC-21 references when updating specifications.

### OD-002

**Real parent verification and consent — DEFERRED; process TO BE DECIDED.** Owner: UNKNOWN. Verification/consent method, evidence, withdrawal and membership-recovery rules are UNKNOWN. Fixture sign-in and demo acknowledgment do not resolve them.

Exit: a documented process appropriate to OD-001's jurisdictions and data uses, with testable success, refusal, failure, withdrawal and recovery behavior. Depends on OD-001 and future production identity/data flows; blocks real-family onboarding only. Revisit FR-12.2–12.3, SC-007/SC-07, SC-009/SC-09 and AC-21 when resolved.

### OD-003

**Versions, composition and rule evidence — BLOCKED; selection TO BE DECIDED.** Owner: UNKNOWN. Node.js and React.js versions, implementation language/build tooling and relevant runtime/test-machine details are UNKNOWN (ARCHITECTURE.md AQ-3).

Exit: record authoritative version scope; resolve matching manifests, prompts and source records; establish applicable, compatible direct/transitive selections; and map each affected rule to substantive guidance and a confirmed enforcement point. Version confirmation alone does not establish control coverage. A rule stays BLOCKED if no eligible source supports it. This blocks source-backed promotion of SC-001–008 and future production mappings, not the existing requirements. Do not select React 19, TypeScript 7, ES2026 or Node.js 24 merely because an unselected candidate includes them.

### OD-004

**Server, request and session contract — BLOCKED; design TO BE DECIDED.** Owner: UNKNOWN. ARCHITECTURE.md AQ-2 and AQ-4 leave the framework, JSON transport, cookie sessions, serialized commits and event delivery proposed. Fixture credential storage/verification, session issuance/revocation behavior, request defenses, header handling and request-work limits lack a complete implementation contract.

Exit: confirm the architecture and concrete enforcement points, specify defenses compatible with the required loopback HTTP demo, and define rejection/lifecycle tests. Do not infer Fastify, password algorithms, cookie flags, request-size/time/rate limits or a production TLS model. Depends on OD-003; blocks affected SC-001–003 and SC-005–008 details. Idle accounting and disconnected display require OD-007 and OD-008 separately.

### OD-005

**Native mobile scope and toolchain — BLOCKED; applicability TO BE DECIDED.** Owner: UNKNOWN. React Native is supplied but the confirmed demo is browser-only (ARCHITECTURE.md AQ-1); Android/iOS targets, SDKs and compiler versions are UNKNOWN.

Exit: either explicitly retain the browser-only scope and exclude native packs, or record an authorized mobile scope with a coherent supported toolchain and reconcile NFR-3's loopback boundary before selecting native compositions. Depends on AQ-1 and OD-003; blocks native-specific rules only. It does not authorize changing the current network or privacy boundary.

### OD-006

**Optional validation, policy and container technologies — BLOCKED; adoption TO BE DECIDED.** Owner: UNKNOWN. OPA, Zod and Dockerfile/BuildKit adoption and versions are UNKNOWN. Required validation, domain policy and a local process do not establish those products.

Exit: record exclusion or confirmed use/version and actual enforcement/build surface, then resolve applicable compositions under OD-003. Container selection also needs platform and builder facts; no deployment is inferred. This blocks only technology-specific guidance, not the required validation, authorization or local operation. Prisma remains inapplicable under the current no-database requirement; introducing persistence needs an authoritative scope change.

### OD-007

**Idle lifetime accounting — BLOCKED; refresh predicate TO BE DECIDED.** Owner: UNKNOWN. NFR-2 fixes the 30-minute idle and two-hour absolute bounds, but ARCHITECTURE.md AQ-4 leaves the explicit authenticated requests that refresh idle time unresolved. The architecture excludes passive event connections/heartbeats as lifetime extensions.

Exit: specify the refresh predicate and controlled-clock tests for activity, passive connections, expiry and deletion, preserving both fixed bounds and purging associated sessions/metadata. Depends on OD-004; blocks complete SC-006 verification. No new retention period is introduced.

### OD-008

**Disconnected reader and policy invalidation — BLOCKED; behavior TO BE DECIDED.** Owner: UNKNOWN. REQUIREMENTS.md FR-9.5 requires immediate loss of access after policy changes; FR-10.3 preserves the last valid scene on generation failure. ARCHITECTURE.md AQ-5 leaves the disconnected visible state unresolved.

Exit: record the visible behavior in DESIGN.md and the access/reconnection contract in ARCHITECTURE.md, then define pass/fail tests for disconnect, policy change, revocation, expiry and reconnect. Distinguish generation failure from inability to establish current authorization; do not claim that server invalidation retracts text already seen offline. Depends on OD-004 and OD-007; blocks full SC-003 reader verification. This entry does not choose a speculative display or transport mechanism.
