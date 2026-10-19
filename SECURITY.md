# Security

## Secure-Coding Inputs

- Read: `REQUIREMENTS.md`, `DESIGN.md`, `ARCHITECTURE.md`, and the supplied Manicode candidate notes. Existing `SECURITY.md`: missing; no prior SC or OD IDs to preserve.
- Authority: requirements define behavior and obligations; design defines interaction, rendering, and browser behavior; architecture defines components, interfaces, flows, and boundaries. Candidate packs do not establish project facts. Requirements labelled ASSUMPTION are adopted first-release requirements (`REQUIREMENTS.md`, introduction; `ARCHITECTURE.md` §1); proposed architecture is not a confirmed implementation.
- Confirmed choices: Node.js, Fastify, ReactJS, and React Native, without versions (`ARCHITECTURE.md` §2, Required Architecture Inputs). The supplied Node.js/framework and Fastify/runtime labels conflict; their proposed reinterpretation remains TO BE DECIDED (AQ-1). Native platforms and workflow scope are UNKNOWN (AQ-2). No application implementation exists (`DESIGN.md`, Overview; `ARCHITECTURE.md` §1).
- Confirmed behavior: verified email and email-link access; Organizer/Attendee roles, Admin-controlled grants, current event staff assignments, ownership checks, and restricted suspension behavior (`REQUIREMENTS.md` FR-6.1–FR-6.17). Passkeys and an authentication library are not established.
- Confirmed data boundaries: restricted exact addresses; consent for food-note sharing; private public-page exclusions; Attendee ownership; shopper and email filtering (`REQUIREMENTS.md` FR-2.12, FR-3.10, FR-4.7, FR-4.14, FR-11.1–FR-11.2; `DESIGN.md`, Components and Do's and Don'ts).
- Confirmed financial constraints: server-validated payment evidence, capacity consistency, repeated-confirmation deduplication, refund caps, and payout deduplication (`REQUIREMENTS.md` FR-8.5, FR-8.12–FR-8.24, FR-9.16–FR-9.18; `ARCHITECTURE.md` §8, Persistence and consistency).
- Confirmed integration boundary: dedicated payment and email outbound gateways with separate clients, credentials, configuration, and retry/failure state; a distinct inbound payment adapter (`ARCHITECTURE.md` §8, Isolated outbound gateways and DR-9). A gateway does not imply Open Policy Agent.
- Confirmed record obligations: actor/time/outcome audit records, private-note deletion after 90 days, financial retention for 24 months after last change, exclusion of private notes from financial records, and eligible consent withdrawal (`REQUIREMENTS.md` FR-11.3–FR-11.7). Jurisdictions and statutory duties are UNKNOWN; classification and deletion coverage are TO BE DECIDED (AQ-7).
- Material gaps: versions, provider contracts, link/session controls, first Admin provisioning, persistence, execution settings, hosting, update transport, and browser support remain unresolved (`ARCHITECTURE.md` AQ-3–AQ-8). PostgreSQL, opaque-cookie sessions, and two-second polling remain proposals. Zod, Prisma, Better Auth, OPA, Docker, TypeScript, Kotlin, and Swift use is not confirmed. No supplied note resolves these gaps.
- Threat-model status: `THREAT_MODEL.md` records specification-level threats and privacy tradeoffs only. It supplies no implemented vulnerability, effective control, approved rating, owner, or deadline. Stage 06 found no application implementation, and stage 05 found no specified AI/ML lifecycle.

## Selected Manicode Prompts

Corpus root: `/Users/jmanico/Dropbox/github/aegis/secure-coding-knowledge`.

Paths below are relative to that absolute root. Candidate manifests and prompt/source scope were inspected. Corpus resolution conventions come from `README.md`; project eligibility takes precedence over its fallback-version advice. A catalog include is not evidence that the project uses its technology or version.

**Direct selection evidence**

All ten candidates are **TO BE DECIDED**, not SELECTED:

