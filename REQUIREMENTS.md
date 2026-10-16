# Requirements

## Required Requirement Inputs

- Project purpose: Provide a story platform for children under a shared family account. Use stories and related challenges to help children learn and grow. Let parents guide lessons according to their values, within quality and safety limits. Let children choose the course of a story. Let parents use the platform to tell stories themselves. Support learning from homework and school subjects through educational stories.
- Primary users / actors: Two or more parents and multiple children under the same family account. Parents act as administrators and can tell stories to their children.
- Core workflows: Understand children, their preferences, and their wishes. Generate stories dynamically and let children make story choices. Let parents in a family account guide lessons through their values and lesson selections. Provide stories for parents to tell to their children. Let parents enter homework and school subjects for educational stories. Let children respond to educational challenges related to stories.
- Business objects / data entities: Family accounts, children, parents, preferences, wishes, stories, lessons, story choices, parent values, parent lesson selections, homework, school subjects, and educational challenges.
- External integrations: None for the demo. Stories are composed at runtime from reviewed local templates; no AI, email, analytics, advertising, payment, school, or cloud service is connected (OQ-26).
- Authentication / roles: Seeded fictional parent accounts sign in with demo usernames and passwords. Server sessions enforce parent administration and family membership. A parent starts a child session scoped to one child; returning to administration requires parent sign-in. Demo credentials do not verify a real parent (OQ-8, OQ-27; production verification: SECURITY.md OD-002).
- Regulatory or privacy constraints: Intended markets are the United States, all EU member countries, and Ukraine. Account for GDPR in EU operation, applicable US privacy and child-data laws in US operation, and applicable Ukrainian law in Ukrainian operation. Use GDPR-style privacy protections as a product baseline for Ukraine without treating that as a substitute for Ukrainian law. The demo uses fictional data locally; real-family operation depends on SECURITY.md OD-001 and OD-002 (OQ-28).

## Scope and decision authority

The user selected ages 6–12, the United States, all EU member countries, Ukraine, GDPR, and US privacy/child-data law. The user then authorized the assistant to decide the remaining questions because this is a demo. [DECISIONS.md](DECISIONS.md) records the resulting decisions and their provenance.

The deliverable specified here is a local, English-language, adult-operated demonstration using fictional families. It demonstrates parent and child workflows but does not onboard real families. Public hosting, real child information, live AI generation, payments, advertising, uploads, voice capture, and school integrations are outside the demo. Country scope describes the intended product markets, not an existing public launch. No application has been implemented in this repository yet.

## Functional Requirements

### Story Generation

- **FR-1.1** The system MUST generate stories during use.

### Story Choices

- **FR-2.1** The system MUST present story choices to the child.
- **FR-2.2** The system MUST let the child select a story choice.
- **FR-2.3** The system MUST continue the story according to the child's selected choice.

### Parent Administration

- **FR-3.1** The system MUST provide an administrator role for parents within their family account.
- **FR-3.2** The system MUST let each parent select lessons for each child in their family account.
- **FR-3.3** The system MUST limit lessons in a child's stories to the parents' lesson selections for that child.
- **FR-3.4** The system MUST NOT let children change the lesson selections made by parents.
- **FR-3.5** The system MUST limit lessons in a child's challenges to the parents' lesson selections for that child.
- **FR-3.6** The system MUST let parents provide values to guide lessons for their children.
- **FR-3.7** The system MUST use parent values to guide lessons in stories and challenges.

### Parent Storytelling

- **FR-4.1** The system MUST present story content to parents for them to tell the story to their children.

### Educational Stories

- **FR-5.1** The system MUST let parents enter homework for their children.
- **FR-5.2** The system MUST let parents enter the subjects their children study at school.
- **FR-5.3** The system MUST generate educational stories based on homework that a parent enters.
- **FR-5.4** The system MUST generate educational stories based on school subjects that a parent enters.

### Educational Challenges

- **FR-6.1** The system MUST present educational challenges related to the child's story.
- **FR-6.2** The system MUST let children respond to educational challenges.

### Family Accounts

- **FR-7.1** The system MUST group parents and children under the same family account.
- **FR-7.2** The system MUST support two or more parents in a family account.
- **FR-7.3** The system MUST support multiple children in a family account.

## Resolved demo behavior

### Profiles and family membership

