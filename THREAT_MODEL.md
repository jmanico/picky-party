# THREAT_MODEL_REPORT

**System:** Picky Party first-release cooking-event website specification  
**Date:** 2026-10-19  
**Classification:** Not supplied  
**Version:** 1.0

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Scope and Methodology](#2-scope-and-methodology)
3. [System Architecture](#3-system-architecture)
4. [Threat Inventory](#4-threat-inventory)
5. [Risk Matrix](#5-risk-matrix)
6. [Control Gap Analysis](#6-control-gap-analysis)
7. [Action Register](#7-action-register)
8. [Requirement Traceability](#8-requirement-traceability)
9. [Appendices](#9-appendices)

## 1. Executive Summary

**Overall risk: Undetermined.** The model supplies no approved common likelihood/impact method, mapping rules, appetite, thresholds, or evidence needed to rank the findings. It is therefore invalid to combine the methodologies into a heat map or a single severity distribution.

The pipeline retained **45 specification-level records**: 14 unrated STRIDE threats, 8 PASTA scenarios with unresolved ratings, 8 LINDDUN privacy records with no score, 4 attack-tree roots with unknown likelihood/impact and conditional paths, and 11 unranked FMEA failure modes. Stage 05 found AI/ML analysis **Not applicable** to the documented first release. Stage 06 found **no application implementation**: the repository scan identified specifications and a static SVG but no source, configuration, dependencies, schemas, tests, runtime/deployment artifacts, CI, containers, or infrastructure code. No record is proof of an implemented vulnerability or an effective control.

The model repeatedly identifies authorization and audience enforcement, booking/payment consistency, refund/payout deduplication, availability of updates and durable work, and private-note copy lifecycle as material business concerns. That repetition comes mainly from different methods applied to the same four specifications, so it is corroborating analysis rather than independent implementation evidence. LINDDUN records `T-023`–`T-029` preserve intentional or required privacy tradeoffs; they are not vulnerability findings. STRIDE records `T-012` and `T-013` are availability/failure risks and do not assume an attacker or hostile provider.

The specifications were hardened after the pipeline analysis with threat-linked product behavior, architecture placement, rendering rules, blocked security outcomes, and one new unresolved decision, `OD-013`. Those changes are catalogued in §8.2. They do not retroactively change the downstream model reproduced unedited in Appendix A, do not establish implementation, and do not supply risk owners or deadlines.

No supplied assessment prioritizes the findings. The report therefore preserves model order. The immediate evidence need is implementation and decision material: identity/session contracts; provider contracts; persistence and durable-work design; complete privacy-copy lifecycle; deployment/operations evidence; and code, configuration, tests, and runtime observations.

## 2. Scope and Methodology

### 2.1 System Description

The modeled system is the Picky Party first-release website for publishing cooking events, collecting consented food needs, assigning cooks and shoppers, taking payment, managing bookings/cancellations/refunds/payouts, issuing staff updates and notices, producing preparation/shopping information, auditing state changes, and applying deletion/retention rules (`SCP-001`, `E-REQ`, `E-ARCH`, `E-DES`).

### 2.2 Scope

In scope: specified web workflows; logical client, application, persistence, payment, and email boundaries; identity; event and recipe data; orders and food requests; booking and finance; staff updates; planning; audit; deletion; retention; and rendering behavior.

Excluded or unresolved: group bookings, extra portions, offline payments, waitlists, discounts, automatic dietary certification, unresolved native workflows, and unspecified deployment topology. Native frameworks are mentioned but native platforms, workflows, parity, storage, link handling, printing, and accessibility mappings are unresolved.

### 2.3 Methodology

| Method ID | Method | Pipeline disposition | Findings |
| --- | --- | --- | ---: |
| `M-00` | STRIDE | complete across six categories; none; all 14 threats unrated | 14 |
| `M-01` | PASTA | seven stages completed with evidence gaps; none; eight qualitative impacts and unresolved ratings | 8 |
| `M-02` | LINDDUN | seven privacy types dispositioned across nine flows; no scores; required disclosures distinguished from misuse/control failure | 8 |
| `M-03` | Attack-tree decomposition | four trees, 42 source nodes, ten conditional paths; no path-comparison method; likelihood/impact unknown | 4 |
| `M-04` | FMEA | eight passes; 11 functions assessed and mobile not assessed; none; all failure modes unranked | 11 |
| `M-05` | AI/ML lifecycle and taxonomy review | not applicable to documented first-release system; MITRE ATLAS v2026.09; OWASP ML Security Top 10 2023 draft v0.2; OWASP GenAI LLM Top 10 2026 | 0 |
| `M-06` | Repository reconnaissance | complete inventory; no implementation to assess; not applicable | 0 |
| `M-07` | Document absorption | four documents normalized; four unranked architecture risks preserved | 0 |

STRIDE, PASTA, LINDDUN, attack trees, and FMEA provide distinct security, privacy, path, and failure perspectives. Their records remain separate and are linked where they address the same underlying event. Stage 05 checked AI/ML lifecycle and taxonomies and found them not applicable to the documented first release. Stage 06 directly inventoried the repository and found no implementation to analyze. Stage 07 normalized the supplied documents.

### 2.4 Automation Coverage

| Coverage ID | Area | Methods | Artifacts | Recorded status | Limits |
| --- | --- | --- | --- | --- | --- |
| `CV-001` | Source specifications | `M-00`, `M-01`, `M-02`, `M-03`, `M-04`, `M-05`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | assessed repeatedly from the same four document claims; repetitions are not independent confirmation | All source documents are undated except DESIGN.md's alpha revision; authors unknown. |
| `CV-002` | Identity, authorization, and sessions | `M-00`, `M-01`, `M-03`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | threats and gaps assessed | No link/session/Admin-bootstrap implementation or tests. |
| `CV-003` | Privacy and personal-data flows | `M-00`, `M-01`, `M-02`, `M-03`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | audiences, intended disclosures, misuse paths, and lifecycle assessed | Jurisdiction, transparency/intervention, provider fields, full copy inventory, readers, and backups unresolved. |
| `CV-004` | Booking, payment, refund, and payout integrity | `M-00`, `M-01`, `M-03`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC` | threats, failures, paths, and requirements assessed | Provider contract, schema, transactions, idempotency, and tests absent. |
| `CV-005` | Availability, staff updates, durable work | `M-00`, `M-01`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | timing/failure scenarios assessed | Transport and execution unselected; no load/failure/restart tests. |
| `CV-006` | Rendering and accessibility | `M-01`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | specified interactions assessed | No browser matrix, rendered app, or accessibility/security tests. |
| `CV-007` | Implementation and runtime | `M-06` | `E-REPO` | not assessable; repository directly establishes absence of implementation artifacts | This is independent repository evidence of absence, not proof of a vulnerability or of future implementation choices. |
| `CV-008` | AI/ML lifecycle | `M-05`, `M-06` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES`, `E-AI`, `E-REPO` | not applicable to documented first release; no AI/ML element in specifications or repository | Reassess if AI/ML, LLM, retrieval, agent, or tool behavior is added. |
| `CV-009` | Attack-path coverage | `M-01`, `M-03` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | 18 conditional or assumption-marked paths retained | No path-ranking evidence; all success depends on assumed control failure or unresolved implementation. |
| `CV-010` | Risk prioritization | `M-00`, `M-01`, `M-02`, `M-03`, `M-04`, `M-07` | `E-REQ`, `E-ARCH`, `E-SEC`, `E-DES` | unresolved across all findings | No approved common scale, mapping, appetite, factors, thresholds, ownership, or loss evidence. |
| `CV-011` | Single-source conclusions | None | None | identified | Repository artifact inventory/absence comes only from M-06 direct scan., AI taxonomy release inventories come only from M-05 external verification., LINDDUN intended-disclosure privacy framing comes only from M-02 although underlying facts are in requirements., Pre-confirmation cook-update field ambiguity was identified only by M-02., Document authors/date gaps and source visualization inventory are normalized only by M-07. |
| `CV-012` | Unassessed areas | None | None | explicit | Native workflows/platforms, Deployment/runtime/network topology, Operational identities and administrator access, Secrets/build/release/CI, Monitoring/incident response/backup/restore, Legal compliance, Implemented control effectiveness |

### 2.5 Data Sources

| Evidence ID | Artifact | Kind/producer | Recorded status or records |
| --- | --- | --- | --- |
| `E-REQ` | REQUIREMENTS.md | behavioral authority | adopted intended behavior, including labeled assumptions; not implementation evidence |
| `E-ARCH` | ARCHITECTURE.md | logical architecture | one confirmed gateway-isolation constraint; other mechanisms proposed, unknown, or to be decided |
| `E-SEC` | SECURITY.md | security decision/status document | SC-001 through SC-009 BLOCKED; no active secure-coding composition or implemented control |
| `E-DES` | DESIGN.md | interaction/rendering specification | assumption-based design intent; no rendered implementation |
| `E-REPO` | Repository inventory | repository reconnaissance | Eight root files: seven Markdown documents and one SVG; no source, dependency manifest, lockfile, schema, test, runtime config, CI, container, IaC, or deployment artifact |
| `E-AI` | AI/ML taxonomy verification | external method provenance | MITRE ATLAS v2026.09, OWASP ML Security Top 10 2023 draft v0.2, and OWASP GenAI LLM Top 10 2026 checked; all not applicable to documented scope |
| `EV-00` | .threat-model-work/00-stride.md | STRIDE analyzer | 14 threats |
| `EV-01` | .threat-model-work/01-pasta.md | PASTA analyzer | 8 threats, 8 paths, 8 unresolved risks |
| `EV-02` | .threat-model-work/02-linddun.md | LINDDUN analyzer | 8 privacy threats and risks |
| `EV-03` | .threat-model-work/03-attack-tree.md | Attack-tree analyzer | 4 root threats, 4 trees, 10 conditional paths |
| `EV-04` | .threat-model-work/04-fmea.md | FMEA analyzer | 11 unranked failure modes |
| `EV-05` | .threat-model-work/05-ai-ml.md | AI/ML analyzer | no threats; lifecycle and three taxonomies not applicable |
| `EV-06` | .threat-model-work/06-repository.md | Repository reconnaissance | no implementation findings; five evidence gaps |
| `EV-07` | .threat-model-work/07-documents.md | Document absorption | normalized documents, system, controls, requirements, risks, and gaps |

### 2.6 Limitations

- The repository contains no application implementation. Control presence and effectiveness cannot be verified.
- The four source specifications were the common evidence base for most stages; repeated findings are not independent confirmation.
- No approved common risk scale, FMEA factors, loss evidence, ownership register, deadlines, or risk appetite exists.
- Provider selection/contracts, identity/session lifecycle, persistence/concurrency, deployment/network topology, operational identities, secrets, CI/release, monitoring, incident response, backup/restore, and native scope are unresolved.
- Jurisdiction, legal applicability, private-note classification boundaries, audit readers, address/nonfinancial retention, and complete copy/deletion/restoration coverage are unresolved.
- All attack-tree paths are conditionally satisfiable; all PASTA paths are assumption-marked. No exploitability was demonstrated.
- Stage 05 is Not applicable to current documented scope and must be rerun if AI/ML, LLM, retrieval, agent, or tool behavior is introduced.

## 3. System Architecture

### 3.1 System Context

Figure 1 (`FIG-001`, source `DGM-001`) places the Picky Party scope between Visitors, account roles, an untrusted/unauthorized requester, and separate payment/email services. Client HTTP JSON is proposed; provider protocols remain unresolved. The payment and email exchanges remain separate. Full figure material is in Appendix B.

### 3.2 Component Architecture

Figure 2 (`FIG-002`, source `DGM-002`) shows web/native clients, the trusted application, persistence, the isolated payment integration, the separate email integration, external providers, and proposed durable work. Node.js/Fastify roles and versions remain unresolved, PostgreSQL is proposed, and no cache, queue, file store, concrete service split, or deployment node is specified.

### 3.3 Data Flow

Figure 3 (`FIG-003`, source `DGM-003`) traces `F-001`–`F-009` and `D-001`–`D-007`. Figure 5 (`FIG-005`) overlays exact requirement groups through explicit `RQ→T→F` references and is not a compliance verdict. No sequence figure was produced because no supplied assessment selected a flow for emphasis; selecting one would invent prioritization.

### 3.4 Trust Boundaries

| Boundary | Direction | Status | Control evidence |
| --- | --- | --- | --- |
| `B-001` Client to application | `Z-001`, `Z-002` → `Z-003` | HTTP JSON proposed; native unresolved | document claims only; evidence `E-ARCH`, `E-SEC` |
| `B-002` Application to persistence | `Z-003` → `Z-004` | proposed; interfaces/technology unresolved | evidence gap; evidence `E-ARCH`, `E-SEC` |
| `B-003` Financial workflows to payment gateway/provider | `Z-003`, `Z-005` → `Z-007` | gateway separation confirmed; contract unresolved | claimed logical boundary; implementation absent; evidence `E-ARCH`, `E-SEC` |
| `B-004` Payment callback inbound | `Z-007` → `Z-005`, `Z-003` | logical adapter specified; protocol/authenticity unresolved | evidence gap; evidence `E-ARCH`, `E-SEC` |
| `B-005` Identity/notices to email gateway/provider | `Z-003`, `Z-006` → `Z-007` | gateway separation confirmed; contract unresolved | claimed logical boundary; implementation absent; evidence `E-ARCH`, `E-SEC` |
| `B-006` Audience-specific response projections | `Z-003` → `Z-001`, `Z-002` | restrictions required; server enforcement proposed | document claim only; evidence `E-REQ`, `E-ARCH`, `E-DES` |

Payment and email gateway separation is an approved logical constraint, but no implementation establishes it. Other internal boundaries are proposed or unresolved.

### 3.5 Attack Surface

Figure 6 (`FIG-006`, source `DGM-005`) covers every modeled entry point. Threat counts are derived reference counts, not risk scores.

| Entry point | Status | Access model from figure brief | Linked threat count |
| --- | --- | --- | ---: |
| `EP-001` Public calendar, event page, and QR URL | required | Public; no authentication required. Public-field projection C-003. | 6 |
| `EP-002` Email verification/sign-in link | required; lifecycle unresolved | Possession of verification/sign-in artifact; lifecycle unresolved. Session control C-011. | 5 |
| `EP-003` Authenticated views/actions | required; endpoint specification absent | Authenticated. Ownership, role, suspension, and current assignment C-002; endpoints unspecified. | 29 |
| `EP-004` Checkout browser flow | required; protocol unresolved | Authentication requirement not stated in the model. Order/hold and payment checks C-002/C-006. | 9 |
| `EP-005` Payment callbacks/reconciliation | logical entry; protocol unresolved | Provider-origin authentication protocol unresolved. Evidence/state authorization C-006/C-007. | 19 |
| `EP-006` Email delivery gateway | logical entry; provider unresolved | Gateway/provider authentication unresolved. Isolation and filtered notices C-001/C-013. | 8 |
| `EP-007` Scheduled/retry work | proposed durable-work mechanism | Operational identity unresolved. Eligibility, deduplication, and durable execution C-007/C-008. | 21 |

## 4. Threat Inventory

Threats are grouped by source methodology and retain source order. No cross-method ranking is implied.

## 4.1 STRIDE

<a id="t-001-email-link-or-session-impersonation"></a>
### T-001: Email-link or session impersonation

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Spoofing  
**Affected assets/elements:** `A-001` Account identity and access records, `D-001` Identity, verification, session, role, suspension, and assignment data, `F-002` Verify and sign in through email link, `EP-002` Email verification/sign-in link  
**Trust boundary:** `B-001`, `B-005`

#### Description

Another person's verification/sign-in link or session identifier is treated as that account; lifecycle is unresolved.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Another person's verification/sign-in link or session identifier is treated as that account; lifecycle is unresolved.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege. Magnitude is unknown or unresolved.

#### Existing Controls

`C-011` Verified-email access, logout, and revocable sessions — behavior required; session proposal unapproved; lifecycle/Admin bootstrap unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-002-unauthenticated-payment-result-accepted-as-provider-evidence"></a>
### T-002: Unauthenticated payment result accepted as provider evidence

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Spoofing  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `B-004` Payment callback inbound, `F-005` Checkout, callback, validation, and booking confirmation, `EP-005` Payment callbacks/reconciliation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

A payment callback message causes financial/booking state without authentic-origin validation.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: A payment callback message causes financial/booking state without authentic-origin validation.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-003-client-controlled-business-transition"></a>
### T-003: Client-controlled business transition

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Tampering  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `F-003` Create event and expose exact location to authorized audiences, `F-004` Submit, review, accept, and prepare food requests, `F-006` Cancel, refund, reconcile, and pay out, `EP-003` Authenticated views/actions  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Untrusted ownership, assignment, price, capacity, recipe, order, acceptance, cancellation, or transition values alter commitments or eligibility.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Untrusted ownership, assignment, price, capacity, recipe, order, acceptance, cancellation, or transition values alter commitments or eligibility.

#### Business Impact

Linked model risk families: Invalid event, order, or recipe state. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-005` Server-owned transitions, launch validation, and immutable snapshots — required outcomes with proposed placement; implementation absent (evidence E-REQ, E-ARCH)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-004-altered-late-duplicate-or-replayed-financial-evidence"></a>
### T-004: Altered, late, duplicate, or replayed financial evidence

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Tampering  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `F-005` Checkout, callback, validation, and booking confirmation, `F-006` Cancel, refund, reconcile, and pay out, `EP-005` Payment callbacks/reconciliation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Invalid evidence creates a booking, exceeds a refund cap, or duplicates a payout unless validated/deduplicated.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Invalid evidence creates a booking, exceeds a refund cap, or duplicates a payout unless validated/deduplicated.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription, Excess refund, duplicate payout, or delayed finance. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-007` Refund caps, payout eligibility, and financial deduplication — required outcomes with proposed mechanisms; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-005-concurrent-capacity-corruption"></a>
### T-005: Concurrent capacity corruption

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Tampering  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `B-002` Application to persistence, `F-005` Checkout, callback, validation, and booking confirmation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Overlapping checkout, confirmation, cancellation, or capacity changes exceed capacity or fail atomic hold replacement.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Overlapping checkout, confirmation, cancellation, or capacity changes exceed capacity or fail atomic hold replacement.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-006-duplicate-or-out-of-order-work-applies-stale-effects"></a>
### T-006: Duplicate or out-of-order work applies stale effects

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Tampering  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `F-005` Checkout, callback, validation, and booking confirmation, `F-006` Cancel, refund, reconcile, and pay out, `F-009` Audit, delete private notes, and retain financial records, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Scheduled tasks, callbacks, retries, or reconciliation repeat expiry/refund/payout/notification effects or apply stale state.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Scheduled tasks, callbacks, retries, or reconciliation repeat expiry/refund/payout/notification effects or apply stale state.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-007` Refund caps, payout eligibility, and financial deduplication — required outcomes with proposed mechanisms; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-007-state-change-lacks-attributable-evidence"></a>
### T-007: State change lacks attributable evidence

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Repudiation  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-006` Cancel, refund, reconcile, and pay out, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

An actor disputes a change when actor/time/outcome is absent, incomplete, or disconnected from records/provider references.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: An actor disputes a change when actor/time/outcome is absent, incomplete, or disconnected from records/provider references.

#### Business Impact

Linked model risk families: Attributable records unavailable or over-linkable. Magnitude is unknown or unresolved.

#### Existing Controls

`C-009` Attributable audit — required behavior; audience, integrity, nonfinancial retention, and implementation unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-008-public-or-wrong-account-projection-exposes-restricted-data"></a>
### T-008: Public or wrong-account projection exposes restricted data

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Information Disclosure  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-003` Exact event address and access instructions, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `B-006` Audience-specific response projections  
**Trust boundary:** `B-006`

#### Description

A response exposes exact addresses, orders, dietary requests, payments, or updates beyond public/owned records.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: A response exposes exact addresses, orders, dietary requests, payments, or updates beyond public/owned records.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-009-shopper-or-email-projection-leaks-restricted-fields"></a>
### T-009: Shopper or email projection leaks restricted fields

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Information Disclosure  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-003` Exact event address and access instructions, `D-004` Food needs, private notes, recipes, variants, and handling notes, `F-007` Staff update, polling, and reconnect replay, `F-008` Persist account notice and send filtered email, `B-005` Identity/notices to email gateway/provider, `B-006` Audience-specific response projections  
**Trust boundary:** `B-001`, `B-002`, `B-005`, `B-006`

#### Description

Shopper views or email notices disclose Attendee names, private food notes, or exact addresses.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Shopper views or email notices disclose Attendee names, private food notes, or exact addresses.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-013` Persistent account notices and filtered email fallback — required behavior; provider/implementation unresolved (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-010-removed-staff-retain-currentreplayed-access"></a>
### T-010: Removed staff retain current/replayed access

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Information Disclosure  
**Affected assets/elements:** `A-001` Account identity and access records, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-001` Identity, verification, session, role, suspension, and assignment data, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-007` Staff update, polling, and reconnect replay, `EP-003` Authenticated views/actions  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

A removed cook/shopper continues to receive state or replay because assignment is not checked per read.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: A removed cook/shopper continues to receive state or replay because assignment is not checked per read.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-011-private-food-notes-survive-deletionwithdrawal"></a>
### T-011: Private food notes survive deletion/withdrawal

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Information Disclosure  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-002`, `B-006`

#### Description

Private notes remain in updates, jobs, audit, derived records, or backups after withdrawal or the 90-day point.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Private notes remain in updates, jobs, audit, derived records, or backups after withdrawal or the 90-day point.

#### Business Impact

Linked model risk families: Private-note survival beyond deletion/withdrawal. Magnitude is unknown or unresolved.

#### Existing Controls

`C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-012-polling-or-durable-work-misses-service-targets"></a>
### T-012: Polling or durable work misses service targets

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Denial of Service  
**Affected assets/elements:** `A-005` Staff updates, notices, delivery state, audit records, and pending work, `F-001` Publish and discover, `F-006` Cancel, refund, reconcile, and pay out, `F-007` Staff update, polling, and reconnect replay, `F-009` Audit, delete private notes, and retain financial records, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Staff replay or work dispatch falls behind and misses update, reconnect, refund, or availability targets.

**Interpretation:** Availability/failure risk; no attacker or deliberate action is assumed.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Staff replay or work dispatch falls behind and misses update, reconnect, refund, or availability targets.

#### Business Impact

Linked model risk families: Update, work, or read availability misses targets. Magnitude is unknown or unresolved.

#### Existing Controls

`C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-012` Canonical, accessible, and visibly stale presentation — required/design behavior; not rendered or tested (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-013-email-failure-delays-accessnotices-or-financial-work"></a>
### T-013: Email failure delays access/notices or financial work

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Denial of Service  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-008` Email integration credentials and client configuration, `F-002` Verify and sign in through email link, `F-006` Cancel, refund, reconcile, and pay out, `F-008` Persist account notice and send filtered email  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-005`, `B-006`

#### Description

Email backlog delays access/notices and, if isolation fails, required financial work.

**Interpretation:** Availability/dependency failure risk; no hostile email provider or attacker is assumed.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Email backlog delays access/notices and, if isolation fails, required financial work.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance, Update, work, or read availability misses targets. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-013` Persistent account notices and filtered email fallback — required behavior; provider/implementation unresolved (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-014-account-exceeds-ownership-assignment-role-or-suspension-scope"></a>
### T-014: Account exceeds ownership, assignment, role, or suspension scope

**Rating:** source: unrated; unified: unresolved  
**Rating method:** STRIDE; none; all 14 threats unrated  
**Category:** Elevation of Privilege  
**Affected assets/elements:** `A-001` Account identity and access records, `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `F-003` Create event and expose exact location to authorized audiences, `F-004` Submit, review, accept, and prepare food requests, `F-006` Cancel, refund, reconcile, and pay out, `F-007` Staff update, polling, and reconnect replay  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

An account acts on another order/event, an unassigned event, or Admin-only operation.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: An account acts on another order/event, an unassigned event, or Admin-only operation.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

## 4.2 PASTA

<a id="t-015-unauthorized-actor-reads-or-changes-restricted-records"></a>
### T-015: Unauthorized actor reads or changes restricted records

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-001` Account identity and access records, `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `B-001` Client to application, `B-006` Audience-specific response projections  
**Trust boundary:** `B-001`, `B-006`

#### Description

Client requests cross ownership, role, suspension, assignment, or audience boundaries; success requires failed enforcement.

#### Attack Scenario

1. `AP-011` (assumption-marked): Request another audience's record; authorization/projection fails; restricted data/state is returned/changed.

Assumptions: Success requires an absent/defective control; no defect evidenced.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege, Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-016-untrusted-or-repeated-payment-evidence-corrupts-state"></a>
### T-016: Untrusted or repeated payment evidence corrupts state

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-007` Payment integration credentials and client configuration, `B-004` Payment callback inbound, `F-005` Checkout, callback, validation, and booking confirmation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Callback, reconciliation, retry, or browser-return evidence is accepted without required validation/deduplication.

#### Attack Scenario

1. `AP-012` (assumption-marked): Deliver/replay payment result; validation/deduplication fails; invalid booking/financial state results.

Assumptions: Success requires validation/deduplication failure.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-017-concurrent-capacity-changes-misallocate-a-seat"></a>
### T-017: Concurrent capacity changes misallocate a seat

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `F-005` Checkout, callback, validation, and booking confirmation, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Checkout, confirmation, cancellation, expiry, or capacity edits observe inconsistent occupancy.

#### Attack Scenario

1. `AP-013` (assumption-marked): Overlap capacity changes; shared atomic rule fails; occupancy/seat allocation becomes inconsistent.

Assumptions: Operations overlap and consistency enforcement fails.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-018-repeated-refund-or-payout-exceeds-authorized-value"></a>
### T-018: Repeated refund or payout exceeds authorized value

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-007` Payment integration credentials and client configuration, `F-006` Cancel, refund, reconcile, and pay out, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Admin/background/callback/reconciliation retries bypass operation identity, caps, obligations, or eligibility.

#### Attack Scenario

1. `AP-014` (assumption-marked): Repeat financial invocation; cap/eligibility/deduplication fails; excess refund/duplicate payout results.

Assumptions: Duplicate invocation occurs and enforcement fails.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-007` Refund caps, payout eligibility, and financial deduplication — required outcomes with proposed mechanisms; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-019-private-notes-or-addresses-leak-through-projectioncopy"></a>
### T-019: Private notes or addresses leak through projection/copy

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-003` Exact event address and access instructions, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-007` Staff update, polling, and reconnect replay, `F-008` Persist account notice and send filtered email, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-001`, `B-002`, `B-005`, `B-006`

#### Description

Public, shopper, email, replay, job, audit, financial, derived, or backup copies exceed audience/lifecycle.

#### Attack Scenario

1. `AP-015` (assumption-marked): Restricted content is copied; filtering/deletion misses copy; content is disclosed/retained.

Assumptions: A secondary copy contains restricted content and filtering/deletion misses it.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure, Private-note survival beyond deletion/withdrawal. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-020-email-integration-failure-controls-financial-work"></a>
### T-020: Email integration failure controls financial work

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-007` Payment integration credentials and client configuration, `A-008` Email integration credentials and client configuration, `F-006` Cancel, refund, reconcile, and pay out, `F-008` Persist account notice and send filtered email  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-005`, `B-006`

#### Description

Shared state/capacity could let email outage delay finance despite confirmed isolation requirement.

#### Attack Scenario

1. `AP-016` (assumption-marked): Email retries accumulate; execution isolation fails; financial operation is delayed.

Assumptions: Email fails and required separation is not implemented.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-021-lost-delayed-replayed-or-stale-staff-updates"></a>
### T-021: Lost, delayed, replayed, or stale staff updates

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-006` Presentation and transient client state, `F-007` Staff update, polling, and reconnect replay  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Cursor, reconnect, polling, or work failure omits changes, serves obsolete content, or ignores removed assignment.

#### Attack Scenario

1. `AP-017` (assumption-marked): Staff reconnects; cursor/assignment/privacy/durability fails; stale/incomplete/unauthorized data displays.

Assumptions: A delivery/cursor/revision/assignment check fails.

#### Business Impact

Linked model risk families: Update, work, or read availability misses targets, Misleading or inaccessible security-relevant rendering. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-012` Canonical, accessible, and visibly stale presentation — required/design behavior; not rendered or tested (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-022-email-access-artifact-permits-impersonation"></a>
### T-022: Email access artifact permits impersonation

**Rating:** likelihood: unresolved; impact: unresolved; overall: unresolved  
**Rating method:** PASTA; none; eight qualitative impacts and unresolved ratings  
**Category:** PASTA scenario  
**Affected assets/elements:** `A-001` Account identity and access records, `A-008` Email integration credentials and client configuration, `D-001` Identity, verification, session, role, suspension, and assignment data, `F-002` Verify and sign in through email link, `EP-002` Email verification/sign-in link  
**Trust boundary:** `B-001`, `B-005`

#### Description

An unauthorized party obtains/reuses a valid link or session artifact; lifecycle behavior is unresolved.

#### Attack Scenario

1. `AP-018` (assumption-marked): Unauthorized party obtains access artifact; lifecycle permits reuse; authenticated session results.

Assumptions: Unauthorized acquisition and lifecycle-permitted reuse.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege. Magnitude is unknown or unresolved.

#### Existing Controls

`C-011` Verified-email access, logout, and revocable sessions — behavior required; session proposal unapproved; lifecycle/Admin bootstrap unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

## 4.3 LINDDUN

<a id="t-023-permanent-url-enables-longitudinal-event-correlation"></a>
### T-023: Permanent URL enables longitudinal event correlation

**Rating:** likelihood: required public observability; beyond that unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Linking  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `D-002` Public event metadata and permanent URL/QR, `F-001` Publish and discover, `EP-001` Public calendar, event page, and QR URL  
**Trust boundary:** `B-001`, `B-006`

#### Description

Visitors correlate one event over time with Organizer, city, schedule, menu, price, availability, and cancellation state.

**Interpretation:** Intentional product disclosure and privacy tradeoff, not a vulnerability finding.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Visitors correlate one event over time with Organizer, city, schedule, menu, price, availability, and cancellation state.

#### Business Impact

Linked model risk families: Intended public event linking, identifying, and detecting. Magnitude is unknown or unresolved.

#### Existing Controls

`C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-024-public-event-identifies-organizer-association"></a>
### T-024: Public event identifies Organizer association

**Rating:** likelihood: required disclosure; beyond that unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Identifying  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `D-002` Public event metadata and permanent URL/QR, `F-001` Publish and discover  
**Trust boundary:** `B-001`, `B-006`

#### Description

Organizer name is published with event details as required behavior.

**Interpretation:** Intentional public association and privacy tradeoff, not a vulnerability finding.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Organizer name is published with event details as required behavior.

#### Business Impact

Linked model risk families: Intended public event linking, identifying, and detecting. Magnitude is unknown or unresolved.

#### Existing Controls

`C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-025-cook-view-links-attendee-identity-with-food-needs"></a>
### T-025: Cook view links Attendee identity with food needs

**Rating:** likelihood: required for current cooks; misuse unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Linking and Identifying  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `F-004` Submit, review, accept, and prepare food requests, `ACT-004` Cook  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Confirmed cook view combines name, food needs, quantities, recipes, and handling information.

**Interpretation:** Required disclosure to current cooks and privacy tradeoff, not a vulnerability finding; misuse remains unknown.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Confirmed cook view combines name, food needs, quantities, recipes, and handling information.

#### Business Impact

Linked model risk families: Intended food-needs identity linkage and disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-004` Food-note consent, review, acceptance, and request labeling — required/design behavior; implementation absent (evidence E-REQ, E-DES); `C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-026-public-discovery-reveals-event-existencestate"></a>
### T-026: Public discovery reveals event existence/state

**Rating:** likelihood: required disclosure; beyond that unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Detecting  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `D-002` Public event metadata and permanent URL/QR, `F-001` Publish and discover  
**Trust boundary:** `B-001`, `B-006`

#### Description

Visitors detect launched-event city, time, price, availability, and cancellation state.

**Interpretation:** Intentional public disclosure and privacy tradeoff, not a vulnerability finding.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Visitors detect launched-event city, time, price, availability, and cancellation state.

#### Business Impact

Linked model risk families: Intended public event linking, identifying, and detecting. Magnitude is unknown or unresolved.

#### Existing Controls

`C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-027-permitted-audiences-learn-precise-event-location"></a>
### T-027: Permitted audiences learn precise event location

**Rating:** likelihood: required disclosure to permitted audiences; downstream retention unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Data Disclosure  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `D-003` Exact event address and access instructions, `F-003` Create event and expose exact location to authorized audiences  
**Trust boundary:** `B-001`, `B-006`

#### Description

Confirmed Attendees, current staff, Organizer, and Admin receive exact address; downstream handling is unspecified.

**Interpretation:** Required audience disclosure and privacy tradeoff, not a vulnerability finding; downstream handling remains unknown.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Confirmed Attendees, current staff, Organizer, and Admin receive exact address; downstream handling is unspecified.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-028-food-needs-disclose-personal-circumstances-to-organizercook"></a>
### T-028: Food needs disclose personal circumstances to Organizer/cook

**Rating:** likelihood: occurs for consented workflows; misuse unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Data Disclosure  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-004` Food needs, private notes, recipes, variants, and handling notes, `F-004` Submit, review, accept, and prepare food requests  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Consented food information crosses to Organizer and cook with identity/handling details; shopper/email exclusions differ.

**Interpretation:** Consented workflow disclosure and privacy tradeoff, not a vulnerability finding; misuse remains unknown.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Consented food information crosses to Organizer and cook with identity/handling details; shopper/email exclusions differ.

#### Business Impact

Linked model risk families: Intended food-needs identity linkage and disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-004` Food-note consent, review, acceptance, and request labeling — required/design behavior; implementation absent (evidence E-REQ, E-DES); `C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-029-auditfinancial-history-creates-attributable-long-term-linkage"></a>
### T-029: Audit/financial history creates attributable long-term linkage

**Rating:** likelihood: required record creation; access/use unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Non-repudiation, Linking, and Identifying  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-002`, `B-006`

#### Description

Actor/time/outcome and 24-month financial records bind people to event and financial activity.

**Interpretation:** Required attributable-record creation and privacy tradeoff, not a vulnerability finding; record readers and use remain unknown.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Actor/time/outcome and 24-month financial records bind people to event and financial activity.

#### Business Impact

Linked model risk families: Attributable records unavailable or over-linkable. Magnitude is unknown or unresolved.

#### Existing Controls

`C-009` Attributable audit — required behavior; audience, integrity, nonfinancial retention, and implementation unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-030-private-note-copies-outlive-deletion-lifecycle"></a>
### T-030: Private-note copies outlive deletion lifecycle

**Rating:** likelihood: unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** LINDDUN; no scores; required disclosures distinguished from misuse/control failure  
**Category:** Data Disclosure  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-002`, `B-006`

#### Description

Snapshots, operations, derived records, or backups retain private content; reference-only design is unconfirmed.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Snapshots, operations, derived records, or backups retain private content; reference-only design is unconfirmed.

#### Business Impact

Linked model risk families: Private-note survival beyond deletion/withdrawal. Magnitude is unknown or unresolved.

#### Existing Controls

`C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

## 4.4 Attack-tree decomposition

<a id="t-031-obtain-restricted-data-without-audience-entitlement"></a>
### T-031: Obtain restricted data without audience entitlement

**Rating:** likelihood: unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** Attack-tree decomposition; no path-comparison method; likelihood/impact unknown  
**Category:** Attack-tree root  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `F-001` Publish and discover, `F-007` Staff update, polling, and reconnect replay  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Public projection, cross-Attendee read, or former-staff replay succeeds after a required control fails.

#### Attack Scenario

1. `AP-001` (conditionally satisfiable): Public request plus failed public-field exclusion.
2. `AP-002` (conditionally satisfiable): Authenticated cross-record selection plus failed ownership enforcement.
3. `AP-003` (conditionally satisfiable): Former-staff cursor, replay request, and failed current-assignment enforcement.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege, Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-032-confirm-booking-without-acceptable-payment-and-valid-hold"></a>
### T-032: Confirm booking without acceptable payment and valid hold

**Rating:** likelihood: unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** Attack-tree decomposition; no path-comparison method; likelihood/impact unknown  
**Category:** Attack-tree root  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `F-005` Checkout, callback, validation, and booking confirmation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Browser return, invalid/replayed provider evidence, or over-capacity hold reaches confirmation after controls fail.

#### Attack Scenario

1. `AP-004` (conditionally satisfiable): Checkout plus browser-controlled result plus failed authoritative-evidence rule.
2. `AP-005` (conditionally satisfiable): Invalid/repeated provider evidence plus failed validation/deduplication.
3. `AP-006` (conditionally satisfiable): Simultaneous last-seat requests plus failed consistency plus invalid-hold confirmation.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-033-excess-refund-or-duplicate-payout"></a>
### T-033: Excess refund or duplicate payout

**Rating:** likelihood: unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** Attack-tree decomposition; no path-comparison method; likelihood/impact unknown  
**Category:** Attack-tree root  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `F-006` Cancel, refund, reconcile, and pay out  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Repeated financial work plus failed cap/deduplication and provider completion transfers excess value.

#### Attack Scenario

1. `AP-007` (conditionally satisfiable): Repeated refund plus failed aggregate cap plus provider acceptance.
2. `AP-008` (conditionally satisfiable): Repeated payout plus failed deduplication plus provider completion.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance. Magnitude is unknown or unresolved.

#### Existing Controls

`C-007` Refund caps, payout eligibility, and financial deduplication — required outcomes with proposed mechanisms; implementation absent (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-034-private-note-remains-accessible-after-deletionwithdrawal"></a>
### T-034: Private note remains accessible after deletion/withdrawal

**Rating:** likelihood: unknown; impact: unknown; score: not assigned; unified: unresolved  
**Rating method:** Attack-tree decomposition; no path-comparison method; likelihood/impact unknown  
**Category:** Attack-tree root  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state, `F-009` Audit, delete private notes, and retain financial records  
**Trust boundary:** `B-002`, `B-006`

#### Description

Operational copy or retained classification survives source deletion and remains readable.

#### Attack Scenario

1. `AP-009` (conditionally satisfiable): Copied note plus source deletion plus readable surviving copy.
2. `AP-010` (conditionally satisfiable): Private content enters retained record, falls outside deletion classification, and remains readable.

#### Business Impact

Linked model risk families: Private-note survival beyond deletion/withdrawal. Magnitude is unknown or unresolved.

#### Existing Controls

`C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

## 4.5 FMEA

<a id="t-035-identityauthorization-returns-wrong-decision"></a>
### T-035: Identity/authorization returns wrong decision

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-001` Account identity and access records, `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `F-002` Verify and sign in through email link, `EP-003` Authenticated views/actions  
**Trust boundary:** `B-001`, `B-005`

#### Description

Email/session, role, ownership, suspension, Admin-grant, or assignment enforcement admits unauthorized access or rejects preserved access.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Email/session, role, ownership, suspension, Admin-grant, or assignment enforcement admits unauthorized access or rejects preserved access.

#### Business Impact

Linked model risk families: Identity impersonation or excess privilege, Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-011` Verified-email access, logout, and revocable sessions — behavior required; session proposal unapproved; lifecycle/Admin bootstrap unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-036-event-publication-or-recipe-snapshot-invalid"></a>
### T-036: Event publication or recipe snapshot invalid

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients, `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-002` Public event metadata and permanent URL/QR, `D-004` Food needs, private notes, recipes, variants, and handling notes, `F-001` Publish and discover, `F-003` Create event and expose exact location to authorized audiences  
**Trust boundary:** `B-001`, `B-006`

#### Description

Launch/lifecycle/visibility/time/immutability/snapshot processing stores or serves invalid state.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Launch/lifecycle/visibility/time/immutability/snapshot processing stores or serves invalid state.

#### Business Impact

Linked model risk families: Invalid event, order, or recipe state. Magnitude is unknown or unresolved.

#### Existing Controls

`C-005` Server-owned transitions, launch validation, and immutable snapshots — required outcomes with proposed placement; implementation absent (evidence E-REQ, E-ARCH); `C-012` Canonical, accessible, and visibly stale presentation — required/design behavior; not rendered or tested (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-037-food-requestconsentacceptanceorder-state-advances-incorrectly"></a>
### T-037: Food request/consent/acceptance/order state advances incorrectly

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `F-004` Submit, review, accept, and prepare food requests  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Consent, review, acceptance, payment, cutoff, or cancellation gates fail.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Consent, review, acceptance, payment, cutoff, or cancellation gates fail.

#### Business Impact

Linked model risk families: Invalid event, order, or recipe state. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-004` Food-note consent, review, acceptance, and request labeling — required/design behavior; implementation absent (evidence E-REQ, E-DES); `C-005` Server-owned transitions, launch validation, and immutable snapshots — required outcomes with proposed placement; implementation absent (evidence E-REQ, E-ARCH)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-038-seat-holdcapacity-accounting-inconsistent"></a>
### T-038: Seat hold/capacity accounting inconsistent

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `F-005` Checkout, callback, validation, and booking confirmation, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Overlapping operations oversubscribe, retain/release wrong hold, or create duplicate bookings.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Overlapping operations oversubscribe, retain/release wrong hold, or create duplicate bookings.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-039-payment-result-validatedreconcileddeduplicated-incorrectly"></a>
### T-039: Payment result validated/reconciled/deduplicated incorrectly

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-007` Payment integration credentials and client configuration, `F-005` Checkout, callback, validation, and booking confirmation, `EP-005` Payment callbacks/reconciliation  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`

#### Description

Payment input changes state without valid evidence, amount/currency, hold, event state, or operation identity.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Payment input changes state without valid evidence, amount/currency, hold, event state, or operation identity.

#### Business Impact

Linked model risk families: Invalid booking, payment state, or oversubscription. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-006` Payment evidence, capacity, booking, and confirmation integrity — required outcomes with proposed transaction/deduplication; provider/persistence unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-040-refundpayout-late-excessive-duplicate-or-email-blocked"></a>
### T-040: Refund/payout late, excessive, duplicate, or email-blocked

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-007` Payment integration credentials and client configuration, `A-008` Email integration credentials and client configuration, `F-006` Cancel, refund, reconcile, and pay out, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Wrong financial amount, eligibility, identity, timing, or execution dependency causes loss or delay.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Wrong financial amount, eligibility, identity, timing, or execution dependency causes loss or delay.

#### Business Impact

Linked model risk families: Excess refund, duplicate payout, or delayed finance, Update, work, or read availability misses targets. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-007` Refund caps, payout eligibility, and financial deduplication — required outcomes with proposed mechanisms; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-041-preparationshopping-output-wrong-or-privacy-leaking"></a>
### T-041: Preparation/shopping output wrong or privacy-leaking

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `F-004` Submit, review, accept, and prepare food requests, `F-007` Staff update, polling, and reconnect replay  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Wrong orders/variants/conversions/rounding or audience projection yields bad quantities or disclosure.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Wrong orders/variants/conversions/rounding or audience projection yields bad quantities or disclosure.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure. Magnitude is unknown or unresolved.

#### Existing Controls

`C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-014` Deterministic ingredient planning — required behavior; exact arithmetic proposed; implementation absent (evidence E-REQ, E-ARCH)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-042-staff-updatereconnect-lost-stale-duplicate-or-mis-scoped"></a>
### T-042: Staff update/reconnect lost, stale, duplicate, or mis-scoped

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-006` Presentation and transient client state, `F-007` Staff update, polling, and reconnect replay  
**Trust boundary:** `B-001`, `B-002`, `B-006`

#### Description

Staff view differs from current authorized state because delivery, cursor, authorization, privacy, or rendering fails.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Staff view differs from current authorized state because delivery, cursor, authorization, privacy, or rendering fails.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure, Update, work, or read availability misses targets, Misleading or inaccessible security-relevant rendering. Magnitude is unknown or unresolved.

#### Existing Controls

`C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization — required behavior; server placement proposed; implementation absent (evidence E-REQ, E-ARCH, E-SEC); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-012` Canonical, accessible, and visibly stale presentation — required/design behavior; not rendered or tested (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-043-durable-work-audit-or-retention-incomplete"></a>
### T-043: Durable work, audit, or retention incomplete

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings, `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `F-006` Cancel, refund, reconcile, and pay out, `F-009` Audit, delete private notes, and retain financial records, `EP-007` Scheduled/retry work  
**Trust boundary:** `B-001`, `B-002`, `B-003`, `B-004`, `B-006`

#### Description

Restart, scheduled work, audit fields, or deletion/retention diverges from source state.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Restart, scheduled work, audit fields, or deletion/retention diverges from source state.

#### Business Impact

Linked model risk families: Private-note survival beyond deletion/withdrawal, Attributable records unavailable or over-linkable, Update, work, or read availability misses targets. Magnitude is unknown or unresolved.

#### Existing Controls

`C-008` Durable work, updates, cursor replay, and independent dispatch — required outcomes with proposed mechanisms; transport/execution unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-009` Attributable audit — required behavior; audience, integrity, nonfinancial retention, and implementation unresolved (evidence E-REQ, E-ARCH, E-SEC); `C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation — required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved (evidence E-REQ, E-ARCH, E-SEC)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-044-email-accessnotice-fails-without-safe-fallback"></a>
### T-044: Email access/notice fails without safe fallback

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-001` Account identity and access records, `A-005` Staff updates, notices, delivery state, audit records, and pending work, `A-008` Email integration credentials and client configuration, `F-002` Verify and sign in through email link, `F-008` Persist account notice and send filtered email  
**Trust boundary:** `B-001`, `B-002`, `B-005`, `B-006`

#### Description

Access/notice delivery or persistence fails, email leaks restricted fields, or isolation failure cascades to finance.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: Access/notice delivery or persistence fails, email leaks restricted fields, or isolation failure cascades to finance.

#### Business Impact

Linked model risk families: Unauthorized restricted-data disclosure, Update, work, or read availability misses targets. Magnitude is unknown or unresolved.

#### Existing Controls

`C-001` Payment/email gateway isolation — approved logical architecture constraint; implementation absent (evidence E-ARCH, E-SEC, EV-07); `C-003` Audience-specific projections and field minimization — required field outcomes plus proposed server projections; implementation absent (evidence E-REQ, E-ARCH, E-DES); `C-013` Persistent account notices and filtered email fallback — required behavior; provider/implementation unresolved (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

<a id="t-045-web-presentation-misstates-statevalueerrorstaleness"></a>
### T-045: Web presentation misstates state/value/error/staleness

**Rating:** source: unranked; factors absent; unified: unresolved  
**Rating method:** FMEA; none; all failure modes unranked  
**Category:** FMEA failure mode  
**Affected assets/elements:** `A-006` Presentation and transient client state, `D-002` Public event metadata and permanent URL/QR, `D-004` Food needs, private notes, recipes, variants, and handling notes, `D-005` Order, hold, booking, attendance, and ingredient-planning state, `D-006` Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity, `D-007` Staff updates, cursors, account notices, audit records, work metadata, and delivery state  
**Trust boundary:** Not supplied

#### Description

UI conflates state, omits price/deadline/errors, loses input, or breaks keyboard/focus/reflow.

#### Attack Scenario

No step-by-step path was supplied. Recorded scenario: UI conflates state, omits price/deadline/errors, loses input, or breaks keyboard/focus/reflow.

#### Business Impact

Linked model risk families: Invalid event, order, or recipe state, Misleading or inaccessible security-relevant rendering. Magnitude is unknown or unresolved.

#### Existing Controls

`C-012` Canonical, accessible, and visibly stale presentation — required/design behavior; not rendered or tested (evidence E-REQ, E-ARCH, E-DES)

#### Recommended Mitigations

Not supplied as a threat-attached implementation plan. Referenced controls preserve required, approved logical, proposed, unresolved, or BLOCKED status and must not be treated as implemented. Owner, priority, effort, and target date: Not supplied.

#### Residual Risk

Not assessed.

## 5. Risk Matrix

### 5.1 Risk Heat Map

No combined heat map is valid. The model has no approved common likelihood-impact method or mapping, and all unified risk ratings are unresolved. Overall risk remains **Undetermined**.

### 5.2 Risk by Category

| Method | Recorded category | Count | Threat IDs |
| --- | --- | ---: | --- |
| STRIDE | Spoofing | 2 | `T-001`, `T-002` |
| STRIDE | Tampering | 4 | `T-003`, `T-004`, `T-005`, `T-006` |
| STRIDE | Repudiation | 1 | `T-007` |
| STRIDE | Information Disclosure | 4 | `T-008`, `T-009`, `T-010`, `T-011` |
| STRIDE | Denial of Service | 2 | `T-012`, `T-013` |
| STRIDE | Elevation of Privilege | 1 | `T-014` |
| PASTA | PASTA scenario | 8 | `T-015`, `T-016`, `T-017`, `T-018`, `T-019`, `T-020`, `T-021`, `T-022` |
| LINDDUN | Linking | 1 | `T-023` |
| LINDDUN | Identifying | 1 | `T-024` |
| LINDDUN | Linking and Identifying | 1 | `T-025` |
| LINDDUN | Detecting | 1 | `T-026` |
| LINDDUN | Data Disclosure | 3 | `T-027`, `T-028`, `T-030` |
| LINDDUN | Non-repudiation, Linking, and Identifying | 1 | `T-029` |
| Attack-tree decomposition | Attack-tree root | 4 | `T-031`, `T-032`, `T-033`, `T-034` |
| FMEA | FMEA failure mode | 11 | `T-035`, `T-036`, `T-037`, `T-038`, `T-039`, `T-040`, `T-041`, `T-042`, `T-043`, `T-044`, `T-045` |

### 5.3 Risk by Component

Counts below are references, not severity rankings.

| Asset | Threat references | Threat IDs |
| --- | ---: | --- |
| `A-003` Orders, food needs, consent, proposals, accepted recipes, holds, and bookings | 29 | `T-002`, `T-003`, `T-004`, `T-005`, `T-006`, `T-008`, `T-009`, `T-010`, `T-011`, `T-014`, `T-015`, `T-016`, `T-017`, `T-019`, `T-021`, `T-025`, `T-028`, `T-030`, `T-031`, `T-032`, `T-034`, `T-035`, `T-036`, `T-037`, `T-038`, `T-039`, `T-041`, `T-042`, `T-043` |
| `A-005` Staff updates, notices, delivery state, audit records, and pending work | 22 | `T-006`, `T-007`, `T-008`, `T-009`, `T-010`, `T-011`, `T-012`, `T-013`, `T-015`, `T-018`, `T-019`, `T-020`, `T-021`, `T-029`, `T-030`, `T-031`, `T-034`, `T-035`, `T-040`, `T-042`, `T-043`, `T-044` |
| `A-004` Connected-account, payment, refund, payout, fee, and reconciliation records | 20 | `T-002`, `T-003`, `T-004`, `T-006`, `T-007`, `T-008`, `T-013`, `T-014`, `T-015`, `T-016`, `T-018`, `T-020`, `T-029`, `T-031`, `T-032`, `T-033`, `T-035`, `T-039`, `T-040`, `T-043` |
| `A-002` Events, addresses, assignments, URLs, dishes, recipes, and ingredients | 12 | `T-003`, `T-008`, `T-014`, `T-015`, `T-019`, `T-023`, `T-024`, `T-026`, `T-027`, `T-031`, `T-035`, `T-036` |
| `A-001` Account identity and access records | 7 | `T-001`, `T-010`, `T-014`, `T-015`, `T-022`, `T-035`, `T-044` |
| `A-008` Email integration credentials and client configuration | 5 | `T-013`, `T-020`, `T-022`, `T-040`, `T-044` |
| `A-007` Payment integration credentials and client configuration | 5 | `T-016`, `T-018`, `T-020`, `T-039`, `T-040` |
| `A-006` Presentation and transient client state | 3 | `T-021`, `T-042`, `T-045` |

| Flow | Threat references | Threat IDs |
| --- | ---: | --- |
| `F-006` Cancel, refund, reconcile, and pay out | 12 | `T-003`, `T-004`, `T-006`, `T-007`, `T-012`, `T-013`, `T-014`, `T-018`, `T-020`, `T-033`, `T-040`, `T-043` |
| `F-009` Audit, delete private notes, and retain financial records | 9 | `T-006`, `T-007`, `T-011`, `T-012`, `T-019`, `T-029`, `T-030`, `T-034`, `T-043` |
| `F-007` Staff update, polling, and reconnect replay | 9 | `T-009`, `T-010`, `T-012`, `T-014`, `T-019`, `T-021`, `T-031`, `T-041`, `T-042` |
| `F-005` Checkout, callback, validation, and booking confirmation | 9 | `T-002`, `T-004`, `T-005`, `T-006`, `T-016`, `T-017`, `T-032`, `T-038`, `T-039` |
| `F-004` Submit, review, accept, and prepare food requests | 6 | `T-003`, `T-014`, `T-025`, `T-028`, `T-037`, `T-041` |
| `F-001` Publish and discover | 6 | `T-012`, `T-023`, `T-024`, `T-026`, `T-031`, `T-036` |
| `F-008` Persist account notice and send filtered email | 5 | `T-009`, `T-013`, `T-019`, `T-020`, `T-044` |
| `F-002` Verify and sign in through email link | 5 | `T-001`, `T-013`, `T-022`, `T-035`, `T-044` |
| `F-003` Create event and expose exact location to authorized audiences | 4 | `T-003`, `T-014`, `T-027`, `T-036` |

### 5.4 Risk Trend

Not assessed. No prior threat model or comparable historical rating set was supplied.

## 6. Control Gap Analysis

### 6.1 Controls Inventory

| Control | Status | Evidence | Mechanism/scope or dependency |
| --- | --- | --- | --- |
| `C-001` Payment/email gateway isolation | approved logical architecture constraint; implementation absent | `E-ARCH`, `E-SEC`, `EV-07` | Separate ports, adapters, clients, credentials, config, retry/failure state, execution capacity; distinct payment callback adapter. |
| `C-002` Ownership, role, suspension, Admin-grant, and current-assignment authorization | required behavior; server placement proposed; implementation absent | `E-REQ`, `E-ARCH`, `E-SEC` | Protected reads/actions and replay entitlement. |
| `C-003` Audience-specific projections and field minimization | required field outcomes plus proposed server projections; implementation absent | `E-REQ`, `E-ARCH`, `E-DES` | Public/Attendee/Organizer/cook/shopper/Admin, address, shopper, email, and own-record filters. |
| `C-004` Food-note consent, review, acceptance, and request labeling | required/design behavior; implementation absent | `E-REQ`, `E-DES` | Consent before sharing; Organizer review; Attendee acceptance; no certification claim. |
| `C-005` Server-owned transitions, launch validation, and immutable snapshots | required outcomes with proposed placement; implementation absent | `E-REQ`, `E-ARCH` | Event/order commands, cutoff/time rules, event and accepted-recipe snapshots. |
| `C-006` Payment evidence, capacity, booking, and confirmation integrity | required outcomes with proposed transaction/deduplication; provider/persistence unresolved | `E-REQ`, `E-ARCH`, `E-SEC` | Authenticity, amount/currency, hold/event checks, capacity serialization, atomic replacement, operation identity. |
| `C-007` Refund caps, payout eligibility, and financial deduplication | required outcomes with proposed mechanisms; implementation absent | `E-REQ`, `E-ARCH`, `E-SEC` | Aggregate refund cap, unresolved obligations, unique payout proceeds, retries. |
| `C-008` Durable work, updates, cursor replay, and independent dispatch | required outcomes with proposed mechanisms; transport/execution unresolved | `E-REQ`, `E-ARCH`, `E-SEC` | Commit work/update records with state, resume after restart, current state/history, replay authorization. |
| `C-009` Attributable audit | required behavior; audience, integrity, nonfinancial retention, and implementation unresolved | `E-REQ`, `E-ARCH`, `E-SEC` | Actor, time, and outcome for required state changes. |
| `C-010` Private-note deletion, financial exclusion, retention, and reference-only propagation | required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved | `E-REQ`, `E-ARCH`, `E-SEC` | 90-day/withdrawal deletion, 24-month financial subset, no private notes in retained finance, proposed references instead of copies. |
| `C-011` Verified-email access, logout, and revocable sessions | behavior required; session proposal unapproved; lifecycle/Admin bootstrap unresolved | `E-REQ`, `E-ARCH`, `E-SEC` | Required verification/sign-in/logout; proposed opaque server session. |
| `C-012` Canonical, accessible, and visibly stale presentation | required/design behavior; not rendered or tested | `E-REQ`, `E-ARCH`, `E-DES` | States, values, field errors, retained input, staleness, focus, keyboard, reflow. |
| `C-013` Persistent account notices and filtered email fallback | required behavior; provider/implementation unresolved | `E-REQ`, `E-ARCH`, `E-DES` | Account notice remains when email fails; restricted fields excluded. |
| `C-014` Deterministic ingredient planning | required behavior; exact arithmetic proposed; implementation absent | `E-REQ`, `E-ARCH` | Confirmed-order filter, accepted snapshots, unit families, exact conversions, upward rounding, visible calculation time. |
| `C-015` SC-001 Server boundary controls | BLOCKED | `E-SEC` | OD-001, OD-005, OD-008 |
| `C-016` SC-002 Web rendering/browser controls | BLOCKED | `E-SEC` | OD-003, OD-008, OD-012 |
| `C-017` SC-003 Identity/authorization | BLOCKED | `E-SEC` | OD-003, OD-004, OD-008 |
| `C-018` SC-004 Native authentication/storage | BLOCKED | `E-SEC` | OD-002, OD-003, OD-008 |
| `C-019` SC-005 Persistence/financial consistency | BLOCKED | `E-SEC` | OD-006, OD-009 |
| `C-020` SC-006 Provider boundary implementation | BLOCKED | `E-SEC` | OD-007, OD-009 |
| `C-021` SC-007 Private data/audit lifecycle | BLOCKED | `E-SEC` | OD-006, OD-008, OD-010 |
| `C-022` SC-008 Build/deployment controls | BLOCKED | `E-SEC` | OD-007, OD-008 |
| `C-023` SC-009 Staff-update authorization | BLOCKED | `E-SEC` | OD-001, OD-010, OD-011 |

No control is implemented or verified. `C-001` records an approved logical gateway-isolation constraint with implementation absent. `C-015`–`C-023` preserve the BLOCKED status of `SC-001`–`SC-009`.

### 6.2 Gap Analysis

No demonstrated implementation vulnerability is recorded because no implementation exists. The following are evidence, decision, specification, metadata, or coverage gaps.

| Gap | Type | Topic | Missing | Needed evidence |
| --- | --- | --- | --- | --- |
| `G-001` | evidence gap | Implementation and control effectiveness | Source, config, dependencies, schemas, tests, runtime/deployment artifacts, logs, observations. | Implemented artifacts and scoped verification results. |
| `G-002` | decision/evidence gap | Identity, session, Admin bootstrap, and authorization | Link contents/expiry/reuse/revocation, session lifetime/revocation, first Admin provisioning, native credential transport, enforcement interfaces. | Approved identity/session/Admin/authorization contract plus implementation/tests. |
| `G-003` | decision/evidence gap | Payment/email providers and data contracts | Provider selection, fields, authenticity, browser return, reconciliation, idempotency, refund/payout/fees, delivery, retention, timing. | Provider ADRs and authenticated interface/data-lifecycle contracts. |
| `G-004` | decision/evidence gap | Persistence, concurrency, durable execution, backup/restore | Schema, relationships, constraints, transactions, locking, operation IDs, retry/reconciliation, scheduler, backup/restore/deletion behavior. | Database/consistency design, durable-work contract, and recovery verification. |
| `G-005` | decision/evidence gap | Deployment, networks, secrets, operations, build/release | Hosting/topology, network boundaries, secret provisioning, operational identities/access, containers/IaC, CI/release, monitoring, incident response. | Deployment/network diagrams and operational/build/security runbooks. |
| `G-006` | decision/evidence gap | Technology versions and compatibility | Resolved Node/Fastify roles/versions and React, React Native, language/toolchain, validation, auth, data-access, policy, container decisions. | Approved version/compatibility decision record and eligible secure-coding provenance. |
| `G-007` | decision/evidence gap | Privacy lifecycle, transparency, intervention, and legal scope | Jurisdictions/duties; private-note boundary; purposes/recipients/notices; correction/export; ineligible-cancellation withdrawal; copy/readers/derived/cache/export/backup deletion; nonfinancial/address retention. | Authoritative legal applicability plus data inventory/classification, notice/consent, recipient, access, and retention/deletion matrices. |
| `G-008` | specification gap | Pre-confirmation cook update contents | FR-4.1 requires a cook update when an order is placed; FR-4.5 enumerates named food-needs content only for confirmed orders. | Explicit field-level projection for pre-confirmation cook updates. |
| `G-009` | decision/evidence gap | Staff update transport, replay, and timing | Transport choice, paging/cursor/revision semantics, replay authorization, retry behavior, end-to-end load/reconnect/failure results. | Approved protocol and load/reconnect/failure tests. |
| `G-010` | decision/evidence gap | Native, API, browser, and rendering scope | API schemas/authorization declarations, native platforms/workflows/parity/link/storage/printing/accessibility, browsers/rendering/breakpoints and rendered validation. | Versioned API, native scope, browser/rendering matrix, resolved DQ-1-DQ-3, and rendered tests. |
| `G-011` | risk-method gap | Risk and path prioritization/ownership | Common likelihood/impact method, FMEA factors/scales, mappings, appetite, thresholds, loss data, path comparison, owners, deadlines. | Approved risk method/mappings and ownership register. |
| `G-012` | scope-change trigger | Future AI/ML | No implementation independently confirms specification-level absence forever; future AI/ML is not prohibited project-wide. | Re-run lifecycle/taxonomy analysis if an AI/ML, LLM, retrieval, agent, or tool component is proposed. |
| `G-013` | metadata gap | Document provenance | Authors and dates for all four specifications; editions for three; README has title only. | Document ownership/revision metadata and useful repository setup/inventory documentation. |
| `G-014` | coverage gap | Components with no implementation-level threat validation | Every component, boundary, flow, and document-only control lacks code/config/runtime validation; mobile is not functionally assessed. | Implementation artifacts tied to the unified component/flow IDs and targeted verification evidence. |

### 6.3 Defense in Depth Review

The model attaches exactly one control record to 16 threats: `T-005`, `T-007`, `T-011`, `T-014`, `T-017`, `T-020`, `T-022`, `T-023`, `T-024`, `T-026`, `T-030`, `T-032`, `T-033`, `T-034`, `T-038`, `T-045`. This is a modeling count, not proof that runtime defense depends on one effective mechanism. Threats with no control record: None. Control composition and effectiveness remain unverified because implementation evidence is absent.

Cross-method links show recurring control families: authorization/projections (`C-002`, `C-003`), payment/capacity integrity (`C-006`, `C-007`), durable work/replay (`C-008`), audit (`C-009`), and private-note lifecycle (`C-010`). Gateway isolation (`C-001`) is logically approved, but no code, configuration, execution-capacity, credential, or retry-state evidence demonstrates it.

### 6.4 Evidence Coverage Analysis

The matrix records `Assessed` when the coverage record names the method for that area and `Not assessed` otherwise. It describes analysis coverage, not control effectiveness.

| Area | M-00 | M-01 | M-02 | M-03 | M-04 | M-05 | M-06 | M-07 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Source specifications | Assessed | Assessed | Assessed | Assessed | Assessed | Assessed | Not assessed | Assessed |
| Identity, authorization, and sessions | Assessed | Assessed | Not assessed | Assessed | Assessed | Not assessed | Not assessed | Assessed |
| Privacy and personal-data flows | Assessed | Assessed | Assessed | Assessed | Assessed | Not assessed | Not assessed | Assessed |
| Booking, payment, refund, and payout integrity | Assessed | Assessed | Not assessed | Assessed | Assessed | Not assessed | Not assessed | Assessed |
| Availability, staff updates, durable work | Assessed | Assessed | Not assessed | Not assessed | Assessed | Not assessed | Not assessed | Assessed |
| Rendering and accessibility | Not assessed | Assessed | Not assessed | Not assessed | Assessed | Not assessed | Not assessed | Assessed |
| Implementation and runtime | Not assessed | Not assessed | Not assessed | Not assessed | Not assessed | Not assessed | Assessed | Not assessed |
| AI/ML lifecycle | Not assessed | Not assessed | Not assessed | Not assessed | Not assessed | Assessed | Assessed | Not assessed |
| Attack-path coverage | Not assessed | Assessed | Not assessed | Assessed | Not assessed | Not assessed | Not assessed | Not assessed |
| Risk prioritization | Assessed | Assessed | Assessed | Assessed | Assessed | Not assessed | Not assessed | Assessed |

The strongest independent evidence is stage 06's repository inventory (`E-REPO`): it directly establishes that no implementation artifacts were present. It does not validate or invalidate any planned control. All threat records derive principally from the same specifications. Cross-method recurrence increases perspective coverage but does not provide independent runtime confirmation.

Single-source conclusions are preserved in `CV-011`: repository absence (`M-06`), AI taxonomy releases (`M-05`), LINDDUN privacy framing and the pre-confirmation cook-field ambiguity (`M-02`), and document provenance/visualization inventory (`M-07`). Unassessed areas are listed in `CV-012`.

Unresolved conflicts:

| Conflict | Topic | Status | Evidence |
| --- | --- | --- | --- |
| `CF-001` | Node.js and Fastify technical roles | unresolved | `E-ARCH`, `E-SEC` |
| `CF-002` | Candidate Node.js baselines | unresolved; candidate packs inactive | `E-SEC`, `E-REPO` |
| `CF-003` | Control status terminology | reconciled as status layers, not contradictory claims | `E-REQ`, `E-ARCH`, `E-SEC`, `E-REPO` |
| `CF-004` | Cook and shopper identity | resolved within behavioral scope | `E-REQ`, `E-ARCH` |

## 7. Action Register

| Threat | Mitigation | Priority | Owner | Effort | Target date | Evidence/status |
| --- | --- | --- | --- | --- | --- | --- |

No rows are populated because the downstream model attaches controls but no threat-specific mitigation record with action metadata. Priority, owner, effort, and target date are **Not supplied**. The specification-hardening changes in §8.2 are documented outcomes, not evidence of implementation or a substitute for an owned action register.

## 8. Requirement Traceability

### 8.1 Pipeline Requirement Groups

This section traces exact model records. `Not assessed` is used because the model contains no implementation evidence and this report makes no compliance determination.

| Requirement | Exact source IDs | Related threats | Controls | Supporting evidence | Conflicts/open gaps | Assessment |
| --- | --- | --- | --- | --- | --- | --- |
| `RQ-001` Authorization and audience restrictions | FR-2.12, FR-6.6 through FR-6.16, FR-11.1, FR-11.2 | `T-008`, `T-010`, `T-014`, `T-015`, `T-031`, `T-035`, `T-042` | `C-002`, `C-003` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-002` Event lifecycle and snapshots | FR-1, FR-2, FR-5, FR-7.8, FR-7.9 | `T-003`, `T-036`, `T-045` | `C-005`, `C-012` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-003` Consent, food review, acceptance, and changes | FR-3, FR-11.7 | `T-003`, `T-025`, `T-028`, `T-037` | `C-004`, `C-005`, `C-010` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-004` Capacity and payment confirmation | FR-8, NFR-2.2 | `T-002`, `T-004`, `T-005`, `T-016`, `T-017`, `T-032`, `T-038`, `T-039` | `C-006` | `E-REQ`, `E-ARCH` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-005` Refund and payout integrity/timing | FR-9, NFR-1.5 | `T-004`, `T-006`, `T-013`, `T-018`, `T-020`, `T-033`, `T-040` | `C-001`, `C-007`, `C-008` | `E-REQ`, `E-ARCH` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-006` Preparation and deterministic shopping | FR-4.5 through FR-4.8, FR-10, NFR-2.3 | `T-009`, `T-025`, `T-028`, `T-041` | `C-003`, `C-014` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-007` Durable staff updates and reconnect | FR-4.1 through FR-4.11, NFR-1.1 through NFR-1.3, NFR-3.6 | `T-010`, `T-012`, `T-021`, `T-042`, `T-045` | `C-002`, `C-008`, `C-012` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-008` Email access/notices and fallback | FR-4.12 through FR-4.14, FR-6.2 through FR-6.4 | `T-001`, `T-009`, `T-013`, `T-020`, `T-022`, `T-044` | `C-001`, `C-011`, `C-013` | `E-REQ`, `E-ARCH`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-009` Audit, deletion, and retention | FR-11.3 through FR-11.7, NFR-2.1 | `T-007`, `T-011`, `T-019`, `T-029`, `T-030`, `T-034`, `T-043` | `C-009`, `C-010` | `E-REQ`, `E-ARCH`, `E-SEC` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-010` Payment/email integration isolation | ARCHITECTURE §2, ARCHITECTURE §8, DR-9 | `T-013`, `T-020`, `T-040`, `T-044` | `C-001` | `E-ARCH`, `E-SEC` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |
| `RQ-011` Security-relevant rendering/accessibility | NFR-3, DESIGN Components, DESIGN Do's and Don'ts | `T-021`, `T-042`, `T-045` | `C-012` | `E-REQ`, `E-DES` | No direct RQ→gap link supplied; `G-001` and `G-014` establish absent implementation validation; `CF-003` preserves status layers. | Not assessed |

### 8.2 Post-analysis Specification Hardening

The current specifications contain the following changes applied after the Appendix A model was produced. They are evidence that the written specifications were hardened; they are not implementation evidence, risk re-ratings, assigned ownership, or deadlines. Appendix A remains the unedited stage-10 model.

| Owning file | Applied change | Driving threat IDs | Remaining status/decision |
| --- | --- | --- | --- |
| `REQUIREMENTS.md` | `FR-1.15` makes public fields, Organizer name, permanent URL, and persistent cancellation notice explicit at launch preview. | `T-023`, `T-024`, `T-026` | Required behavior; implementation absent. |
| `REQUIREMENTS.md` | `FR-3.25`–`FR-3.26` define pre-consent information/recipient/purpose disclosure and consent outcome/time evidence. | `T-025`, `T-028`, `T-037` | Required behavior; exact pre-confirmation staff fields and some withdrawal behavior remain in `OD-013`. |
| `REQUIREMENTS.md` | `FR-4.15` requires current-assignment checks for every current-state read, poll, and replay; cursors/cached responses confer no access. | `T-010`, `T-021`, `T-042` | Required behavior; transport/cursor/paging/revision implementation remains unresolved. |
| `REQUIREMENTS.md` | `FR-6.18` requires current session, role, ownership, suspension, and assignment evaluation for each protected operation. | `T-003`, `T-008`, `T-014`, `T-015`, `T-035` | Required behavior; identity/session/Admin bootstrap decisions unresolved. |
| `REQUIREMENTS.md` | Hardened `FR-8.12` rejects browser returns as payment evidence and requires authenticated provider evidence for amount/currency/hold/event; `FR-8.25` applies each authorized transition and external financial side effect at most once while allowing later authorized lifecycle progress. | `T-002`, `T-004`, `T-006`, `T-016`, `T-018`, `T-032`, `T-033`, `T-039`, `T-040` | Provider and persistence contracts unresolved. |
| `REQUIREMENTS.md` | `FR-11.8` expands audit linkage; `FR-11.9` keeps private-note content only in owning order records and permits opaque references; `NFR-2.5` defines replay/idempotency outcomes. | `T-004`, `T-006`, `T-007`, `T-011`, `T-018`, `T-019`, `T-029`, `T-030`, `T-033`, `T-034`, `T-040`, `T-043` | Audit readers, nonfinancial retention, derived/cache/export/backup lifecycle unresolved. |
| `ARCHITECTURE.md` | Places authorized audience projections, current-operation authorization, non-authoritative browser returns, authenticated/deduplicated provider evidence, consistent replay revisions, operation-linked audit, and opaque private-note references in the logical design and diagrams. | `T-001`–`T-026`, `T-028`–`T-037`, `T-039`–`T-044` | Most mechanisms remain proposed; only payment/email logical isolation is confirmed. |
| `DESIGN.md` | Adds public-disclosure preview, authorized field rendering, informed food-note consent, the latest authoritative payment state after browser return, an access-ended live state, and rules against presenting cached/cursor/client-return state as authority. | `T-002`, `T-004`, `T-008`, `T-010`, `T-016`, `T-021`, `T-023`–`T-028`, `T-031`, `T-037`, `T-039`, `T-042`, `T-045` | Rendering remains unimplemented and untested. |
| `SECURITY.md` | Adds threat-driven required outcomes to `SC-001`, `SC-003`, `SC-005`, `SC-006`, `SC-007`, and `SC-009`; all affected `SC` rules remain `BLOCKED`. | `T-001`–`T-022`, `T-025`, `T-027`–`T-030`, `T-032`–`T-035`, `T-038`–`T-040`, `T-042`–`T-045` as linked in each rule. | Dependencies remain unresolved; no ACTIVE secure-coding rule. |
| `SECURITY.md` | Refines `OD-003`, `OD-005`, `OD-006`, `OD-009`, `OD-010`, `OD-011`, and adds `OD-013` for consent, withdrawal, and pre-confirmation staff disclosure. | `T-001`–`T-006`, `T-007`, `T-010`–`T-013`, `T-016`–`T-022`, `T-025`, `T-027`–`T-030`, `T-032`–`T-035`, `T-037`–`T-045` as linked in each decision. | Owners remain UNKNOWN; no deadlines supplied. |

`G-008` remains a material historical pipeline gap: `FR-4.1` requires a cook update when an order is placed while `FR-4.5` enumerates named food-needs content only for confirmed orders. The hardening pass records the unresolved choice in `OD-013` rather than inventing a pre-confirmation field set. Private-note content and retained recipe/handling information also remain distinct classifications; `OD-010` retains the unresolved copy/readers/retention/restoration decisions.

## 9. Appendices

### Appendix A — Full Downstream Threat-Model JSON

The following JSON is reproduced unedited from `.threat-model-work/10-visuals.md`.

```json
{
  "scope": [
    {
      "id": "SCP-001",
      "system": "Picky Party first-release cooking-event website specification",
      "analysis_date": "2026-10-19",
      "implementation_status": "No application implementation exists",
      "included_fragments": [
        "EV-00",
        "EV-01",
        "EV-02",
        "EV-03",
        "EV-04",
        "EV-05",
        "EV-06",
        "EV-07"
      ],
      "in_scope": [
        "Specified web workflows",
        "Logical client/application/persistence/payment/email boundaries",
        "Identity, event, food-request, booking, finance, staff-update, planning, audit, deletion, retention, and rendering behavior"
      ],
      "exclusions": [
        "Group bookings",
        "Extra portions",
        "Offline payments",
        "Waitlists",
        "Discounts",
        "Automatic dietary certification",
        "Unresolved native workflows",
        "Unspecified deployment topology"
      ],
      "merge_order": [
        "00 STRIDE",
        "01 PASTA",
        "02 LINDDUN",
        "03 Attack trees",
        "04 FMEA",
        "05 AI/ML",
        "06 Repository reconnaissance",
        "07 Document absorption"
      ],
      "identity_decisions": [
        "Organizer and Attendee are account roles; cook and shopper remain distinct event assignments because their authorized fields differ.",
        "The attack-tree unauthorized requester and PASTA untrusted client are represented by one generic threat-agent identity without asserting a motive or capability beyond sending requests.",
        "Document-absorption system records are the normalized identity base; analyzer-local IDs remain in source_refs.",
        "Threats are never deduplicated across methods; related records are cross-linked."
      ],
      "risk_disposition": "No approved common method or mapping exists; no unified rating is computed.",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES",
        "E-REPO"
      ]
    }
  ],
  "evidence": [
    {
      "id": "E-REQ",
      "artifact": "REQUIREMENTS.md",
      "kind": "behavioral authority",
      "revision": "not supplied",
      "date": "unknown",
      "status": "adopted intended behavior, including labeled assumptions; not implementation evidence",
      "source_refs": [
        "00:S00-E-001",
        "01:E-01",
        "02:L2-E-001",
        "03:AT3-E-001",
        "05:S05-E-001",
        "06:S06-E-004",
        "07:DA7-E-001"
      ]
    },
    {
      "id": "E-ARCH",
      "artifact": "ARCHITECTURE.md",
      "kind": "logical architecture",
      "revision": "not supplied",
      "date": "unknown",
      "status": "one confirmed gateway-isolation constraint; other mechanisms proposed, unknown, or to be decided",
      "source_refs": [
        "00:S00-E-002",
        "01:E-02",
        "02:L2-E-002",
        "03:AT3-E-002",
        "05:S05-E-002",
        "06:S06-E-005",
        "07:DA7-E-002"
      ]
    },
    {
      "id": "E-SEC",
      "artifact": "SECURITY.md",
      "kind": "security decision/status document",
      "revision": "not supplied",
      "date": "unknown",
      "status": "SC-001 through SC-009 BLOCKED; no active secure-coding composition or implemented control",
      "source_refs": [
        "00:S00-E-003",
        "01:E-03",
        "02:L2-E-003",
        "03:AT3-E-003",
        "05:S05-E-003",
        "06:S06-E-006",
        "07:DA7-E-003"
      ]
    },
    {
      "id": "E-DES",
      "artifact": "DESIGN.md",
      "kind": "interaction/rendering specification",
      "revision": "alpha",
      "date": "unknown",
      "status": "assumption-based design intent; no rendered implementation",
      "source_refs": [
        "00:S00-E-004",
        "01:E-04",
        "02:L2-E-004",
        "03:AT3-E-004",
        "05:S05-E-004",
        "06:S06-E-007",
        "07:DA7-E-004"
      ]
    },
    {
      "id": "E-REPO",
      "artifact": "Repository inventory",
      "kind": "repository reconnaissance",
      "date": "2026-10-19",
      "status": "Eight root files: seven Markdown documents and one SVG; no source, dependency manifest, lockfile, schema, test, runtime config, CI, container, IaC, or deployment artifact",
      "source_refs": [
        "06:S06-E-001",
        "06:S06-E-002",
        "06:S06-E-005",
        "06:S06-E-006",
        "06:S06-E-007",
        "06:S06-E-009",
        "06:S06-E-010"
      ]
    },
    {
      "id": "E-AI",
      "artifact": "AI/ML taxonomy verification",
      "kind": "external method provenance",
      "date": "2026-10-19",
      "status": "MITRE ATLAS v2026.09, OWASP ML Security Top 10 2023 draft v0.2, and OWASP GenAI LLM Top 10 2026 checked; all not applicable to documented scope",
      "source_refs": [
        "05:S05-M-001",
        "05:S05-M-002",
        "05:S05-M-003"
      ]
    },
    {
      "id": "EV-00",
      "artifact": ".threat-model-work/00-stride.md",
      "producer": "STRIDE analyzer",
      "records": "14 threats",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    },
    {
      "id": "EV-01",
      "artifact": ".threat-model-work/01-pasta.md",
      "producer": "PASTA analyzer",
      "records": "8 threats, 8 paths, 8 unresolved risks",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    },
    {
      "id": "EV-02",
      "artifact": ".threat-model-work/02-linddun.md",
      "producer": "LINDDUN analyzer",
      "records": "8 privacy threats and risks",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    },
    {
      "id": "EV-03",
      "artifact": ".threat-model-work/03-attack-tree.md",
      "producer": "Attack-tree analyzer",
      "records": "4 root threats, 4 trees, 10 conditional paths",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    },
    {
      "id": "EV-04",
      "artifact": ".threat-model-work/04-fmea.md",
      "producer": "FMEA analyzer",
      "records": "11 unranked failure modes",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    },
    {
      "id": "EV-05",
      "artifact": ".threat-model-work/05-ai-ml.md",
      "producer": "AI/ML analyzer",
      "records": "no threats; lifecycle and three taxonomies not applicable",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES",
        "E-AI"
      ]
    },
    {
      "id": "EV-06",
      "artifact": ".threat-model-work/06-repository.md",
      "producer": "Repository reconnaissance",
      "records": "no implementation findings; five evidence gaps",
      "underlying_evidence_ids": [
        "E-REPO"
      ]
    },
    {
      "id": "EV-07",
      "artifact": ".threat-model-work/07-documents.md",
      "producer": "Document absorption",
      "records": "normalized documents, system, controls, requirements, risks, and gaps",
      "underlying_evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ]
    }
  ],
  "system": {
    "assets": [
      {
        "id": "A-001",
        "name": "Account identity and access records",
        "owner": "Identity and access",
        "status": "behavior required; storage/implementation unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ],
        "source_refs": [
          "07:DA7-AS-001",
          "00:S00-AST-001",
          "01:A-04",
          "04:FN-03"
        ]
      },
      {
        "id": "A-002",
        "name": "Events, addresses, assignments, URLs, dishes, recipes, and ingredients",
        "owner": "Events and recipes",
        "status": "behavior required; module proposed",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ],
        "source_refs": [
          "07:DA7-AS-002",
          "01:A-01",
          "01:A-05",
          "04:FN-04"
        ]
      },
      {
        "id": "A-003",
        "name": "Orders, food needs, consent, proposals, accepted recipes, holds, and bookings",
        "owner": "Orders and bookings",
        "status": "behavior required; module proposed",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ],
        "source_refs": [
          "07:DA7-AS-003",
          "01:A-01",
          "01:A-02",
          "04:FN-05"
        ]
      },
      {
        "id": "A-004",
        "name": "Connected-account, payment, refund, payout, fee, and reconciliation records",
        "owner": "Financial workflows",
        "status": "behavior required; provider/persistence unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ],
        "source_refs": [
          "07:DA7-AS-004",
          "01:A-03",
          "04:FN-06"
        ]
      },
      {
        "id": "A-005",
        "name": "Staff updates, notices, delivery state, audit records, and pending work",
        "owner": "Updates/notices and durable work",
        "status": "behavior required; implementation/retention unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ],
        "source_refs": [
          "07:DA7-AS-005",
          "01:A-06",
          "01:A-07",
          "04:FN-10",
          "04:FN-11"
        ]
      },
      {
        "id": "A-006",
        "name": "Presentation and transient client state",
        "owner": "Web presentation; mobile ownership unresolved",
        "status": "ReactJS named; native scope unresolved",
        "evidence_ids": [
          "E-ARCH",
          "E-DES"
        ],
        "source_refs": [
          "07:DA7-AS-006",
          "04:FN-01",
          "04:FN-02"
        ]
      },
      {
        "id": "A-007",
        "name": "Payment integration credentials and client configuration",
        "owner": "Payment outbound gateway",
        "status": "logical isolation confirmed; implementation unresolved",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ],
        "source_refs": [
          "07:DA7-AS-007",
          "01:A-08",
          "04:FN-07"
        ]
      },
      {
        "id": "A-008",
        "name": "Email integration credentials and client configuration",
        "owner": "Email outbound gateway",
        "status": "logical isolation confirmed; implementation unresolved",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ],
        "source_refs": [
          "07:DA7-AS-008",
          "01:A-08",
          "04:FN-08"
        ]
      }
    ],
    "actors": [
      {
        "id": "ACT-001",
        "name": "Visitor",
        "kind": "legitimate external actor",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-002",
        "name": "Organizer",
        "kind": "account role",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-003",
        "name": "Attendee",
        "kind": "account role",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-004",
        "name": "Cook",
        "kind": "event assignment",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-005",
        "name": "Shopper",
        "kind": "event assignment",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-006",
        "name": "Admin",
        "kind": "privileged role; first provisioning unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "ACT-007",
        "name": "Payment service",
        "kind": "external provider; selection unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-008",
        "name": "Email service",
        "kind": "external provider; selection unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "ACT-009",
        "name": "Untrusted or unauthorized requester",
        "kind": "generic threat agent",
        "capability": "Can send requests; access, motive, and resources unknown",
        "evidence_ids": [
          "E-ARCH",
          "EV-01",
          "EV-03"
        ],
        "source_refs": [
          "01:ACT-09",
          "03:AT3-ACT-007"
        ]
      },
      {
        "id": "ACT-010",
        "name": "Durable work dispatcher",
        "kind": "proposed internal actor",
        "evidence_ids": [
          "E-ARCH",
          "EV-01",
          "EV-04"
        ]
      }
    ],
    "data": [
      {
        "id": "D-001",
        "name": "Identity, verification, session, role, suspension, and assignment data",
        "classification": "personal/access data; detailed classification unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "D-002",
        "name": "Public event metadata and permanent URL/QR",
        "classification": "required public data for launched events",
        "evidence_ids": [
          "E-REQ",
          "E-DES"
        ]
      },
      {
        "id": "D-003",
        "name": "Exact event address and access instructions",
        "classification": "restricted audience",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-DES"
        ]
      },
      {
        "id": "D-004",
        "name": "Food needs, private notes, recipes, variants, and handling notes",
        "classification": "private/audience-specific; exact boundary unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "D-005",
        "name": "Order, hold, booking, attendance, and ingredient-planning state",
        "classification": "non-public operational/account data",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "D-006",
        "name": "Payment, refund, payout, fee, amount, receipt, provider reference, and operation identity",
        "classification": "non-public financial data; specified subset retained 24 months",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      },
      {
        "id": "D-007",
        "name": "Staff updates, cursors, account notices, audit records, work metadata, and delivery state",
        "classification": "audience-filtered; nonfinancial retention unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-SEC"
        ]
      }
    ],
    "zones": [
      {
        "id": "Z-001",
        "name": "Untrusted web client",
        "status": "proposed logical zone",
        "evidence_ids": [
          "E-ARCH"
        ]
      },
      {
        "id": "Z-002",
        "name": "Native client",
        "status": "framework named; platforms/workflows unresolved",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "Z-003",
        "name": "Trusted application",
        "status": "proposed logical zone",
        "evidence_ids": [
          "E-ARCH"
        ]
      },
      {
        "id": "Z-004",
        "name": "Persistence",
        "status": "logical boundary; PostgreSQL proposed",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "Z-005",
        "name": "Isolated payment integration",
        "status": "logical isolation confirmed",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "Z-006",
        "name": "Separate email integration",
        "status": "logical isolation confirmed",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "Z-007",
        "name": "External providers",
        "status": "required boundary; providers unresolved",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH"
        ]
      }
    ],
    "boundaries": [
      {
        "id": "B-001",
        "name": "Client to application",
        "status": "HTTP JSON proposed; native unresolved",
        "from_ids": [
          "Z-001",
          "Z-002"
        ],
        "to_ids": [
          "Z-003"
        ],
        "control_status": "document claims only",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "B-002",
        "name": "Application to persistence",
        "status": "proposed; interfaces/technology unresolved",
        "from_ids": [
          "Z-003"
        ],
        "to_ids": [
          "Z-004"
        ],
        "control_status": "evidence gap",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "B-003",
        "name": "Financial workflows to payment gateway/provider",
        "status": "gateway separation confirmed; contract unresolved",
        "from_ids": [
          "Z-003",
          "Z-005"
        ],
        "to_ids": [
          "Z-007"
        ],
        "control_status": "claimed logical boundary; implementation absent",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "B-004",
        "name": "Payment callback inbound",
        "status": "logical adapter specified; protocol/authenticity unresolved",
        "from_ids": [
          "Z-007"
        ],
        "to_ids": [
          "Z-005",
          "Z-003"
        ],
        "control_status": "evidence gap",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "B-005",
        "name": "Identity/notices to email gateway/provider",
        "status": "gateway separation confirmed; contract unresolved",
        "from_ids": [
          "Z-003",
          "Z-006"
        ],
        "to_ids": [
          "Z-007"
        ],
        "control_status": "claimed logical boundary; implementation absent",
        "evidence_ids": [
          "E-ARCH",
          "E-SEC"
        ]
      },
      {
        "id": "B-006",
        "name": "Audience-specific response projections",
        "status": "restrictions required; server enforcement proposed",
        "from_ids": [
          "Z-003"
        ],
        "to_ids": [
          "Z-001",
          "Z-002"
        ],
        "control_status": "document claim only",
        "evidence_ids": [
          "E-REQ",
          "E-ARCH",
          "E-DES"
        ]
      }
    ],
    "flows": [
      {
        "id": "F-001",
        "name": "Publish and discover",
        "data_ids": [
          "D-002"
        ],
        "boundary_ids": [
          "B-001",
          "B-006"
        ],
        "status": "required; implementation absent",
        "source_refs": [
          "07:DA7-F-001",
          "00:S00-FLW-001",
          "02:L2-F-001"
        ]
      },
      {
        "id": "F-002",
        "name": "Verify and sign in through email link",
        "data_ids": [
          "D-001"
        ],
        "boundary_ids": [
          "B-001",
          "B-005"
        ],
        "status": "required; provider/lifecycle unresolved",
        "source_refs": [
          "07:DA7-F-002",
          "00:S00-FLW-002",
          "02:L2-F-002"
        ]
      },
      {
        "id": "F-003",
        "name": "Create event and expose exact location to authorized audiences",
        "data_ids": [
          "D-003"
        ],
        "boundary_ids": [
          "B-001",
          "B-006"
        ],
        "status": "required; implementation absent",
        "source_refs": [
          "07:DA7-F-003",
          "02:L2-F-003"
        ]
      },
      {
        "id": "F-004",
        "name": "Submit, review, accept, and prepare food requests",
        "data_ids": [
          "D-004",
          "D-005"
        ],
        "boundary_ids": [
          "B-001",
          "B-002",
          "B-006"
        ],
        "status": "required; private-note lifecycle unresolved",
        "source_refs": [
          "07:DA7-F-004",
          "02:L2-F-004",
          "02:L2-F-005"
        ]
      },
      {
        "id": "F-005",
        "name": "Checkout, callback, validation, and booking confirmation",
        "data_ids": [
          "D-005",
          "D-006"
        ],
        "boundary_ids": [
          "B-001",
          "B-002",
          "B-003",
          "B-004"
        ],
        "status": "required; provider/implementation unresolved",
        "source_refs": [
          "07:DA7-F-005",
          "00:S00-FLW-004",
          "00:S00-FLW-005",
          "02:L2-F-006",
          "03:AT3-F-004"
        ]
      },
      {
        "id": "F-006",
        "name": "Cancel, refund, reconcile, and pay out",
        "data_ids": [
          "D-005",
          "D-006",
          "D-007"
        ],
        "boundary_ids": [
          "B-001",
          "B-002",
          "B-003",
          "B-004",
          "B-006"
        ],
        "status": "required; durable execution/provider/persistence unresolved",
        "source_refs": [
          "07:DA7-F-006",
          "02:L2-F-007",
          "03:AT3-F-005"
        ]
      },
      {
        "id": "F-007",
        "name": "Staff update, polling, and reconnect replay",
        "data_ids": [
          "D-004",
          "D-005",
          "D-007"
        ],
        "boundary_ids": [
          "B-001",
          "B-002",
          "B-006"
        ],
        "status": "required; polling proposed/to be decided",
        "source_refs": [
          "07:DA7-F-007",
          "00:S00-FLW-006",
          "03:AT3-F-003"
        ]
      },
      {
        "id": "F-008",
        "name": "Persist account notice and send filtered email",
        "data_ids": [
          "D-001",
          "D-007"
        ],
        "boundary_ids": [
          "B-002",
          "B-005",
          "B-006"
        ],
        "status": "required; provider unresolved",
        "source_refs": [
          "07:DA7-F-008",
          "00:S00-FLW-007",
          "02:L2-F-008"
        ]
      },
      {
        "id": "F-009",
        "name": "Audit, delete private notes, and retain financial records",
        "data_ids": [
          "D-004",
          "D-006",
          "D-007"
        ],
        "boundary_ids": [
          "B-002",
          "B-006"
        ],
        "status": "required; classification/copies/backups/readers unresolved",
        "source_refs": [
          "07:DA7-F-009",
          "00:S00-FLW-008",
          "02:L2-F-009",
          "03:AT3-F-006"
        ]
      }
    ],
    "entry_points": [
      {
        "id": "EP-001",
        "name": "Public calendar, event page, and QR URL",
        "flow_ids": [
          "F-001"
        ],
        "status": "required"
      },
      {
        "id": "EP-002",
        "name": "Email verification/sign-in link",
        "flow_ids": [
          "F-002"
        ],
        "status": "required; lifecycle unresolved"
      },
      {
        "id": "EP-003",
        "name": "Authenticated views/actions",
        "flow_ids": [
          "F-003",
          "F-004",
          "F-006",
          "F-007",
          "F-009"
        ],
        "status": "required; endpoint specification absent"
      },
      {
        "id": "EP-004",
        "name": "Checkout browser flow",
        "flow_ids": [
          "F-005"
        ],
        "status": "required; protocol unresolved"
      },
      {
        "id": "EP-005",
        "name": "Payment callbacks/reconciliation",
        "flow_ids": [
          "F-005",
          "F-006"
        ],
        "status": "logical entry; protocol unresolved"
      },
      {
        "id": "EP-006",
        "name": "Email delivery gateway",
        "flow_ids": [
          "F-002",
          "F-008"
        ],
        "status": "logical entry; provider unresolved"
      },
      {
        "id": "EP-007",
        "name": "Scheduled/retry work",
        "flow_ids": [
          "F-006",
          "F-008",
          "F-009"
        ],
        "status": "proposed durable-work mechanism"
      }
    ]
  },
  "methods": [
    {
      "id": "M-00",
      "name": "STRIDE",
      "source": "EV-00",
      "status": "complete across six categories",
      "rating_method": "none; all 14 threats unrated"
    },
    {
      "id": "M-01",
      "name": "PASTA",
      "source": "EV-01",
      "status": "seven stages completed with evidence gaps",
      "rating_method": "none; eight qualitative impacts and unresolved ratings"
    },
    {
      "id": "M-02",
      "name": "LINDDUN",
      "source": "EV-02",
      "status": "seven privacy types dispositioned across nine flows",
      "rating_method": "no scores; required disclosures distinguished from misuse/control failure"
    },
    {
      "id": "M-03",
      "name": "Attack-tree decomposition",
      "source": "EV-03",
      "status": "four trees, 42 source nodes, ten conditional paths",
      "rating_method": "no path-comparison method; likelihood/impact unknown"
    },
    {
      "id": "M-04",
      "name": "FMEA",
      "source": "EV-04",
      "status": "eight passes; 11 functions assessed and mobile not assessed",
      "rating_method": "none; all failure modes unranked"
    },
    {
      "id": "M-05",
      "name": "AI/ML lifecycle and taxonomy review",
      "source": "EV-05",
      "status": "not applicable to documented first-release system",
      "coverage": "MITRE ATLAS v2026.09; OWASP ML Security Top 10 2023 draft v0.2; OWASP GenAI LLM Top 10 2026"
    },
    {
      "id": "M-06",
      "name": "Repository reconnaissance",
      "source": "EV-06",
      "status": "complete inventory; no implementation to assess",
      "rating_method": "not applicable"
    },
    {
      "id": "M-07",
      "name": "Document absorption",
      "source": "EV-07",
      "status": "four documents normalized",
      "rating_method": "four unranked architecture risks preserved"
    }
  ],
  "threats": [
    {
      "id": "T-001",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-001",
      "category": "Spoofing",
      "title": "Email-link or session impersonation",
      "scenario": "Another person's verification/sign-in link or session identifier is treated as that account; lifecycle is unresolved.",
      "affected_ids": [
        "A-001",
        "D-001",
        "F-002",
        "EP-002"
      ],
      "control_ids": [
        "C-011",
        "C-002"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-022",
        "T-035"
      ]
    },
    {
      "id": "T-002",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-002",
      "category": "Spoofing",
      "title": "Unauthenticated payment result accepted as provider evidence",
      "scenario": "A payment callback message causes financial/booking state without authentic-origin validation.",
      "affected_ids": [
        "A-003",
        "A-004",
        "B-004",
        "F-005",
        "EP-005"
      ],
      "control_ids": [
        "C-001",
        "C-006"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-004",
        "T-016",
        "T-032",
        "T-039"
      ]
    },
    {
      "id": "T-003",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-003",
      "category": "Tampering",
      "title": "Client-controlled business transition",
      "scenario": "Untrusted ownership, assignment, price, capacity, recipe, order, acceptance, cancellation, or transition values alter commitments or eligibility.",
      "affected_ids": [
        "A-002",
        "A-003",
        "A-004",
        "F-003",
        "F-004",
        "F-006",
        "EP-003"
      ],
      "control_ids": [
        "C-002",
        "C-005"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-015",
        "T-036",
        "T-037"
      ]
    },
    {
      "id": "T-004",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-004",
      "category": "Tampering",
      "title": "Altered, late, duplicate, or replayed financial evidence",
      "scenario": "Invalid evidence creates a booking, exceeds a refund cap, or duplicates a payout unless validated/deduplicated.",
      "affected_ids": [
        "A-003",
        "A-004",
        "D-005",
        "D-006",
        "F-005",
        "F-006",
        "EP-005"
      ],
      "control_ids": [
        "C-006",
        "C-007"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-002",
        "T-016",
        "T-018",
        "T-032",
        "T-033",
        "T-039",
        "T-040"
      ]
    },
    {
      "id": "T-005",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-005",
      "category": "Tampering",
      "title": "Concurrent capacity corruption",
      "scenario": "Overlapping checkout, confirmation, cancellation, or capacity changes exceed capacity or fail atomic hold replacement.",
      "affected_ids": [
        "A-003",
        "D-005",
        "B-002",
        "F-005"
      ],
      "control_ids": [
        "C-006"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-017",
        "T-032",
        "T-038"
      ]
    },
    {
      "id": "T-006",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-006",
      "category": "Tampering",
      "title": "Duplicate or out-of-order work applies stale effects",
      "scenario": "Scheduled tasks, callbacks, retries, or reconciliation repeat expiry/refund/payout/notification effects or apply stale state.",
      "affected_ids": [
        "A-003",
        "A-004",
        "A-005",
        "F-005",
        "F-006",
        "F-009",
        "EP-007"
      ],
      "control_ids": [
        "C-006",
        "C-007",
        "C-008"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-018",
        "T-033",
        "T-040",
        "T-043"
      ]
    },
    {
      "id": "T-007",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-007",
      "category": "Repudiation",
      "title": "State change lacks attributable evidence",
      "scenario": "An actor disputes a change when actor/time/outcome is absent, incomplete, or disconnected from records/provider references.",
      "affected_ids": [
        "A-004",
        "A-005",
        "D-006",
        "D-007",
        "F-006",
        "F-009"
      ],
      "control_ids": [
        "C-009"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-029",
        "T-043"
      ]
    },
    {
      "id": "T-008",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-008",
      "category": "Information Disclosure",
      "title": "Public or wrong-account projection exposes restricted data",
      "scenario": "A response exposes exact addresses, orders, dietary requests, payments, or updates beyond public/owned records.",
      "affected_ids": [
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "D-003",
        "D-004",
        "D-005",
        "D-006",
        "D-007",
        "B-006"
      ],
      "control_ids": [
        "C-002",
        "C-003"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-015",
        "T-019",
        "T-031",
        "T-035"
      ]
    },
    {
      "id": "T-009",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-009",
      "category": "Information Disclosure",
      "title": "Shopper or email projection leaks restricted fields",
      "scenario": "Shopper views or email notices disclose Attendee names, private food notes, or exact addresses.",
      "affected_ids": [
        "A-003",
        "A-005",
        "D-003",
        "D-004",
        "F-007",
        "F-008",
        "B-005",
        "B-006"
      ],
      "control_ids": [
        "C-003",
        "C-013"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-019",
        "T-041",
        "T-044"
      ]
    },
    {
      "id": "T-010",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-010",
      "category": "Information Disclosure",
      "title": "Removed staff retain current/replayed access",
      "scenario": "A removed cook/shopper continues to receive state or replay because assignment is not checked per read.",
      "affected_ids": [
        "A-001",
        "A-003",
        "A-005",
        "D-001",
        "D-004",
        "D-007",
        "F-007",
        "EP-003"
      ],
      "control_ids": [
        "C-002",
        "C-008"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-015",
        "T-021",
        "T-031",
        "T-042"
      ]
    },
    {
      "id": "T-011",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-011",
      "category": "Information Disclosure",
      "title": "Private food notes survive deletion/withdrawal",
      "scenario": "Private notes remain in updates, jobs, audit, derived records, or backups after withdrawal or the 90-day point.",
      "affected_ids": [
        "A-003",
        "A-005",
        "D-004",
        "D-007",
        "F-009"
      ],
      "control_ids": [
        "C-010"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-019",
        "T-030",
        "T-034",
        "T-043"
      ]
    },
    {
      "id": "T-012",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-012",
      "category": "Denial of Service",
      "interpretation": "Availability/failure risk; no attacker or deliberate action is assumed.",
      "title": "Polling or durable work misses service targets",
      "scenario": "Staff replay or work dispatch falls behind and misses update, reconnect, refund, or availability targets.",
      "affected_ids": [
        "A-005",
        "F-001",
        "F-006",
        "F-007",
        "F-009",
        "EP-007"
      ],
      "control_ids": [
        "C-008",
        "C-012"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-021",
        "T-042",
        "T-043"
      ]
    },
    {
      "id": "T-013",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-013",
      "category": "Denial of Service",
      "interpretation": "Availability/dependency failure risk; no hostile email provider or attacker is assumed.",
      "title": "Email failure delays access/notices or financial work",
      "scenario": "Email backlog delays access/notices and, if isolation fails, required financial work.",
      "affected_ids": [
        "A-004",
        "A-005",
        "A-008",
        "F-002",
        "F-006",
        "F-008"
      ],
      "control_ids": [
        "C-001",
        "C-008",
        "C-013"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-020",
        "T-040",
        "T-044"
      ]
    },
    {
      "id": "T-014",
      "method_id": "M-00",
      "source_record_id": "00:S00-T-014",
      "category": "Elevation of Privilege",
      "title": "Account exceeds ownership, assignment, role, or suspension scope",
      "scenario": "An account acts on another order/event, an unassigned event, or Admin-only operation.",
      "affected_ids": [
        "A-001",
        "A-002",
        "A-003",
        "A-004",
        "F-003",
        "F-004",
        "F-006",
        "F-007"
      ],
      "control_ids": [
        "C-002"
      ],
      "evidence_ids": [
        "EV-00",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unrated",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-003",
        "T-015",
        "T-031",
        "T-035"
      ]
    },
    {
      "id": "T-015",
      "method_id": "M-01",
      "source_record_id": "01:P-T01",
      "category": "PASTA scenario",
      "title": "Unauthorized actor reads or changes restricted records",
      "scenario": "Client requests cross ownership, role, suspension, assignment, or audience boundaries; success requires failed enforcement.",
      "affected_ids": [
        "A-001",
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "B-001",
        "B-006"
      ],
      "control_ids": [
        "C-002",
        "C-003",
        "C-008"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "assumptions": [
        "Success requires an absent/defective control; no defect evidenced."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-003",
        "T-008",
        "T-010",
        "T-014",
        "T-031",
        "T-035",
        "T-042"
      ]
    },
    {
      "id": "T-016",
      "method_id": "M-01",
      "source_record_id": "01:P-T02",
      "category": "PASTA scenario",
      "title": "Untrusted or repeated payment evidence corrupts state",
      "scenario": "Callback, reconciliation, retry, or browser-return evidence is accepted without required validation/deduplication.",
      "affected_ids": [
        "A-003",
        "A-004",
        "A-007",
        "B-004",
        "F-005"
      ],
      "control_ids": [
        "C-001",
        "C-006"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "assumptions": [
        "Success requires validation/deduplication failure."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-002",
        "T-004",
        "T-032",
        "T-039"
      ]
    },
    {
      "id": "T-017",
      "method_id": "M-01",
      "source_record_id": "01:P-T03",
      "category": "PASTA scenario",
      "title": "Concurrent capacity changes misallocate a seat",
      "scenario": "Checkout, confirmation, cancellation, expiry, or capacity edits observe inconsistent occupancy.",
      "affected_ids": [
        "A-003",
        "D-005",
        "F-005",
        "EP-007"
      ],
      "control_ids": [
        "C-006"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "assumptions": [
        "Operations overlap and consistency enforcement fails."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-005",
        "T-032",
        "T-038"
      ]
    },
    {
      "id": "T-018",
      "method_id": "M-01",
      "source_record_id": "01:P-T04",
      "category": "PASTA scenario",
      "title": "Repeated refund or payout exceeds authorized value",
      "scenario": "Admin/background/callback/reconciliation retries bypass operation identity, caps, obligations, or eligibility.",
      "affected_ids": [
        "A-004",
        "A-005",
        "A-007",
        "F-006",
        "EP-007"
      ],
      "control_ids": [
        "C-001",
        "C-006",
        "C-007"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "assumptions": [
        "Duplicate invocation occurs and enforcement fails."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-004",
        "T-006",
        "T-033",
        "T-040"
      ]
    },
    {
      "id": "T-019",
      "method_id": "M-01",
      "source_record_id": "01:P-T05",
      "category": "PASTA scenario",
      "title": "Private notes or addresses leak through projection/copy",
      "scenario": "Public, shopper, email, replay, job, audit, financial, derived, or backup copies exceed audience/lifecycle.",
      "affected_ids": [
        "A-002",
        "A-003",
        "A-005",
        "D-003",
        "D-004",
        "D-007",
        "F-007",
        "F-008",
        "F-009"
      ],
      "control_ids": [
        "C-002",
        "C-003",
        "C-010"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "assumptions": [
        "A secondary copy contains restricted content and filtering/deletion misses it."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-008",
        "T-009",
        "T-011",
        "T-030",
        "T-034",
        "T-043",
        "T-044"
      ]
    },
    {
      "id": "T-020",
      "method_id": "M-01",
      "source_record_id": "01:P-T06",
      "category": "PASTA scenario",
      "title": "Email integration failure controls financial work",
      "scenario": "Shared state/capacity could let email outage delay finance despite confirmed isolation requirement.",
      "affected_ids": [
        "A-004",
        "A-005",
        "A-007",
        "A-008",
        "F-006",
        "F-008"
      ],
      "control_ids": [
        "C-001"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "assumptions": [
        "Email fails and required separation is not implemented."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-013",
        "T-040",
        "T-044"
      ]
    },
    {
      "id": "T-021",
      "method_id": "M-01",
      "source_record_id": "01:P-T07",
      "category": "PASTA scenario",
      "title": "Lost, delayed, replayed, or stale staff updates",
      "scenario": "Cursor, reconnect, polling, or work failure omits changes, serves obsolete content, or ignores removed assignment.",
      "affected_ids": [
        "A-003",
        "A-005",
        "A-006",
        "F-007"
      ],
      "control_ids": [
        "C-002",
        "C-008",
        "C-012"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "assumptions": [
        "A delivery/cursor/revision/assignment check fails."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-010",
        "T-012",
        "T-042",
        "T-045"
      ]
    },
    {
      "id": "T-022",
      "method_id": "M-01",
      "source_record_id": "01:P-T08",
      "category": "PASTA scenario",
      "title": "Email access artifact permits impersonation",
      "scenario": "An unauthorized party obtains/reuses a valid link or session artifact; lifecycle behavior is unresolved.",
      "affected_ids": [
        "A-001",
        "A-008",
        "D-001",
        "F-002",
        "EP-002"
      ],
      "control_ids": [
        "C-011"
      ],
      "evidence_ids": [
        "EV-01",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "assumptions": [
        "Unauthorized acquisition and lifecycle-permitted reuse."
      ],
      "rating": {
        "likelihood": "unresolved",
        "impact": "unresolved",
        "overall": "unresolved"
      },
      "related_threat_ids": [
        "T-001",
        "T-035"
      ]
    },
    {
      "id": "T-023",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-001",
      "category": "Linking",
      "interpretation": "Intentional product disclosure and privacy tradeoff, not a vulnerability finding.",
      "title": "Permanent URL enables longitudinal event correlation",
      "scenario": "Visitors correlate one event over time with Organizer, city, schedule, menu, price, availability, and cancellation state.",
      "affected_ids": [
        "A-002",
        "D-002",
        "F-001",
        "EP-001"
      ],
      "control_ids": [
        "C-003"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "likelihood": "required public observability; beyond that unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-024",
        "T-026"
      ]
    },
    {
      "id": "T-024",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-002",
      "interpretation": "Intentional public association and privacy tradeoff, not a vulnerability finding.",
      "category": "Identifying",
      "title": "Public event identifies Organizer association",
      "scenario": "Organizer name is published with event details as required behavior.",
      "affected_ids": [
        "A-002",
        "D-002",
        "F-001"
      ],
      "control_ids": [
        "C-003"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ"
      ],
      "rating": {
        "likelihood": "required disclosure; beyond that unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-023",
        "T-026"
      ]
    },
    {
      "id": "T-025",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-003",
      "interpretation": "Required disclosure to current cooks and privacy tradeoff, not a vulnerability finding; misuse remains unknown.",
      "category": "Linking and Identifying",
      "title": "Cook view links Attendee identity with food needs",
      "scenario": "Confirmed cook view combines name, food needs, quantities, recipes, and handling information.",
      "affected_ids": [
        "A-003",
        "D-004",
        "D-005",
        "F-004",
        "ACT-004"
      ],
      "control_ids": [
        "C-004",
        "C-002"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "likelihood": "required for current cooks; misuse unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-028",
        "T-037",
        "T-041"
      ]
    },
    {
      "id": "T-026",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-004",
      "interpretation": "Intentional public disclosure and privacy tradeoff, not a vulnerability finding.",
      "category": "Detecting",
      "title": "Public discovery reveals event existence/state",
      "scenario": "Visitors detect launched-event city, time, price, availability, and cancellation state.",
      "affected_ids": [
        "A-002",
        "D-002",
        "F-001"
      ],
      "control_ids": [
        "C-003"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ"
      ],
      "rating": {
        "likelihood": "required disclosure; beyond that unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-023",
        "T-024"
      ]
    },
    {
      "id": "T-027",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-005",
      "interpretation": "Required audience disclosure and privacy tradeoff, not a vulnerability finding; downstream handling remains unknown.",
      "category": "Data Disclosure",
      "title": "Permitted audiences learn precise event location",
      "scenario": "Confirmed Attendees, current staff, Organizer, and Admin receive exact address; downstream handling is unspecified.",
      "affected_ids": [
        "A-002",
        "D-003",
        "F-003"
      ],
      "control_ids": [
        "C-002",
        "C-003"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "likelihood": "required disclosure to permitted audiences; downstream retention unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-019"
      ]
    },
    {
      "id": "T-028",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-006",
      "interpretation": "Consented workflow disclosure and privacy tradeoff, not a vulnerability finding; misuse remains unknown.",
      "category": "Data Disclosure",
      "title": "Food needs disclose personal circumstances to Organizer/cook",
      "scenario": "Consented food information crosses to Organizer and cook with identity/handling details; shopper/email exclusions differ.",
      "affected_ids": [
        "A-003",
        "D-004",
        "F-004"
      ],
      "control_ids": [
        "C-004",
        "C-002",
        "C-003"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "likelihood": "occurs for consented workflows; misuse unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-025",
        "T-037",
        "T-041"
      ]
    },
    {
      "id": "T-029",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-007",
      "interpretation": "Required attributable-record creation and privacy tradeoff, not a vulnerability finding; record readers and use remain unknown.",
      "category": "Non-repudiation, Linking, and Identifying",
      "title": "Audit/financial history creates attributable long-term linkage",
      "scenario": "Actor/time/outcome and 24-month financial records bind people to event and financial activity.",
      "affected_ids": [
        "A-004",
        "A-005",
        "D-006",
        "D-007",
        "F-009"
      ],
      "control_ids": [
        "C-009",
        "C-010"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "likelihood": "required record creation; access/use unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-007",
        "T-043"
      ]
    },
    {
      "id": "T-030",
      "method_id": "M-02",
      "source_record_id": "02:L2-TH-008",
      "category": "Data Disclosure",
      "title": "Private-note copies outlive deletion lifecycle",
      "scenario": "Snapshots, operations, derived records, or backups retain private content; reference-only design is unconfirmed.",
      "affected_ids": [
        "A-003",
        "A-005",
        "D-004",
        "D-007",
        "F-009"
      ],
      "control_ids": [
        "C-010"
      ],
      "evidence_ids": [
        "EV-02",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "likelihood": "unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-011",
        "T-019",
        "T-034",
        "T-043"
      ]
    },
    {
      "id": "T-031",
      "method_id": "M-03",
      "source_record_id": "03:AT3-TH-001",
      "category": "Attack-tree root",
      "title": "Obtain restricted data without audience entitlement",
      "scenario": "Public projection, cross-Attendee read, or former-staff replay succeeds after a required control fails.",
      "affected_ids": [
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "F-001",
        "F-007"
      ],
      "control_ids": [
        "C-002",
        "C-003",
        "C-008"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "likelihood": "unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-008",
        "T-010",
        "T-014",
        "T-015",
        "T-035",
        "T-042"
      ]
    },
    {
      "id": "T-032",
      "method_id": "M-03",
      "source_record_id": "03:AT3-TH-002",
      "category": "Attack-tree root",
      "title": "Confirm booking without acceptable payment and valid hold",
      "scenario": "Browser return, invalid/replayed provider evidence, or over-capacity hold reaches confirmation after controls fail.",
      "affected_ids": [
        "A-003",
        "A-004",
        "D-005",
        "D-006",
        "F-005"
      ],
      "control_ids": [
        "C-006"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "likelihood": "unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-002",
        "T-004",
        "T-005",
        "T-016",
        "T-017",
        "T-038",
        "T-039"
      ]
    },
    {
      "id": "T-033",
      "method_id": "M-03",
      "source_record_id": "03:AT3-TH-003",
      "category": "Attack-tree root",
      "title": "Excess refund or duplicate payout",
      "scenario": "Repeated financial work plus failed cap/deduplication and provider completion transfers excess value.",
      "affected_ids": [
        "A-004",
        "D-006",
        "F-006"
      ],
      "control_ids": [
        "C-007"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH"
      ],
      "rating": {
        "likelihood": "unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-004",
        "T-006",
        "T-018",
        "T-040"
      ]
    },
    {
      "id": "T-034",
      "method_id": "M-03",
      "source_record_id": "03:AT3-TH-004",
      "category": "Attack-tree root",
      "title": "Private note remains accessible after deletion/withdrawal",
      "scenario": "Operational copy or retained classification survives source deletion and remains readable.",
      "affected_ids": [
        "A-003",
        "A-005",
        "D-004",
        "D-007",
        "F-009"
      ],
      "control_ids": [
        "C-010"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "likelihood": "unknown",
        "impact": "unknown",
        "score": "not assigned",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-011",
        "T-019",
        "T-030",
        "T-043"
      ]
    },
    {
      "id": "T-035",
      "method_id": "M-04",
      "source_record_id": "04:FM-01",
      "category": "FMEA failure mode",
      "title": "Identity/authorization returns wrong decision",
      "scenario": "Email/session, role, ownership, suspension, Admin-grant, or assignment enforcement admits unauthorized access or rejects preserved access.",
      "affected_ids": [
        "A-001",
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "F-002",
        "EP-003"
      ],
      "control_ids": [
        "C-002",
        "C-003",
        "C-011"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-001",
        "T-008",
        "T-014",
        "T-015",
        "T-022",
        "T-031"
      ]
    },
    {
      "id": "T-036",
      "method_id": "M-04",
      "source_record_id": "04:FM-02",
      "category": "FMEA failure mode",
      "title": "Event publication or recipe snapshot invalid",
      "scenario": "Launch/lifecycle/visibility/time/immutability/snapshot processing stores or serves invalid state.",
      "affected_ids": [
        "A-002",
        "A-003",
        "D-002",
        "D-004",
        "F-001",
        "F-003"
      ],
      "control_ids": [
        "C-005",
        "C-012"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-003"
      ]
    },
    {
      "id": "T-037",
      "method_id": "M-04",
      "source_record_id": "04:FM-03",
      "category": "FMEA failure mode",
      "title": "Food request/consent/acceptance/order state advances incorrectly",
      "scenario": "Consent, review, acceptance, payment, cutoff, or cancellation gates fail.",
      "affected_ids": [
        "A-003",
        "D-004",
        "D-005",
        "F-004"
      ],
      "control_ids": [
        "C-002",
        "C-004",
        "C-005"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-003",
        "T-025",
        "T-028"
      ]
    },
    {
      "id": "T-038",
      "method_id": "M-04",
      "source_record_id": "04:FM-04",
      "category": "FMEA failure mode",
      "title": "Seat hold/capacity accounting inconsistent",
      "scenario": "Overlapping operations oversubscribe, retain/release wrong hold, or create duplicate bookings.",
      "affected_ids": [
        "A-003",
        "D-005",
        "F-005",
        "EP-007"
      ],
      "control_ids": [
        "C-006"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-005",
        "T-017",
        "T-032"
      ]
    },
    {
      "id": "T-039",
      "method_id": "M-04",
      "source_record_id": "04:FM-05",
      "category": "FMEA failure mode",
      "title": "Payment result validated/reconciled/deduplicated incorrectly",
      "scenario": "Payment input changes state without valid evidence, amount/currency, hold, event state, or operation identity.",
      "affected_ids": [
        "A-003",
        "A-004",
        "A-007",
        "F-005",
        "EP-005"
      ],
      "control_ids": [
        "C-001",
        "C-006"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-002",
        "T-004",
        "T-016",
        "T-032"
      ]
    },
    {
      "id": "T-040",
      "method_id": "M-04",
      "source_record_id": "04:FM-06",
      "category": "FMEA failure mode",
      "title": "Refund/payout late, excessive, duplicate, or email-blocked",
      "scenario": "Wrong financial amount, eligibility, identity, timing, or execution dependency causes loss or delay.",
      "affected_ids": [
        "A-004",
        "A-005",
        "A-007",
        "A-008",
        "F-006",
        "EP-007"
      ],
      "control_ids": [
        "C-001",
        "C-007",
        "C-008"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-004",
        "T-006",
        "T-013",
        "T-018",
        "T-020",
        "T-033"
      ]
    },
    {
      "id": "T-041",
      "method_id": "M-04",
      "source_record_id": "04:FM-07",
      "category": "FMEA failure mode",
      "title": "Preparation/shopping output wrong or privacy-leaking",
      "scenario": "Wrong orders/variants/conversions/rounding or audience projection yields bad quantities or disclosure.",
      "affected_ids": [
        "A-003",
        "D-004",
        "D-005",
        "F-004",
        "F-007"
      ],
      "control_ids": [
        "C-003",
        "C-014"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-009",
        "T-025",
        "T-028"
      ]
    },
    {
      "id": "T-042",
      "method_id": "M-04",
      "source_record_id": "04:FM-08",
      "category": "FMEA failure mode",
      "title": "Staff update/reconnect lost, stale, duplicate, or mis-scoped",
      "scenario": "Staff view differs from current authorized state because delivery, cursor, authorization, privacy, or rendering fails.",
      "affected_ids": [
        "A-003",
        "A-005",
        "A-006",
        "F-007"
      ],
      "control_ids": [
        "C-002",
        "C-003",
        "C-008",
        "C-012"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-010",
        "T-012",
        "T-015",
        "T-021",
        "T-031",
        "T-045"
      ]
    },
    {
      "id": "T-043",
      "method_id": "M-04",
      "source_record_id": "04:FM-09",
      "category": "FMEA failure mode",
      "title": "Durable work, audit, or retention incomplete",
      "scenario": "Restart, scheduled work, audit fields, or deletion/retention diverges from source state.",
      "affected_ids": [
        "A-003",
        "A-004",
        "A-005",
        "F-006",
        "F-009",
        "EP-007"
      ],
      "control_ids": [
        "C-008",
        "C-009",
        "C-010"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-006",
        "T-007",
        "T-011",
        "T-012",
        "T-019",
        "T-029",
        "T-030",
        "T-034"
      ]
    },
    {
      "id": "T-044",
      "method_id": "M-04",
      "source_record_id": "04:FM-10",
      "category": "FMEA failure mode",
      "title": "Email access/notice fails without safe fallback",
      "scenario": "Access/notice delivery or persistence fails, email leaks restricted fields, or isolation failure cascades to finance.",
      "affected_ids": [
        "A-001",
        "A-005",
        "A-008",
        "F-002",
        "F-008"
      ],
      "control_ids": [
        "C-001",
        "C-003",
        "C-013"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-009",
        "T-013",
        "T-019",
        "T-020",
        "T-040"
      ]
    },
    {
      "id": "T-045",
      "method_id": "M-04",
      "source_record_id": "04:FM-11",
      "category": "FMEA failure mode",
      "title": "Web presentation misstates state/value/error/staleness",
      "scenario": "UI conflates state, omits price/deadline/errors, loses input, or breaks keyboard/focus/reflow.",
      "affected_ids": [
        "A-006",
        "D-002",
        "D-004",
        "D-005",
        "D-006",
        "D-007"
      ],
      "control_ids": [
        "C-012"
      ],
      "evidence_ids": [
        "EV-04",
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "rating": {
        "source": "unranked; factors absent",
        "unified": "unresolved"
      },
      "related_threat_ids": [
        "T-021",
        "T-042"
      ]
    }
  ],
  "controls": [
    {
      "id": "C-001",
      "name": "Payment/email gateway isolation",
      "mechanism_scope": "Separate ports, adapters, clients, credentials, config, retry/failure state, execution capacity; distinct payment callback adapter.",
      "status": "approved logical architecture constraint; implementation absent",
      "evidence_ids": [
        "E-ARCH",
        "E-SEC",
        "EV-07"
      ],
      "source_refs": [
        "07:DA7-C-001",
        "00:S00-CTL-004",
        "02:L2-C-011"
      ]
    },
    {
      "id": "C-002",
      "name": "Ownership, role, suspension, Admin-grant, and current-assignment authorization",
      "mechanism_scope": "Protected reads/actions and replay entitlement.",
      "status": "required behavior; server placement proposed; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "07:DA7-C-002",
        "00:S00-CTL-002",
        "01:C-01",
        "04:C-01"
      ]
    },
    {
      "id": "C-003",
      "name": "Audience-specific projections and field minimization",
      "mechanism_scope": "Public/Attendee/Organizer/cook/shopper/Admin, address, shopper, email, and own-record filters.",
      "status": "required field outcomes plus proposed server projections; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ],
      "source_refs": [
        "07:DA7-C-003",
        "07:DA7-C-004",
        "02:L2-C-001",
        "02:L2-C-002",
        "02:L2-C-005",
        "02:L2-C-006"
      ]
    },
    {
      "id": "C-004",
      "name": "Food-note consent, review, acceptance, and request labeling",
      "mechanism_scope": "Consent before sharing; Organizer review; Attendee acceptance; no certification claim.",
      "status": "required/design behavior; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-DES"
      ],
      "source_refs": [
        "07:DA7-C-005",
        "02:L2-C-003"
      ]
    },
    {
      "id": "C-005",
      "name": "Server-owned transitions, launch validation, and immutable snapshots",
      "mechanism_scope": "Event/order commands, cutoff/time rules, event and accepted-recipe snapshots.",
      "status": "required outcomes with proposed placement; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH"
      ],
      "source_refs": [
        "00:S00-CTL-003",
        "04:C-03",
        "04:C-04",
        "04:C-05"
      ]
    },
    {
      "id": "C-006",
      "name": "Payment evidence, capacity, booking, and confirmation integrity",
      "mechanism_scope": "Authenticity, amount/currency, hold/event checks, capacity serialization, atomic replacement, operation identity.",
      "status": "required outcomes with proposed transaction/deduplication; provider/persistence unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "07:DA7-C-006",
        "00:S00-CTL-005",
        "03:AT3-C-005",
        "03:AT3-C-006"
      ]
    },
    {
      "id": "C-007",
      "name": "Refund caps, payout eligibility, and financial deduplication",
      "mechanism_scope": "Aggregate refund cap, unresolved obligations, unique payout proceeds, retries.",
      "status": "required outcomes with proposed mechanisms; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "03:AT3-C-007",
        "03:AT3-C-008",
        "04:C-12"
      ]
    },
    {
      "id": "C-008",
      "name": "Durable work, updates, cursor replay, and independent dispatch",
      "mechanism_scope": "Commit work/update records with state, resume after restart, current state/history, replay authorization.",
      "status": "required outcomes with proposed mechanisms; transport/execution unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "07:DA7-C-007",
        "00:S00-CTL-008",
        "04:C-14"
      ]
    },
    {
      "id": "C-009",
      "name": "Attributable audit",
      "mechanism_scope": "Actor, time, and outcome for required state changes.",
      "status": "required behavior; audience, integrity, nonfinancial retention, and implementation unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "00:S00-CTL-006",
        "02:L2-C-007"
      ]
    },
    {
      "id": "C-010",
      "name": "Private-note deletion, financial exclusion, retention, and reference-only propagation",
      "mechanism_scope": "90-day/withdrawal deletion, 24-month financial subset, no private notes in retained finance, proposed references instead of copies.",
      "status": "required outcomes plus proposed copy minimization; classification/copy/backup coverage unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "07:DA7-C-009",
        "07:DA7-C-010",
        "02:L2-C-008",
        "02:L2-C-009",
        "03:AT3-C-009",
        "03:AT3-C-010"
      ]
    },
    {
      "id": "C-011",
      "name": "Verified-email access, logout, and revocable sessions",
      "mechanism_scope": "Required verification/sign-in/logout; proposed opaque server session.",
      "status": "behavior required; session proposal unapproved; lifecycle/Admin bootstrap unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "source_refs": [
        "00:S00-CTL-001",
        "02:L2-C-010"
      ]
    },
    {
      "id": "C-012",
      "name": "Canonical, accessible, and visibly stale presentation",
      "mechanism_scope": "States, values, field errors, retained input, staleness, focus, keyboard, reflow.",
      "status": "required/design behavior; not rendered or tested",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "C-013",
      "name": "Persistent account notices and filtered email fallback",
      "mechanism_scope": "Account notice remains when email fails; restricted fields excluded.",
      "status": "required behavior; provider/implementation unresolved",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "C-014",
      "name": "Deterministic ingredient planning",
      "mechanism_scope": "Confirmed-order filter, accepted snapshots, unit families, exact conversions, upward rounding, visible calculation time.",
      "status": "required behavior; exact arithmetic proposed; implementation absent",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH"
      ]
    },
    {
      "id": "C-015",
      "name": "SC-001 Server boundary controls",
      "status": "BLOCKED",
      "dependency": "OD-001, OD-005, OD-008",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-016",
      "name": "SC-002 Web rendering/browser controls",
      "status": "BLOCKED",
      "dependency": "OD-003, OD-008, OD-012",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-017",
      "name": "SC-003 Identity/authorization",
      "status": "BLOCKED",
      "dependency": "OD-003, OD-004, OD-008",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-018",
      "name": "SC-004 Native authentication/storage",
      "status": "BLOCKED",
      "dependency": "OD-002, OD-003, OD-008",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-019",
      "name": "SC-005 Persistence/financial consistency",
      "status": "BLOCKED",
      "dependency": "OD-006, OD-009",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-020",
      "name": "SC-006 Provider boundary implementation",
      "status": "BLOCKED",
      "dependency": "OD-007, OD-009",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-021",
      "name": "SC-007 Private data/audit lifecycle",
      "status": "BLOCKED",
      "dependency": "OD-006, OD-008, OD-010",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-022",
      "name": "SC-008 Build/deployment controls",
      "status": "BLOCKED",
      "dependency": "OD-007, OD-008",
      "evidence_ids": [
        "E-SEC"
      ]
    },
    {
      "id": "C-023",
      "name": "SC-009 Staff-update authorization",
      "status": "BLOCKED",
      "dependency": "OD-001, OD-010, OD-011",
      "evidence_ids": [
        "E-SEC"
      ]
    }
  ],
  "requirements": [
    {
      "id": "RQ-001",
      "name": "Authorization and audience restrictions",
      "source_ids": [
        "FR-2.12",
        "FR-6.6 through FR-6.16",
        "FR-11.1",
        "FR-11.2"
      ],
      "control_ids": [
        "C-002",
        "C-003"
      ],
      "threat_ids": [
        "T-008",
        "T-010",
        "T-014",
        "T-015",
        "T-031",
        "T-035",
        "T-042"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-002",
      "name": "Event lifecycle and snapshots",
      "source_ids": [
        "FR-1",
        "FR-2",
        "FR-5",
        "FR-7.8",
        "FR-7.9"
      ],
      "control_ids": [
        "C-005",
        "C-012"
      ],
      "threat_ids": [
        "T-003",
        "T-036",
        "T-045"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-003",
      "name": "Consent, food review, acceptance, and changes",
      "source_ids": [
        "FR-3",
        "FR-11.7"
      ],
      "control_ids": [
        "C-004",
        "C-005",
        "C-010"
      ],
      "threat_ids": [
        "T-003",
        "T-025",
        "T-028",
        "T-037"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-004",
      "name": "Capacity and payment confirmation",
      "source_ids": [
        "FR-8",
        "NFR-2.2"
      ],
      "control_ids": [
        "C-006"
      ],
      "threat_ids": [
        "T-002",
        "T-004",
        "T-005",
        "T-016",
        "T-017",
        "T-032",
        "T-038",
        "T-039"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH"
      ]
    },
    {
      "id": "RQ-005",
      "name": "Refund and payout integrity/timing",
      "source_ids": [
        "FR-9",
        "NFR-1.5"
      ],
      "control_ids": [
        "C-001",
        "C-007",
        "C-008"
      ],
      "threat_ids": [
        "T-004",
        "T-006",
        "T-013",
        "T-018",
        "T-020",
        "T-033",
        "T-040"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH"
      ]
    },
    {
      "id": "RQ-006",
      "name": "Preparation and deterministic shopping",
      "source_ids": [
        "FR-4.5 through FR-4.8",
        "FR-10",
        "NFR-2.3"
      ],
      "control_ids": [
        "C-003",
        "C-014"
      ],
      "threat_ids": [
        "T-009",
        "T-025",
        "T-028",
        "T-041"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-007",
      "name": "Durable staff updates and reconnect",
      "source_ids": [
        "FR-4.1 through FR-4.11",
        "NFR-1.1 through NFR-1.3",
        "NFR-3.6"
      ],
      "control_ids": [
        "C-002",
        "C-008",
        "C-012"
      ],
      "threat_ids": [
        "T-010",
        "T-012",
        "T-021",
        "T-042",
        "T-045"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-008",
      "name": "Email access/notices and fallback",
      "source_ids": [
        "FR-4.12 through FR-4.14",
        "FR-6.2 through FR-6.4"
      ],
      "control_ids": [
        "C-001",
        "C-011",
        "C-013"
      ],
      "threat_ids": [
        "T-001",
        "T-009",
        "T-013",
        "T-020",
        "T-022",
        "T-044"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "RQ-009",
      "name": "Audit, deletion, and retention",
      "source_ids": [
        "FR-11.3 through FR-11.7",
        "NFR-2.1"
      ],
      "control_ids": [
        "C-009",
        "C-010"
      ],
      "threat_ids": [
        "T-007",
        "T-011",
        "T-019",
        "T-029",
        "T-030",
        "T-034",
        "T-043"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ]
    },
    {
      "id": "RQ-010",
      "name": "Payment/email integration isolation",
      "source_ids": [
        "ARCHITECTURE §2",
        "ARCHITECTURE §8",
        "DR-9"
      ],
      "control_ids": [
        "C-001"
      ],
      "threat_ids": [
        "T-013",
        "T-020",
        "T-040",
        "T-044"
      ],
      "evidence_ids": [
        "E-ARCH",
        "E-SEC"
      ]
    },
    {
      "id": "RQ-011",
      "name": "Security-relevant rendering/accessibility",
      "source_ids": [
        "NFR-3",
        "DESIGN Components",
        "DESIGN Do's and Don'ts"
      ],
      "control_ids": [
        "C-012"
      ],
      "threat_ids": [
        "T-021",
        "T-042",
        "T-045"
      ],
      "evidence_ids": [
        "E-REQ",
        "E-DES"
      ]
    }
  ],
  "risks": [
    {
      "id": "R-001",
      "name": "Identity impersonation or excess privilege",
      "threat_ids": [
        "T-001",
        "T-014",
        "T-015",
        "T-022",
        "T-031",
        "T-035"
      ],
      "source_risk_refs": [
        "01:R-01",
        "01:R-08",
        "04:R-01"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "attack-tree unknown",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-002",
      "name": "Invalid event, order, or recipe state",
      "threat_ids": [
        "T-003",
        "T-036",
        "T-037",
        "T-045"
      ],
      "source_risk_refs": [
        "04:R-02",
        "04:R-03",
        "04:R-11"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-003",
      "name": "Invalid booking, payment state, or oversubscription",
      "threat_ids": [
        "T-002",
        "T-004",
        "T-005",
        "T-016",
        "T-017",
        "T-032",
        "T-038",
        "T-039"
      ],
      "source_risk_refs": [
        "01:R-02",
        "01:R-03",
        "03:AT3-RISK-002",
        "04:R-04",
        "04:R-05"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "attack-tree unknown",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-004",
      "name": "Excess refund, duplicate payout, or delayed finance",
      "threat_ids": [
        "T-004",
        "T-006",
        "T-013",
        "T-018",
        "T-020",
        "T-033",
        "T-040"
      ],
      "source_risk_refs": [
        "01:R-04",
        "01:R-06",
        "04:R-06",
        "03:AT3-RISK-003",
        "07:DA7-RISK-001"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "attack-tree unknown",
        "FMEA unranked",
        "document risk not rated"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-005",
      "name": "Unauthorized restricted-data disclosure",
      "threat_ids": [
        "T-008",
        "T-009",
        "T-010",
        "T-015",
        "T-019",
        "T-027",
        "T-031",
        "T-035",
        "T-041",
        "T-042",
        "T-044"
      ],
      "source_risk_refs": [
        "01:R-01",
        "01:R-05",
        "02:L2-RISK-005",
        "02:L2-RISK-006",
        "03:AT3-RISK-001",
        "04:R-07",
        "04:R-08",
        "04:R-10"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "LINDDUN not assigned",
        "attack-tree unknown",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-006",
      "name": "Intended public event linking, identifying, and detecting",
      "threat_ids": [
        "T-023",
        "T-024",
        "T-026"
      ],
      "source_risk_refs": [
        "02:L2-RISK-001",
        "02:L2-RISK-002",
        "02:L2-RISK-004"
      ],
      "source_ratings": [
        "LINDDUN likelihood bounded to required disclosure; impact unknown; score not assigned"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-007",
      "name": "Intended food-needs identity linkage and disclosure",
      "threat_ids": [
        "T-025",
        "T-028"
      ],
      "source_risk_refs": [
        "02:L2-RISK-003",
        "02:L2-RISK-006"
      ],
      "source_ratings": [
        "LINDDUN required consented/current-cook disclosure; misuse likelihood and impact unknown"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-008",
      "name": "Private-note survival beyond deletion/withdrawal",
      "threat_ids": [
        "T-011",
        "T-019",
        "T-030",
        "T-034",
        "T-043"
      ],
      "source_risk_refs": [
        "01:R-05",
        "02:L2-RISK-008",
        "03:AT3-RISK-004",
        "04:R-09",
        "07:DA7-RISK-003"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "LINDDUN not assigned",
        "attack-tree unknown",
        "FMEA unranked",
        "document risk not rated"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-009",
      "name": "Attributable records unavailable or over-linkable",
      "threat_ids": [
        "T-007",
        "T-029",
        "T-043"
      ],
      "source_risk_refs": [
        "02:L2-RISK-007",
        "04:R-09"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "LINDDUN not assigned",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-010",
      "name": "Update, work, or read availability misses targets",
      "threat_ids": [
        "T-012",
        "T-013",
        "T-021",
        "T-040",
        "T-042",
        "T-043",
        "T-044"
      ],
      "source_risk_refs": [
        "01:R-06",
        "01:R-07",
        "04:R-08",
        "04:R-09",
        "04:R-10",
        "07:DA7-RISK-002"
      ],
      "source_ratings": [
        "STRIDE unrated",
        "PASTA unresolved",
        "FMEA unranked",
        "document risk not rated"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-011",
      "name": "Misleading or inaccessible security-relevant rendering",
      "threat_ids": [
        "T-021",
        "T-042",
        "T-045"
      ],
      "source_risk_refs": [
        "01:R-07",
        "04:R-08",
        "04:R-11"
      ],
      "source_ratings": [
        "PASTA unresolved",
        "FMEA unranked"
      ],
      "unified_rating": "unresolved"
    },
    {
      "id": "R-012",
      "name": "Native and technology ambiguity",
      "threat_ids": [],
      "source_risk_refs": [
        "07:DA7-RISK-004"
      ],
      "source_ratings": [
        "document risk not rated"
      ],
      "unified_rating": "unresolved",
      "note": "Architecture risk retained as an evidence/implementation-boundary risk; no threat invented."
    }
  ],
  "attack_trees": [
    {
      "id": "TREE-001",
      "method_id": "M-03",
      "source_tree_id": "03:AT3-TREE-001",
      "threat_id": "T-031",
      "root": "Obtain restricted data without audience entitlement",
      "operator": "OR",
      "branches": [
        "Public read plus failed field exclusion",
        "Authenticated cross-record request plus failed ownership check",
        "Former-staff replay plus failed current-assignment check"
      ],
      "source_node_count": 12,
      "path_ids": [
        "AP-001",
        "AP-002",
        "AP-003"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH",
        "E-DES"
      ]
    },
    {
      "id": "TREE-002",
      "method_id": "M-03",
      "source_tree_id": "03:AT3-TREE-002",
      "threat_id": "T-032",
      "root": "Confirm booking without acceptable payment and valid hold",
      "operator": "OR",
      "branches": [
        "Browser-controlled return treated as authoritative",
        "Invalid/replayed provider evidence accepted",
        "Over-capacity hold confirmed"
      ],
      "source_node_count": 12,
      "path_ids": [
        "AP-004",
        "AP-005",
        "AP-006"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH"
      ]
    },
    {
      "id": "TREE-003",
      "method_id": "M-03",
      "source_tree_id": "03:AT3-TREE-003",
      "threat_id": "T-033",
      "root": "Excess refund or duplicate payout",
      "operator": "OR",
      "branches": [
        "Repeated refund plus failed cap plus provider acceptance",
        "Repeated payout plus failed deduplication plus provider completion"
      ],
      "source_node_count": 9,
      "path_ids": [
        "AP-007",
        "AP-008"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH"
      ]
    },
    {
      "id": "TREE-004",
      "method_id": "M-03",
      "source_tree_id": "03:AT3-TREE-004",
      "threat_id": "T-034",
      "root": "Private note remains accessible after required deletion",
      "operator": "OR",
      "branches": [
        "Operational copy survives source deletion",
        "Private content classified as retained recipe/handling data"
      ],
      "source_node_count": 9,
      "path_ids": [
        "AP-009",
        "AP-010"
      ],
      "evidence_ids": [
        "EV-03",
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ]
    }
  ],
  "attack_paths": [
    {
      "id": "AP-001",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-001",
      "tree_id": "TREE-001",
      "threat_id": "T-031",
      "description": "Public request plus failed public-field exclusion.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "No implementation/response evidence; control failure assumed."
      ]
    },
    {
      "id": "AP-002",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-002",
      "tree_id": "TREE-001",
      "threat_id": "T-031",
      "description": "Authenticated cross-record selection plus failed ownership enforcement.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Record-selector interface and implementation unknown."
      ]
    },
    {
      "id": "AP-003",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-003",
      "tree_id": "TREE-001",
      "threat_id": "T-031",
      "description": "Former-staff cursor, replay request, and failed current-assignment enforcement.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Transport/cursor/implementation unresolved."
      ]
    },
    {
      "id": "AP-004",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-004",
      "tree_id": "TREE-002",
      "threat_id": "T-032",
      "description": "Checkout plus browser-controlled result plus failed authoritative-evidence rule.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Provider/browser-return contract unresolved."
      ]
    },
    {
      "id": "AP-005",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-005",
      "tree_id": "TREE-002",
      "threat_id": "T-032",
      "description": "Invalid/repeated provider evidence plus failed validation/deduplication.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Callback/reconciliation implementation unresolved."
      ]
    },
    {
      "id": "AP-006",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-006",
      "tree_id": "TREE-002",
      "threat_id": "T-032",
      "description": "Simultaneous last-seat requests plus failed consistency plus invalid-hold confirmation.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Persistence/transaction design unresolved."
      ]
    },
    {
      "id": "AP-007",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-007",
      "tree_id": "TREE-003",
      "threat_id": "T-033",
      "description": "Repeated refund plus failed aggregate cap plus provider acceptance.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Provider contract/implementation unresolved."
      ]
    },
    {
      "id": "AP-008",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-008",
      "tree_id": "TREE-003",
      "threat_id": "T-033",
      "description": "Repeated payout plus failed deduplication plus provider completion.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Provider contract/implementation unresolved."
      ]
    },
    {
      "id": "AP-009",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-009",
      "tree_id": "TREE-004",
      "threat_id": "T-034",
      "description": "Copied note plus source deletion plus readable surviving copy.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Copy inventory/storage/backups/readers unresolved."
      ]
    },
    {
      "id": "AP-010",
      "method_id": "M-03",
      "source_path_id": "03:AT3-PATH-010",
      "tree_id": "TREE-004",
      "threat_id": "T-034",
      "description": "Private content enters retained record, falls outside deletion classification, and remains readable.",
      "status": "conditionally satisfiable",
      "likelihood": "unknown",
      "impact": "unknown",
      "assumptions": [
        "Private-note versus recipe/handling classification unresolved."
      ]
    },
    {
      "id": "AP-011",
      "method_id": "M-01",
      "source_path_id": "01:AP-01",
      "threat_id": "T-015",
      "description": "Request another audience's record; authorization/projection fails; restricted data/state is returned/changed.",
      "status": "assumption-marked",
      "control_ids": [
        "C-002",
        "C-003"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-012",
      "method_id": "M-01",
      "source_path_id": "01:AP-02",
      "threat_id": "T-016",
      "description": "Deliver/replay payment result; validation/deduplication fails; invalid booking/financial state results.",
      "status": "assumption-marked",
      "control_ids": [
        "C-001",
        "C-006"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-013",
      "method_id": "M-01",
      "source_path_id": "01:AP-03",
      "threat_id": "T-017",
      "description": "Overlap capacity changes; shared atomic rule fails; occupancy/seat allocation becomes inconsistent.",
      "status": "assumption-marked",
      "control_ids": [
        "C-006"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-014",
      "method_id": "M-01",
      "source_path_id": "01:AP-04",
      "threat_id": "T-018",
      "description": "Repeat financial invocation; cap/eligibility/deduplication fails; excess refund/duplicate payout results.",
      "status": "assumption-marked",
      "control_ids": [
        "C-007"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-015",
      "method_id": "M-01",
      "source_path_id": "01:AP-05",
      "threat_id": "T-019",
      "description": "Restricted content is copied; filtering/deletion misses copy; content is disclosed/retained.",
      "status": "assumption-marked",
      "control_ids": [
        "C-003",
        "C-010"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-016",
      "method_id": "M-01",
      "source_path_id": "01:AP-06",
      "threat_id": "T-020",
      "description": "Email retries accumulate; execution isolation fails; financial operation is delayed.",
      "status": "assumption-marked",
      "control_ids": [
        "C-001"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-017",
      "method_id": "M-01",
      "source_path_id": "01:AP-07",
      "threat_id": "T-021",
      "description": "Staff reconnects; cursor/assignment/privacy/durability fails; stale/incomplete/unauthorized data displays.",
      "status": "assumption-marked",
      "control_ids": [
        "C-002",
        "C-003",
        "C-008",
        "C-012"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    },
    {
      "id": "AP-018",
      "method_id": "M-01",
      "source_path_id": "01:AP-08",
      "threat_id": "T-022",
      "description": "Unauthorized party obtains access artifact; lifecycle permits reuse; authenticated session results.",
      "status": "assumption-marked",
      "control_ids": [
        "C-011"
      ],
      "evidence_ids": [
        "EV-01"
      ]
    }
  ],
  "visualizations": [
    {
      "id": "V-001",
      "name": "Component and trust-boundary diagram",
      "type": "Mermaid flowchart source",
      "source": "ARCHITECTURE.md §5 / DA7-VIZ-001",
      "status": "Payment/email separation confirmed; other internal boundaries proposed; not a rendered verification",
      "depicts_ids": [
        "Z-001",
        "Z-003",
        "Z-004",
        "Z-005",
        "Z-006",
        "Z-007",
        "B-001",
        "B-002",
        "B-003",
        "B-005"
      ]
    },
    {
      "id": "V-002",
      "name": "Checkout and payment-result sequence",
      "type": "Mermaid sequence source",
      "source": "ARCHITECTURE.md §6 / DA7-VIZ-002",
      "status": "Logical design; provider/persistence/implementation unresolved",
      "depicts_ids": [
        "F-005",
        "F-006",
        "ACT-003",
        "ACT-007",
        "A-003",
        "A-004"
      ]
    },
    {
      "id": "DGM-001",
      "title": "Picky Party System Context",
      "purpose": "Show the system, its people, providers, data exchanges, and trust crossings.",
      "audience": [
        "Executives",
        "Product",
        "Security"
      ],
      "view": "system-context",
      "model_record_ids": [
        "SCP-001",
        "ACT-001",
        "ACT-002",
        "ACT-003",
        "ACT-004",
        "ACT-005",
        "ACT-006",
        "ACT-007",
        "ACT-008",
        "ACT-009",
        "B-001",
        "B-003",
        "B-004",
        "B-005",
        "B-006",
        "F-001",
        "F-002",
        "F-005",
        "F-006",
        "F-008"
      ],
      "specification": {
        "elements": [
          {
            "id": "SCP-001",
            "label": "Picky Party first-release website",
            "kind": "system scope",
            "zone": "Modeled system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-001",
            "label": "Visitor",
            "kind": "legitimate external actor",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-002",
            "label": "Organizer",
            "kind": "account role",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-003",
            "label": "Attendee",
            "kind": "account role",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-004",
            "label": "Cook",
            "kind": "event assignment",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-005",
            "label": "Shopper",
            "kind": "event assignment",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-006",
            "label": "Admin",
            "kind": "privileged role; first provisioning unresolved",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-007",
            "label": "Payment service",
            "kind": "external provider; selection unresolved",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-008",
            "label": "Email service",
            "kind": "external provider; selection unresolved",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-009",
            "label": "Untrusted or unauthorized requester",
            "kind": "generic threat agent",
            "zone": "External to system",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          }
        ],
        "connections": [
          {
            "source_id": "ACT-001",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Discover launched events (F-001)",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Required public event data (D-002)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-023",
                "T-024",
                "T-026",
                "T-031"
              ],
              "control_ids": [
                "C-003"
              ]
            }
          },
          {
            "source_id": "ACT-002",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Organize events, review food needs, manage finance",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Personal, restricted, operational, and financial (D-001–D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-014",
                "T-015",
                "T-019",
                "T-028"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-004"
              ]
            }
          },
          {
            "source_id": "ACT-003",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Order, checkout, attend, cancel",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Identity, food, booking, and finance (D-001,D-004–D-006)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-005",
                "T-016",
                "T-017"
              ],
              "control_ids": [
                "C-002",
                "C-004",
                "C-006"
              ]
            }
          },
          {
            "source_id": "ACT-004",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Prepare assigned event food",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Restricted food and order data (D-004,D-005,D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-010",
                "T-025",
                "T-028",
                "T-041"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-008"
              ]
            }
          },
          {
            "source_id": "ACT-005",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Shop for assigned event",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Restricted planning and update data (D-005,D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-009",
                "T-010",
                "T-041",
                "T-042"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-008"
              ]
            }
          },
          {
            "source_id": "ACT-006",
            "destination_id": "SCP-001",
            "direction": "bidirectional",
            "label": "Administer accounts, events, and finance",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Privileged personal, operational, and financial data (D-001–D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-014",
                "T-015",
                "T-018",
                "T-029"
              ],
              "control_ids": [
                "C-002",
                "C-007",
                "C-009"
              ]
            }
          },
          {
            "source_id": "SCP-001",
            "destination_id": "ACT-007",
            "direction": "bidirectional",
            "label": "Payment, callback, refund, payout, reconciliation (F-005,F-006)",
            "protocol": "Unresolved",
            "data_sensitivity": "Non-public financial data (D-006)",
            "boundary_crossings": [
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-004",
                "T-016",
                "T-018"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "SCP-001",
            "destination_id": "ACT-008",
            "direction": "outbound",
            "label": "Verification links and filtered notices (F-002,F-008)",
            "protocol": "Unresolved",
            "data_sensitivity": "Access and audience-filtered notice data (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-013",
                "T-020",
                "T-022",
                "T-044"
              ],
              "control_ids": [
                "C-001",
                "C-011",
                "C-013"
              ]
            }
          },
          {
            "source_id": "ACT-009",
            "destination_id": "SCP-001",
            "direction": "inbound",
            "label": "Requests; exact flow unresolved",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Request-dependent; unknown",
            "boundary_crossings": [
              "B-001"
            ],
            "refs": {
              "threat_ids": [
                "T-015",
                "T-031"
              ],
              "control_ids": [
                "C-002",
                "C-003"
              ]
            }
          }
        ],
        "boundary_groups": [
          {
            "id": "BG-SYSTEM",
            "label": "Modeled system boundary",
            "member_ids": [
              "SCP-001"
            ],
            "model_boundary_ids": [
              "B-001",
              "B-003",
              "B-004",
              "B-005",
              "B-006"
            ],
            "status": "Logical scope only; deployment topology unresolved"
          }
        ],
        "annotations": [
          "Use neutral threat markers; no comparable ordered rating exists.",
          "Payment and email are distinct external exchanges."
        ],
        "ordering_constraints": [
          "Place SCP-001 centrally.",
          "Place people left, providers right, ACT-009 below.",
          "Do not merge payment and email crossings."
        ],
        "legend": [
          {
            "symbol": "solid box",
            "meaning": "modeled actor/system element"
          },
          {
            "symbol": "dashed boundary",
            "meaning": "trust boundary crossing"
          },
          {
            "symbol": "T-nnn",
            "meaning": "neutral threat reference; no severity implied"
          }
        ],
        "text_preview": [
          "People and generic requester -> [SCP-001 Picky Party] <-> payment provider",
          "[SCP-001 Picky Party] -> email provider"
        ]
      },
      "omissions": [
        "Exact provider products, deployment/network topology, and native-client exchanges are unresolved.",
        "Protocol is known only as proposed HTTP JSON at the client boundary; provider protocols are unresolved."
      ],
      "validation_notes": [
        "All external actors ACT-001–ACT-009 represented.",
        "All listed threat IDs exist; ranking intentionally omitted."
      ]
    },
    {
      "id": "DGM-002",
      "title": "Picky Party Containers and Components",
      "purpose": "Show logical client, application, persistence, payment, email, provider, and durable-work structure.",
      "audience": [
        "Developers",
        "Architects",
        "Security"
      ],
      "view": "container-component",
      "model_record_ids": [
        "Z-001",
        "Z-002",
        "Z-003",
        "Z-004",
        "Z-005",
        "Z-006",
        "Z-007",
        "ACT-010",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "specification": {
        "elements": [
          {
            "id": "Z-001",
            "label": "Untrusted web client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "ReactJS named; version unresolved",
            "refs": {
              "threat_ids": [
                "T-015",
                "T-045"
              ],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-002",
            "label": "Native client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "React Native named; platforms/workflows unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-003",
            "label": "Trusted application",
            "kind": "application zone",
            "zone": "Application",
            "technology": "Node.js/Fastify roles and versions unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-002",
                "C-005",
                "C-008"
              ]
            }
          },
          {
            "id": "Z-004",
            "label": "Persistence",
            "kind": "data zone",
            "zone": "Persistence",
            "technology": "PostgreSQL proposed; decision unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-006",
                "C-007",
                "C-009",
                "C-010"
              ]
            }
          },
          {
            "id": "Z-005",
            "label": "Isolated payment integration",
            "kind": "gateway zone",
            "zone": "Payment integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "id": "Z-006",
            "label": "Separate email integration",
            "kind": "gateway zone",
            "zone": "Email integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-013",
                "T-020"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "id": "Z-007",
            "label": "External providers",
            "kind": "external zone",
            "zone": "Outside system",
            "technology": "Providers unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-010",
            "label": "Durable work dispatcher",
            "kind": "proposed internal actor",
            "zone": "Application; exact component unresolved",
            "technology": "Unresolved",
            "refs": {
              "threat_ids": [
                "T-006",
                "T-012",
                "T-043"
              ],
              "control_ids": [
                "C-008"
              ]
            }
          }
        ],
        "connections": [
          {
            "source_id": "Z-001/Z-002",
            "destination_id": "Z-003",
            "direction": "bidirectional",
            "label": "Client requests and responses",
            "protocol": "HTTP JSON proposed; native unresolved",
            "data_sensitivity": "Public through restricted (D-001–D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-008",
                "T-009",
                "T-015"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-012"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-004",
            "direction": "bidirectional",
            "label": "State persistence",
            "protocol": "Unresolved",
            "data_sensitivity": "Personal, restricted, operational, financial (D-001,D-003–D-007)",
            "boundary_crossings": [
              "B-002"
            ],
            "refs": {
              "threat_ids": [
                "T-005"
              ],
              "control_ids": [
                "C-006",
                "C-007",
                "C-009",
                "C-010"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-005",
            "direction": "bidirectional",
            "label": "Payment commands and validated results",
            "protocol": "Unresolved",
            "data_sensitivity": "Financial (D-006)",
            "boundary_crossings": [
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "Z-005",
            "destination_id": "Z-007",
            "direction": "bidirectional",
            "label": "Payment provider operations",
            "protocol": "Unresolved",
            "data_sensitivity": "Financial (D-006)",
            "boundary_crossings": [
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-006",
            "direction": "outbound",
            "label": "Access and notice dispatch",
            "protocol": "Unresolved",
            "data_sensitivity": "Access and filtered notice data (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-009"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "source_id": "Z-006",
            "destination_id": "Z-007",
            "direction": "outbound",
            "label": "Email provider delivery",
            "protocol": "Unresolved",
            "data_sensitivity": "Access and filtered notice data (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "source_id": "ACT-010",
            "destination_id": "Z-003/Z-004/Z-005/Z-006",
            "direction": "internal/bidirectional",
            "label": "Scheduled, retry, reconciliation, notification work",
            "protocol": "Unresolved",
            "data_sensitivity": "Operational and financial metadata (D-006,D-007)",
            "boundary_crossings": [
              "B-002",
              "B-003",
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-006",
                "T-012",
                "T-043"
              ],
              "control_ids": [
                "C-008"
              ]
            }
          }
        ],
        "boundary_groups": [
          {
            "id": "BG-CLIENT",
            "label": "Client/application trust boundary",
            "member_ids": [
              "Z-001",
              "Z-002",
              "Z-003"
            ],
            "model_boundary_ids": [
              "B-001",
              "B-006"
            ],
            "status": "HTTP JSON and server projections proposed; native unresolved"
          },
          {
            "id": "BG-PERSIST",
            "label": "Application/persistence trust boundary",
            "member_ids": [
              "Z-003",
              "Z-004"
            ],
            "model_boundary_ids": [
              "B-002"
            ],
            "status": "Interfaces and technology unresolved"
          },
          {
            "id": "BG-PAY",
            "label": "Isolated payment integration boundary",
            "member_ids": [
              "Z-003",
              "Z-005",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-003",
              "B-004"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          },
          {
            "id": "BG-EMAIL",
            "label": "Separate email integration boundary",
            "member_ids": [
              "Z-003",
              "Z-006",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-005"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          }
        ],
        "annotations": [
          "Dashed groups represent trust boundaries, not deployment networks.",
          "Technology labels preserve proposed/unresolved status."
        ],
        "ordering_constraints": [
          "Clients left; application center; persistence below; payment and email gateways right; providers far right.",
          "Keep payment and email gateways separate.",
          "Place ACT-010 near application/persistence without implying a deployed service."
        ],
        "legend": [
          {
            "symbol": "solid box",
            "meaning": "logical zone or actor"
          },
          {
            "symbol": "dashed group",
            "meaning": "trust boundary"
          },
          {
            "symbol": "proposed/unresolved",
            "meaning": "evidence status, not implementation"
          }
        ],
        "text_preview": [
          "Z-001/Z-002 -> Z-003 <-> Z-004",
          "Z-003 <-> Z-005 <-> Z-007",
          "Z-003 -> Z-006 -> Z-007",
          "ACT-010 -> Z-003/Z-004/Z-005/Z-006"
        ]
      },
      "omissions": [
        "No cache, queue, file store, concrete service split, endpoint list, or deployment node is specified.",
        "Exact technology versions and Node.js/Fastify roles are unresolved."
      ],
      "validation_notes": [
        "Component names match model zones.",
        "Only confirmed payment/email logical separation is shown as confirmed; other placement remains proposed or unresolved."
      ]
    },
    {
      "id": "DGM-003",
      "title": "Picky Party Data Flows",
      "purpose": "Trace all nine modeled flows, their data classifications, protocols, and trust crossings.",
      "audience": [
        "Security",
        "Privacy",
        "Developers",
        "Auditors"
      ],
      "view": "data-flow",
      "model_record_ids": [
        "F-001",
        "F-002",
        "F-003",
        "F-004",
        "F-005",
        "F-006",
        "F-007",
        "F-008",
        "F-009",
        "D-001",
        "D-002",
        "D-003",
        "D-004",
        "D-005",
        "D-006",
        "D-007",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "specification": {
        "elements": [
          {
            "id": "Z-001",
            "label": "Untrusted web client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "ReactJS named; version unresolved",
            "refs": {
              "threat_ids": [
                "T-015",
                "T-045"
              ],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-002",
            "label": "Native client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "React Native named; platforms/workflows unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-003",
            "label": "Trusted application",
            "kind": "application zone",
            "zone": "Application",
            "technology": "Node.js/Fastify roles and versions unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-002",
                "C-005",
                "C-008"
              ]
            }
          },
          {
            "id": "Z-004",
            "label": "Persistence",
            "kind": "data zone",
            "zone": "Persistence",
            "technology": "PostgreSQL proposed; decision unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-006",
                "C-007",
                "C-009",
                "C-010"
              ]
            }
          },
          {
            "id": "Z-005",
            "label": "Isolated payment integration",
            "kind": "gateway zone",
            "zone": "Payment integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "id": "Z-006",
            "label": "Separate email integration",
            "kind": "gateway zone",
            "zone": "Email integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-013",
                "T-020"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "id": "Z-007",
            "label": "External providers",
            "kind": "external zone",
            "zone": "Outside system",
            "technology": "Providers unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-010",
            "label": "Durable work dispatcher",
            "kind": "proposed internal actor",
            "zone": "Application; exact component unresolved",
            "technology": "Unresolved",
            "refs": {
              "threat_ids": [
                "T-006",
                "T-012",
                "T-043"
              ],
              "control_ids": [
                "C-008"
              ]
            }
          }
        ],
        "connections": [
          {
            "source_id": "Z-003",
            "destination_id": "ACT-001",
            "direction": "outbound",
            "label": "Publish and discover (F-001)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "required public data for launched events",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-012",
                "T-023",
                "T-024",
                "T-026",
                "T-031",
                "T-036"
              ],
              "control_ids": [
                "C-003"
              ]
            }
          },
          {
            "source_id": "Z-003/Z-006/Z-007",
            "destination_id": "Z-001/Z-002",
            "direction": "outbound then inbound link use",
            "label": "Verify and sign in through email link (F-002)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "personal/access data; detailed classification unresolved",
            "boundary_crossings": [
              "B-001",
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-001",
                "T-013",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": [
                "C-011",
                "C-013"
              ]
            }
          },
          {
            "source_id": "ACT-002/Z-003",
            "destination_id": "Z-001/Z-002",
            "direction": "bidirectional",
            "label": "Create event and expose exact location to authorized audiences (F-003)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "restricted audience",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-014",
                "T-027",
                "T-036"
              ],
              "control_ids": [
                "C-002",
                "C-003"
              ]
            }
          },
          {
            "source_id": "ACT-003/Z-003/Z-004",
            "destination_id": "ACT-002/ACT-004 via Z-003",
            "direction": "bidirectional",
            "label": "Submit, review, accept, and prepare food requests (F-004)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "private/audience-specific; exact boundary unresolved, non-public operational/account data",
            "boundary_crossings": [
              "B-001",
              "B-002",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-014",
                "T-025",
                "T-028",
                "T-037",
                "T-041"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-004"
              ]
            }
          },
          {
            "source_id": "Z-001/Z-002/Z-003/Z-005",
            "destination_id": "Z-004/Z-007",
            "direction": "bidirectional including callback",
            "label": "Checkout, callback, validation, and booking confirmation (F-005)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "non-public operational/account data, non-public financial data; specified subset retained 24 months",
            "boundary_crossings": [
              "B-001",
              "B-002",
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-004",
                "T-005",
                "T-006",
                "T-016",
                "T-017",
                "T-032",
                "T-038",
                "T-039"
              ],
              "control_ids": [
                "C-001",
                "C-006"
              ]
            }
          },
          {
            "source_id": "Z-001/Z-002/Z-003/Z-005",
            "destination_id": "Z-004/Z-007",
            "direction": "bidirectional",
            "label": "Cancel, refund, reconcile, and pay out (F-006)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "non-public operational/account data, non-public financial data; specified subset retained 24 months, audience-filtered; nonfinancial retention unresolved",
            "boundary_crossings": [
              "B-001",
              "B-002",
              "B-003",
              "B-004",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-012",
                "T-013",
                "T-014",
                "T-018",
                "T-020",
                "T-033",
                "T-040",
                "T-043"
              ],
              "control_ids": [
                "C-001",
                "C-007",
                "C-008"
              ]
            }
          },
          {
            "source_id": "Z-003/Z-004",
            "destination_id": "ACT-004/ACT-005 via Z-001/Z-002",
            "direction": "outbound/replay",
            "label": "Staff update, polling, and reconnect replay (F-007)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "private/audience-specific; exact boundary unresolved, non-public operational/account data, audience-filtered; nonfinancial retention unresolved",
            "boundary_crossings": [
              "B-001",
              "B-002",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-009",
                "T-010",
                "T-012",
                "T-014",
                "T-019",
                "T-021",
                "T-031",
                "T-041",
                "T-042"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-008",
                "C-012"
              ]
            }
          },
          {
            "source_id": "Z-003/Z-004/Z-006",
            "destination_id": "ACT-008 and account client",
            "direction": "outbound",
            "label": "Persist account notice and send filtered email (F-008)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "personal/access data; detailed classification unresolved, audience-filtered; nonfinancial retention unresolved",
            "boundary_crossings": [
              "B-002",
              "B-005",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-009",
                "T-013",
                "T-019",
                "T-020",
                "T-044"
              ],
              "control_ids": [
                "C-001",
                "C-003",
                "C-013"
              ]
            }
          },
          {
            "source_id": "Z-003/ACT-010",
            "destination_id": "Z-004",
            "direction": "bidirectional/internal",
            "label": "Audit, delete private notes, and retain financial records (F-009)",
            "protocol": "HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved",
            "data_sensitivity": "private/audience-specific; exact boundary unresolved, non-public financial data; specified subset retained 24 months, audience-filtered; nonfinancial retention unresolved",
            "boundary_crossings": [
              "B-002",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-006",
                "T-007",
                "T-011",
                "T-012",
                "T-019",
                "T-029",
                "T-030",
                "T-034",
                "T-043"
              ],
              "control_ids": [
                "C-008",
                "C-009",
                "C-010"
              ]
            }
          }
        ],
        "boundary_groups": [
          {
            "id": "BG-CLIENT",
            "label": "Client/application trust boundary",
            "member_ids": [
              "Z-001",
              "Z-002",
              "Z-003"
            ],
            "model_boundary_ids": [
              "B-001",
              "B-006"
            ],
            "status": "HTTP JSON and server projections proposed; native unresolved"
          },
          {
            "id": "BG-PERSIST",
            "label": "Application/persistence trust boundary",
            "member_ids": [
              "Z-003",
              "Z-004"
            ],
            "model_boundary_ids": [
              "B-002"
            ],
            "status": "Interfaces and technology unresolved"
          },
          {
            "id": "BG-PAY",
            "label": "Isolated payment integration boundary",
            "member_ids": [
              "Z-003",
              "Z-005",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-003",
              "B-004"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          },
          {
            "id": "BG-EMAIL",
            "label": "Separate email integration boundary",
            "member_ids": [
              "Z-003",
              "Z-006",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-005"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          }
        ],
        "annotations": [
          "Mark every D-003, D-004, D-006, and D-007 carrying flow as sensitive.",
          "F-001 public disclosure and F-003/F-004/F-009 privacy lifecycle distinctions must remain visible."
        ],
        "ordering_constraints": [
          "Follow F-001 through F-009 top-to-bottom.",
          "Keep provider legs beside their gateway.",
          "Show B-006 response projection separately from B-001 request crossing."
        ],
        "legend": [
          {
            "symbol": "public",
            "meaning": "required public data D-002"
          },
          {
            "symbol": "sensitive",
            "meaning": "restricted/personal/financial/audience-filtered data"
          },
          {
            "symbol": "dashed crossing",
            "meaning": "one or more B-nnn trust boundaries"
          }
        ],
        "text_preview": [
          "F-001 public discovery: application -> visitor",
          "F-002 access: application -> email -> client -> application",
          "F-003/F-004 audience data: account roles <-> application <-> persistence",
          "F-005/F-006 finance: clients/application <-> persistence/payment",
          "F-007/F-008 updates/notices: application -> staff/account/email",
          "F-009 lifecycle: application/work dispatcher <-> persistence"
        ]
      },
      "omissions": [
        "Exact message schemas, provider protocols, persistence protocol, field-level pre-confirmation cook update projection, and native paths are unresolved."
      ],
      "validation_notes": [
        "All F-001–F-009 and D-001–D-007 are represented.",
        "Sensitivity text is copied from model classifications; no new classification assigned."
      ]
    },
    {
      "id": "DGM-004",
      "title": "Picky Party Threat-Annotated Architecture",
      "purpose": "Overlay every stable threat ID on the architecture without implying a common severity.",
      "audience": [
        "Security reviewers",
        "Developers",
        "Architects"
      ],
      "view": "threat-annotated-architecture",
      "model_record_ids": [
        "Z-001",
        "Z-002",
        "Z-003",
        "Z-004",
        "Z-005",
        "Z-006",
        "Z-007",
        "A-001",
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "A-006",
        "A-007",
        "A-008",
        "T-001",
        "T-002",
        "T-003",
        "T-004",
        "T-005",
        "T-006",
        "T-007",
        "T-008",
        "T-009",
        "T-010",
        "T-011",
        "T-012",
        "T-013",
        "T-014",
        "T-015",
        "T-016",
        "T-017",
        "T-018",
        "T-019",
        "T-020",
        "T-021",
        "T-022",
        "T-023",
        "T-024",
        "T-025",
        "T-026",
        "T-027",
        "T-028",
        "T-029",
        "T-030",
        "T-031",
        "T-032",
        "T-033",
        "T-034",
        "T-035",
        "T-036",
        "T-037",
        "T-038",
        "T-039",
        "T-040",
        "T-041",
        "T-042",
        "T-043",
        "T-044",
        "T-045",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "specification": {
        "elements": [
          {
            "id": "Z-001",
            "label": "Untrusted web client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "ReactJS named; version unresolved",
            "refs": {
              "threat_ids": [
                "T-015",
                "T-045"
              ],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-002",
            "label": "Native client",
            "kind": "client zone",
            "zone": "Client",
            "technology": "React Native named; platforms/workflows unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-012"
              ]
            }
          },
          {
            "id": "Z-003",
            "label": "Trusted application",
            "kind": "application zone",
            "zone": "Application",
            "technology": "Node.js/Fastify roles and versions unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-002",
                "C-005",
                "C-008"
              ]
            }
          },
          {
            "id": "Z-004",
            "label": "Persistence",
            "kind": "data zone",
            "zone": "Persistence",
            "technology": "PostgreSQL proposed; decision unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-006",
                "C-007",
                "C-009",
                "C-010"
              ]
            }
          },
          {
            "id": "Z-005",
            "label": "Isolated payment integration",
            "kind": "gateway zone",
            "zone": "Payment integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "id": "Z-006",
            "label": "Separate email integration",
            "kind": "gateway zone",
            "zone": "Email integration",
            "technology": "Separate adapter/client/config required; implementation absent",
            "refs": {
              "threat_ids": [
                "T-013",
                "T-020"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "id": "Z-007",
            "label": "External providers",
            "kind": "external zone",
            "zone": "Outside system",
            "technology": "Providers unresolved",
            "refs": {
              "threat_ids": [],
              "control_ids": []
            }
          },
          {
            "id": "ACT-010",
            "label": "Durable work dispatcher",
            "kind": "proposed internal actor",
            "zone": "Application; exact component unresolved",
            "technology": "Unresolved",
            "refs": {
              "threat_ids": [
                "T-006",
                "T-012",
                "T-043"
              ],
              "control_ids": [
                "C-008"
              ]
            }
          },
          {
            "id": "A-001",
            "label": "Account identity and access records",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-001",
                "T-010",
                "T-014",
                "T-015",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-002",
            "label": "Events, addresses, assignments, URLs, dishes, recipes, and ingredients",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-003",
                "T-008",
                "T-014",
                "T-015",
                "T-019",
                "T-023",
                "T-024",
                "T-026",
                "T-027",
                "T-031",
                "T-035",
                "T-036"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-003",
            "label": "Orders, food needs, consent, proposals, accepted recipes, holds, and bookings",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-002",
                "T-003",
                "T-004",
                "T-005",
                "T-006",
                "T-008",
                "T-009",
                "T-010",
                "T-011",
                "T-014",
                "T-015",
                "T-016",
                "T-017",
                "T-019",
                "T-021",
                "T-025",
                "T-028",
                "T-030",
                "T-031",
                "T-032",
                "T-034",
                "T-035",
                "T-036",
                "T-037",
                "T-038",
                "T-039",
                "T-041",
                "T-042",
                "T-043"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-004",
            "label": "Connected-account, payment, refund, payout, fee, and reconciliation records",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-002",
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-008",
                "T-013",
                "T-014",
                "T-015",
                "T-016",
                "T-018",
                "T-020",
                "T-029",
                "T-031",
                "T-032",
                "T-033",
                "T-035",
                "T-039",
                "T-040",
                "T-043"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-005",
            "label": "Staff updates, notices, delivery state, audit records, and pending work",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-006",
                "T-007",
                "T-008",
                "T-009",
                "T-010",
                "T-011",
                "T-012",
                "T-013",
                "T-015",
                "T-018",
                "T-019",
                "T-020",
                "T-021",
                "T-029",
                "T-030",
                "T-031",
                "T-034",
                "T-035",
                "T-040",
                "T-042",
                "T-043",
                "T-044"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-006",
            "label": "Presentation and transient client state",
            "kind": "asset annotation anchor",
            "zone": "Placement unresolved",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-021",
                "T-042",
                "T-045"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-007",
            "label": "Payment integration credentials and client configuration",
            "kind": "asset annotation anchor",
            "zone": "Z-005",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-016",
                "T-018",
                "T-020",
                "T-039",
                "T-040"
              ],
              "control_ids": []
            }
          },
          {
            "id": "A-008",
            "label": "Email integration credentials and client configuration",
            "kind": "asset annotation anchor",
            "zone": "Z-006",
            "technology": "Not applicable / unresolved",
            "refs": {
              "threat_ids": [
                "T-013",
                "T-020",
                "T-022",
                "T-040",
                "T-044"
              ],
              "control_ids": []
            }
          }
        ],
        "connections": [
          {
            "source_id": "Z-001/Z-002",
            "destination_id": "Z-003",
            "direction": "bidirectional",
            "label": "Client requests and responses",
            "protocol": "HTTP JSON proposed; native unresolved",
            "data_sensitivity": "Public through restricted (D-001–D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-008",
                "T-009",
                "T-015"
              ],
              "control_ids": [
                "C-002",
                "C-003",
                "C-012"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-004",
            "direction": "bidirectional",
            "label": "State persistence",
            "protocol": "Unresolved",
            "data_sensitivity": "Personal, restricted, operational, financial (D-001,D-003–D-007)",
            "boundary_crossings": [
              "B-002"
            ],
            "refs": {
              "threat_ids": [
                "T-005"
              ],
              "control_ids": [
                "C-006",
                "C-007",
                "C-009",
                "C-010"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-005",
            "direction": "bidirectional",
            "label": "Payment commands and validated results",
            "protocol": "Unresolved",
            "data_sensitivity": "Financial (D-006)",
            "boundary_crossings": [
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "Z-005",
            "destination_id": "Z-007",
            "direction": "bidirectional",
            "label": "Payment provider operations",
            "protocol": "Unresolved",
            "data_sensitivity": "Financial (D-006)",
            "boundary_crossings": [
              "B-003",
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-016"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "Z-003",
            "destination_id": "Z-006",
            "direction": "outbound",
            "label": "Access and notice dispatch",
            "protocol": "Unresolved",
            "data_sensitivity": "Access and filtered notice data (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-009"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "source_id": "Z-006",
            "destination_id": "Z-007",
            "direction": "outbound",
            "label": "Email provider delivery",
            "protocol": "Unresolved",
            "data_sensitivity": "Access and filtered notice data (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "source_id": "ACT-010",
            "destination_id": "Z-003/Z-004/Z-005/Z-006",
            "direction": "internal/bidirectional",
            "label": "Scheduled, retry, reconciliation, notification work",
            "protocol": "Unresolved",
            "data_sensitivity": "Operational and financial metadata (D-006,D-007)",
            "boundary_crossings": [
              "B-002",
              "B-003",
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-006",
                "T-012",
                "T-043"
              ],
              "control_ids": [
                "C-008"
              ]
            }
          }
        ],
        "boundary_groups": [
          {
            "id": "BG-CLIENT",
            "label": "Client/application trust boundary",
            "member_ids": [
              "Z-001",
              "Z-002",
              "Z-003"
            ],
            "model_boundary_ids": [
              "B-001",
              "B-006"
            ],
            "status": "HTTP JSON and server projections proposed; native unresolved"
          },
          {
            "id": "BG-PERSIST",
            "label": "Application/persistence trust boundary",
            "member_ids": [
              "Z-003",
              "Z-004"
            ],
            "model_boundary_ids": [
              "B-002"
            ],
            "status": "Interfaces and technology unresolved"
          },
          {
            "id": "BG-PAY",
            "label": "Isolated payment integration boundary",
            "member_ids": [
              "Z-003",
              "Z-005",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-003",
              "B-004"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          },
          {
            "id": "BG-EMAIL",
            "label": "Separate email integration boundary",
            "member_ids": [
              "Z-003",
              "Z-006",
              "Z-007"
            ],
            "model_boundary_ids": [
              "B-005"
            ],
            "status": "Logical isolation confirmed; implementation/protocol unresolved"
          }
        ],
        "annotations": [
          "Use one neutral T-nnn marker style for all threats.",
          "Place markers on A-nnn asset anchors because most asset placement is unresolved; do not infer a storage component.",
          "T-012/T-013 are availability/failure risks, not attacker assertions.",
          "T-023–T-029 intentional/required disclosures are privacy tradeoffs, not vulnerability findings."
        ],
        "ordering_constraints": [
          "Reuse DGM-002 layout.",
          "Place A-001–A-006 in an unplaced asset rail; A-007 beside Z-005 and A-008 beside Z-006.",
          "Cluster threat markers by asset; use callouts to keep architecture readable."
        ],
        "legend": [
          {
            "symbol": "T-001",
            "meaning": "Email-link or session impersonation"
          },
          {
            "symbol": "T-002",
            "meaning": "Unauthenticated payment result accepted as provider evidence"
          },
          {
            "symbol": "T-003",
            "meaning": "Client-controlled business transition"
          },
          {
            "symbol": "T-004",
            "meaning": "Altered, late, duplicate, or replayed financial evidence"
          },
          {
            "symbol": "T-005",
            "meaning": "Concurrent capacity corruption"
          },
          {
            "symbol": "T-006",
            "meaning": "Duplicate or out-of-order work applies stale effects"
          },
          {
            "symbol": "T-007",
            "meaning": "State change lacks attributable evidence"
          },
          {
            "symbol": "T-008",
            "meaning": "Public or wrong-account projection exposes restricted data"
          },
          {
            "symbol": "T-009",
            "meaning": "Shopper or email projection leaks restricted fields"
          },
          {
            "symbol": "T-010",
            "meaning": "Removed staff retain current/replayed access"
          },
          {
            "symbol": "T-011",
            "meaning": "Private food notes survive deletion/withdrawal"
          },
          {
            "symbol": "T-012",
            "meaning": "Polling or durable work misses service targets"
          },
          {
            "symbol": "T-013",
            "meaning": "Email failure delays access/notices or financial work"
          },
          {
            "symbol": "T-014",
            "meaning": "Account exceeds ownership, assignment, role, or suspension scope"
          },
          {
            "symbol": "T-015",
            "meaning": "Unauthorized actor reads or changes restricted records"
          },
          {
            "symbol": "T-016",
            "meaning": "Untrusted or repeated payment evidence corrupts state"
          },
          {
            "symbol": "T-017",
            "meaning": "Concurrent capacity changes misallocate a seat"
          },
          {
            "symbol": "T-018",
            "meaning": "Repeated refund or payout exceeds authorized value"
          },
          {
            "symbol": "T-019",
            "meaning": "Private notes or addresses leak through projection/copy"
          },
          {
            "symbol": "T-020",
            "meaning": "Email integration failure controls financial work"
          },
          {
            "symbol": "T-021",
            "meaning": "Lost, delayed, replayed, or stale staff updates"
          },
          {
            "symbol": "T-022",
            "meaning": "Email access artifact permits impersonation"
          },
          {
            "symbol": "T-023",
            "meaning": "Permanent URL enables longitudinal event correlation"
          },
          {
            "symbol": "T-024",
            "meaning": "Public event identifies Organizer association"
          },
          {
            "symbol": "T-025",
            "meaning": "Cook view links Attendee identity with food needs"
          },
          {
            "symbol": "T-026",
            "meaning": "Public discovery reveals event existence/state"
          },
          {
            "symbol": "T-027",
            "meaning": "Permitted audiences learn precise event location"
          },
          {
            "symbol": "T-028",
            "meaning": "Food needs disclose personal circumstances to Organizer/cook"
          },
          {
            "symbol": "T-029",
            "meaning": "Audit/financial history creates attributable long-term linkage"
          },
          {
            "symbol": "T-030",
            "meaning": "Private-note copies outlive deletion lifecycle"
          },
          {
            "symbol": "T-031",
            "meaning": "Obtain restricted data without audience entitlement"
          },
          {
            "symbol": "T-032",
            "meaning": "Confirm booking without acceptable payment and valid hold"
          },
          {
            "symbol": "T-033",
            "meaning": "Excess refund or duplicate payout"
          },
          {
            "symbol": "T-034",
            "meaning": "Private note remains accessible after deletion/withdrawal"
          },
          {
            "symbol": "T-035",
            "meaning": "Identity/authorization returns wrong decision"
          },
          {
            "symbol": "T-036",
            "meaning": "Event publication or recipe snapshot invalid"
          },
          {
            "symbol": "T-037",
            "meaning": "Food request/consent/acceptance/order state advances incorrectly"
          },
          {
            "symbol": "T-038",
            "meaning": "Seat hold/capacity accounting inconsistent"
          },
          {
            "symbol": "T-039",
            "meaning": "Payment result validated/reconciled/deduplicated incorrectly"
          },
          {
            "symbol": "T-040",
            "meaning": "Refund/payout late, excessive, duplicate, or email-blocked"
          },
          {
            "symbol": "T-041",
            "meaning": "Preparation/shopping output wrong or privacy-leaking"
          },
          {
            "symbol": "T-042",
            "meaning": "Staff update/reconnect lost, stale, duplicate, or mis-scoped"
          },
          {
            "symbol": "T-043",
            "meaning": "Durable work, audit, or retention incomplete"
          },
          {
            "symbol": "T-044",
            "meaning": "Email access/notice fails without safe fallback"
          },
          {
            "symbol": "T-045",
            "meaning": "Web presentation misstates state/value/error/staleness"
          }
        ],
        "text_preview": [
          "[Unplaced asset rail A-001–A-006 with neutral T-nnn markers]",
          "Z-001/Z-002 -> Z-003 <-> Z-004",
          "Z-003 <-> Z-005[A-007] <-> Z-007",
          "Z-003 -> Z-006[A-008] -> Z-007"
        ]
      },
      "omissions": [
        "Component placement for A-001–A-006 is unresolved, so markers cannot be placed more specifically.",
        "No unified threat rating exists; no color, size, order, or emphasis implies severity."
      ],
      "validation_notes": [
        "Every T-001–T-045 appears in the legend and at least one asset or boundary reference.",
        "Related methods remain distinct; no threat IDs are merged."
      ]
    },
    {
      "id": "DGM-005",
      "title": "Picky Party Attack Surface",
      "purpose": "Show all modeled entry points with authentication, authorization, and derived threat counts.",
      "audience": [
        "Security reviewers",
        "Developers",
        "Auditors"
      ],
      "view": "attack-surface",
      "model_record_ids": [
        "EP-001",
        "EP-002",
        "EP-003",
        "EP-004",
        "EP-005",
        "EP-006",
        "EP-007",
        "T-001",
        "T-002",
        "T-003",
        "T-004",
        "T-005",
        "T-006",
        "T-007",
        "T-008",
        "T-009",
        "T-010",
        "T-011",
        "T-012",
        "T-013",
        "T-014",
        "T-015",
        "T-016",
        "T-017",
        "T-018",
        "T-019",
        "T-020",
        "T-021",
        "T-022",
        "T-023",
        "T-024",
        "T-025",
        "T-026",
        "T-027",
        "T-028",
        "T-029",
        "T-030",
        "T-031",
        "T-032",
        "T-033",
        "T-034",
        "T-035",
        "T-036",
        "T-037",
        "T-038",
        "T-039",
        "T-040",
        "T-041",
        "T-042",
        "T-043",
        "T-044",
        "T-045",
        "C-001",
        "C-002",
        "C-003",
        "C-004",
        "C-005",
        "C-006",
        "C-007",
        "C-008",
        "C-009",
        "C-010",
        "C-011",
        "C-012",
        "C-013",
        "C-014",
        "C-015",
        "C-016",
        "C-017",
        "C-018",
        "C-019",
        "C-020",
        "C-021",
        "C-022",
        "C-023"
      ],
      "specification": {
        "elements": [
          {
            "id": "EP-001",
            "label": "Public calendar, event page, and QR URL",
            "kind": "entry point",
            "zone": "External-facing",
            "authentication_authorization": "Public; no authentication required. Public-field projection C-003.",
            "threat_count": 6,
            "refs": {
              "threat_ids": [
                "T-012",
                "T-023",
                "T-024",
                "T-026",
                "T-031",
                "T-036"
              ],
              "control_ids": [
                "C-003"
              ]
            }
          },
          {
            "id": "EP-002",
            "label": "Email verification/sign-in link",
            "kind": "entry point",
            "zone": "External-facing",
            "authentication_authorization": "Possession of verification/sign-in artifact; lifecycle unresolved. Session control C-011.",
            "threat_count": 5,
            "refs": {
              "threat_ids": [
                "T-001",
                "T-013",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": [
                "C-011"
              ]
            }
          },
          {
            "id": "EP-003",
            "label": "Authenticated views/actions",
            "kind": "entry point",
            "zone": "External-facing",
            "authentication_authorization": "Authenticated. Ownership, role, suspension, and current assignment C-002; endpoints unspecified.",
            "threat_count": 29,
            "refs": {
              "threat_ids": [
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-009",
                "T-010",
                "T-011",
                "T-012",
                "T-013",
                "T-014",
                "T-018",
                "T-019",
                "T-020",
                "T-021",
                "T-025",
                "T-027",
                "T-028",
                "T-029",
                "T-030",
                "T-031",
                "T-033",
                "T-034",
                "T-035",
                "T-036",
                "T-037",
                "T-040",
                "T-041",
                "T-042",
                "T-043"
              ],
              "control_ids": [
                "C-002",
                "C-003"
              ]
            }
          },
          {
            "id": "EP-004",
            "label": "Checkout browser flow",
            "kind": "entry point",
            "zone": "External-facing",
            "authentication_authorization": "Authentication requirement not stated in the model. Order/hold and payment checks C-002/C-006.",
            "threat_count": 9,
            "refs": {
              "threat_ids": [
                "T-002",
                "T-004",
                "T-005",
                "T-006",
                "T-016",
                "T-017",
                "T-032",
                "T-038",
                "T-039"
              ],
              "control_ids": [
                "C-002",
                "C-006"
              ]
            }
          },
          {
            "id": "EP-005",
            "label": "Payment callbacks/reconciliation",
            "kind": "entry point",
            "zone": "External-facing",
            "authentication_authorization": "Provider-origin authentication protocol unresolved. Evidence/state authorization C-006/C-007.",
            "threat_count": 19,
            "refs": {
              "threat_ids": [
                "T-002",
                "T-003",
                "T-004",
                "T-005",
                "T-006",
                "T-007",
                "T-012",
                "T-013",
                "T-014",
                "T-016",
                "T-017",
                "T-018",
                "T-020",
                "T-032",
                "T-033",
                "T-038",
                "T-039",
                "T-040",
                "T-043"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "id": "EP-006",
            "label": "Email delivery gateway",
            "kind": "entry point",
            "zone": "Integration/internal",
            "authentication_authorization": "Gateway/provider authentication unresolved. Isolation and filtered notices C-001/C-013.",
            "threat_count": 8,
            "refs": {
              "threat_ids": [
                "T-001",
                "T-009",
                "T-013",
                "T-019",
                "T-020",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "id": "EP-007",
            "label": "Scheduled/retry work",
            "kind": "entry point",
            "zone": "Integration/internal",
            "authentication_authorization": "Operational identity unresolved. Eligibility, deduplication, and durable execution C-007/C-008.",
            "threat_count": 21,
            "refs": {
              "threat_ids": [
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-009",
                "T-011",
                "T-012",
                "T-013",
                "T-014",
                "T-017",
                "T-018",
                "T-019",
                "T-020",
                "T-029",
                "T-030",
                "T-033",
                "T-034",
                "T-038",
                "T-040",
                "T-043",
                "T-044"
              ],
              "control_ids": [
                "C-007",
                "C-008"
              ]
            }
          }
        ],
        "connections": [
          {
            "source_id": "ACT-001",
            "destination_id": "EP-001",
            "direction": "inbound",
            "label": "Public discovery",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Required public (D-002)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-012",
                "T-023",
                "T-024",
                "T-026",
                "T-031",
                "T-036"
              ],
              "control_ids": [
                "C-003"
              ]
            }
          },
          {
            "source_id": "ACT-008/Z-001/Z-002",
            "destination_id": "EP-002",
            "direction": "email then inbound browser use",
            "label": "Verification/sign-in link",
            "protocol": "Email protocol and link lifecycle unresolved",
            "data_sensitivity": "Access data (D-001)",
            "boundary_crossings": [
              "B-005",
              "B-001"
            ],
            "refs": {
              "threat_ids": [
                "T-001",
                "T-013",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": [
                "C-011"
              ]
            }
          },
          {
            "source_id": "ACT-002/ACT-003/ACT-004/ACT-005/ACT-006",
            "destination_id": "EP-003",
            "direction": "bidirectional",
            "label": "Authenticated views and actions",
            "protocol": "HTTP JSON proposed",
            "data_sensitivity": "Restricted and financial (D-001,D-003–D-007)",
            "boundary_crossings": [
              "B-001",
              "B-006"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-009",
                "T-010",
                "T-011",
                "T-012",
                "T-013",
                "T-014",
                "T-018",
                "T-019",
                "T-020",
                "T-021",
                "T-025",
                "T-027",
                "T-028",
                "T-029",
                "T-030",
                "T-031",
                "T-033",
                "T-034",
                "T-035",
                "T-036",
                "T-037",
                "T-040",
                "T-041",
                "T-042",
                "T-043"
              ],
              "control_ids": [
                "C-002",
                "C-003"
              ]
            }
          },
          {
            "source_id": "ACT-003",
            "destination_id": "EP-004",
            "direction": "bidirectional",
            "label": "Checkout browser flow",
            "protocol": "Protocol unresolved",
            "data_sensitivity": "Booking and financial (D-005,D-006)",
            "boundary_crossings": [
              "B-001",
              "B-003"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-004",
                "T-005",
                "T-006",
                "T-016",
                "T-017",
                "T-032",
                "T-038",
                "T-039"
              ],
              "control_ids": [
                "C-002",
                "C-006"
              ]
            }
          },
          {
            "source_id": "ACT-007",
            "destination_id": "EP-005",
            "direction": "inbound/bidirectional",
            "label": "Callbacks and reconciliation",
            "protocol": "Protocol/authenticity unresolved",
            "data_sensitivity": "Financial (D-006)",
            "boundary_crossings": [
              "B-004"
            ],
            "refs": {
              "threat_ids": [
                "T-002",
                "T-003",
                "T-004",
                "T-005",
                "T-006",
                "T-007",
                "T-012",
                "T-013",
                "T-014",
                "T-016",
                "T-017",
                "T-018",
                "T-020",
                "T-032",
                "T-033",
                "T-038",
                "T-039",
                "T-040",
                "T-043"
              ],
              "control_ids": [
                "C-001",
                "C-006",
                "C-007"
              ]
            }
          },
          {
            "source_id": "SCP-001",
            "destination_id": "EP-006/ACT-008",
            "direction": "outbound",
            "label": "Email delivery",
            "protocol": "Provider unresolved",
            "data_sensitivity": "Access and filtered notice (D-001,D-007)",
            "boundary_crossings": [
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-001",
                "T-009",
                "T-013",
                "T-019",
                "T-020",
                "T-022",
                "T-035",
                "T-044"
              ],
              "control_ids": [
                "C-001",
                "C-013"
              ]
            }
          },
          {
            "source_id": "ACT-010",
            "destination_id": "EP-007/SCP-001",
            "direction": "internal",
            "label": "Scheduled and retry work",
            "protocol": "Unresolved",
            "data_sensitivity": "Operational/financial metadata (D-006,D-007)",
            "boundary_crossings": [
              "B-002",
              "B-003",
              "B-005"
            ],
            "refs": {
              "threat_ids": [
                "T-003",
                "T-004",
                "T-006",
                "T-007",
                "T-009",
                "T-011",
                "T-012",
                "T-013",
                "T-014",
                "T-017",
                "T-018",
                "T-019",
                "T-020",
                "T-029",
                "T-030",
                "T-033",
                "T-034",
                "T-038",
                "T-040",
                "T-043",
                "T-044"
              ],
              "control_ids": [
                "C-007",
                "C-008"
              ]
            }
          }
        ],
        "boundary_groups": [
          {
            "id": "BG-ENTRY",
            "label": "System entry boundary",
            "member_ids": [
              "EP-001",
              "EP-002",
              "EP-003",
              "EP-004",
              "EP-005",
              "EP-006",
              "EP-007"
            ],
            "model_boundary_ids": [
              "B-001",
              "B-003",
              "B-004",
              "B-005",
              "B-006"
            ],
            "status": "Entry points are logical; endpoint/protocol detail is incomplete"
          }
        ],
        "annotations": [
          "Threat count equals distinct threats whose affected_ids contain the entry point or one of its flow_ids.",
          "Use equal neutral styling for every threat; counts do not imply severity."
        ],
        "ordering_constraints": [
          "Order EP-001 through EP-007.",
          "Group public/user, provider, and internal-work entries without ranking them."
        ],
        "legend": [
          {
            "symbol": "EP-nnn",
            "meaning": "stable entry point ID"
          },
          {
            "symbol": "count",
            "meaning": "derived number of linked threats; not a score"
          },
          {
            "symbol": "T-nnn",
            "meaning": "neutral linked threat"
          }
        ],
        "text_preview": [
          "EP-001 Public calendar, event page, and QR URL: 6 linked threats",
          "EP-002 Email verification/sign-in link: 5 linked threats",
          "EP-003 Authenticated views/actions: 29 linked threats",
          "EP-004 Checkout browser flow: 9 linked threats",
          "EP-005 Payment callbacks/reconciliation: 19 linked threats",
          "EP-006 Email delivery gateway: 8 linked threats",
          "EP-007 Scheduled/retry work: 21 linked threats"
        ]
      },
      "omissions": [
        "Concrete API routes, upload/admin-panel endpoints, endpoint schemas, rate limits, provider authentication, operational identities, and native entry points are not specified."
      ],
      "validation_notes": [
        "All EP-001–EP-007 represented.",
        "Counts are reproducible from affected entry point/flow IDs and do not create a risk ranking."
      ]
    },
    {
      "id": "FIG-001",
      "figure_number": 1,
      "title": "System Context (Executive View)",
      "view": "Executive View",
      "source_diagram_id": "DGM-001",
      "purpose": "Explain the product, people, providers, sensitive exchanges, and business-facing uncertainty without implementation detail.",
      "audience": [
        "Decision makers",
        "Product leadership",
        "Customer security reviewers"
      ],
      "scope": "SCP-001, external actors ACT-001–ACT-009, core exchanges, and system boundary.",
      "model_record_ids": [
        "SCP-001",
        "ACT-001",
        "ACT-002",
        "ACT-003",
        "ACT-004",
        "ACT-005",
        "ACT-006",
        "ACT-007",
        "ACT-008",
        "ACT-009",
        "B-001",
        "B-003",
        "B-004",
        "B-005",
        "B-006",
        "F-001",
        "F-002",
        "F-005",
        "F-006",
        "F-008"
      ],
      "intentionally_omitted_ids": [
        "ACT-010",
        "Z-001–Z-007",
        "A-001–A-008",
        "Internal implementation details"
      ],
      "layout": {
        "direction": "Left to right",
        "groups": [
          "People/requester",
          "System",
          "Payment and email providers"
        ],
        "hierarchy": "SCP-001 is primary; exchanges are secondary; neutral threat callouts are tertiary.",
        "boundary_regions": [
          "System boundary with B-001/B-003/B-004/B-005/B-006 crossing labels"
        ]
      },
      "annotations": [
        "Business effects only: account misuse, incorrect financial state, disclosure, delayed work.",
        "Payment and email remain visibly separate.",
        "No severity ranking."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT"
      ],
      "alt_text": "Executive context view with Picky Party centered, people and an untrusted requester on the left, and separate payment and email providers on the right. Public, restricted, and financial exchanges cross labeled trust boundaries. Neutral threat badges carry stable IDs without severity.",
      "linear_reading_order": [
        "Title and purpose",
        "People and requester",
        "System scope",
        "Payment provider exchange",
        "Email provider exchange",
        "Boundary and threat legend"
      ],
      "unresolved_rendering_decisions": [
        "Caller density limit and palette",
        "Page orientation",
        "Which four business-impact callouts fit the final medium"
      ],
      "validation_checks": [
        "All ACT-001–ACT-009 present",
        "Every connection has protocol/data text",
        "Payment/email paths are separate",
        "No rating cue"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Actors: equal 1.5×0.55 units left",
          "SCP-001: 3.0×2.2 units center",
          "Providers: equal 1.7×0.8 units right"
        ],
        "connection_paths": [
          "Orthogonal arrows; place protocol and data on one line where possible",
          "Use P or S tags on every exchange",
          "Crossings intersect the dashed system boundary once"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    },
    {
      "id": "FIG-002",
      "figure_number": 2,
      "title": "Container Architecture",
      "view": "Architecture View",
      "source_diagram_id": "DGM-002",
      "purpose": "Show the complete logical container structure and technology/status evidence for architecture review.",
      "audience": [
        "Developers",
        "Architecture review board",
        "Security architects"
      ],
      "scope": "Z-001–Z-007, ACT-010, B-001–B-006, and their specified connections.",
      "model_record_ids": [
        "Z-001",
        "Z-002",
        "Z-003",
        "Z-004",
        "Z-005",
        "Z-006",
        "Z-007",
        "ACT-010",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "intentionally_omitted_ids": [
        "A-001–A-008 as placed data stores",
        "Caches, queues, file stores, deployment nodes, and services not present in the model"
      ],
      "layout": {
        "direction": "Left to right",
        "groups": [
          "Clients",
          "Application and persistence",
          "Payment gateway",
          "Email gateway",
          "External providers"
        ],
        "hierarchy": "Clients feed the application; persistence is below it; gateways are separate peer branches; provider zone is last.",
        "boundary_regions": [
          "BG-CLIENT",
          "BG-PERSIST",
          "BG-PAY",
          "BG-EMAIL"
        ]
      },
      "annotations": [
        "Technology status appears beneath each Z-nnn label.",
        "Use ? / dotted treatment for proposed or unresolved technologies.",
        "Logical isolation does not imply implementation."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "alt_text": "Architecture view with web and unresolved native clients at left, the trusted application in the center above persistence, separate payment and email gateway hexagons to the right, external providers at far right, and a proposed durable-work actor near application and persistence.",
      "linear_reading_order": [
        "Title",
        "Client group",
        "Application",
        "Persistence",
        "Durable work",
        "Payment branch",
        "Email branch",
        "External providers",
        "Legend"
      ],
      "unresolved_rendering_decisions": [
        "Caller palette and page width",
        "Final wrapping of long technology labels",
        "Whether external providers need separate product boxes once providers are selected"
      ],
      "validation_checks": [
        "Names and technology statuses match DGM-002",
        "No cache/queue/service invented",
        "All B-001–B-006 crossings trace",
        "Gateway isolation status says logical/implementation absent"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Z-001/Z-002: 1.8×0.9 units left stack",
          "Z-003: 2.3×1.2 center",
          "Z-004: 2.3×1.0 below Z-003 cylinder",
          "Z-005/Z-006: 1.9×1.0 right stack hexagons",
          "Z-007: 2.0×1.4 far right",
          "ACT-010: 1.8×0.7 below-left of Z-003"
        ],
        "connection_paths": [
          "Orthogonal lines with arrowheads",
          "Separate parallel payment/email paths",
          "Internal work path dotted because implementation is proposed"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    },
    {
      "id": "FIG-003",
      "figure_number": 3,
      "title": "Data Flow Diagram",
      "view": "Security and Privacy View",
      "source_diagram_id": "DGM-003",
      "purpose": "Trace F-001–F-009 with classifications, protocols, controls, and trust crossings.",
      "audience": [
        "Security reviewers",
        "Privacy reviewers",
        "Developers",
        "Auditors"
      ],
      "scope": "All modeled data D-001–D-007 and flows F-001–F-009.",
      "model_record_ids": [
        "F-001",
        "F-002",
        "F-003",
        "F-004",
        "F-005",
        "F-006",
        "F-007",
        "F-008",
        "F-009",
        "D-001",
        "D-002",
        "D-003",
        "D-004",
        "D-005",
        "D-006",
        "D-007",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "intentionally_omitted_ids": [
        "Field schemas",
        "Native-specific flows",
        "Unspecified provider and persistence protocols"
      ],
      "layout": {
        "direction": "Top to bottom",
        "groups": [
          "Public and access flows",
          "Event/food flows",
          "Finance flows",
          "Updates/notices/lifecycle flows"
        ],
        "hierarchy": "Each numbered flow is one horizontal swim lane; components repeat as lane participants rather than creating new identities.",
        "boundary_regions": [
          "B-001/B-006 client crossing",
          "B-002 persistence crossing",
          "B-003/B-004 payment crossing",
          "B-005 email crossing"
        ]
      },
      "annotations": [
        "Apply P only to F-001 public data.",
        "Apply S to flows carrying D-003,D-004,D-006,or D-007.",
        "Show exact D-nnn, B-nnn, T-nnn, and C-nnn references."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "alt_text": "Nine horizontal swim lanes show public discovery, access email, location, food request, checkout, finance, updates, notices, and lifecycle flows. Each lane names data classifications, unresolved protocols, controls, threats, and dashed boundary crossings.",
      "linear_reading_order": [
        "Title and legend",
        "F-001 through F-009 in numeric order",
        "Data and control callouts per lane",
        "Omissions note"
      ],
      "unresolved_rendering_decisions": [
        "Page size may require two panels while retaining one figure number",
        "Caller palette",
        "Label wrapping for F-006 and F-009"
      ],
      "validation_checks": [
        "Every F-001–F-009 appears once",
        "Every D-001–D-007 appears",
        "Sensitive tags match classifications",
        "Boundary IDs match each source flow",
        "No inferred protocol"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Nine equal-height swim lanes; 0.7–0.9 units each",
          "Participant columns fixed across lanes",
          "Legend in lower-right margin"
        ],
        "connection_paths": [
          "Straight left-to-right arrows within each lane",
          "Dashed vertical dividers for boundaries",
          "Return/callback arrows offset below request arrows"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    },
    {
      "id": "FIG-004",
      "figure_number": 4,
      "title": "Threat-Annotated Architecture (Security View)",
      "view": "Security View",
      "source_diagram_id": "DGM-004",
      "purpose": "Place every T-001–T-045 on supported asset or boundary anchors while keeping the architecture legible.",
      "audience": [
        "Security teams",
        "Penetration-test planners",
        "Developers"
      ],
      "scope": "DGM-002 architecture plus A-001–A-008 anchors and all 45 methodology-specific threats.",
      "model_record_ids": [
        "Z-001",
        "Z-002",
        "Z-003",
        "Z-004",
        "Z-005",
        "Z-006",
        "Z-007",
        "A-001",
        "A-002",
        "A-003",
        "A-004",
        "A-005",
        "A-006",
        "A-007",
        "A-008",
        "T-001",
        "T-002",
        "T-003",
        "T-004",
        "T-005",
        "T-006",
        "T-007",
        "T-008",
        "T-009",
        "T-010",
        "T-011",
        "T-012",
        "T-013",
        "T-014",
        "T-015",
        "T-016",
        "T-017",
        "T-018",
        "T-019",
        "T-020",
        "T-021",
        "T-022",
        "T-023",
        "T-024",
        "T-025",
        "T-026",
        "T-027",
        "T-028",
        "T-029",
        "T-030",
        "T-031",
        "T-032",
        "T-033",
        "T-034",
        "T-035",
        "T-036",
        "T-037",
        "T-038",
        "T-039",
        "T-040",
        "T-041",
        "T-042",
        "T-043",
        "T-044",
        "T-045",
        "B-001",
        "B-002",
        "B-003",
        "B-004",
        "B-005",
        "B-006"
      ],
      "intentionally_omitted_ids": [
        "Risk colors, severity order, exploit claims, and implementation findings"
      ],
      "layout": {
        "direction": "Left to right with lower asset rail",
        "groups": [
          "Architecture base",
          "Unplaced asset rail A-001–A-006",
          "Gateway assets A-007/A-008",
          "Threat callout gutter"
        ],
        "hierarchy": "Architecture remains primary; grouped neutral badges are secondary; full threat legend is a side panel.",
        "boundary_regions": [
          "Same BG-CLIENT/BG-PERSIST/BG-PAY/BG-EMAIL regions as Figure 2"
        ]
      },
      "annotations": [
        "All T-nnn markers have equal visual weight.",
        "T-012/T-013 carry AVAILABILITY/FAILURE captions.",
        "T-023–T-029 carry PRIVACY TRADEOFF captions.",
        "Method records remain separate even when cross-linked."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL",
        "ST-PRIVACY"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL",
        "ST-PRIVACY"
      ],
      "alt_text": "The architecture from Figure 2 is overlaid with equal neutral threat badges. Assets whose component placement is unresolved appear in a lower rail. Availability/failure and intentional privacy-tradeoff records have explicit captions. A side legend maps all T-001 through T-045 to titles.",
      "linear_reading_order": [
        "Title",
        "Architecture base",
        "Asset rail",
        "Boundary callouts",
        "Threat clusters",
        "Full T-nnn legend",
        "Unresolved-placement note"
      ],
      "unresolved_rendering_decisions": [
        "Final callout pagination",
        "Caller palette",
        "Whether full threat legend sits beside or immediately after the figure"
      ],
      "validation_checks": [
        "Every T-001–T-045 appears at least once and in legend",
        "No color/order implies severity",
        "A-001–A-006 remain unplaced",
        "T-023–T-029 not labeled vulnerabilities",
        "T-012/T-013 not framed as attacks"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Reuse Figure 2 positions exactly",
          "A-001–A-006: six equal tagged boxes in lower rail",
          "A-007 adjacent Z-005; A-008 adjacent Z-006",
          "Threat legend: two columns, 9 pt minimum"
        ],
        "connection_paths": [
          "Reuse Figure 2 connections",
          "Leader lines from badges to anchors; no arrow semantics",
          "Bundle related callouts without merging IDs"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    },
    {
      "id": "FIG-005",
      "figure_number": 5,
      "title": "Data Flow with Supplied Requirement Annotations",
      "view": "Requirement View",
      "source_diagram_id": "DGM-003",
      "purpose": "Show exact sourced requirement groups on the data flows they connect to through explicit model threat mappings; this is not a compliance verdict.",
      "audience": [
        "Requirements reviewers",
        "Security architects",
        "Auditors"
      ],
      "scope": "F-001–F-009, RQ-001–RQ-011, their exact source IDs, and explicit RQ→T→F trace.",
      "model_record_ids": [
        "F-001",
        "F-002",
        "F-003",
        "F-004",
        "F-005",
        "F-006",
        "F-007",
        "F-008",
        "F-009",
        "RQ-001",
        "RQ-002",
        "RQ-003",
        "RQ-004",
        "RQ-005",
        "RQ-006",
        "RQ-007",
        "RQ-008",
        "RQ-009",
        "RQ-010",
        "RQ-011",
        "T-001",
        "T-002",
        "T-003",
        "T-004",
        "T-005",
        "T-006",
        "T-007",
        "T-008",
        "T-009",
        "T-010",
        "T-011",
        "T-012",
        "T-013",
        "T-014",
        "T-015",
        "T-016",
        "T-017",
        "T-018",
        "T-019",
        "T-020",
        "T-021",
        "T-022",
        "T-023",
        "T-024",
        "T-025",
        "T-026",
        "T-027",
        "T-028",
        "T-029",
        "T-030",
        "T-031",
        "T-032",
        "T-033",
        "T-034",
        "T-035",
        "T-036",
        "T-037",
        "T-038",
        "T-039",
        "T-040",
        "T-041",
        "T-042",
        "T-043",
        "T-044",
        "T-045"
      ],
      "intentionally_omitted_ids": [
        "Legal scope",
        "Compliance status",
        "Requirements with no explicit RQ→T→F trace"
      ],
      "layout": {
        "direction": "Top to bottom",
        "groups": [
          "Flow lanes from Figure 3",
          "Requirement callout column",
          "Exact source-ID key"
        ],
        "hierarchy": "Flows remain primary; RQ tags attach through callouts; exact FR/NFR/architecture/design sources appear in the side key.",
        "boundary_regions": [
          "Reuse Figure 3 boundary regions"
        ]
      },
      "annotations": [
        {
          "flow_id": "F-001",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-031"
              ]
            },
            {
              "requirement_id": "RQ-002",
              "source_ids": [
                "FR-1",
                "FR-2",
                "FR-5",
                "FR-7.8",
                "FR-7.9"
              ],
              "via_threat_ids": [
                "T-036"
              ]
            },
            {
              "requirement_id": "RQ-007",
              "source_ids": [
                "FR-4.1 through FR-4.11",
                "NFR-1.1 through NFR-1.3",
                "NFR-3.6"
              ],
              "via_threat_ids": [
                "T-012"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-002",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-035"
              ]
            },
            {
              "requirement_id": "RQ-005",
              "source_ids": [
                "FR-9",
                "NFR-1.5"
              ],
              "via_threat_ids": [
                "T-013"
              ]
            },
            {
              "requirement_id": "RQ-008",
              "source_ids": [
                "FR-4.12 through FR-4.14",
                "FR-6.2 through FR-6.4"
              ],
              "via_threat_ids": [
                "T-001",
                "T-013",
                "T-022",
                "T-044"
              ]
            },
            {
              "requirement_id": "RQ-010",
              "source_ids": [
                "ARCHITECTURE §2",
                "ARCHITECTURE §8",
                "DR-9"
              ],
              "via_threat_ids": [
                "T-013",
                "T-044"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-003",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-014"
              ]
            },
            {
              "requirement_id": "RQ-002",
              "source_ids": [
                "FR-1",
                "FR-2",
                "FR-5",
                "FR-7.8",
                "FR-7.9"
              ],
              "via_threat_ids": [
                "T-003",
                "T-036"
              ]
            },
            {
              "requirement_id": "RQ-003",
              "source_ids": [
                "FR-3",
                "FR-11.7"
              ],
              "via_threat_ids": [
                "T-003"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-004",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-014"
              ]
            },
            {
              "requirement_id": "RQ-002",
              "source_ids": [
                "FR-1",
                "FR-2",
                "FR-5",
                "FR-7.8",
                "FR-7.9"
              ],
              "via_threat_ids": [
                "T-003"
              ]
            },
            {
              "requirement_id": "RQ-003",
              "source_ids": [
                "FR-3",
                "FR-11.7"
              ],
              "via_threat_ids": [
                "T-003",
                "T-025",
                "T-028",
                "T-037"
              ]
            },
            {
              "requirement_id": "RQ-006",
              "source_ids": [
                "FR-4.5 through FR-4.8",
                "FR-10",
                "NFR-2.3"
              ],
              "via_threat_ids": [
                "T-025",
                "T-028",
                "T-041"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-005",
          "requirements": [
            {
              "requirement_id": "RQ-004",
              "source_ids": [
                "FR-8",
                "NFR-2.2"
              ],
              "via_threat_ids": [
                "T-002",
                "T-004",
                "T-005",
                "T-016",
                "T-017",
                "T-032",
                "T-038",
                "T-039"
              ]
            },
            {
              "requirement_id": "RQ-005",
              "source_ids": [
                "FR-9",
                "NFR-1.5"
              ],
              "via_threat_ids": [
                "T-004",
                "T-006"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-006",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-014"
              ]
            },
            {
              "requirement_id": "RQ-002",
              "source_ids": [
                "FR-1",
                "FR-2",
                "FR-5",
                "FR-7.8",
                "FR-7.9"
              ],
              "via_threat_ids": [
                "T-003"
              ]
            },
            {
              "requirement_id": "RQ-003",
              "source_ids": [
                "FR-3",
                "FR-11.7"
              ],
              "via_threat_ids": [
                "T-003"
              ]
            },
            {
              "requirement_id": "RQ-004",
              "source_ids": [
                "FR-8",
                "NFR-2.2"
              ],
              "via_threat_ids": [
                "T-004"
              ]
            },
            {
              "requirement_id": "RQ-005",
              "source_ids": [
                "FR-9",
                "NFR-1.5"
              ],
              "via_threat_ids": [
                "T-004",
                "T-006",
                "T-013",
                "T-018",
                "T-020",
                "T-033",
                "T-040"
              ]
            },
            {
              "requirement_id": "RQ-007",
              "source_ids": [
                "FR-4.1 through FR-4.11",
                "NFR-1.1 through NFR-1.3",
                "NFR-3.6"
              ],
              "via_threat_ids": [
                "T-012"
              ]
            },
            {
              "requirement_id": "RQ-008",
              "source_ids": [
                "FR-4.12 through FR-4.14",
                "FR-6.2 through FR-6.4"
              ],
              "via_threat_ids": [
                "T-013",
                "T-020"
              ]
            },
            {
              "requirement_id": "RQ-009",
              "source_ids": [
                "FR-11.3 through FR-11.7",
                "NFR-2.1"
              ],
              "via_threat_ids": [
                "T-007",
                "T-043"
              ]
            },
            {
              "requirement_id": "RQ-010",
              "source_ids": [
                "ARCHITECTURE §2",
                "ARCHITECTURE §8",
                "DR-9"
              ],
              "via_threat_ids": [
                "T-013",
                "T-020",
                "T-040"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-007",
          "requirements": [
            {
              "requirement_id": "RQ-001",
              "source_ids": [
                "FR-2.12",
                "FR-6.6 through FR-6.16",
                "FR-11.1",
                "FR-11.2"
              ],
              "via_threat_ids": [
                "T-010",
                "T-014",
                "T-031",
                "T-042"
              ]
            },
            {
              "requirement_id": "RQ-006",
              "source_ids": [
                "FR-4.5 through FR-4.8",
                "FR-10",
                "NFR-2.3"
              ],
              "via_threat_ids": [
                "T-009",
                "T-041"
              ]
            },
            {
              "requirement_id": "RQ-007",
              "source_ids": [
                "FR-4.1 through FR-4.11",
                "NFR-1.1 through NFR-1.3",
                "NFR-3.6"
              ],
              "via_threat_ids": [
                "T-010",
                "T-012",
                "T-021",
                "T-042"
              ]
            },
            {
              "requirement_id": "RQ-008",
              "source_ids": [
                "FR-4.12 through FR-4.14",
                "FR-6.2 through FR-6.4"
              ],
              "via_threat_ids": [
                "T-009"
              ]
            },
            {
              "requirement_id": "RQ-009",
              "source_ids": [
                "FR-11.3 through FR-11.7",
                "NFR-2.1"
              ],
              "via_threat_ids": [
                "T-019"
              ]
            },
            {
              "requirement_id": "RQ-011",
              "source_ids": [
                "NFR-3",
                "DESIGN Components",
                "DESIGN Do's and Don'ts"
              ],
              "via_threat_ids": [
                "T-021",
                "T-042"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-008",
          "requirements": [
            {
              "requirement_id": "RQ-005",
              "source_ids": [
                "FR-9",
                "NFR-1.5"
              ],
              "via_threat_ids": [
                "T-013",
                "T-020"
              ]
            },
            {
              "requirement_id": "RQ-006",
              "source_ids": [
                "FR-4.5 through FR-4.8",
                "FR-10",
                "NFR-2.3"
              ],
              "via_threat_ids": [
                "T-009"
              ]
            },
            {
              "requirement_id": "RQ-008",
              "source_ids": [
                "FR-4.12 through FR-4.14",
                "FR-6.2 through FR-6.4"
              ],
              "via_threat_ids": [
                "T-009",
                "T-013",
                "T-020",
                "T-044"
              ]
            },
            {
              "requirement_id": "RQ-009",
              "source_ids": [
                "FR-11.3 through FR-11.7",
                "NFR-2.1"
              ],
              "via_threat_ids": [
                "T-019"
              ]
            },
            {
              "requirement_id": "RQ-010",
              "source_ids": [
                "ARCHITECTURE §2",
                "ARCHITECTURE §8",
                "DR-9"
              ],
              "via_threat_ids": [
                "T-013",
                "T-020",
                "T-044"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        {
          "flow_id": "F-009",
          "requirements": [
            {
              "requirement_id": "RQ-005",
              "source_ids": [
                "FR-9",
                "NFR-1.5"
              ],
              "via_threat_ids": [
                "T-006"
              ]
            },
            {
              "requirement_id": "RQ-007",
              "source_ids": [
                "FR-4.1 through FR-4.11",
                "NFR-1.1 through NFR-1.3",
                "NFR-3.6"
              ],
              "via_threat_ids": [
                "T-012"
              ]
            },
            {
              "requirement_id": "RQ-009",
              "source_ids": [
                "FR-11.3 through FR-11.7",
                "NFR-2.1"
              ],
              "via_threat_ids": [
                "T-007",
                "T-011",
                "T-019",
                "T-029",
                "T-030",
                "T-034",
                "T-043"
              ]
            }
          ],
          "derivation": "Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."
        },
        "Association is derived from explicit model links and does not assert that a requirement directly names the flow.",
        "No pass/fail or compliance badge."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL",
        "ST-REQUIREMENT"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL",
        "ST-REQUIREMENT"
      ],
      "alt_text": "The nine data-flow lanes from Figure 3 include square RQ-nnn tags. A side key expands each requirement group to exact FR, NFR, architecture, or design source IDs and lists the T-nnn links that connect it to each flow. No compliance result is shown.",
      "linear_reading_order": [
        "Title and non-verdict note",
        "F-001 through F-009",
        "RQ tags per lane",
        "Exact requirement source key",
        "Trace rule",
        "Legend"
      ],
      "unresolved_rendering_decisions": [
        "Page width and callout wrapping",
        "Caller palette",
        "Whether source key is beside or beneath figure"
      ],
      "validation_checks": [
        "Every annotation has an RQ→T→F trace",
        "Exact source_ids preserved verbatim",
        "All RQ-001–RQ-011 appear where traced",
        "No legal/compliance inference"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Reuse Figure 3 lanes",
          "Requirement tags: 0.45×0.3 units at lane right",
          "Source key: 35–40% page width or full-width continuation panel"
        ],
        "connection_paths": [
          "Reuse Figure 3 paths",
          "Thin leader lines from RQ tags to flow lanes",
          "Do not route requirement leaders across data arrows"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    },
    {
      "id": "FIG-006",
      "figure_number": 6,
      "title": "Attack Surface Map",
      "view": "Security View",
      "source_diagram_id": "DGM-005",
      "purpose": "Show EP-001–EP-007 with access model, controls, and reproducible neutral threat counts.",
      "audience": [
        "Security reviewers",
        "Developers",
        "Auditors"
      ],
      "scope": "All modeled entry points and their actor/system relationships.",
      "model_record_ids": [
        "EP-001",
        "EP-002",
        "EP-003",
        "EP-004",
        "EP-005",
        "EP-006",
        "EP-007",
        "T-001",
        "T-002",
        "T-003",
        "T-004",
        "T-005",
        "T-006",
        "T-007",
        "T-008",
        "T-009",
        "T-010",
        "T-011",
        "T-012",
        "T-013",
        "T-014",
        "T-015",
        "T-016",
        "T-017",
        "T-018",
        "T-019",
        "T-020",
        "T-021",
        "T-022",
        "T-023",
        "T-024",
        "T-025",
        "T-026",
        "T-027",
        "T-028",
        "T-029",
        "T-030",
        "T-031",
        "T-032",
        "T-033",
        "T-034",
        "T-035",
        "T-036",
        "T-037",
        "T-038",
        "T-039",
        "T-040",
        "T-041",
        "T-042",
        "T-043",
        "T-044",
        "T-045",
        "C-001",
        "C-002",
        "C-003",
        "C-004",
        "C-005",
        "C-006",
        "C-007",
        "C-008",
        "C-009",
        "C-010",
        "C-011",
        "C-012",
        "C-013",
        "C-014",
        "C-015",
        "C-016",
        "C-017",
        "C-018",
        "C-019",
        "C-020",
        "C-021",
        "C-022",
        "C-023"
      ],
      "intentionally_omitted_ids": [
        "Unspecified API routes",
        "Uploads",
        "Admin-panel routes",
        "Native-only entries",
        "Rate limits"
      ],
      "layout": {
        "direction": "Left to right",
        "groups": [
          "Public/user entries",
          "Provider entries",
          "Internal scheduled work"
        ],
        "hierarchy": "Entry points are peers; threat count is metadata and never controls size, color, or order.",
        "boundary_regions": [
          "Single system-entry boundary labeled with B-001/B-003/B-004/B-005/B-006"
        ]
      },
      "annotations": [
        "Show authentication/authorization text beneath each EP-nnn.",
        "Threat counts use equal typography and are explicitly not scores.",
        "Use ? on unresolved provider authentication and operational identity."
      ],
      "legend_entries": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "style_token_ids": [
        "ST-ACTOR",
        "ST-COMPONENT",
        "ST-DATA",
        "ST-GATEWAY",
        "ST-BOUNDARY",
        "ST-PUBLIC",
        "ST-SENSITIVE",
        "ST-UNRESOLVED",
        "ST-THREAT",
        "ST-CONTROL"
      ],
      "alt_text": "Seven equally styled entry-point cards show public discovery, email sign-in, authenticated actions, checkout, payment callbacks, email delivery, and scheduled work. Each card names authentication and authorization evidence, controls, linked T-nnn IDs, and a threat count that is not a score.",
      "linear_reading_order": [
        "Title and count rule",
        "EP-001–EP-004 user-facing group",
        "EP-005–EP-006 provider group",
        "EP-007 internal-work group",
        "Legend and omissions"
      ],
      "unresolved_rendering_decisions": [
        "Caller palette",
        "Landscape or two-row arrangement",
        "Card height needed for EP-003 and EP-007 text"
      ],
      "validation_checks": [
        "All EP-001–EP-007 present",
        "Counts match explicit entry/flow references",
        "Equal styling irrespective of count",
        "Unknown auth stays unknown"
      ],
      "layout_specification": {
        "positions_sizes_types": [
          "Seven equal-width cards, minimum 1.8×1.3 units",
          "Arrange 4 cards top row, 3 bottom row or one horizontal strip",
          "System boundary behind cards, not around external actors"
        ],
        "connection_paths": [
          "Straight actor-to-card-to-system paths",
          "Provider callback uses inbound arrow",
          "Internal work uses dotted path"
        ],
        "boundary_treatment": "Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.",
        "rating_style_assignments": "None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.",
        "typography": {
          "title": "18–22 pt semibold",
          "section": "14–16 pt semibold",
          "component": "11–12 pt medium",
          "relationship": "9–10 pt; wrap once at most",
          "annotation": "9–10 pt minimum",
          "font": "Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"
        }
      }
    }
  ],
  "coverage": [
    {
      "id": "CV-001",
      "area": "Source specifications",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-02",
        "M-03",
        "M-04",
        "M-05",
        "M-07"
      ],
      "status": "assessed repeatedly from the same four document claims; repetitions are not independent confirmation",
      "limits": "All source documents are undated except DESIGN.md's alpha revision; authors unknown."
    },
    {
      "id": "CV-002",
      "area": "Identity, authorization, and sessions",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-03",
        "M-04",
        "M-07"
      ],
      "status": "threats and gaps assessed",
      "limits": "No link/session/Admin-bootstrap implementation or tests."
    },
    {
      "id": "CV-003",
      "area": "Privacy and personal-data flows",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-02",
        "M-03",
        "M-04",
        "M-07"
      ],
      "status": "audiences, intended disclosures, misuse paths, and lifecycle assessed",
      "limits": "Jurisdiction, transparency/intervention, provider fields, full copy inventory, readers, and backups unresolved."
    },
    {
      "id": "CV-004",
      "area": "Booking, payment, refund, and payout integrity",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-03",
        "M-04",
        "M-07"
      ],
      "status": "threats, failures, paths, and requirements assessed",
      "limits": "Provider contract, schema, transactions, idempotency, and tests absent."
    },
    {
      "id": "CV-005",
      "area": "Availability, staff updates, durable work",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-04",
        "M-07"
      ],
      "status": "timing/failure scenarios assessed",
      "limits": "Transport and execution unselected; no load/failure/restart tests."
    },
    {
      "id": "CV-006",
      "area": "Rendering and accessibility",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-01",
        "M-04",
        "M-07"
      ],
      "status": "specified interactions assessed",
      "limits": "No browser matrix, rendered app, or accessibility/security tests."
    },
    {
      "id": "CV-007",
      "area": "Implementation and runtime",
      "artifacts": [
        "E-REPO"
      ],
      "methods": [
        "M-06"
      ],
      "status": "not assessable; repository directly establishes absence of implementation artifacts",
      "limits": "This is independent repository evidence of absence, not proof of a vulnerability or of future implementation choices."
    },
    {
      "id": "CV-008",
      "area": "AI/ML lifecycle",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES",
        "E-AI",
        "E-REPO"
      ],
      "methods": [
        "M-05",
        "M-06"
      ],
      "status": "not applicable to documented first release; no AI/ML element in specifications or repository",
      "limits": "Reassess if AI/ML, LLM, retrieval, agent, or tool behavior is added."
    },
    {
      "id": "CV-009",
      "area": "Attack-path coverage",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-01",
        "M-03"
      ],
      "status": "18 conditional or assumption-marked paths retained",
      "limits": "No path-ranking evidence; all success depends on assumed control failure or unresolved implementation."
    },
    {
      "id": "CV-010",
      "area": "Risk prioritization",
      "artifacts": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-DES"
      ],
      "methods": [
        "M-00",
        "M-01",
        "M-02",
        "M-03",
        "M-04",
        "M-07"
      ],
      "status": "unresolved across all findings",
      "limits": "No approved common scale, mapping, appetite, factors, thresholds, ownership, or loss evidence."
    },
    {
      "id": "CV-011",
      "area": "Single-source conclusions",
      "status": "identified",
      "items": [
        "Repository artifact inventory/absence comes only from M-06 direct scan.",
        "AI taxonomy release inventories come only from M-05 external verification.",
        "LINDDUN intended-disclosure privacy framing comes only from M-02 although underlying facts are in requirements.",
        "Pre-confirmation cook-update field ambiguity was identified only by M-02.",
        "Document authors/date gaps and source visualization inventory are normalized only by M-07."
      ]
    },
    {
      "id": "CV-012",
      "area": "Unassessed areas",
      "status": "explicit",
      "items": [
        "Native workflows/platforms",
        "Deployment/runtime/network topology",
        "Operational identities and administrator access",
        "Secrets/build/release/CI",
        "Monitoring/incident response/backup/restore",
        "Legal compliance",
        "Implemented control effectiveness"
      ]
    }
  ],
  "conflicts": [
    {
      "id": "CF-001",
      "topic": "Node.js and Fastify technical roles",
      "values": [
        "Input labels Fastify as runtime and Node.js as framework.",
        "ARCHITECTURE.md proposes Node.js runtime with Fastify framework pending acceptance."
      ],
      "status": "unresolved",
      "source_refs": [
        "00:S00-CON-001",
        "01:CF-01",
        "02:L2-CON-001",
        "03:AT3-CON-001",
        "06:S06-CON-001",
        "07:DA7-CON-001"
      ],
      "evidence_ids": [
        "E-ARCH",
        "E-SEC"
      ]
    },
    {
      "id": "CF-002",
      "topic": "Candidate Node.js baselines",
      "values": [
        "Direct candidate Node.js 26.",
        "Several inactive candidate compositions include Node.js 24.",
        "Repository establishes no selected version."
      ],
      "status": "unresolved; candidate packs inactive",
      "source_refs": [
        "00:S00-CON-002",
        "01:CF-02",
        "06:S06-CON-002"
      ],
      "evidence_ids": [
        "E-SEC",
        "E-REPO"
      ]
    },
    {
      "id": "CF-003",
      "topic": "Control status terminology",
      "values": [
        "Requirements describe required behavior.",
        "Architecture confirms only gateway isolation and proposes most mechanisms.",
        "SECURITY.md blocks every secure-coding rule.",
        "Repository has no implementation artifacts."
      ],
      "status": "reconciled as status layers, not contradictory claims",
      "resolution": "Unified controls use implemented only for code/config evidence; none qualifies. Required, approved logical, proposed, and BLOCKED states remain distinct.",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH",
        "E-SEC",
        "E-REPO"
      ]
    },
    {
      "id": "CF-004",
      "topic": "Cook and shopper identity",
      "values": [
        "Some analyzer fragments combine cook/shopper as a staff actor.",
        "Requirements and document absorption define distinct assignments with different data fields."
      ],
      "status": "resolved within behavioral scope",
      "resolution": "Retain distinct ACT-004 Cook and ACT-005 Shopper; combined source references map to both.",
      "evidence_ids": [
        "E-REQ",
        "E-ARCH"
      ]
    }
  ],
  "gaps": [
    {
      "id": "G-001",
      "type": "evidence gap",
      "topic": "Implementation and control effectiveness",
      "missing": "Source, config, dependencies, schemas, tests, runtime/deployment artifacts, logs, observations.",
      "needed": "Implemented artifacts and scoped verification results.",
      "source_refs": [
        "00:S00-GAP-001",
        "01:G-10",
        "02:L2-G-008",
        "03:AT3-G-001",
        "04:G-01",
        "04:G-02",
        "06:S06-GAP-001",
        "07:DA7-G-002"
      ]
    },
    {
      "id": "G-002",
      "type": "decision/evidence gap",
      "topic": "Identity, session, Admin bootstrap, and authorization",
      "missing": "Link contents/expiry/reuse/revocation, session lifetime/revocation, first Admin provisioning, native credential transport, enforcement interfaces.",
      "needed": "Approved identity/session/Admin/authorization contract plus implementation/tests.",
      "source_refs": [
        "00:S00-GAP-002",
        "01:G-06",
        "02:L2-G-006",
        "03:AT3-G-007",
        "04:G-08",
        "07:DA7-G-004"
      ]
    },
    {
      "id": "G-003",
      "type": "decision/evidence gap",
      "topic": "Payment/email providers and data contracts",
      "missing": "Provider selection, fields, authenticity, browser return, reconciliation, idempotency, refund/payout/fees, delivery, retention, timing.",
      "needed": "Provider ADRs and authenticated interface/data-lifecycle contracts.",
      "source_refs": [
        "00:S00-GAP-003",
        "01:G-06",
        "02:L2-G-002",
        "03:AT3-G-003",
        "04:G-08",
        "07:DA7-G-005"
      ]
    },
    {
      "id": "G-004",
      "type": "decision/evidence gap",
      "topic": "Persistence, concurrency, durable execution, backup/restore",
      "missing": "Schema, relationships, constraints, transactions, locking, operation IDs, retry/reconciliation, scheduler, backup/restore/deletion behavior.",
      "needed": "Database/consistency design, durable-work contract, and recovery verification.",
      "source_refs": [
        "00:S00-GAP-004",
        "01:G-04",
        "03:AT3-G-004",
        "04:G-03",
        "07:DA7-G-007"
      ]
    },
    {
      "id": "G-005",
      "type": "decision/evidence gap",
      "topic": "Deployment, networks, secrets, operations, build/release",
      "missing": "Hosting/topology, network boundaries, secret provisioning, operational identities/access, containers/IaC, CI/release, monitoring, incident response.",
      "needed": "Deployment/network diagrams and operational/build/security runbooks.",
      "source_refs": [
        "00:S00-GAP-005",
        "01:G-03",
        "03:AT3-G-008",
        "04:G-04",
        "06:S06-GAP-003",
        "06:S06-GAP-004",
        "07:DA7-G-008"
      ]
    },
    {
      "id": "G-006",
      "type": "decision/evidence gap",
      "topic": "Technology versions and compatibility",
      "missing": "Resolved Node/Fastify roles/versions and React, React Native, language/toolchain, validation, auth, data-access, policy, container decisions.",
      "needed": "Approved version/compatibility decision record and eligible secure-coding provenance.",
      "source_refs": [
        "00:S00-GAP-006",
        "01:G-05",
        "06:S06-GAP-002",
        "07:DA7-G-003"
      ]
    },
    {
      "id": "G-007",
      "type": "decision/evidence gap",
      "topic": "Privacy lifecycle, transparency, intervention, and legal scope",
      "missing": "Jurisdictions/duties; private-note boundary; purposes/recipients/notices; correction/export; ineligible-cancellation withdrawal; copy/readers/derived/cache/export/backup deletion; nonfinancial/address retention.",
      "needed": "Authoritative legal applicability plus data inventory/classification, notice/consent, recipient, access, and retention/deletion matrices.",
      "source_refs": [
        "00:S00-GAP-007",
        "01:G-13",
        "02:L2-G-001",
        "02:L2-G-003",
        "02:L2-G-004",
        "02:L2-G-005",
        "03:AT3-G-005",
        "04:G-09",
        "07:DA7-G-010"
      ]
    },
    {
      "id": "G-008",
      "type": "specification gap",
      "topic": "Pre-confirmation cook update contents",
      "missing": "FR-4.1 requires a cook update when an order is placed; FR-4.5 enumerates named food-needs content only for confirmed orders.",
      "needed": "Explicit field-level projection for pre-confirmation cook updates.",
      "source_refs": [
        "02:L2-G-007"
      ],
      "evidence_ids": [
        "E-REQ"
      ]
    },
    {
      "id": "G-009",
      "type": "decision/evidence gap",
      "topic": "Staff update transport, replay, and timing",
      "missing": "Transport choice, paging/cursor/revision semantics, replay authorization, retry behavior, end-to-end load/reconnect/failure results.",
      "needed": "Approved protocol and load/reconnect/failure tests.",
      "source_refs": [
        "00:S00-GAP-008",
        "01:G-14",
        "03:AT3-G-002",
        "04:G-10",
        "07:DA7-G-009"
      ]
    },
    {
      "id": "G-010",
      "type": "decision/evidence gap",
      "topic": "Native, API, browser, and rendering scope",
      "missing": "API schemas/authorization declarations, native platforms/workflows/parity/link/storage/printing/accessibility, browsers/rendering/breakpoints and rendered validation.",
      "needed": "Versioned API, native scope, browser/rendering matrix, resolved DQ-1-DQ-3, and rendered tests.",
      "source_refs": [
        "00:S00-GAP-009",
        "01:G-07",
        "02:L2-G-009",
        "04:G-05",
        "07:DA7-G-006",
        "07:DA7-G-012"
      ]
    },
    {
      "id": "G-011",
      "type": "risk-method gap",
      "topic": "Risk and path prioritization/ownership",
      "missing": "Common likelihood/impact method, FMEA factors/scales, mappings, appetite, thresholds, loss data, path comparison, owners, deadlines.",
      "needed": "Approved risk method/mappings and ownership register.",
      "source_refs": [
        "00:S00-GAP-010",
        "01:G-01",
        "01:G-02",
        "01:G-12",
        "03:AT3-G-006",
        "04:G-07",
        "05:S05-GAP-003",
        "07:DA7-G-011"
      ]
    },
    {
      "id": "G-012",
      "type": "scope-change trigger",
      "topic": "Future AI/ML",
      "missing": "No implementation independently confirms specification-level absence forever; future AI/ML is not prohibited project-wide.",
      "needed": "Re-run lifecycle/taxonomy analysis if an AI/ML, LLM, retrieval, agent, or tool component is proposed.",
      "source_refs": [
        "05:S05-GAP-001",
        "05:S05-GAP-002"
      ]
    },
    {
      "id": "G-013",
      "type": "metadata gap",
      "topic": "Document provenance",
      "missing": "Authors and dates for all four specifications; editions for three; README has title only.",
      "needed": "Document ownership/revision metadata and useful repository setup/inventory documentation.",
      "source_refs": [
        "06:S06-GAP-005",
        "07:DA7-G-001"
      ]
    },
    {
      "id": "G-014",
      "type": "coverage gap",
      "topic": "Components with no implementation-level threat validation",
      "missing": "Every component, boundary, flow, and document-only control lacks code/config/runtime validation; mobile is not functionally assessed.",
      "needed": "Implementation artifacts tied to the unified component/flow IDs and targeted verification evidence.",
      "source_refs": [
        "06:S06-COV-001",
        "06:S06-COV-002",
        "06:S06-COV-003",
        "06:S06-COV-004",
        "06:S06-COV-005",
        "06:S06-COV-006",
        "06:S06-COV-008"
      ]
    }
  ]
}
```

### Appendix B — Diagram Specifications and Figure Briefs

#### B.1 Renderer-Neutral Source Specifications
#### Picky Party System Context

**Diagram ID:** `DGM-001`  
**Purpose:** Show the system, its people, providers, data exchanges, and trust crossings.  
**Audience:** Executives, Product, Security

##### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| SCP-001 | Picky Party first-release website | system scope | Modeled system | Threats: None; Controls: None |
| ACT-001 | Visitor | legitimate external actor | External to system | Threats: None; Controls: None |
| ACT-002 | Organizer | account role | External to system | Threats: None; Controls: None |
| ACT-003 | Attendee | account role | External to system | Threats: None; Controls: None |
| ACT-004 | Cook | event assignment | External to system | Threats: None; Controls: None |
| ACT-005 | Shopper | event assignment | External to system | Threats: None; Controls: None |
| ACT-006 | Admin | privileged role; first provisioning unresolved | External to system | Threats: None; Controls: None |
| ACT-007 | Payment service | external provider; selection unresolved | External to system | Threats: None; Controls: None |
| ACT-008 | Email service | external provider; selection unresolved | External to system | Threats: None; Controls: None |
| ACT-009 | Untrusted or unauthorized requester | generic threat agent | External to system | Threats: None; Controls: None |

##### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-001 | SCP-001 | bidirectional | Discover launched events (F-001); HTTP JSON proposed | Required public event data (D-002) | B-001, B-006 | Threats: T-023, T-024, T-026, T-031; Controls: C-003 |
| ACT-002 | SCP-001 | bidirectional | Organize events, review food needs, manage finance; HTTP JSON proposed | Personal, restricted, operational, and financial (D-001–D-007) | B-001, B-006 | Threats: T-014, T-015, T-019, T-028; Controls: C-002, C-003, C-004 |
| ACT-003 | SCP-001 | bidirectional | Order, checkout, attend, cancel; HTTP JSON proposed | Identity, food, booking, and finance (D-001,D-004–D-006) | B-001, B-006 | Threats: T-003, T-005, T-016, T-017; Controls: C-002, C-004, C-006 |
| ACT-004 | SCP-001 | bidirectional | Prepare assigned event food; HTTP JSON proposed | Restricted food and order data (D-004,D-005,D-007) | B-001, B-006 | Threats: T-010, T-025, T-028, T-041; Controls: C-002, C-003, C-008 |
| ACT-005 | SCP-001 | bidirectional | Shop for assigned event; HTTP JSON proposed | Restricted planning and update data (D-005,D-007) | B-001, B-006 | Threats: T-009, T-010, T-041, T-042; Controls: C-002, C-003, C-008 |
| ACT-006 | SCP-001 | bidirectional | Administer accounts, events, and finance; HTTP JSON proposed | Privileged personal, operational, and financial data (D-001–D-007) | B-001, B-006 | Threats: T-014, T-015, T-018, T-029; Controls: C-002, C-007, C-009 |
| SCP-001 | ACT-007 | bidirectional | Payment, callback, refund, payout, reconciliation (F-005,F-006); Unresolved | Non-public financial data (D-006) | B-003, B-004 | Threats: T-002, T-004, T-016, T-018; Controls: C-001, C-006, C-007 |
| SCP-001 | ACT-008 | outbound | Verification links and filtered notices (F-002,F-008); Unresolved | Access and audience-filtered notice data (D-001,D-007) | B-005 | Threats: T-013, T-020, T-022, T-044; Controls: C-001, C-011, C-013 |
| ACT-009 | SCP-001 | inbound | Requests; exact flow unresolved; HTTP JSON proposed | Request-dependent; unknown | B-001 | Threats: T-015, T-031; Controls: C-002, C-003 |

##### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-SYSTEM | Modeled system boundary | SCP-001 | B-001, B-003, B-004, B-005, B-006 | Logical scope only; deployment topology unresolved |

##### Annotations and ordering

- Use neutral threat markers; no comparable ordered rating exists.
- Payment and email are distinct external exchanges.

- Place SCP-001 centrally.
- Place people left, providers right, ACT-009 below.
- Do not merge payment and email crossings.

##### Legend

| Symbol or label | Meaning |
| --- | --- |
| solid box | modeled actor/system element |
| dashed boundary | trust boundary crossing |
| T-nnn | neutral threat reference; no severity implied |

##### Text preview

```text
People and generic requester -> [SCP-001 Picky Party] <-> payment provider
[SCP-001 Picky Party] -> email provider
```

##### Omissions

- Exact provider products, deployment/network topology, and native-client exchanges are unresolved.
- Protocol is known only as proposed HTTP JSON at the client boundary; provider protocols are unresolved.

##### Validation notes

- All external actors ACT-001–ACT-009 represented.
- All listed threat IDs exist; ranking intentionally omitted.

#### Picky Party Containers and Components

**Diagram ID:** `DGM-002`  
**Purpose:** Show logical client, application, persistence, payment, email, provider, and durable-work structure.  
**Audience:** Developers, Architects, Security

##### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| Z-001 | Untrusted web client | client zone | Client | Threats: T-015, T-045; Controls: C-012; Technology/status: ReactJS named; version unresolved |
| Z-002 | Native client | client zone | Client | Threats: None; Controls: C-012; Technology/status: React Native named; platforms/workflows unresolved |
| Z-003 | Trusted application | application zone | Application | Threats: None; Controls: C-002, C-005, C-008; Technology/status: Node.js/Fastify roles and versions unresolved |
| Z-004 | Persistence | data zone | Persistence | Threats: None; Controls: C-006, C-007, C-009, C-010; Technology/status: PostgreSQL proposed; decision unresolved |
| Z-005 | Isolated payment integration | gateway zone | Payment integration | Threats: T-002, T-016; Controls: C-001, C-006, C-007; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-006 | Separate email integration | gateway zone | Email integration | Threats: T-013, T-020; Controls: C-001, C-013; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-007 | External providers | external zone | Outside system | Threats: None; Controls: None; Technology/status: Providers unresolved |
| ACT-010 | Durable work dispatcher | proposed internal actor | Application; exact component unresolved | Threats: T-006, T-012, T-043; Controls: C-008; Technology/status: Unresolved |

##### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| Z-001/Z-002 | Z-003 | bidirectional | Client requests and responses; HTTP JSON proposed; native unresolved | Public through restricted (D-001–D-007) | B-001, B-006 | Threats: T-008, T-009, T-015; Controls: C-002, C-003, C-012 |
| Z-003 | Z-004 | bidirectional | State persistence; Unresolved | Personal, restricted, operational, financial (D-001,D-003–D-007) | B-002 | Threats: T-005; Controls: C-006, C-007, C-009, C-010 |
| Z-003 | Z-005 | bidirectional | Payment commands and validated results; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-005 | Z-007 | bidirectional | Payment provider operations; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-003 | Z-006 | outbound | Access and notice dispatch; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: T-009; Controls: C-001, C-013 |
| Z-006 | Z-007 | outbound | Email provider delivery; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: None; Controls: C-001, C-013 |
| ACT-010 | Z-003/Z-004/Z-005/Z-006 | internal/bidirectional | Scheduled, retry, reconciliation, notification work; Unresolved | Operational and financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-006, T-012, T-043; Controls: C-008 |

##### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

##### Annotations and ordering

- Dashed groups represent trust boundaries, not deployment networks.
- Technology labels preserve proposed/unresolved status.

- Clients left; application center; persistence below; payment and email gateways right; providers far right.
- Keep payment and email gateways separate.
- Place ACT-010 near application/persistence without implying a deployed service.

##### Legend

| Symbol or label | Meaning |
| --- | --- |
| solid box | logical zone or actor |
| dashed group | trust boundary |
| proposed/unresolved | evidence status, not implementation |

##### Text preview

```text
Z-001/Z-002 -> Z-003 <-> Z-004
Z-003 <-> Z-005 <-> Z-007
Z-003 -> Z-006 -> Z-007
ACT-010 -> Z-003/Z-004/Z-005/Z-006
```

##### Omissions

- No cache, queue, file store, concrete service split, endpoint list, or deployment node is specified.
- Exact technology versions and Node.js/Fastify roles are unresolved.

##### Validation notes

- Component names match model zones.
- Only confirmed payment/email logical separation is shown as confirmed; other placement remains proposed or unresolved.

#### Picky Party Data Flows

**Diagram ID:** `DGM-003`  
**Purpose:** Trace all nine modeled flows, their data classifications, protocols, and trust crossings.  
**Audience:** Security, Privacy, Developers, Auditors

##### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| Z-001 | Untrusted web client | client zone | Client | Threats: T-015, T-045; Controls: C-012; Technology/status: ReactJS named; version unresolved |
| Z-002 | Native client | client zone | Client | Threats: None; Controls: C-012; Technology/status: React Native named; platforms/workflows unresolved |
| Z-003 | Trusted application | application zone | Application | Threats: None; Controls: C-002, C-005, C-008; Technology/status: Node.js/Fastify roles and versions unresolved |
| Z-004 | Persistence | data zone | Persistence | Threats: None; Controls: C-006, C-007, C-009, C-010; Technology/status: PostgreSQL proposed; decision unresolved |
| Z-005 | Isolated payment integration | gateway zone | Payment integration | Threats: T-002, T-016; Controls: C-001, C-006, C-007; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-006 | Separate email integration | gateway zone | Email integration | Threats: T-013, T-020; Controls: C-001, C-013; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-007 | External providers | external zone | Outside system | Threats: None; Controls: None; Technology/status: Providers unresolved |
| ACT-010 | Durable work dispatcher | proposed internal actor | Application; exact component unresolved | Threats: T-006, T-012, T-043; Controls: C-008; Technology/status: Unresolved |

##### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| Z-003 | ACT-001 | outbound | Publish and discover (F-001); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | required public data for launched events | B-001, B-006 | Threats: T-012, T-023, T-024, T-026, T-031, T-036; Controls: C-003 |
| Z-003/Z-006/Z-007 | Z-001/Z-002 | outbound then inbound link use | Verify and sign in through email link (F-002); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | personal/access data; detailed classification unresolved | B-001, B-005 | Threats: T-001, T-013, T-022, T-035, T-044; Controls: C-011, C-013 |
| ACT-002/Z-003 | Z-001/Z-002 | bidirectional | Create event and expose exact location to authorized audiences (F-003); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | restricted audience | B-001, B-006 | Threats: T-003, T-014, T-027, T-036; Controls: C-002, C-003 |
| ACT-003/Z-003/Z-004 | ACT-002/ACT-004 via Z-003 | bidirectional | Submit, review, accept, and prepare food requests (F-004); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | private/audience-specific; exact boundary unresolved, non-public operational/account data | B-001, B-002, B-006 | Threats: T-003, T-014, T-025, T-028, T-037, T-041; Controls: C-002, C-003, C-004 |
| Z-001/Z-002/Z-003/Z-005 | Z-004/Z-007 | bidirectional including callback | Checkout, callback, validation, and booking confirmation (F-005); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | non-public operational/account data, non-public financial data; specified subset retained 24 months | B-001, B-002, B-003, B-004 | Threats: T-002, T-004, T-005, T-006, T-016, T-017, T-032, T-038, T-039; Controls: C-001, C-006 |
| Z-001/Z-002/Z-003/Z-005 | Z-004/Z-007 | bidirectional | Cancel, refund, reconcile, and pay out (F-006); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | non-public operational/account data, non-public financial data; specified subset retained 24 months, audience-filtered; nonfinancial retention unresolved | B-001, B-002, B-003, B-004, B-006 | Threats: T-003, T-004, T-006, T-007, T-012, T-013, T-014, T-018, T-020, T-033, T-040, T-043; Controls: C-001, C-007, C-008 |
| Z-003/Z-004 | ACT-004/ACT-005 via Z-001/Z-002 | outbound/replay | Staff update, polling, and reconnect replay (F-007); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | private/audience-specific; exact boundary unresolved, non-public operational/account data, audience-filtered; nonfinancial retention unresolved | B-001, B-002, B-006 | Threats: T-009, T-010, T-012, T-014, T-019, T-021, T-031, T-041, T-042; Controls: C-002, C-003, C-008, C-012 |
| Z-003/Z-004/Z-006 | ACT-008 and account client | outbound | Persist account notice and send filtered email (F-008); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | personal/access data; detailed classification unresolved, audience-filtered; nonfinancial retention unresolved | B-002, B-005, B-006 | Threats: T-009, T-013, T-019, T-020, T-044; Controls: C-001, C-003, C-013 |
| Z-003/ACT-010 | Z-004 | bidirectional/internal | Audit, delete private notes, and retain financial records (F-009); HTTP JSON proposed where B-001/B-006 applies; provider and persistence protocols unresolved | private/audience-specific; exact boundary unresolved, non-public financial data; specified subset retained 24 months, audience-filtered; nonfinancial retention unresolved | B-002, B-006 | Threats: T-006, T-007, T-011, T-012, T-019, T-029, T-030, T-034, T-043; Controls: C-008, C-009, C-010 |

##### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

##### Annotations and ordering

- Mark every D-003, D-004, D-006, and D-007 carrying flow as sensitive.
- F-001 public disclosure and F-003/F-004/F-009 privacy lifecycle distinctions must remain visible.

- Follow F-001 through F-009 top-to-bottom.
- Keep provider legs beside their gateway.
- Show B-006 response projection separately from B-001 request crossing.

##### Legend

| Symbol or label | Meaning |
| --- | --- |
| public | required public data D-002 |
| sensitive | restricted/personal/financial/audience-filtered data |
| dashed crossing | one or more B-nnn trust boundaries |

##### Text preview

```text
F-001 public discovery: application -> visitor
F-002 access: application -> email -> client -> application
F-003/F-004 audience data: account roles <-> application <-> persistence
F-005/F-006 finance: clients/application <-> persistence/payment
F-007/F-008 updates/notices: application -> staff/account/email
F-009 lifecycle: application/work dispatcher <-> persistence
```

##### Omissions

- Exact message schemas, provider protocols, persistence protocol, field-level pre-confirmation cook update projection, and native paths are unresolved.

##### Validation notes

- All F-001–F-009 and D-001–D-007 are represented.
- Sensitivity text is copied from model classifications; no new classification assigned.

#### Picky Party Threat-Annotated Architecture

**Diagram ID:** `DGM-004`  
**Purpose:** Overlay every stable threat ID on the architecture without implying a common severity.  
**Audience:** Security reviewers, Developers, Architects

##### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| Z-001 | Untrusted web client | client zone | Client | Threats: T-015, T-045; Controls: C-012; Technology/status: ReactJS named; version unresolved |
| Z-002 | Native client | client zone | Client | Threats: None; Controls: C-012; Technology/status: React Native named; platforms/workflows unresolved |
| Z-003 | Trusted application | application zone | Application | Threats: None; Controls: C-002, C-005, C-008; Technology/status: Node.js/Fastify roles and versions unresolved |
| Z-004 | Persistence | data zone | Persistence | Threats: None; Controls: C-006, C-007, C-009, C-010; Technology/status: PostgreSQL proposed; decision unresolved |
| Z-005 | Isolated payment integration | gateway zone | Payment integration | Threats: T-002, T-016; Controls: C-001, C-006, C-007; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-006 | Separate email integration | gateway zone | Email integration | Threats: T-013, T-020; Controls: C-001, C-013; Technology/status: Separate adapter/client/config required; implementation absent |
| Z-007 | External providers | external zone | Outside system | Threats: None; Controls: None; Technology/status: Providers unresolved |
| ACT-010 | Durable work dispatcher | proposed internal actor | Application; exact component unresolved | Threats: T-006, T-012, T-043; Controls: C-008; Technology/status: Unresolved |
| A-001 | Account identity and access records | asset annotation anchor | Placement unresolved | Threats: T-001, T-010, T-014, T-015, T-022, T-035, T-044; Controls: None; Technology/status: Not applicable / unresolved |
| A-002 | Events, addresses, assignments, URLs, dishes, recipes, and ingredients | asset annotation anchor | Placement unresolved | Threats: T-003, T-008, T-014, T-015, T-019, T-023, T-024, T-026, T-027, T-031, T-035, T-036; Controls: None; Technology/status: Not applicable / unresolved |
| A-003 | Orders, food needs, consent, proposals, accepted recipes, holds, and bookings | asset annotation anchor | Placement unresolved | Threats: T-002, T-003, T-004, T-005, T-006, T-008, T-009, T-010, T-011, T-014, T-015, T-016, T-017, T-019, T-021, T-025, T-028, T-030, T-031, T-032, T-034, T-035, T-036, T-037, T-038, T-039, T-041, T-042, T-043; Controls: None; Technology/status: Not applicable / unresolved |
| A-004 | Connected-account, payment, refund, payout, fee, and reconciliation records | asset annotation anchor | Placement unresolved | Threats: T-002, T-003, T-004, T-006, T-007, T-008, T-013, T-014, T-015, T-016, T-018, T-020, T-029, T-031, T-032, T-033, T-035, T-039, T-040, T-043; Controls: None; Technology/status: Not applicable / unresolved |
| A-005 | Staff updates, notices, delivery state, audit records, and pending work | asset annotation anchor | Placement unresolved | Threats: T-006, T-007, T-008, T-009, T-010, T-011, T-012, T-013, T-015, T-018, T-019, T-020, T-021, T-029, T-030, T-031, T-034, T-035, T-040, T-042, T-043, T-044; Controls: None; Technology/status: Not applicable / unresolved |
| A-006 | Presentation and transient client state | asset annotation anchor | Placement unresolved | Threats: T-021, T-042, T-045; Controls: None; Technology/status: Not applicable / unresolved |
| A-007 | Payment integration credentials and client configuration | asset annotation anchor | Z-005 | Threats: T-016, T-018, T-020, T-039, T-040; Controls: None; Technology/status: Not applicable / unresolved |
| A-008 | Email integration credentials and client configuration | asset annotation anchor | Z-006 | Threats: T-013, T-020, T-022, T-040, T-044; Controls: None; Technology/status: Not applicable / unresolved |

##### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| Z-001/Z-002 | Z-003 | bidirectional | Client requests and responses; HTTP JSON proposed; native unresolved | Public through restricted (D-001–D-007) | B-001, B-006 | Threats: T-008, T-009, T-015; Controls: C-002, C-003, C-012 |
| Z-003 | Z-004 | bidirectional | State persistence; Unresolved | Personal, restricted, operational, financial (D-001,D-003–D-007) | B-002 | Threats: T-005; Controls: C-006, C-007, C-009, C-010 |
| Z-003 | Z-005 | bidirectional | Payment commands and validated results; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-005 | Z-007 | bidirectional | Payment provider operations; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-003 | Z-006 | outbound | Access and notice dispatch; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: T-009; Controls: C-001, C-013 |
| Z-006 | Z-007 | outbound | Email provider delivery; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: None; Controls: C-001, C-013 |
| ACT-010 | Z-003/Z-004/Z-005/Z-006 | internal/bidirectional | Scheduled, retry, reconciliation, notification work; Unresolved | Operational and financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-006, T-012, T-043; Controls: C-008 |

##### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

##### Annotations and ordering

- Use one neutral T-nnn marker style for all threats.
- Place markers on A-nnn asset anchors because most asset placement is unresolved; do not infer a storage component.
- T-012/T-013 are availability/failure risks, not attacker assertions.
- T-023–T-029 intentional/required disclosures are privacy tradeoffs, not vulnerability findings.

- Reuse DGM-002 layout.
- Place A-001–A-006 in an unplaced asset rail; A-007 beside Z-005 and A-008 beside Z-006.
- Cluster threat markers by asset; use callouts to keep architecture readable.

##### Legend

| Symbol or label | Meaning |
| --- | --- |
| T-001 | Email-link or session impersonation |
| T-002 | Unauthenticated payment result accepted as provider evidence |
| T-003 | Client-controlled business transition |
| T-004 | Altered, late, duplicate, or replayed financial evidence |
| T-005 | Concurrent capacity corruption |
| T-006 | Duplicate or out-of-order work applies stale effects |
| T-007 | State change lacks attributable evidence |
| T-008 | Public or wrong-account projection exposes restricted data |
| T-009 | Shopper or email projection leaks restricted fields |
| T-010 | Removed staff retain current/replayed access |
| T-011 | Private food notes survive deletion/withdrawal |
| T-012 | Polling or durable work misses service targets |
| T-013 | Email failure delays access/notices or financial work |
| T-014 | Account exceeds ownership, assignment, role, or suspension scope |
| T-015 | Unauthorized actor reads or changes restricted records |
| T-016 | Untrusted or repeated payment evidence corrupts state |
| T-017 | Concurrent capacity changes misallocate a seat |
| T-018 | Repeated refund or payout exceeds authorized value |
| T-019 | Private notes or addresses leak through projection/copy |
| T-020 | Email integration failure controls financial work |
| T-021 | Lost, delayed, replayed, or stale staff updates |
| T-022 | Email access artifact permits impersonation |
| T-023 | Permanent URL enables longitudinal event correlation |
| T-024 | Public event identifies Organizer association |
| T-025 | Cook view links Attendee identity with food needs |
| T-026 | Public discovery reveals event existence/state |
| T-027 | Permitted audiences learn precise event location |
| T-028 | Food needs disclose personal circumstances to Organizer/cook |
| T-029 | Audit/financial history creates attributable long-term linkage |
| T-030 | Private-note copies outlive deletion lifecycle |
| T-031 | Obtain restricted data without audience entitlement |
| T-032 | Confirm booking without acceptable payment and valid hold |
| T-033 | Excess refund or duplicate payout |
| T-034 | Private note remains accessible after deletion/withdrawal |
| T-035 | Identity/authorization returns wrong decision |
| T-036 | Event publication or recipe snapshot invalid |
| T-037 | Food request/consent/acceptance/order state advances incorrectly |
| T-038 | Seat hold/capacity accounting inconsistent |
| T-039 | Payment result validated/reconciled/deduplicated incorrectly |
| T-040 | Refund/payout late, excessive, duplicate, or email-blocked |
| T-041 | Preparation/shopping output wrong or privacy-leaking |
| T-042 | Staff update/reconnect lost, stale, duplicate, or mis-scoped |
| T-043 | Durable work, audit, or retention incomplete |
| T-044 | Email access/notice fails without safe fallback |
| T-045 | Web presentation misstates state/value/error/staleness |

##### Text preview

```text
[Unplaced asset rail A-001–A-006 with neutral T-nnn markers]
Z-001/Z-002 -> Z-003 <-> Z-004
Z-003 <-> Z-005[A-007] <-> Z-007
Z-003 -> Z-006[A-008] -> Z-007
```

##### Omissions

- Component placement for A-001–A-006 is unresolved, so markers cannot be placed more specifically.
- No unified threat rating exists; no color, size, order, or emphasis implies severity.

##### Validation notes

- Every T-001–T-045 appears in the legend and at least one asset or boundary reference.
- Related methods remain distinct; no threat IDs are merged.

#### Picky Party Attack Surface

**Diagram ID:** `DGM-005`  
**Purpose:** Show all modeled entry points with authentication, authorization, and derived threat counts.  
**Audience:** Security reviewers, Developers, Auditors

##### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| EP-001 | Public calendar, event page, and QR URL | entry point | External-facing | Threats: T-012, T-023, T-024, T-026, T-031, T-036; Controls: C-003; Access: Public; no authentication required. Public-field projection C-003.; Threat count: 6 |
| EP-002 | Email verification/sign-in link | entry point | External-facing | Threats: T-001, T-013, T-022, T-035, T-044; Controls: C-011; Access: Possession of verification/sign-in artifact; lifecycle unresolved. Session control C-011.; Threat count: 5 |
| EP-003 | Authenticated views/actions | entry point | External-facing | Threats: T-003, T-004, T-006, T-007, T-009, T-010, T-011, T-012, T-013, T-014, T-018, T-019, T-020, T-021, T-025, T-027, T-028, T-029, T-030, T-031, T-033, T-034, T-035, T-036, T-037, T-040, T-041, T-042, T-043; Controls: C-002, C-003; Access: Authenticated. Ownership, role, suspension, and current assignment C-002; endpoints unspecified.; Threat count: 29 |
| EP-004 | Checkout browser flow | entry point | External-facing | Threats: T-002, T-004, T-005, T-006, T-016, T-017, T-032, T-038, T-039; Controls: C-002, C-006; Access: Authentication requirement not stated in the model. Order/hold and payment checks C-002/C-006.; Threat count: 9 |
| EP-005 | Payment callbacks/reconciliation | entry point | External-facing | Threats: T-002, T-003, T-004, T-005, T-006, T-007, T-012, T-013, T-014, T-016, T-017, T-018, T-020, T-032, T-033, T-038, T-039, T-040, T-043; Controls: C-001, C-006, C-007; Access: Provider-origin authentication protocol unresolved. Evidence/state authorization C-006/C-007.; Threat count: 19 |
| EP-006 | Email delivery gateway | entry point | Integration/internal | Threats: T-001, T-009, T-013, T-019, T-020, T-022, T-035, T-044; Controls: C-001, C-013; Access: Gateway/provider authentication unresolved. Isolation and filtered notices C-001/C-013.; Threat count: 8 |
| EP-007 | Scheduled/retry work | entry point | Integration/internal | Threats: T-003, T-004, T-006, T-007, T-009, T-011, T-012, T-013, T-014, T-017, T-018, T-019, T-020, T-029, T-030, T-033, T-034, T-038, T-040, T-043, T-044; Controls: C-007, C-008; Access: Operational identity unresolved. Eligibility, deduplication, and durable execution C-007/C-008.; Threat count: 21 |

##### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-001 | EP-001 | inbound | Public discovery; HTTP JSON proposed | Required public (D-002) | B-001, B-006 | Threats: T-012, T-023, T-024, T-026, T-031, T-036; Controls: C-003 |
| ACT-008/Z-001/Z-002 | EP-002 | email then inbound browser use | Verification/sign-in link; Email protocol and link lifecycle unresolved | Access data (D-001) | B-005, B-001 | Threats: T-001, T-013, T-022, T-035, T-044; Controls: C-011 |
| ACT-002/ACT-003/ACT-004/ACT-005/ACT-006 | EP-003 | bidirectional | Authenticated views and actions; HTTP JSON proposed | Restricted and financial (D-001,D-003–D-007) | B-001, B-006 | Threats: T-003, T-004, T-006, T-007, T-009, T-010, T-011, T-012, T-013, T-014, T-018, T-019, T-020, T-021, T-025, T-027, T-028, T-029, T-030, T-031, T-033, T-034, T-035, T-036, T-037, T-040, T-041, T-042, T-043; Controls: C-002, C-003 |
| ACT-003 | EP-004 | bidirectional | Checkout browser flow; Protocol unresolved | Booking and financial (D-005,D-006) | B-001, B-003 | Threats: T-002, T-004, T-005, T-006, T-016, T-017, T-032, T-038, T-039; Controls: C-002, C-006 |
| ACT-007 | EP-005 | inbound/bidirectional | Callbacks and reconciliation; Protocol/authenticity unresolved | Financial (D-006) | B-004 | Threats: T-002, T-003, T-004, T-005, T-006, T-007, T-012, T-013, T-014, T-016, T-017, T-018, T-020, T-032, T-033, T-038, T-039, T-040, T-043; Controls: C-001, C-006, C-007 |
| SCP-001 | EP-006/ACT-008 | outbound | Email delivery; Provider unresolved | Access and filtered notice (D-001,D-007) | B-005 | Threats: T-001, T-009, T-013, T-019, T-020, T-022, T-035, T-044; Controls: C-001, C-013 |
| ACT-010 | EP-007/SCP-001 | internal | Scheduled and retry work; Unresolved | Operational/financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-003, T-004, T-006, T-007, T-009, T-011, T-012, T-013, T-014, T-017, T-018, T-019, T-020, T-029, T-030, T-033, T-034, T-038, T-040, T-043, T-044; Controls: C-007, C-008 |

##### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-ENTRY | System entry boundary | EP-001, EP-002, EP-003, EP-004, EP-005, EP-006, EP-007 | B-001, B-003, B-004, B-005, B-006 | Entry points are logical; endpoint/protocol detail is incomplete |

##### Annotations and ordering

- Threat count equals distinct threats whose affected_ids contain the entry point or one of its flow_ids.
- Use equal neutral styling for every threat; counts do not imply severity.

- Order EP-001 through EP-007.
- Group public/user, provider, and internal-work entries without ranking them.

##### Legend

| Symbol or label | Meaning |
| --- | --- |
| EP-nnn | stable entry point ID |
| count | derived number of linked threats; not a score |
| T-nnn | neutral linked threat |

##### Text preview

```text
EP-001 Public calendar, event page, and QR URL: 6 linked threats
EP-002 Email verification/sign-in link: 5 linked threats
EP-003 Authenticated views/actions: 29 linked threats
EP-004 Checkout browser flow: 9 linked threats
EP-005 Payment callbacks/reconciliation: 19 linked threats
EP-006 Email delivery gateway: 8 linked threats
EP-007 Scheduled/retry work: 21 linked threats
```

##### Omissions

- Concrete API routes, upload/admin-panel endpoints, endpoint schemas, rate limits, provider authentication, operational identities, and native entry points are not specified.

##### Validation notes

- All EP-001–EP-007 represented.
- Counts are reproducible from affected entry point/flow IDs and do not create a risk ranking.

#### B.2 Publication Figure Briefs
#### Diagram Set

##### Figure 1: System Context (Executive View)

**Figure brief ID:** `FIG-001`  
**Source diagram:** `DGM-001`  
**Purpose:** Explain the product, people, providers, sensitive exchanges, and business-facing uncertainty without implementation detail.  
**Audience:** Decision makers, Product leadership, Customer security reviewers  
**Scope:** SCP-001, external actors ACT-001–ACT-009, core exchanges, and system boundary.

**Included model IDs:** SCP-001, ACT-001, ACT-002, ACT-003, ACT-004, ACT-005, ACT-006, ACT-007, ACT-008, ACT-009, B-001, B-003, B-004, B-005, B-006, F-001, F-002, F-005, F-006, F-008

**Intentionally omitted:** ACT-010, Z-001–Z-007, A-001–A-008, Internal implementation details

**Layout and hierarchy**

- Direction: Left to right
- Groups: People/requester, System, Payment and email providers
- Hierarchy: SCP-001 is primary; exchanges are secondary; neutral threat callouts are tertiary.
- Boundary regions: System boundary with B-001/B-003/B-004/B-005/B-006 crossing labels

**Annotations**

- Business effects only: account misuse, incorrect financial state, disclosure, delayed work.
- Payment and email remain visibly separate.
- No severity ranking.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT

**Alt text:** Executive context view with Picky Party centered, people and an untrusted requester on the left, and separate payment and email providers on the right. Public, restricted, and financial exchanges cross labeled trust boundaries. Neutral threat badges carry stable IDs without severity.

**Linear reading order:** Title and purpose, People and requester, System scope, Payment provider exchange, Email provider exchange, Boundary and threat legend

**Unresolved rendering decisions**

- Caller density limit and palette
- Page orientation
- Which four business-impact callouts fit the final medium

**Validation checks**

- All ACT-001–ACT-009 present
- Every connection has protocol/data text
- Payment/email paths are separate
- No rating cue

##### Figure 2: Container Architecture

**Figure brief ID:** `FIG-002`  
**Source diagram:** `DGM-002`  
**Purpose:** Show the complete logical container structure and technology/status evidence for architecture review.  
**Audience:** Developers, Architecture review board, Security architects  
**Scope:** Z-001–Z-007, ACT-010, B-001–B-006, and their specified connections.

**Included model IDs:** Z-001, Z-002, Z-003, Z-004, Z-005, Z-006, Z-007, ACT-010, B-001, B-002, B-003, B-004, B-005, B-006

**Intentionally omitted:** A-001–A-008 as placed data stores, Caches, queues, file stores, deployment nodes, and services not present in the model

**Layout and hierarchy**

- Direction: Left to right
- Groups: Clients, Application and persistence, Payment gateway, Email gateway, External providers
- Hierarchy: Clients feed the application; persistence is below it; gateways are separate peer branches; provider zone is last.
- Boundary regions: BG-CLIENT, BG-PERSIST, BG-PAY, BG-EMAIL

**Annotations**

- Technology status appears beneath each Z-nnn label.
- Use ? / dotted treatment for proposed or unresolved technologies.
- Logical isolation does not imply implementation.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-DATA, ST-GATEWAY, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT, ST-CONTROL

**Alt text:** Architecture view with web and unresolved native clients at left, the trusted application in the center above persistence, separate payment and email gateway hexagons to the right, external providers at far right, and a proposed durable-work actor near application and persistence.

**Linear reading order:** Title, Client group, Application, Persistence, Durable work, Payment branch, Email branch, External providers, Legend

**Unresolved rendering decisions**

- Caller palette and page width
- Final wrapping of long technology labels
- Whether external providers need separate product boxes once providers are selected

**Validation checks**

- Names and technology statuses match DGM-002
- No cache/queue/service invented
- All B-001–B-006 crossings trace
- Gateway isolation status says logical/implementation absent

##### Figure 3: Data Flow Diagram

**Figure brief ID:** `FIG-003`  
**Source diagram:** `DGM-003`  
**Purpose:** Trace F-001–F-009 with classifications, protocols, controls, and trust crossings.  
**Audience:** Security reviewers, Privacy reviewers, Developers, Auditors  
**Scope:** All modeled data D-001–D-007 and flows F-001–F-009.

**Included model IDs:** F-001, F-002, F-003, F-004, F-005, F-006, F-007, F-008, F-009, D-001, D-002, D-003, D-004, D-005, D-006, D-007, B-001, B-002, B-003, B-004, B-005, B-006

**Intentionally omitted:** Field schemas, Native-specific flows, Unspecified provider and persistence protocols

**Layout and hierarchy**

- Direction: Top to bottom
- Groups: Public and access flows, Event/food flows, Finance flows, Updates/notices/lifecycle flows
- Hierarchy: Each numbered flow is one horizontal swim lane; components repeat as lane participants rather than creating new identities.
- Boundary regions: B-001/B-006 client crossing, B-002 persistence crossing, B-003/B-004 payment crossing, B-005 email crossing

**Annotations**

- Apply P only to F-001 public data.
- Apply S to flows carrying D-003,D-004,D-006,or D-007.
- Show exact D-nnn, B-nnn, T-nnn, and C-nnn references.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-DATA, ST-GATEWAY, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT, ST-CONTROL

**Alt text:** Nine horizontal swim lanes show public discovery, access email, location, food request, checkout, finance, updates, notices, and lifecycle flows. Each lane names data classifications, unresolved protocols, controls, threats, and dashed boundary crossings.

**Linear reading order:** Title and legend, F-001 through F-009 in numeric order, Data and control callouts per lane, Omissions note

**Unresolved rendering decisions**

- Page size may require two panels while retaining one figure number
- Caller palette
- Label wrapping for F-006 and F-009

**Validation checks**

- Every F-001–F-009 appears once
- Every D-001–D-007 appears
- Sensitive tags match classifications
- Boundary IDs match each source flow
- No inferred protocol

##### Figure 4: Threat-Annotated Architecture (Security View)

**Figure brief ID:** `FIG-004`  
**Source diagram:** `DGM-004`  
**Purpose:** Place every T-001–T-045 on supported asset or boundary anchors while keeping the architecture legible.  
**Audience:** Security teams, Penetration-test planners, Developers  
**Scope:** DGM-002 architecture plus A-001–A-008 anchors and all 45 methodology-specific threats.

**Included model IDs:** Z-001, Z-002, Z-003, Z-004, Z-005, Z-006, Z-007, A-001, A-002, A-003, A-004, A-005, A-006, A-007, A-008, T-001, T-002, T-003, T-004, T-005, T-006, T-007, T-008, T-009, T-010, T-011, T-012, T-013, T-014, T-015, T-016, T-017, T-018, T-019, T-020, T-021, T-022, T-023, T-024, T-025, T-026, T-027, T-028, T-029, T-030, T-031, T-032, T-033, T-034, T-035, T-036, T-037, T-038, T-039, T-040, T-041, T-042, T-043, T-044, T-045, B-001, B-002, B-003, B-004, B-005, B-006

**Intentionally omitted:** Risk colors, severity order, exploit claims, and implementation findings

**Layout and hierarchy**

- Direction: Left to right with lower asset rail
- Groups: Architecture base, Unplaced asset rail A-001–A-006, Gateway assets A-007/A-008, Threat callout gutter
- Hierarchy: Architecture remains primary; grouped neutral badges are secondary; full threat legend is a side panel.
- Boundary regions: Same BG-CLIENT/BG-PERSIST/BG-PAY/BG-EMAIL regions as Figure 2

**Annotations**

- All T-nnn markers have equal visual weight.
- T-012/T-013 carry AVAILABILITY/FAILURE captions.
- T-023–T-029 carry PRIVACY TRADEOFF captions.
- Method records remain separate even when cross-linked.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-DATA, ST-GATEWAY, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT, ST-CONTROL, ST-PRIVACY

**Alt text:** The architecture from Figure 2 is overlaid with equal neutral threat badges. Assets whose component placement is unresolved appear in a lower rail. Availability/failure and intentional privacy-tradeoff records have explicit captions. A side legend maps all T-001 through T-045 to titles.

**Linear reading order:** Title, Architecture base, Asset rail, Boundary callouts, Threat clusters, Full T-nnn legend, Unresolved-placement note

**Unresolved rendering decisions**

- Final callout pagination
- Caller palette
- Whether full threat legend sits beside or immediately after the figure

**Validation checks**

- Every T-001–T-045 appears at least once and in legend
- No color/order implies severity
- A-001–A-006 remain unplaced
- T-023–T-029 not labeled vulnerabilities
- T-012/T-013 not framed as attacks

##### Figure 5: Data Flow with Supplied Requirement Annotations

**Figure brief ID:** `FIG-005`  
**Source diagram:** `DGM-003`  
**Purpose:** Show exact sourced requirement groups on the data flows they connect to through explicit model threat mappings; this is not a compliance verdict.  
**Audience:** Requirements reviewers, Security architects, Auditors  
**Scope:** F-001–F-009, RQ-001–RQ-011, their exact source IDs, and explicit RQ→T→F trace.

**Included model IDs:** F-001, F-002, F-003, F-004, F-005, F-006, F-007, F-008, F-009, RQ-001, RQ-002, RQ-003, RQ-004, RQ-005, RQ-006, RQ-007, RQ-008, RQ-009, RQ-010, RQ-011, T-001, T-002, T-003, T-004, T-005, T-006, T-007, T-008, T-009, T-010, T-011, T-012, T-013, T-014, T-015, T-016, T-017, T-018, T-019, T-020, T-021, T-022, T-023, T-024, T-025, T-026, T-027, T-028, T-029, T-030, T-031, T-032, T-033, T-034, T-035, T-036, T-037, T-038, T-039, T-040, T-041, T-042, T-043, T-044, T-045

**Intentionally omitted:** Legal scope, Compliance status, Requirements with no explicit RQ→T→F trace

**Layout and hierarchy**

- Direction: Top to bottom
- Groups: Flow lanes from Figure 3, Requirement callout column, Exact source-ID key
- Hierarchy: Flows remain primary; RQ tags attach through callouts; exact FR/NFR/architecture/design sources appear in the side key.
- Boundary regions: Reuse Figure 3 boundary regions

**Annotations**

- `F-001`: {"flow_id":"F-001","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-031"]},{"requirement_id":"RQ-002","source_ids":["FR-1","FR-2","FR-5","FR-7.8","FR-7.9"],"via_threat_ids":["T-036"]},{"requirement_id":"RQ-007","source_ids":["FR-4.1 through FR-4.11","NFR-1.1 through NFR-1.3","NFR-3.6"],"via_threat_ids":["T-012"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-002`: {"flow_id":"F-002","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-035"]},{"requirement_id":"RQ-005","source_ids":["FR-9","NFR-1.5"],"via_threat_ids":["T-013"]},{"requirement_id":"RQ-008","source_ids":["FR-4.12 through FR-4.14","FR-6.2 through FR-6.4"],"via_threat_ids":["T-001","T-013","T-022","T-044"]},{"requirement_id":"RQ-010","source_ids":["ARCHITECTURE §2","ARCHITECTURE §8","DR-9"],"via_threat_ids":["T-013","T-044"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-003`: {"flow_id":"F-003","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-014"]},{"requirement_id":"RQ-002","source_ids":["FR-1","FR-2","FR-5","FR-7.8","FR-7.9"],"via_threat_ids":["T-003","T-036"]},{"requirement_id":"RQ-003","source_ids":["FR-3","FR-11.7"],"via_threat_ids":["T-003"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-004`: {"flow_id":"F-004","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-014"]},{"requirement_id":"RQ-002","source_ids":["FR-1","FR-2","FR-5","FR-7.8","FR-7.9"],"via_threat_ids":["T-003"]},{"requirement_id":"RQ-003","source_ids":["FR-3","FR-11.7"],"via_threat_ids":["T-003","T-025","T-028","T-037"]},{"requirement_id":"RQ-006","source_ids":["FR-4.5 through FR-4.8","FR-10","NFR-2.3"],"via_threat_ids":["T-025","T-028","T-041"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-005`: {"flow_id":"F-005","requirements":[{"requirement_id":"RQ-004","source_ids":["FR-8","NFR-2.2"],"via_threat_ids":["T-002","T-004","T-005","T-016","T-017","T-032","T-038","T-039"]},{"requirement_id":"RQ-005","source_ids":["FR-9","NFR-1.5"],"via_threat_ids":["T-004","T-006"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-006`: {"flow_id":"F-006","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-014"]},{"requirement_id":"RQ-002","source_ids":["FR-1","FR-2","FR-5","FR-7.8","FR-7.9"],"via_threat_ids":["T-003"]},{"requirement_id":"RQ-003","source_ids":["FR-3","FR-11.7"],"via_threat_ids":["T-003"]},{"requirement_id":"RQ-004","source_ids":["FR-8","NFR-2.2"],"via_threat_ids":["T-004"]},{"requirement_id":"RQ-005","source_ids":["FR-9","NFR-1.5"],"via_threat_ids":["T-004","T-006","T-013","T-018","T-020","T-033","T-040"]},{"requirement_id":"RQ-007","source_ids":["FR-4.1 through FR-4.11","NFR-1.1 through NFR-1.3","NFR-3.6"],"via_threat_ids":["T-012"]},{"requirement_id":"RQ-008","source_ids":["FR-4.12 through FR-4.14","FR-6.2 through FR-6.4"],"via_threat_ids":["T-013","T-020"]},{"requirement_id":"RQ-009","source_ids":["FR-11.3 through FR-11.7","NFR-2.1"],"via_threat_ids":["T-007","T-043"]},{"requirement_id":"RQ-010","source_ids":["ARCHITECTURE §2","ARCHITECTURE §8","DR-9"],"via_threat_ids":["T-013","T-020","T-040"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-007`: {"flow_id":"F-007","requirements":[{"requirement_id":"RQ-001","source_ids":["FR-2.12","FR-6.6 through FR-6.16","FR-11.1","FR-11.2"],"via_threat_ids":["T-010","T-014","T-031","T-042"]},{"requirement_id":"RQ-006","source_ids":["FR-4.5 through FR-4.8","FR-10","NFR-2.3"],"via_threat_ids":["T-009","T-041"]},{"requirement_id":"RQ-007","source_ids":["FR-4.1 through FR-4.11","NFR-1.1 through NFR-1.3","NFR-3.6"],"via_threat_ids":["T-010","T-012","T-021","T-042"]},{"requirement_id":"RQ-008","source_ids":["FR-4.12 through FR-4.14","FR-6.2 through FR-6.4"],"via_threat_ids":["T-009"]},{"requirement_id":"RQ-009","source_ids":["FR-11.3 through FR-11.7","NFR-2.1"],"via_threat_ids":["T-019"]},{"requirement_id":"RQ-011","source_ids":["NFR-3","DESIGN Components","DESIGN Do's and Don'ts"],"via_threat_ids":["T-021","T-042"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-008`: {"flow_id":"F-008","requirements":[{"requirement_id":"RQ-005","source_ids":["FR-9","NFR-1.5"],"via_threat_ids":["T-013","T-020"]},{"requirement_id":"RQ-006","source_ids":["FR-4.5 through FR-4.8","FR-10","NFR-2.3"],"via_threat_ids":["T-009"]},{"requirement_id":"RQ-008","source_ids":["FR-4.12 through FR-4.14","FR-6.2 through FR-6.4"],"via_threat_ids":["T-009","T-013","T-020","T-044"]},{"requirement_id":"RQ-009","source_ids":["FR-11.3 through FR-11.7","NFR-2.1"],"via_threat_ids":["T-019"]},{"requirement_id":"RQ-010","source_ids":["ARCHITECTURE §2","ARCHITECTURE §8","DR-9"],"via_threat_ids":["T-013","T-020","T-044"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- `F-009`: {"flow_id":"F-009","requirements":[{"requirement_id":"RQ-005","source_ids":["FR-9","NFR-1.5"],"via_threat_ids":["T-006"]},{"requirement_id":"RQ-007","source_ids":["FR-4.1 through FR-4.11","NFR-1.1 through NFR-1.3","NFR-3.6"],"via_threat_ids":["T-012"]},{"requirement_id":"RQ-009","source_ids":["FR-11.3 through FR-11.7","NFR-2.1"],"via_threat_ids":["T-007","T-011","T-019","T-029","T-030","T-034","T-043"]}],"derivation":"Explicit RQ threat_ids intersect explicit threat affected_ids for this flow."}
- Association is derived from explicit model links and does not assert that a requirement directly names the flow.
- No pass/fail or compliance badge.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-DATA, ST-GATEWAY, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT, ST-CONTROL, ST-REQUIREMENT

**Alt text:** The nine data-flow lanes from Figure 3 include square RQ-nnn tags. A side key expands each requirement group to exact FR, NFR, architecture, or design source IDs and lists the T-nnn links that connect it to each flow. No compliance result is shown.

**Linear reading order:** Title and non-verdict note, F-001 through F-009, RQ tags per lane, Exact requirement source key, Trace rule, Legend

**Unresolved rendering decisions**

- Page width and callout wrapping
- Caller palette
- Whether source key is beside or beneath figure

**Validation checks**

- Every annotation has an RQ→T→F trace
- Exact source_ids preserved verbatim
- All RQ-001–RQ-011 appear where traced
- No legal/compliance inference

##### Figure 6: Attack Surface Map

**Figure brief ID:** `FIG-006`  
**Source diagram:** `DGM-005`  
**Purpose:** Show EP-001–EP-007 with access model, controls, and reproducible neutral threat counts.  
**Audience:** Security reviewers, Developers, Auditors  
**Scope:** All modeled entry points and their actor/system relationships.

**Included model IDs:** EP-001, EP-002, EP-003, EP-004, EP-005, EP-006, EP-007, T-001, T-002, T-003, T-004, T-005, T-006, T-007, T-008, T-009, T-010, T-011, T-012, T-013, T-014, T-015, T-016, T-017, T-018, T-019, T-020, T-021, T-022, T-023, T-024, T-025, T-026, T-027, T-028, T-029, T-030, T-031, T-032, T-033, T-034, T-035, T-036, T-037, T-038, T-039, T-040, T-041, T-042, T-043, T-044, T-045, C-001, C-002, C-003, C-004, C-005, C-006, C-007, C-008, C-009, C-010, C-011, C-012, C-013, C-014, C-015, C-016, C-017, C-018, C-019, C-020, C-021, C-022, C-023

**Intentionally omitted:** Unspecified API routes, Uploads, Admin-panel routes, Native-only entries, Rate limits

**Layout and hierarchy**

- Direction: Left to right
- Groups: Public/user entries, Provider entries, Internal scheduled work
- Hierarchy: Entry points are peers; threat count is metadata and never controls size, color, or order.
- Boundary regions: Single system-entry boundary labeled with B-001/B-003/B-004/B-005/B-006

**Annotations**

- Show authentication/authorization text beneath each EP-nnn.
- Threat counts use equal typography and are explicitly not scores.
- Use ? on unresolved provider authentication and operational identity.

**Style and legend tokens:** ST-ACTOR, ST-COMPONENT, ST-DATA, ST-GATEWAY, ST-BOUNDARY, ST-PUBLIC, ST-SENSITIVE, ST-UNRESOLVED, ST-THREAT, ST-CONTROL

**Alt text:** Seven equally styled entry-point cards show public discovery, email sign-in, authenticated actions, checkout, payment callbacks, email delivery, and scheduled work. Each card names authentication and authorization evidence, controls, linked T-nnn IDs, and a threat count that is not a score.

**Linear reading order:** Title and count rule, EP-001–EP-004 user-facing group, EP-005–EP-006 provider group, EP-007 internal-work group, Legend and omissions

**Unresolved rendering decisions**

- Caller palette
- Landscape or two-row arrangement
- Card height needed for EP-003 and EP-007 text

**Validation checks**

- All EP-001–EP-007 present
- Counts match explicit entry/flow references
- Equal styling irrespective of count
- Unknown auth stays unknown

##### Sequence View Disposition

No sequence figure is emitted. The supplied model has no approved comparable rating method or other assessment that selects a data flow for emphasis. Selecting one would invent prioritization. Authentication checkpoints and boundary crossings remain documented in Figures 3, 5, and 6.

##### Layout Specifications

###### Figure 1: System Context (Executive View)

- Positions, sizes, types: Actors: equal 1.5×0.55 units left, SCP-001: 3.0×2.2 units center, Providers: equal 1.7×0.8 units right
- Connections: Orthogonal arrows; place protocol and data on one line where possible, Use P or S tags on every exchange, Crossings intersect the dashed system boundary once
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

###### Figure 2: Container Architecture

- Positions, sizes, types: Z-001/Z-002: 1.8×0.9 units left stack, Z-003: 2.3×1.2 center, Z-004: 2.3×1.0 below Z-003 cylinder, Z-005/Z-006: 1.9×1.0 right stack hexagons, Z-007: 2.0×1.4 far right, ACT-010: 1.8×0.7 below-left of Z-003
- Connections: Orthogonal lines with arrowheads, Separate parallel payment/email paths, Internal work path dotted because implementation is proposed
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

###### Figure 3: Data Flow Diagram

- Positions, sizes, types: Nine equal-height swim lanes; 0.7–0.9 units each, Participant columns fixed across lanes, Legend in lower-right margin
- Connections: Straight left-to-right arrows within each lane, Dashed vertical dividers for boundaries, Return/callback arrows offset below request arrows
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

###### Figure 4: Threat-Annotated Architecture (Security View)

- Positions, sizes, types: Reuse Figure 2 positions exactly, A-001–A-006: six equal tagged boxes in lower rail, A-007 adjacent Z-005; A-008 adjacent Z-006, Threat legend: two columns, 9 pt minimum
- Connections: Reuse Figure 2 connections, Leader lines from badges to anchors; no arrow semantics, Bundle related callouts without merging IDs
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

###### Figure 5: Data Flow with Supplied Requirement Annotations

- Positions, sizes, types: Reuse Figure 3 lanes, Requirement tags: 0.45×0.3 units at lane right, Source key: 35–40% page width or full-width continuation panel
- Connections: Reuse Figure 3 paths, Thin leader lines from RQ tags to flow lanes, Do not route requirement leaders across data arrows
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

###### Figure 6: Attack Surface Map

- Positions, sizes, types: Seven equal-width cards, minimum 1.8×1.3 units, Arrange 4 cards top row, 3 bottom row or one horizontal strip, System boundary behind cards, not around external actors
- Connections: Straight actor-to-card-to-system paths, Provider callback uses inbound arrow, Internal work uses dotted path
- Boundaries: Use ST-BOUNDARY: labeled 2 pt dashed regions; never use shading alone.
- Rating tokens: None. The model has no comparable ordered rating scheme; all T-nnn markers use ST-THREAT at equal weight.
- Typography: {"title":"18–22 pt semibold","section":"14–16 pt semibold","component":"11–12 pt medium","relationship":"9–10 pt; wrap once at most","annotation":"9–10 pt minimum","font":"Caller-approved accessible sans serif; preserve T-nnn, C-nnn, RQ-nnn exactly"}

##### Diagram Legend

| Token | Use | Shape | Color role | Required non-color cue |
| --- | --- | --- | --- | --- |
| ST-ACTOR | External actor | Rounded rectangle with actor glyph and ACT-nnn label | Caller-approved neutral | Actor glyph + rounded border |
| ST-COMPONENT | Internal component/zone | Solid rectangle with Z-nnn label | Caller-approved neutral | Solid border + component label |
| ST-DATA | Persistence/data asset | Cylinder for Z-004; tagged rectangle for A-nnn anchors | Caller-approved neutral | Cylinder or A tag |
| ST-GATEWAY | Payment/email gateway | Hexagon with Z-005/Z-006 label | Caller-approved distinct neutrals | Hexagon + PAYMENT/EMAIL text |
| ST-BOUNDARY | Trust boundary | Region | Caller-approved low-contrast tint | 2 pt dashed border + B-nnn label |
| ST-PUBLIC | Required public flow | Directed line | Caller-approved neutral | P tag + solid line |
| ST-SENSITIVE | Restricted/personal/financial flow | Directed line | Caller-approved accent | S tag + 2 pt line |
| ST-UNRESOLVED | Unresolved/proposed detail | Callout or border | Caller-approved neutral | Dotted border + ? label |
| ST-THREAT | Threat reference | Circular T-nnn badge | Single caller-approved neutral for all threats | T-nnn text; equal size/weight |
| ST-PRIVACY | Intentional/required privacy tradeoff T-023–T-029 | Circular T-nnn badge with PRIVACY TRADEOFF caption | Same neutral as threats | Caption; no vulnerability or severity implication |
| ST-CONTROL | Control reference | C-nnn text tag | Caller-approved neutral | C prefix + status text |
| ST-REQUIREMENT | Requirement annotation | RQ-nnn square tag | Caller-approved neutral | RQ prefix + square border |

All tokens require caller approval at render time. The renderer must retain the listed label, shape, border, or line-pattern cue so color is never the sole carrier of meaning. No style token expresses threat severity because the model provides no comparable ordered rating scheme.

### Appendix C — Automation and Evidence-Coverage Summary

- Stages 00–04 completed STRIDE, PASTA, LINDDUN, attack-tree, and FMEA analysis from the supplied specifications.
- Stage 05 checked the documented lifecycle against the named AI/ML taxonomies and recorded Not applicable; no AI/ML threats were created.
- Stage 06 directly scanned the repository and found no implementation to analyze.
- Stage 07 normalized the four documents; stage 08 consolidated 45 stable threats; stages 09–10 produced renderer-neutral diagram specifications and figure briefs.
- Coverage records `CV-001`–`CV-012`, conflicts `CF-001`–`CF-004`, and gaps `G-001`–`G-014` remain authoritative in Appendix A.

### Appendix D — Repository Analysis Findings

Stage 06 recorded eight root files at scan time: seven Markdown documents and one SVG. It found no source, dependency manifest, lockfile, schema, tests, runtime configuration, CI, container, infrastructure-as-code, or deployment artifact. Consequently, repository-level vulnerability, control-presence, and control-effectiveness assessment was Not applicable. This is evidence of absence in the scanned repository, not proof of a vulnerability or future architecture.

### Appendix E — Document Sources Reviewed

| Evidence | Document | Role | Provenance limits |
| --- | --- | --- | --- |
| `E-REQ` | `REQUIREMENTS.md` | Behavioral authority | Revision/date/author not supplied; assumptions are intended behavior, not implementation. |
| `E-ARCH` | `ARCHITECTURE.md` | Logical architecture | Payment/email isolation confirmed logically; most mechanisms proposed/unresolved. |
| `E-SEC` | `SECURITY.md` | Security decisions/status | `SC-001`–`SC-009` BLOCKED; no active secure-coding composition. |
| `E-DES` | `DESIGN.md` | Interaction/rendering specification | Alpha design intent; no rendered implementation. |
| `E-REPO` | Repository inventory | Direct artifact inventory | Scan date 2026-10-19; no implementation artifacts found. |
| `E-AI` | AI/ML taxonomy verification | Method provenance | Applicability review only; current scope Not applicable. |

### Appendix F — Glossary

| Term | Meaning in this report |
| --- | --- |
| BLOCKED | A security rule cannot be activated until its named decisions/evidence are resolved. It is not implemented. |
| Claimed/required behavior | A document statement; not code/config/runtime evidence. |
| Evidence gap | Required evidence is missing; absence does not prove a vulnerability. |
| Privacy tradeoff | An intentional or required disclosure/correlation property assessed by LINDDUN; not automatically a vulnerability. |
| Threat | A methodology-specific scenario or failure record with a stable `T-nnn` ID. |
| Unified rating | A common risk result. None was computed because no approved common method/mapping exists. |
| Verified | Effectiveness demonstrated by evidence. No control in this model is verified. |