- `js/nodejs/26`: Node.js named, version UNKNOWN, role conflict unresolved (`ARCHITECTURE.md` Required Architecture Inputs, AQ-1, AQ-5); OD-001.
- `js/react-native/0.87`: React Native confirmed, version and platform scope UNKNOWN (`ARCHITECTURE.md` §8, API and frontend; AQ-2, AQ-5); OD-002.
- `js/fastify/5.12`: Fastify named, version UNKNOWN, role conflict unresolved (`ARCHITECTURE.md` Required Architecture Inputs, AQ-1, AQ-5); OD-001.
- `js/better-auth/1.7`: required email-link behavior does not select Better Auth or its version (`REQUIREMENTS.md` FR-6.2–FR-6.4; `ARCHITECTURE.md` AQ-4); OD-003.
- `jvm/android-sdk/37`: Android targets and passkeys UNKNOWN (`ARCHITECTURE.md` AQ-2); OD-002. The pack scopes Android runtime and compile/target levels; React Native selection alone cannot establish them.
- `swift/ios-sdk/27`: iOS targets, SDK/toolchain, and passkeys UNKNOWN (`ARCHITECTURE.md` AQ-2); OD-002.
- `policy/open-policy-agent/1.20`: OPA use/version UNKNOWN; isolated provider gateways do not establish a policy engine (`ARCHITECTURE.md` §8, Isolated outbound gateways); OD-004.
- `js/zod/4`: validation requirements do not select Zod or its version (`REQUIREMENTS.md` FR-1.8–FR-1.11, FR-7.4; `ARCHITECTURE.md` §4, AQ-5); OD-005.
- `js/prisma/7.10`: data access technology/version UNKNOWN; PostgreSQL is only proposed (`ARCHITECTURE.md` §4, AQ-5); OD-006.
- `infra/dockerfile/1`: container use, Dockerfile syntax, builder, and host scope UNKNOWN (`ARCHITECTURE.md` §7, AQ-5); OD-007. This pack scopes BuildKit/Linux builds.

**Eligible ordered composition**

Empty: no direct pack is SELECTED, so no transitive pack is eligible through a selected root. No candidate prompt supplies active implementation rules in this file.

**Preamble, separately**

- `content/preamble.md`: read; general application and verification guidance, not a technology selection or a source of project-specific mechanisms. Its conflict-precedence advice does not resolve project-document conflicts here. It is not used to activate controls from ineligible packs.

**Candidate dependency order and provenance — not an active composition**

Each directory below contains the inspected `manifest.json`; prompt and source paths are explicit. Parent-before-child order is shown for auditing dependencies, with shared parents listed once. The two Node.js lines remain alternatives, not a resolved combined baseline.

1. Transitive `js/javascript/ES2026`: `content/js/javascript/ES2026/prompt.md`; `content/js/javascript/ES2026/sources.md`. No parents. Project language/version scope UNKNOWN; OD-008.
2. Transitive `js/react/19`: `content/js/react/19/prompt.md`; `content/js/react/19/sources.md`. Includes JavaScript ES2026. ReactJS is confirmed, React 19 and rendering hosts are not; OD-008.
3. Transitive `js/typescript/7`: `content/js/typescript/7/prompt.md`; `content/js/typescript/7/sources.md`. Includes JavaScript ES2026. TypeScript use/version UNKNOWN; OD-008.
4. Transitive `js/nodejs/24`: `content/js/nodejs/24/prompt.md`; `content/js/nodejs/24/sources.md`. Includes JavaScript ES2026. Version UNKNOWN; OD-001, OD-008.
5. Direct `js/nodejs/26`: `content/js/nodejs/26/prompt.md`; `content/js/nodejs/26/sources.md`. Includes JavaScript ES2026.
6. Direct `js/react-native/0.87`: `content/js/react-native/0.87/prompt.md`; `content/js/react-native/0.87/sources.md`. Includes React 19 and TypeScript 7.
7. Direct `js/fastify/5.12`: `content/js/fastify/5.12/prompt.md`; `content/js/fastify/5.12/sources.md`. Includes Node.js 24 and TypeScript 7.
8. Direct `js/better-auth/1.7`: `content/js/better-auth/1.7/prompt.md`; `content/js/better-auth/1.7/sources.md`. Includes Node.js 24 and TypeScript 7.
9. Transitive `jvm/kotlin/2.4`: `content/jvm/kotlin/2.4/prompt.md`; `content/jvm/kotlin/2.4/sources.md`. No parents. Project use/version UNKNOWN; OD-002, OD-008.
10. Direct `jvm/android-sdk/37`: `content/jvm/android-sdk/37/prompt.md`; `content/jvm/android-sdk/37/sources.md`. Includes Kotlin 2.4.
11. Transitive `swift/swift/6.4`: `content/swift/swift/6.4/prompt.md`; `content/swift/swift/6.4/sources.md`. No parents. Project use/version UNKNOWN; OD-002, OD-008.
12. Direct `swift/ios-sdk/27`: `content/swift/ios-sdk/27/prompt.md`; `content/swift/ios-sdk/27/sources.md`. Includes Swift 6.4.
13. Direct `policy/open-policy-agent/1.20`: `content/policy/open-policy-agent/1.20/prompt.md`; `content/policy/open-policy-agent/1.20/sources.md`. No parents.
14. Direct `js/zod/4`: `content/js/zod/4/prompt.md`; `content/js/zod/4/sources.md`. Includes TypeScript 7.
15. Direct `js/prisma/7.10`: `content/js/prisma/7.10/prompt.md`; `content/js/prisma/7.10/sources.md`. Includes Node.js 24 and TypeScript 7.
16. Direct `infra/dockerfile/1`: `content/infra/dockerfile/1/prompt.md`; `content/infra/dockerfile/1/sources.md`. No parents.