- **FR-8.1** Support ages 6–12 inclusive, grouped into reading bands 6–8 and 9–12. Seed two fictional parents and three fictional children aged 6, 9, and 12 in one family. Seed a second family for isolation checks.
- **FR-8.2** Parent-created profiles contain a catalog alias/avatar, age in years, up to three interest tags, and one optional wish tag. Do not request real names, birth dates, email addresses, location, photos, health information, or school identifiers. Parents set initial preferences; children can change only their allowed interest/wish tags.
- **FR-8.3** Use age band for reading complexity and challenge difficulty; use interests and wishes for story setting and characters. These inputs cannot change parent-selected lessons, safety policy, or subject facts.
- **FR-8.4** Allow 1–4 parents and 0–8 children per family; an empty family can add a child before starting stories. Any parent can add a fictional parent from the unused fixture-account catalog or remove another parent. Reject removal of the last parent. Removing a parent revokes their sessions; removing a child deletes that child's story, homework, preference, and challenge records and revokes child sessions. Family deletion removes all records and sessions. Joining a real person is outside the demo.

### Lessons, values, and parent controls

- **FR-9.1** Offer kindness, honesty, perseverance, cooperation, curiosity, and respect as lesson and parent-value tags. Values rank selected lessons; they cannot add unselected lessons. No free-text values or custom lessons are accepted.
- **FR-9.2** A valid lesson names an observable, age-appropriate action, models it without shame or coercion, and includes a reflection question tied to that action. Reviewed catalog entries must satisfy all three checks.
- **FR-9.3** Parents must create a child profile and explicitly select at least one lesson before starting a story. No lessons are preselected. An empty lesson selection blocks a new story and offers the parent a setup link; the child sees a request to ask a parent.
- **FR-9.4** Parent values and lesson selections are shared per child. Equal parent administrators edit the same versioned policy. A stale save is rejected with a conflict message and requires reload and explicit resubmission; there is no silent merge or parent priority.
- **FR-9.5** Any lesson or values change immediately ends access to affected existing story content and marks all of that child's saved/in-progress stories stale. The reader receives a restart message. A newly started story uses the new policy; do not silently rewrite an existing story.
- **FR-9.6** Parents can select reading band within the supported age bands, enable/disable challenges, start/pause/restart a story, inspect outcomes, edit preferences, choose educational material, remove a story, export family records as JSON, and delete child/family data. Children cannot change these controls.

### Story progression and safety

- **FR-10.1** A Start Story button begins a five-scene story. Generate one scene at a time by composing approved fragments using the selected lesson, current branch state, reading band, and interest/wish tags. This is template-based generation, not a model call.
- **FR-10.2** Scenes 1–4 each end with two distinct choices. Each choice changes a named story-state field and selects a reviewed next-scene path that respects prior events. Scene 5 concludes the story. A scene has 60–100 words for ages 6–8 or 100–160 words for ages 9–12.
- **FR-10.3** Failure leaves the last valid scene and progress unchanged. Show Retry and Return to family screen. An idempotent retry cannot duplicate a scene or challenge. Never substitute unchecked content.
- **FR-10.4** Parent storytelling mode displays the same story in large text with pause, repeat scene, next choice, and restart controls. The parent reads aloud and selects the child's spoken choice. There is no microphone or audio upload.
- **FR-10.5** Content and guidance must exclude sexual content, graphic violence, hate, humiliation, coercion, dangerous instructions, requests for secrets or contact details, and medical/legal advice. A child may safely refuse any story choice by leaving the story. Safety policy overrides parent selections.
- **FR-10.6** Invalid catalog IDs, unsupported guidance, unsafe material, or incompatible content combinations are rejected before generation or state mutation. Parents receive a short reason and safe supported alternatives. Children receive a neutral message to ask a parent. Do not store rejected text or present it back to a child.

### Educational stories and challenges

