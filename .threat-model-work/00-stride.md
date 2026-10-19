# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "S00-SCOPE-001",
    "system": "Picky Party first-release cooking-event website specification",
    "in_scope": [
      "Public event discovery and permanent event URLs/QR codes.",
      "Verified-email accounts; Organizer, Attendee, and Admin capabilities; event-scoped cook and shopper assignments.",
      "Event, recipe, food-request, booking, payment, refund, payout, staff-update, ingredient-planning, audit, and retention workflows.",
      "Specified logical web, application, persistence, payment, and email boundaries, retaining each boundary's CONFIRMED, PROPOSED, UNKNOWN, or TO BE DECIDED status."
    ],
    "exclusions_verbatim": "The first release supports English and USD. Group bookings, extra portions, offline payments, waitlists, discounts, and automatic dietary certification are outside its scope.",
    "additional_limits": [
      "Native-app scope is unresolved and is not added to the required web workflows.",
      "Deployment topology remains outside ARCHITECTURE.md's requested scope and is UNKNOWN.",
      "No application implementation exists; no control is treated as implemented or effective."
    ]
  },
  "evidence": [
    {
      "id": "S00-E-001",
      "artifact": "REQUIREMENTS.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Required Requirement Inputs", "Product Rules and Terms", "FR-1.1–FR-11.7", "NFR-1.1–NFR-3.6", "Open Questions"],
      "kind": "requirements and adopted assumptions",
      "limits": "Requirements and numerical targets are product decisions, not measured results; external facts remain UNKNOWN."
    },
    {
      "id": "S00-E-002",
      "artifact": "ARCHITECTURE.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["§1–§12", "Required Architecture Inputs", "AQ-1–AQ-8"],
      "kind": "architecture with CONFIRMED, PROPOSED, UNKNOWN, and TO BE DECIDED statements",
      "limits": "This is a design for a system with no implementation; most mechanisms are proposed or unresolved."
    },
    {
      "id": "S00-E-003",
      "artifact": "SECURITY.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Secure-Coding Inputs", "SC-001–SC-009", "OD-001–OD-012"],
      "kind": "security-rule status and open decisions",
      "limits": "All secure-coding rules are BLOCKED; no candidate prompt is active and no external support is independently verified."
    },
    {
      "id": "S00-E-004",
      "artifact": "DESIGN.md",
      "revision": "alpha",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Overview", "Components", "Do's and Don'ts", "DQ-1–DQ-3"],
      "kind": "visual and interaction design",
      "limits": "Visual choices are assumptions; behavior is owned by REQUIREMENTS.md; no implementation exists."
    }
  ],
  "system": {
    "assets": [
      {"id": "S00-AST-001", "name": "Identity and authorization integrity", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
      {"id": "S00-AST-002", "name": "Private event and food-needs confidentiality", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-004"]},
      {"id": "S00-AST-003", "name": "Capacity, order, booking, and recipe integrity", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-AST-004", "name": "Payment, refund, payout, and financial-record integrity", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-AST-005", "name": "Required availability and durable state", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-AST-006", "name": "Auditability and retention obligations", "evidence_ids": ["S00-E-001", "S00-E-002"]}
    ],
    "actors": [
      {"id": "S00-ACT-001", "name": "Visitor", "trust": "untrusted external actor", "evidence_ids": ["S00-E-002"]},
      {"id": "S00-ACT-002", "name": "Organizer", "trust": "authenticated ownership-scoped account actor", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-ACT-003", "name": "Attendee", "trust": "authenticated own-record account actor", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-ACT-004", "name": "Cook / shopper", "trust": "verified account with current event-scoped assignment and audience", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-ACT-005", "name": "Admin", "trust": "privileged account role with Admin-controlled grants", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-ACT-006", "name": "Payment service", "trust": "external provider; provider unresolved", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-ACT-007", "name": "Email service", "trust": "external provider; provider unresolved", "evidence_ids": ["S00-E-001", "S00-E-002"]}
    ],
    "data": [
      {"id": "S00-DAT-001", "name": "Account, email, verification/sign-in, session, role, and suspension data", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-DAT-002", "name": "Public event, calendar, permanent URL, and QR data", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-DAT-003", "name": "Exact event address and access instructions", "classification": "audience-restricted", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-DAT-004", "name": "Food needs, exclusions, cross-contact concerns, handling notes, recipes, and consent", "classification": "private or audience-restricted; exact classification partly unresolved", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
      {"id": "S00-DAT-005", "name": "Orders, proposals, holds, bookings, accepted recipes, and attendance state", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-DAT-006", "name": "Payment-account, payment, refund, fee, payout, receipt, reference, and operation-identity data", "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-DAT-007", "name": "Staff updates, notices, cursors, pending work, delivery status, and audit records", "evidence_ids": ["S00-E-001", "S00-E-002"]}
    ],
    "zones": [
      {"id": "S00-ZON-001", "name": "Untrusted client boundary", "status": "documented logical zone", "evidence_ids": ["S00-E-002"]},
      {"id": "S00-ZON-002", "name": "Trusted application boundary", "status": "proposed logical zone; implementation absent", "evidence_ids": ["S00-E-002"]},
      {"id": "S00-ZON-003", "name": "Database boundary", "status": "proposed persistence; technology/deployment unresolved", "evidence_ids": ["S00-E-002", "S00-E-003"]},
      {"id": "S00-ZON-004", "name": "External payment-provider boundary", "status": "provider unresolved", "evidence_ids": ["S00-E-002"]},
      {"id": "S00-ZON-005", "name": "External email-provider boundary", "status": "provider unresolved", "evidence_ids": ["S00-E-002"]}
    ],
    "boundaries": [
      {"id": "S00-BND-001", "name": "Client-to-application", "from_zone_ids": ["S00-ZON-001"], "to_zone_ids": ["S00-ZON-002"], "evidence_ids": ["S00-E-002"]},
      {"id": "S00-BND-002", "name": "Application-to-persistence", "from_zone_ids": ["S00-ZON-002"], "to_zone_ids": ["S00-ZON-003"], "evidence_ids": ["S00-E-002"]},
      {"id": "S00-BND-003", "name": "Application-to-payment outbound", "from_zone_ids": ["S00-ZON-002"], "to_zone_ids": ["S00-ZON-004"], "evidence_ids": ["S00-E-002"]},
      {"id": "S00-BND-004", "name": "Payment callback inbound", "from_zone_ids": ["S00-ZON-004"], "to_zone_ids": ["S00-ZON-002"], "evidence_ids": ["S00-E-002"]},
      {"id": "S00-BND-005", "name": "Application-to-email outbound", "from_zone_ids": ["S00-ZON-002"], "to_zone_ids": ["S00-ZON-005"], "evidence_ids": ["S00-E-002"]}
    ],
    "flows": [
      {"id": "S00-FLW-001", "name": "Public calendar/event/QR read", "boundary_ids": ["S00-BND-001"], "data_ids": ["S00-DAT-002"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-002", "name": "Account creation, verification, email-link sign-in, session use, and logout", "boundary_ids": ["S00-BND-001", "S00-BND-005"], "data_ids": ["S00-DAT-001"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-003", "name": "Protected event, recipe, assignment, order, review, cancellation, and Admin commands", "boundary_ids": ["S00-BND-001", "S00-BND-002"], "data_ids": ["S00-DAT-003", "S00-DAT-004", "S00-DAT-005", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-004", "name": "Checkout, capability, reconciliation, refund, and payout outbound operations", "boundary_ids": ["S00-BND-002", "S00-BND-003"], "data_ids": ["S00-DAT-005", "S00-DAT-006", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-005", "name": "Payment callback and local financial/booking transition", "boundary_ids": ["S00-BND-004", "S00-BND-002"], "data_ids": ["S00-DAT-005", "S00-DAT-006", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-006", "name": "Audience-filtered staff polling and reconnect replay", "boundary_ids": ["S00-BND-001", "S00-BND-002"], "data_ids": ["S00-DAT-003", "S00-DAT-004", "S00-DAT-005", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-007", "name": "Account and transactional email notice delivery", "boundary_ids": ["S00-BND-005"], "data_ids": ["S00-DAT-001", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-FLW-008", "name": "Expiry, completion, retries, reconciliation, retention, audit, and durable-work dispatch", "boundary_ids": ["S00-BND-002", "S00-BND-003", "S00-BND-005"], "data_ids": ["S00-DAT-004", "S00-DAT-005", "S00-DAT-006", "S00-DAT-007"], "evidence_ids": ["S00-E-001", "S00-E-002"]}
    ],
    "entry_points": [
      {"id": "S00-EP-001", "name": "Public calendar/event/QR destination", "flow_ids": ["S00-FLW-001"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-EP-002", "name": "Account, verification, and email-link access", "flow_ids": ["S00-FLW-002"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-EP-003", "name": "Authenticated commands and audience-specific reads", "flow_ids": ["S00-FLW-003"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-EP-004", "name": "Staff polling/reconnect", "flow_ids": ["S00-FLW-006"], "evidence_ids": ["S00-E-001", "S00-E-002"]},
      {"id": "S00-EP-005", "name": "Payment-provider callback adapter", "flow_ids": ["S00-FLW-005"], "evidence_ids": ["S00-E-002"]}
    ]
  },
  "methods": [
    {"id": "S00-M-001", "name": "STRIDE", "categories": ["Spoofing", "Tampering", "Repudiation", "Information Disclosure", "Denial of Service", "Elevation of Privilege"], "application": "Applied to every modeled element through S00-COV-001–S00-COV-006."}
  ],
  "threats": [
    {
      "id": "S00-T-001",
      "category": "Spoofing",
      "scenario": "A party presenting another person's verification/sign-in link or session identifier could be treated as that account. Email-link and session lifecycles are unresolved.",
      "affected_record_ids": ["S00-AST-001", "S00-ACT-002", "S00-ACT-003", "S00-ACT-004", "S00-ACT-005", "S00-DAT-001", "S00-BND-001", "S00-BND-005", "S00-FLW-002", "S00-EP-002"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-001", "S00-CTL-002"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-002",
      "category": "Spoofing",
      "scenario": "A message at the payment callback entry point could be accepted as provider evidence and cause a financial or booking transition without authentic-origin validation. Provider and callback contracts are unresolved.",
      "affected_record_ids": ["S00-AST-003", "S00-AST-004", "S00-ACT-006", "S00-DAT-005", "S00-DAT-006", "S00-BND-004", "S00-FLW-005", "S00-EP-005"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-004", "S00-CTL-005"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-003",
      "category": "Tampering",
      "scenario": "An untrusted client could submit unauthorized ownership, assignment, price, capacity, recipe, order, acceptance, cancellation, or transition values. Client-controlled transitions could alter commitments, attendance, food handling, or financial eligibility.",
      "affected_record_ids": ["S00-AST-001", "S00-AST-002", "S00-AST-003", "S00-AST-004", "S00-DAT-003", "S00-DAT-004", "S00-DAT-005", "S00-DAT-006", "S00-BND-001", "S00-FLW-003", "S00-EP-003"],
      "evidence_ids": ["S00-E-001", "S00-E-002"],
      "control_ids": ["S00-CTL-002", "S00-CTL-003"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-004",
      "category": "Tampering",
      "scenario": "Altered, late, incorrect, duplicate, or replayed payment evidence could create an invalid/duplicate booking, exceed a refund cap, or duplicate a payout unless evidence, amount, currency, hold/event state, references, and operation identity are validated and deduplicated.",
      "affected_record_ids": ["S00-AST-003", "S00-AST-004", "S00-DAT-005", "S00-DAT-006", "S00-BND-003", "S00-BND-004", "S00-FLW-004", "S00-FLW-005", "S00-FLW-008", "S00-EP-005"],
      "evidence_ids": ["S00-E-001", "S00-E-002"],
      "control_ids": ["S00-CTL-004", "S00-CTL-005"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-005",
      "category": "Tampering",
      "scenario": "Concurrent checkout, confirmation, cancellation, or capacity changes could exceed capacity or fail to atomically replace one valid hold with one booking unless all capacity-changing operations enforce the same consistency rule.",
      "affected_record_ids": ["S00-AST-003", "S00-DAT-005", "S00-BND-002", "S00-FLW-003", "S00-FLW-004", "S00-FLW-005"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-005"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-006",
      "category": "Tampering",
      "scenario": "A duplicated or out-of-order scheduled task, callback, retry, or Admin reconciliation could repeat expiry, refund, payout, or notification effects or apply stale state unless it re-enters the owning workflow with current-state checks and deduplication.",
      "affected_record_ids": ["S00-AST-003", "S00-AST-004", "S00-AST-005", "S00-DAT-005", "S00-DAT-006", "S00-DAT-007", "S00-FLW-005", "S00-FLW-008"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-004", "S00-CTL-006", "S00-CTL-008"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-007",
      "category": "Repudiation",
      "scenario": "An account actor could dispute an event, order, staff-assignment, review, cancellation, or financial state change if the required actor, time, and outcome record is absent, incomplete, or disconnected from the affected record and provider references.",
      "affected_record_ids": ["S00-AST-004", "S00-AST-006", "S00-ACT-002", "S00-ACT-003", "S00-ACT-004", "S00-ACT-005", "S00-DAT-005", "S00-DAT-006", "S00-DAT-007", "S00-FLW-003", "S00-FLW-004", "S00-FLW-005", "S00-FLW-008"],
      "evidence_ids": ["S00-E-001", "S00-E-002"],
      "control_ids": ["S00-CTL-006"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-008",
      "category": "Information Disclosure",
      "scenario": "A public or wrong-account response could expose exact addresses, orders, dietary requests, payment records, or staff updates beyond public fields or the Attendee's own records unless the server constructs and authorizes audience-specific projections.",
      "affected_record_ids": ["S00-AST-002", "S00-AST-004", "S00-ACT-001", "S00-ACT-003", "S00-DAT-002", "S00-DAT-003", "S00-DAT-004", "S00-DAT-005", "S00-DAT-006", "S00-DAT-007", "S00-BND-001", "S00-FLW-001", "S00-FLW-003", "S00-EP-001", "S00-EP-003"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-004"],
      "control_ids": ["S00-CTL-002", "S00-CTL-007"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-009",
      "category": "Information Disclosure",
      "scenario": "Shopper views or email notices could disclose Attendee names, private food notes, or exact addresses because those boundaries permit fewer fields than cook, Organizer, Attendee, or Admin views.",
      "affected_record_ids": ["S00-AST-002", "S00-ACT-004", "S00-ACT-007", "S00-DAT-003", "S00-DAT-004", "S00-DAT-007", "S00-BND-001", "S00-BND-005", "S00-FLW-006", "S00-FLW-007", "S00-EP-004"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-004"],
      "control_ids": ["S00-CTL-002", "S00-CTL-007"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-010",
      "category": "Information Disclosure",
      "scenario": "A removed cook or shopper assignment could continue to receive current state or replayed updates unless current assignment is checked on every staff read and reconnect replay.",
      "affected_record_ids": ["S00-AST-001", "S00-AST-002", "S00-ACT-004", "S00-DAT-003", "S00-DAT-004", "S00-DAT-007", "S00-BND-001", "S00-FLW-006", "S00-EP-004"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-002", "S00-CTL-008"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-011",
      "category": "Information Disclosure",
      "scenario": "Private food notes could survive consent withdrawal or the 90-day deletion point in updates, jobs, audit records, derived records, or backups. Full storage/copy lifecycle coverage is unresolved.",
      "affected_record_ids": ["S00-AST-002", "S00-AST-006", "S00-DAT-004", "S00-DAT-007", "S00-BND-002", "S00-FLW-003", "S00-FLW-006", "S00-FLW-008"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-007"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-012",
      "category": "Denial of Service",
      "scenario": "Staff polling/replay or durable-work dispatch could fall behind at the stated load and miss required update, reconnect, refund-submission, or read-availability targets. Architecture records this risk and requires load validation.",
      "affected_record_ids": ["S00-AST-005", "S00-DAT-007", "S00-BND-001", "S00-BND-002", "S00-FLW-001", "S00-FLW-006", "S00-FLW-008", "S00-EP-001", "S00-EP-004"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-008"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-013",
      "category": "Denial of Service",
      "scenario": "Email failure or backlog could delay access and notices and, if payment/email execution shared mutable failure state or capacity, could delay required financial work. Independent gateways and execution are specified to contain the latter effect.",
      "affected_record_ids": ["S00-AST-001", "S00-AST-004", "S00-AST-005", "S00-ACT-007", "S00-BND-003", "S00-BND-005", "S00-FLW-002", "S00-FLW-004", "S00-FLW-007", "S00-FLW-008"],
      "evidence_ids": ["S00-E-001", "S00-E-002"],
      "control_ids": ["S00-CTL-001", "S00-CTL-004", "S00-CTL-008"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    },
    {
      "id": "S00-T-014",
      "category": "Elevation of Privilege",
      "scenario": "An authenticated account could act on another Attendee's order, another Organizer's event, an event without a current assignment, or an Admin-only operation unless every protected action/read enforces current ownership, assignment, role, suspension, and action-specific authorization.",
      "affected_record_ids": ["S00-AST-001", "S00-AST-002", "S00-AST-003", "S00-AST-004", "S00-ACT-002", "S00-ACT-003", "S00-ACT-004", "S00-ACT-005", "S00-DAT-001", "S00-DAT-003", "S00-DAT-004", "S00-DAT-005", "S00-DAT-006", "S00-DAT-007", "S00-BND-001", "S00-FLW-003", "S00-FLW-006", "S00-EP-003", "S00-EP-004"],
      "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"],
      "control_ids": ["S00-CTL-002"],
      "assumptions": [],
      "supplied_risk_ids": [],
      "rating": "unrated"
    }
  ],
  "controls": [
    {"id": "S00-CTL-001", "name": "Verified-email access and logout", "status": "required behavior; implementation/effectiveness unverified", "description": "FR-6.2–FR-6.4 require verification, email-link sign-in, and session termination; lifecycle and provisioning remain unresolved.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-CTL-002", "name": "Server authorization and audience projections", "status": "required behavior plus proposed placement; implementation/effectiveness unverified", "description": "Ownership, own-order, Admin, assignment, address, food-note, shopper, and email restrictions are specified; architecture places checks/filtering in server workflows.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003", "S00-E-004"]},
    {"id": "S00-CTL-003", "name": "Server-owned validation/transitions and snapshots", "status": "required behavior plus proposed placement; implementation/effectiveness unverified", "description": "The server owns cutoffs, prices, transitions, and calculations; published fields and launched/accepted recipes remain immutable.", "evidence_ids": ["S00-E-001", "S00-E-002"]},
    {"id": "S00-CTL-004", "name": "Isolated gateways and validated payment evidence", "status": "gateway separation confirmed; validation required/proposed; implementation/effectiveness unverified", "description": "Payment/email use separate ports, clients, credentials, retry state, and capacity; callbacks use a distinct adapter and browser return cannot confirm payment.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-CTL-005", "name": "Capacity/financial atomicity and deduplication", "status": "required outcomes with proposed mechanism; implementation/effectiveness unverified", "description": "No oversubscription, duplicate booking, over-refund, or duplicate payout; architecture proposes transactions, common capacity serialization, atomic hold replacement, and stable identifiers.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-CTL-006", "name": "Actor/time/outcome audit records", "status": "required behavior; implementation/integrity/effectiveness unverified", "description": "FR-11.3 covers event, order, staff-assignment, and financial state changes; financial records have required retention.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-CTL-007", "name": "Consent, minimization, and retention/deletion", "status": "required behavior with proposed reference-only copying; implementation/effectiveness unverified", "description": "Food-note consent, audience exclusions, withdrawal deletion, 90-day deletion, and financial-record exclusion are specified; derived/backup coverage remains unresolved.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003", "S00-E-004"]},
    {"id": "S00-CTL-008", "name": "Durable updates/work and independent execution", "status": "required outcomes with proposed mechanism; implementation/limits/effectiveness unverified", "description": "Changes survive restarts; updates replay current authorized state; payment/email work has separate retry state/capacity; timing and availability require validation.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]}
  ],
  "requirements": [
    {"id": "S00-REQ-001", "source_ids": ["FR-6.1–FR-6.17", "FR-11.2"], "topic": "identity, ownership, role, assignment, suspension, and unauthorized actions", "evidence_ids": ["S00-E-001"]},
    {"id": "S00-REQ-002", "source_ids": ["FR-2.12", "FR-3.10", "FR-4.7", "FR-4.14", "FR-11.1–FR-11.7"], "topic": "privacy, consent, filtering, audit, deletion, and retention", "evidence_ids": ["S00-E-001"]},
    {"id": "S00-REQ-003", "source_ids": ["FR-7.8–FR-7.10", "FR-8.1–FR-8.24", "FR-9.1–FR-9.18", "NFR-2.1–NFR-2.3"], "topic": "recipe, capacity, financial, durability, and deduplication integrity", "evidence_ids": ["S00-E-001"]},
    {"id": "S00-REQ-004", "source_ids": ["FR-4.1–FR-4.14", "NFR-1.1–NFR-1.5", "NFR-2.4"], "topic": "updates, notices, timing, refund submission, and availability", "evidence_ids": ["S00-E-001"]},
    {"id": "S00-REQ-005", "source_ids": ["ARCHITECTURE.md §8 DR-1–DR-9"], "topic": "enforcement placement, ownership, adapters, provider validation, and gateway isolation", "evidence_ids": ["S00-E-002"]},
    {"id": "S00-REQ-006", "source_ids": ["DESIGN.md Components", "DESIGN.md Do's and Don'ts"], "topic": "rendering of addresses, notes, prices, deadlines, states, and dietary claims", "evidence_ids": ["S00-E-004"]}
  ],
  "risks": [],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [],
  "coverage": [
    {
      "id": "S00-COV-001",
      "method_id": "S00-M-001",
      "category": "Spoofing",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-001", "S00-AST-003", "S00-AST-004", "S00-ACT-002–S00-ACT-006", "S00-DAT-001", "S00-DAT-005", "S00-DAT-006", "S00-BND-001", "S00-BND-004", "S00-BND-005", "S00-FLW-002", "S00-FLW-005", "S00-EP-002", "S00-EP-005"],
      "threat_ids": ["S00-T-001", "S00-T-002"],
      "other_element_disposition": "assessed; no additional evidenced scenario"
    },
    {
      "id": "S00-COV-002",
      "method_id": "S00-M-001",
      "category": "Tampering",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-001–S00-AST-005", "S00-DAT-003–S00-DAT-007", "S00-BND-001–S00-BND-004", "S00-FLW-003–S00-FLW-005", "S00-FLW-008", "S00-EP-003", "S00-EP-005"],
      "threat_ids": ["S00-T-003", "S00-T-004", "S00-T-005", "S00-T-006"],
      "other_element_disposition": "assessed; no additional evidenced scenario"
    },
    {
      "id": "S00-COV-003",
      "method_id": "S00-M-001",
      "category": "Repudiation",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-004", "S00-AST-006", "S00-ACT-002–S00-ACT-005", "S00-DAT-005–S00-DAT-007", "S00-FLW-003–S00-FLW-005", "S00-FLW-008"],
      "threat_ids": ["S00-T-007"],
      "other_element_disposition": "assessed; no additional evidenced scenario"
    },
    {
      "id": "S00-COV-004",
      "method_id": "S00-M-001",
      "category": "Information Disclosure",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-001", "S00-AST-002", "S00-AST-004", "S00-AST-006", "S00-ACT-001", "S00-ACT-003", "S00-ACT-004", "S00-ACT-007", "S00-DAT-002–S00-DAT-007", "S00-BND-001", "S00-BND-002", "S00-BND-005", "S00-FLW-001", "S00-FLW-003", "S00-FLW-006–S00-FLW-008", "S00-EP-001", "S00-EP-003", "S00-EP-004"],
      "threat_ids": ["S00-T-008", "S00-T-009", "S00-T-010", "S00-T-011"],
      "other_element_disposition": "assessed; no additional evidenced scenario"
    },
    {
      "id": "S00-COV-005",
      "method_id": "S00-M-001",
      "category": "Denial of Service",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-001", "S00-AST-004", "S00-AST-005", "S00-ACT-007", "S00-DAT-007", "S00-BND-001–S00-BND-003", "S00-BND-005", "S00-FLW-001", "S00-FLW-002", "S00-FLW-004", "S00-FLW-006–S00-FLW-008", "S00-EP-001", "S00-EP-004"],
      "threat_ids": ["S00-T-012", "S00-T-013"],
      "other_element_disposition": "assessed; no additional evidenced scenario; request/resource limits remain a gap"
    },
    {
      "id": "S00-COV-006",
      "method_id": "S00-M-001",
      "category": "Elevation of Privilege",
      "all_modeled_element_ids": ["S00-AST-001–S00-AST-006", "S00-ACT-001–S00-ACT-007", "S00-DAT-001–S00-DAT-007", "S00-ZON-001–S00-ZON-005", "S00-BND-001–S00-BND-005", "S00-FLW-001–S00-FLW-008", "S00-EP-001–S00-EP-005"],
      "threat_linked_element_ids": ["S00-AST-001–S00-AST-004", "S00-ACT-002–S00-ACT-005", "S00-DAT-001", "S00-DAT-003–S00-DAT-007", "S00-BND-001", "S00-FLW-003", "S00-FLW-006", "S00-EP-003", "S00-EP-004"],
      "threat_ids": ["S00-T-014"],
      "other_element_disposition": "assessed; no additional evidenced scenario"
    }
  ],
  "conflicts": [
    {
      "id": "S00-CON-001",
      "statement_a": "Developer input names Fastify as server runtime and Node.js as server framework.",
      "statement_b": "ARCHITECTURE.md proposes Node.js as runtime and Fastify as framework; acceptance is TO BE DECIDED.",
      "evidence_ids": ["S00-E-002", "S00-E-003"],
      "disposition": "preserved unresolved"
    },
    {
      "id": "S00-CON-002",
      "statement_a": "Direct candidate js/nodejs/26 was supplied.",
      "statement_b": "Fastify, Better Auth, and Prisma candidate manifests include Node.js 24; no project version establishes precedence.",
      "evidence_ids": ["S00-E-003"],
      "disposition": "preserved unresolved; candidate packs remain inactive"
    }
  ],
  "gaps": [
    {"id": "S00-GAP-001", "description": "No implementation, configuration, deployment, test, operational observation, or control-effectiveness evidence exists.", "evidence_ids": ["S00-E-002", "S00-E-003", "S00-E-004"]},
    {"id": "S00-GAP-002", "description": "Link/session lifecycle, native credential transport, and first Admin provisioning are unresolved.", "evidence_ids": ["S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-003", "description": "Provider selection and authenticity, callback, reconciliation, delivery, refund, fee, payout, and duration contracts are unresolved.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-004", "description": "Persistence, transaction/locking, durable-work retry/reconciliation, and execution settings are unresolved.", "evidence_ids": ["S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-005", "description": "Hosting, build/container scope, secrets, networks, operational access, deployment topology, and versions are unresolved.", "evidence_ids": ["S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-006", "description": "Request-validation implementation, request/resource limits, and logging controls are unresolved; weakness is not inferred.", "evidence_ids": ["S00-E-003"]},
    {"id": "S00-GAP-007", "description": "Jurisdictions are UNKNOWN; private-note classification, derived/backup deletion coverage, and nonfinancial retention are unresolved.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-008", "description": "Update transport/replay is unresolved; proposed polling has not been load-tested against required timing.", "evidence_ids": ["S00-E-002", "S00-E-003"]},
    {"id": "S00-GAP-009", "description": "Browser/rendering and native application/platform/workflow scope remain unresolved.", "evidence_ids": ["S00-E-002", "S00-E-003", "S00-E-004"]},
    {"id": "S00-GAP-010", "description": "No risk method, likelihood, impact, severity, appetite, owner, or deadline is supplied; all threats remain unrated and unassigned.", "evidence_ids": ["S00-E-001", "S00-E-002", "S00-E-003", "S00-E-004"]}
  ]
}
```

## Summary

### Scope and evidence limits

This fragment covers the specified first-release Picky Party website: public event discovery, verified-email access, role- and assignment-scoped event and food workflows, seats and payments, refunds and payouts, staff updates, ingredient planning, audit, and retention. The specified exclusion is: “The first release supports English and USD. Group bookings, extra portions, offline payments, waitlists, discounts, and automatic dietary certification are outside its scope.” Native-app scope and deployment topology remain unresolved.

Requirements are product decisions rather than measured results; architecture separates confirmed boundaries from proposals; every secure-coding rule is blocked; design choices are assumptions; and no implementation evidence exists. Controls are therefore requirements, confirmed design boundaries, or proposals, never implemented or effective controls. No supplied method supports risk ratings, owners, or deadlines.

### System overview

Untrusted clients cross the application boundary for public reads, email-link access, protected commands, and staff polling. The proposed application owns authorization, transitions, audience filtering, capacity, and financial eligibility and crosses a proposed persistence boundary. Confirmed logical isolation separates outbound payment from email; inbound payment results use a separate callback adapter. Providers and contracts remain undecided. Sensitive records include exact addresses, food needs, orders/bookings, financial records, updates, pending work, and audit records.

### STRIDE coverage

| Category | Disposition | Threats |
| --- | --- | --- |
| Spoofing | All modeled elements assessed; evidenced scenarios concern account/link/session identity and payment-callback origin. | S00-T-001–S00-T-002 |
| Tampering | All modeled elements assessed; evidenced scenarios concern untrusted commands, payment replay, concurrent capacity changes, and stale/repeated work. | S00-T-003–S00-T-006 |
| Repudiation | All modeled elements assessed; evidenced scenario concerns actor/time/outcome records. | S00-T-007 |
| Information Disclosure | All modeled elements assessed; scenarios concern public/wrong-account results, shopper/email minimization, revoked staff replay, and deletion coverage. | S00-T-008–S00-T-011 |
| Denial of Service | All modeled elements assessed; scenarios concern polling/work backlog and email failure affecting access/notices or financial execution. Limits remain a gap, not a finding. | S00-T-012–S00-T-013 |
| Elevation of Privilege | All modeled elements assessed; scenario concerns ownership, assignment, role, suspension, and action-specific authorization. | S00-T-014 |

### Threats and control status

The identity design supports S00-T-001 because it exposes email links and sessions while their lifetimes and revocation remain unresolved. The payment callback boundary supports S00-T-002 and S00-T-004: provider origin, amount, currency, hold/event state, and replay/duplicate evidence must be validated. Protected client commands support S00-T-003 and S00-T-014 because authority and current state must come from server workflows.

Capacity and financial invariants support S00-T-005 and S00-T-006. Specifications prohibit oversubscription, duplicate booking, over-refund, and duplicate payout; transaction, locking, and durable-work mechanisms remain proposed. Actor/time/outcome records address S00-T-007, but their operation and integrity are not evidenced.

Distinct audiences for addresses, food needs, orders, payments, and staff updates support S00-T-008–S00-T-010. Public responses, shopper views, email, and replay need different filtering and current-assignment checks. S00-T-011 follows from explicit consent/deletion duties and unresolved copy/backup coverage.

Required update, availability, durability, and refund timing support S00-T-012. S00-T-013 reflects the specified email-failure scenario: independent payment/email gateways and execution are intended to prevent email backlog delaying financial work, but no implementation is evidenced.

### Conflicts and gaps

Node.js/Fastify role labels conflict with their proposed interpretation, and inactive candidate dependencies contain unresolved Node.js 26 versus 24 baselines. Neither is silently resolved.

Material gaps include implementation/test evidence; link/session and first-Admin behavior; provider contracts; persistence, locking, durable work, and reconciliation; deployment, secrets, networks, and operations; request/resource limits and logging; privacy classification and deletion across copies/backups; update transport/load validation; and browser/native scope. These are evidence gaps, not proof of vulnerabilities or absent controls.