No external supporting documentation is represented as independently verified. Corpus source notes record their own reviews; their compatibility qualifications do not establish project compatibility.

## Secure-Coding Rules

No ACTIVE entries: the required eligible technical prompt provenance is unresolved. Existing requirements and confirmed architecture boundaries remain authoritative; these blocked entries neither suspend them nor prescribe speculative mechanisms.

**SC-001 — Server boundary controls**
- **Status:** BLOCKED
- **Required outcome:** Boundary validation and resource/request controls must cover public reads, authenticated commands, staff polling/replay, and provider callback inputs without treating client state as authoritative.
- **Threat drivers:** [T-003](THREAT_MODEL.md#t-003-client-controlled-business-transition), [T-012](THREAT_MODEL.md#t-012-polling-or-durable-work-misses-service-targets), [T-045](THREAT_MODEL.md#t-045-web-presentation-misstates-statevalueerrorstaleness).
- **Dependency:** Confirm runtime/framework roles and versions, eligible baselines, request/resource budgets, and enforcement configuration before specifying HTTP, request validation, resource limits, logging, or outbound-request controls. See [OD-001](#od-001), [OD-005](#od-005), [OD-008](#od-008).

**SC-002 — Web rendering and browser controls**
- **Status:** BLOCKED
- **Dependency:** Confirm React version, browser/rendering scope, and session transport before selecting rendering, browser storage, origin, or request-forgery controls. See [OD-003](#od-003), [OD-008](#od-008), [OD-012](#od-012).

**SC-003 — Identity and authorization**
- **Status:** BLOCKED
- **Required outcome:** Every protected operation must validate the current session, role, ownership, suspension and assignment at the server boundary; prior access, client state and resource identifiers confer no authority.
- **Threat drivers:** [T-001](THREAT_MODEL.md#t-001-email-link-or-session-impersonation), [T-003](THREAT_MODEL.md#t-003-client-controlled-business-transition), [T-014](THREAT_MODEL.md#t-014-account-exceeds-ownership-assignment-role-or-suspension-scope), [T-015](THREAT_MODEL.md#t-015-unauthorized-actor-reads-or-changes-restricted-records), [T-022](THREAT_MODEL.md#t-022-email-access-artifact-permits-impersonation), [T-035](THREAT_MODEL.md#t-035-identityauthorization-returns-wrong-decision).
- **Dependency:** Resolve link expiry/reuse/revocation, session invalidation, first Admin provisioning, implementation selection, and eligible authorization guidance for the existing role/ownership/assignment requirements. See [OD-003](#od-003), [OD-004](#od-004), [OD-008](#od-008).

**SC-004 — Native authentication and storage**
- **Status:** BLOCKED
- **Dependency:** Establish native scope, platforms, versions, credential transport, and whether passkeys are required before selecting native controls. See [OD-002](#od-002), [OD-003](#od-003), [OD-008](#od-008).

**SC-005 — Persistence and financial consistency**
- **Status:** BLOCKED
- **Required outcome:** Capacity changes and financial evidence processing must use authoritative current state and one operation identity so each authorized transition and external side effect is applied at most once; repeated or stale work cannot repeat or reverse it, while later authorized lifecycle progress remains possible. Refund and payout limits remain binding.
- **Threat drivers:** [T-004](THREAT_MODEL.md#t-004-altered-late-duplicate-or-replayed-financial-evidence), [T-005](THREAT_MODEL.md#t-005-concurrent-capacity-corruption), [T-006](THREAT_MODEL.md#t-006-duplicate-or-out-of-order-work-applies-stale-effects), [T-016](THREAT_MODEL.md#t-016-untrusted-or-repeated-payment-evidence-corrupts-state), [T-017](THREAT_MODEL.md#t-017-concurrent-capacity-changes-misallocate-a-seat), [T-018](THREAT_MODEL.md#t-018-repeated-refund-or-payout-exceeds-authorized-value), [T-032](THREAT_MODEL.md#t-032-confirm-booking-without-acceptable-payment-and-valid-hold), [T-033](THREAT_MODEL.md#t-033-excess-refund-or-duplicate-payout), [T-038](THREAT_MODEL.md#t-038-seat-holdcapacity-accounting-inconsistent), [T-040](THREAT_MODEL.md#t-040-refundpayout-late-excessive-duplicate-or-email-blocked).
- **Dependency:** Confirm persistence interfaces, transaction/locking/constraint mechanisms, operation identity, provider contract, and eligible data-access guidance for capacity, bookings, refunds, and payouts. See [OD-006](#od-006), [OD-009](#od-009).

**SC-006 — Provider boundary implementation**
- **Status:** BLOCKED
- **Required outcome:** Only authenticated provider evidence or reconciliation may change payment state; browser returns remain non-authoritative. Payment and email integrations must preserve separate credentials, mutable failure state, retry handling and execution capacity.
- **Threat drivers:** [T-002](THREAT_MODEL.md#t-002-unauthenticated-payment-result-accepted-as-provider-evidence), [T-013](THREAT_MODEL.md#t-013-email-failure-delays-accessnotices-or-financial-work), [T-016](THREAT_MODEL.md#t-016-untrusted-or-repeated-payment-evidence-corrupts-state), [T-020](THREAT_MODEL.md#t-020-email-integration-failure-controls-financial-work), [T-039](THREAT_MODEL.md#t-039-payment-result-validatedreconcileddeduplicated-incorrectly), [T-044](THREAT_MODEL.md#t-044-email-accessnotice-fails-without-safe-fallback).
- **Dependency:** Confirm payment/email provider contracts and eligible implementation guidance for callback-origin validation, credential handling, exact transferred fields, provider idempotency, and independent execution within the already-confirmed isolated gateways. See [OD-007](#od-007), [OD-009](#od-009).

**SC-007 — Private data and audit lifecycle**
- **Status:** BLOCKED
- **Required outcome:** Audience projections minimize fields; audit entries link to affected records and operations without copying private notes; the private-note inventory and deletion process cover every decided copy class and restoration path.
- **Threat drivers:** [T-007](THREAT_MODEL.md#t-007-state-change-lacks-attributable-evidence), [T-008](THREAT_MODEL.md#t-008-public-or-wrong-account-projection-exposes-restricted-data), [T-009](THREAT_MODEL.md#t-009-shopper-or-email-projection-leaks-restricted-fields), [T-011](THREAT_MODEL.md#t-011-private-food-notes-survive-deletionwithdrawal), [T-019](THREAT_MODEL.md#t-019-private-notes-or-addresses-leak-through-projectioncopy), [T-025](THREAT_MODEL.md#t-025-cook-view-links-attendee-identity-with-food-needs), [T-027](THREAT_MODEL.md#t-027-permitted-audiences-learn-precise-event-location), [T-028](THREAT_MODEL.md#t-028-food-needs-disclose-personal-circumstances-to-organizercook), [T-029](THREAT_MODEL.md#t-029-auditfinancial-history-creates-attributable-long-term-linkage), [T-030](THREAT_MODEL.md#t-030-private-note-copies-outlive-deletion-lifecycle), [T-034](THREAT_MODEL.md#t-034-private-note-remains-accessible-after-deletionwithdrawal), [T-043](THREAT_MODEL.md#t-043-durable-work-audit-or-retention-incomplete).
- **Dependency:** Confirm data classification, consent evidence, audit readers/retention, address retention, all copy classes, deletion/restoration coverage, storage/logging implementation, and eligible sources for enforcing audience filtering and required retention. See [OD-006](#od-006), [OD-008](#od-008), [OD-010](#od-010), [OD-013](#od-013).

**SC-008 — Build and deployment controls**
- **Status:** BLOCKED
- **Dependency:** Confirm deployment/build scope and versions before selecting container, secret injection, network, or operational-access controls. See [OD-007](#od-007), [OD-008](#od-008).

**SC-009 — Staff update authorization**
- **Status:** BLOCKED
- **Required outcome:** Every poll and replay checks the current assignment, applies audience filtering, returns one consistent paged revision, and stops data access when assignment ends; cursors confer no access.
- **Threat drivers:** [T-010](THREAT_MODEL.md#t-010-removed-staff-retain-currentreplayed-access), [T-012](THREAT_MODEL.md#t-012-polling-or-durable-work-misses-service-targets), [T-021](THREAT_MODEL.md#t-021-lost-delayed-replayed-or-stale-staff-updates), [T-042](THREAT_MODEL.md#t-042-staff-updatereconnect-lost-stale-duplicate-or-mis-scoped).
- **Dependency:** Confirm update transport and eligible implementation guidance for current-assignment authorization, cursor semantics, paging, consistent revision, replay, assignment-removal behavior, and private response filtering. See [OD-001](#od-001), [OD-010](#od-010), [OD-011](#od-011), [OD-013](#od-013).

## Open Security Decisions

<a id="od-001"></a>
**OD-001 — Runtime and framework scope**
- **Missing/conflict:** Roles conflict under AQ-1; versions are UNKNOWN under AQ-5. Resolution is TO BE DECIDED. Evidence needed: authoritative role correction and version scopes for Node.js and Fastify.
- **Affected:** SC-001, SC-009; candidates `js/nodejs/26`, `js/fastify/5.12`, and transitive Node.js 24.
- **Owner:** UNKNOWN.

<a id="od-002"></a>
**OD-002 — Native platforms and passkeys**
- **Missing/choice:** AQ-2 leaves platforms and workflows unresolved. React Native version, Android compile/target/runtime scope, iOS SDK/deployment/toolchain scope, and passkey behavior are UNKNOWN. Evidence needed: authoritative native scope and versions; requirements establishing any passkey workflows. No passkey requirement is inferred from the candidate labels.
- **Affected:** SC-004; React Native, Android SDK, iOS SDK, Kotlin, and Swift candidates.
- **Owner:** UNKNOWN.

<a id="od-003"></a>
**OD-003 — Email access and session lifecycle**
- **Missing/choice:** AQ-4 leaves email provider, link expiry, reuse and revocation, session lifetime and invalidation, native credential transport, and first Admin provisioning TO BE DECIDED. Better Auth use/version is UNKNOWN. Evidence needed: approved identity/session contracts consistent with FR-6.2–FR-6.4, FR-6.11 and FR-6.18, plus applicable implementation/version evidence. Threats: T-001, T-022, T-035.
- **Affected:** SC-002–SC-004; candidate `js/better-auth/1.7`.
- **Owner:** UNKNOWN.

<a id="od-004"></a>
**OD-004 — Authorization implementation**
- **Missing/choice:** OPA use/version is UNKNOWN. Evidence needed: an authoritative authorization implementation decision and enforcement interfaces; if OPA is selected, its version and policy scope. Required roles and gateway isolation do not select it (`ARCHITECTURE.md` §8, Authentication and privacy boundaries; DR-9).
- **Affected:** SC-003; candidate `policy/open-policy-agent/1.20`.
- **Owner:** UNKNOWN.

<a id="od-005"></a>
**OD-005 — Validation implementation**
- **Missing/choice:** Zod use/version and request/resource budgets are UNKNOWN for public reads, authenticated commands, staff polling/replay and provider callbacks. Evidence needed: confirmed validation implementation and boundary contracts, with approved limits where needed (`ARCHITECTURE.md` §4, AQ-5). Existing field constraints remain defined by FR-1 and FR-7. Threats: T-003, T-012, T-045.
- **Affected:** SC-001; candidate `js/zod/4`.
- **Owner:** UNKNOWN.

<a id="od-006"></a>
**OD-006 — Persistence and execution consistency**
- **Missing/choice:** Database, data-access technology/version, transactions, locking, constraints, operation identity across callbacks/reconciliation/retries/Admin retries, durable-work retry, and reconciliation details are TO BE DECIDED (AQ-5). Evidence needed: accepted persistence interfaces and consistency mechanisms meeting FR-8, FR-9, and NFR-2; Prisma selection/version if used. Threats: T-004–T-006, T-016–T-018, T-032, T-033, T-038–T-040, T-043.
- **Affected:** SC-005, SC-007; candidate `js/prisma/7.10`.
- **Owner:** UNKNOWN.

<a id="od-007"></a>
**OD-007 — Deployment and operational configuration**
- **Missing/choice:** Hosting, container use, build platform, builder/syntax versions, secret provisioning, network boundaries, and operational access are UNKNOWN; execution settings remain TO BE DECIDED (AQ-5). Evidence needed: approved deployment/build and operational contracts. No topology is selected here.
- **Affected:** SC-006, SC-008; candidate `infra/dockerfile/1`.
- **Owner:** UNKNOWN.

<a id="od-008"></a>
**OD-008 — Transitive composition eligibility**
- **Missing/conflict:** Direct Node.js 26 differs from Node.js 24 included by Fastify, Better Auth, and Prisma. No project version establishes precedence. JavaScript ES2026, React 19, TypeScript 7, Kotlin 2.4, and Swift 6.4 applicability is unconfirmed. Resolution is TO BE DECIDED; no baseline is substituted or silently dropped.
- **Evidence needed:** Authoritative language/runtime/framework versions and host scope, followed by compatibility checks against the resolved sources. React Native's source notes do not establish TypeScript 7 toolchain or complete ES2026 host support; Prisma's notes leave generated-client/TypeScript integration checks to the project. Includes alone cannot settle these checks.
- **Affected:** SC-001–SC-004, SC-007, SC-008; all six transitive packs listed above.
- **Owner:** UNKNOWN.

<a id="od-009"></a>
**OD-009 — Provider contracts**
- **Missing/choice:** Payment and email providers, callback-origin verification, browser-return semantics, reconciliation, provider operation identity/idempotency, exact transferred fields, and delivery contracts are TO BE DECIDED (AQ-3, AQ-4). Evidence needed: selected providers and documented interface/authenticity contracts compatible with required payments, refunds, payouts, and email access; eligible implementation guidance. Gateway separation is already confirmed and is not reopened. Threats: T-002, T-004, T-013, T-016, T-018, T-020, T-032, T-033, T-039, T-040, T-044.
- **Affected:** SC-005, SC-006.
- **Owner:** UNKNOWN.

<a id="od-010"></a>
**OD-010 — Privacy and record coverage**
- **Missing/choice:** Jurisdictions/statutory duties are UNKNOWN. Private-note versus retained recipe/handling classification, readers and retention for audit/update/notice/address records, derived/cache/export/backup copy coverage, restoration behavior, and deletion verification are TO BE DECIDED (AQ-7). Evidence needed: documented classification, complete storage/copy lifecycle, and applicable obligations consistent with FR-11.3–FR-11.9. Required 90-day deletion and 24-month financial retention are already established. Threats: T-007, T-011, T-019, T-027, T-029, T-030, T-034, T-043.
- **Affected:** SC-007, SC-009.
- **Owner:** UNKNOWN.

<a id="od-011"></a>
**OD-011 — Update transport**
- **Missing/choice:** Polling acceptance, authorization on every replay, cursor semantics, paging, consistent revision, and assignment-removal behavior are TO BE DECIDED (AQ-6). Evidence needed: accepted transport and authorization/replay contracts meeting FR-4.9–FR-4.15, FR-6.10, FR-6.18, and NFR-1.1–NFR-1.3. Threats: T-010, T-012, T-021, T-042.
- **Affected:** SC-009.
- **Owner:** UNKNOWN.

<a id="od-012"></a>
**OD-012 — Browser and rendering scope**
- **Missing/choice:** Browser support and native equivalents remain TO BE DECIDED (AQ-8); rendering mode and applicable host APIs are UNKNOWN. Evidence needed: documented browser/rendering scope and React version, preserving `DESIGN.md` interaction constraints. Design DQ-1–DQ-3 do not establish security configuration.
- **Affected:** SC-002; transitive `js/react/19` and `js/javascript/ES2026`.
- **Owner:** UNKNOWN.

<a id="od-013"></a>
**OD-013 — Consent, withdrawal, and pre-confirmation staff disclosure**
- **Missing/choice:** The exact pre-confirmation cook/shopper update fields, consent evidence details, notice timing, and withdrawal behavior when cancellation is no longer eligible are TO BE DECIDED. Evidence needed: an approved privacy interaction and data contract consistent with FR-3.10, FR-3.25, FR-3.26, FR-4.1–FR-4.8, and FR-11.7. Threats: T-019, T-025, T-028, T-037, T-041.
- **Affected:** SC-007, SC-009.
- **Owner:** UNKNOWN.