- **FR-11.1** Parents enter fictional homework as plain text up to 200 characters and select one supported subject: arithmetic, reading comprehension, or nature. Arithmetic accepts integer addition/subtraction with operands and result in 0–20 for band 6–8 or 0–100 for band 9–12. Reading accepts a reviewed passage ID; nature accepts a reviewed topic ID (plants, animals, or seasons). No files, links, camera, or school accounts are supported. Unsupported text is rejected with examples of accepted input.
- **FR-11.2** Before starting an educational story, a parent selects exactly one saved homework item or one subject/topic. A normal story can omit educational material. Record the selected item/topic in the story so it is never chosen implicitly from unrelated homework.
- **FR-11.3** Use homework/subject material for learning objectives and selected lessons/values for character behavior. Do not distort educational facts to fit values. If no reviewed safe combination exists, block that combination and ask the parent to choose another.
- **FR-11.4** Every supported educational item must have a learning objective, reviewed explanation, expected answer, and age-band mapping. Calculate arithmetic results in code; use reviewed keys for reading/nature. Release requires the correctness and content checks in ACCEPTANCE.md, not a claim of proven learning outcomes.
- **FR-11.5** Support multiple-choice (three options), true/false, and integer-answer arithmetic challenges. Include an optional ungraded spoken reflection for the parent; no spoken response is captured or stored.
- **FR-11.6** If enabled, present one challenge after scene 2 and one after scene 4, before the next story choice. Disabled challenges are omitted. A child can answer, retry once, or skip; correctness never blocks the story. Challenges do not introduce unselected lessons.
- **FR-11.7** Give encouraging feedback and one reviewed explanation. After a second incorrect answer show the answer and explanation, then continue. No grades, leaderboards, streaks, penalties, or public comparisons. Store only completed/correct/skipped outcomes for parent review during the demo session.

### Demo access and language

- **FR-12.1** Use English for the interface, story catalog, and explanations. Country availability does not imply support for every national language. Include language keys in content so later translation does not require changing story logic; other languages are outside this demo.
- **FR-12.2** Authenticate fixture parents on the server, derive roles and family membership from server records, and authorize every read/write. Child sessions may access only their profile's story/challenge operations and the interest/wish changes permitted by FR-8.2. Passwords and session credentials are not child-profile data and must never be returned in family exports.
- **FR-12.3** Show a persistent fictional-data/local-demo label. Provide parent-accessible review, export, deletion, and reset. Reset destroys current mutable records and sessions before restoring fixtures. Acknowledging the demo notice is not parental identity verification or legal consent.

## Non-Functional Requirements

- **NFR-1 — Privacy:** No real child data, external API calls, analytics, advertising, tracking SDKs, remote assets, or content logs. Use fictional data only. Production obligations are tracked in SECURITY.md OD-001 and OD-002.
- **NFR-2 — Lifetime:** Store mutable state only in server memory; no database, browser storage, backups, service-worker cache, or disk logs. Purge a family after 30 minutes with no authenticated family request or 2 hours from fixture creation, whichever comes first. Purge on reset, deletion, and process shutdown. API responses use Cache-Control: no-store. Audit metadata follows the same lifetime.
- **NFR-3 — Local operation:** Serve the UI and API from http://127.0.0.1:3000 only. Bind only to 127.0.0.1 and reject unexpected Host/Origin headers. No public deployment or remote proxy is part of this demo.
- **NFR-4 — Usability:** Keyboard-operable controls, visible focus, labeled fields, readable contrast, responsive layout from 320 px wide, and at least 44-by-44 CSS-pixel child action targets. Use text plus icons for feedback. Aim for WCAG 2.2 AA; the listed checks must pass before claiming accessibility conformance.
- **NFR-5 — Responsiveness:** On the implementer's documented local test machine, at least 95 of 100 sequential scene-generation requests finish within 1 second with one active family; report machine/runtime details. No artificial delay is necessary.
- **NFR-6 — Integrity:** Reject invalid, stale, out-of-order, duplicate-conflicting, or unauthorized mutations without partially changing state. All story transitions are bounded and deterministic for the same seed and input.
- **NFR-7 — Capacity:** One local process supports the two fixture families, each with at most four parents, eight children, ten homework items per child, and five stories per child. Reject excess creation clearly; do not silently evict records.

## Open Questions

None for the demo. All OQ-1 through OQ-29 answers are recorded in DECISIONS.md. Production legal readiness and verifiable parental consent remain explicitly DEFERRED under SECURITY.md OD-001 and OD-002; they block real-family operation, not fictional-data demo implementation.

## Acceptance and downstream ownership

[ACCEPTANCE.md](ACCEPTANCE.md) maps every functional and non-functional requirement to verification scenarios. [DESIGN.md](DESIGN.md) owns interaction behavior; [ARCHITECTURE.md](ARCHITECTURE.md) owns components and contracts; [SECURITY.md](SECURITY.md) owns secure-coding rules and deferred production decisions; [THREAT_MODEL.md](THREAT_MODEL.md) maps threats to controls and evidence. These are specifications, not claims that checks have run against an implementation.
