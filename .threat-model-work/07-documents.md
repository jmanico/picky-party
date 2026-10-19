# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "DA7-SCOPE-001",
    "system": "Picky Party first-release specification set",
    "analysis_date": "2026-10-19",
    "input_type": "ARCHITECTURE_DOCS",
    "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003", "DA7-E-004"],
    "authority_order": [
      "REQUIREMENTS.md owns behavior, roles, states, workflows, and first-release obligations",
      "ARCHITECTURE.md owns logical components, interfaces, flows, boundaries, and architecture status",
      "SECURITY.md owns secure-coding rule status and open security decisions",
      "DESIGN.md owns visual presentation and interaction rendering"
    ],
    "implementation_status": "No application implementation exists",
    "excluded_evidence": [
      "No source code, runtime configuration, API schema, infrastructure-as-code, deployment record, test result, log, audit report, or penetration-test report was supplied",
      "The Manicode candidate corpus described by SECURITY.md was not supplied as an architecture input to this stage and is retained only as a document claim"
    ]
  },
  "evidence": [
    {
      "id": "DA7-E-001",
      "artifact": "REQUIREMENTS.md",
      "document_type": "Product and system requirements specification",
      "date": "UNKNOWN",
      "author": "UNKNOWN",
      "edition": "No edition stated",
      "document_status": "Current behavioral authority for the supplied specification set; includes adopted first-release ASSUMPTION decisions and explicit UNKNOWN inputs",
      "state_described": "Approved or adopted intended behavior, not observed implementation",
      "extraction": {
        "assets": "Accounts, events, assignments, dishes, recipes, ingredients, orders, dietary requests, holds, bookings, payments, refunds, payouts, updates, notices, QR URLs, audit and retention records",
        "actors": "Visitor, Organizer, Attendee, Admin, cook assignment, shopper assignment, payment service, email service",
        "data": "Identity, addresses, event metadata, food needs, recipes, booking and financial state, notices, audit records",
        "flows": "Event publication, order review, staff updates, payment, refund, payout, email, consent, deletion, and retention",
        "boundaries": "Public/private, per-Attendee ownership, role/assignment, payment provider, and email provider",
        "requirements": "FR-1 through FR-11 and NFR-1 through NFR-3",
        "gaps": "Provider selection, jurisdiction, and statutory duties remain unknown"
      },
      "locators": ["Required Requirement Inputs", "Adopted Decisions", "Product Rules and Terms", "FR-1-FR-11", "NFR-1-NFR-3", "Open Questions"]
    },
    {
      "id": "DA7-E-002",
      "artifact": "ARCHITECTURE.md",
      "document_type": "arc42 logical architecture and decision document",
      "date": "UNKNOWN",
      "author": "UNKNOWN",
      "edition": "No edition stated",
      "document_status": "Mixed: one CONFIRMED integration constraint, named developer choices, PROPOSED architecture, UNKNOWN facts, and TO BE DECIDED questions",
      "state_described": "Design intent; explicitly no implementation",
      "extraction": {
        "assets": "Logical presentation, identity, event, order, financial, gateway, planning, notice, work, persistence, and provider components",
        "actors": "Visitor, Organizer, Attendee, cook, shopper, Admin, payment service, email service",
        "data": "Proposed relational records and audience projections",
        "flows": "Publish/discover, review/prepare, checkout/payment, cancel/settle, notify/reconnect, retention",
        "boundaries": "Untrusted client, trusted application, persistence, isolated payment integration, separate email integration, external providers, audience projections",
        "controls": "Confirmed gateway isolation; proposed server projections, sessions, transactions, durable work, validation, note references, and polling",
        "risks": "Provider capability, update timing, private-note copy survival, and native/technology ambiguity",
        "gaps": "AQ-1 through AQ-8"
      },
      "locators": ["§1-§12", "Required Architecture Inputs", "AQ-1-AQ-8"]
    },
    {
      "id": "DA7-E-003",
      "artifact": "SECURITY.md",
      "document_type": "Secure-coding decision and evidence-status document",
      "date": "UNKNOWN",
      "author": "UNKNOWN",
      "edition": "No edition stated",
      "document_status": "All secure-coding rules BLOCKED; confirmed requirement and architecture claims retained; technology prompt candidates TO BE DECIDED",
      "state_described": "Security requirements intake and unresolved implementation decisions; no implemented or tested controls",
      "extraction": {
        "assets": "Server, web, native, identity, persistence, provider, private data, build/deployment, and staff-update control areas",
        "controls": "SC-001 through SC-009, all BLOCKED",
        "assumptions": "No candidate library or version is selected; named technologies lack resolved versions and scope",
        "gaps": "OD-001 through OD-012; owners are UNKNOWN"
      },
      "locators": ["Secure-Coding Inputs", "Selected Manicode Prompts", "Secure-Coding Rules", "Open Security Decisions"]
    },
    {
      "id": "DA7-E-004",
      "artifact": "DESIGN.md",
      "document_type": "Google-format visual and interaction design specification",
      "date": "UNKNOWN",
      "author": "UNKNOWN",
      "edition": "alpha",
      "document_status": "ASSUMPTION-based proposed design constrained by REQUIREMENTS.md; brand, typeface, and breakpoints TO BE DECIDED",
      "state_described": "Design intent; explicitly no implementation",
      "extraction": {
        "assets": "Public, account, event, order, checkout, staff, Organizer, and Admin presentation patterns",
        "data": "Rendered event, address, food-needs, ingredient, financial, and status fields",
        "flows": "User interactions and live-update rendering",
        "controls": "Visual distinction, accessible interaction, audience-aware rendering, consent separation, private-field exclusions",
        "gaps": "DQ-1 through DQ-3 and browser/native rendering scope"
      },
      "locators": ["YAML front matter version", "Overview", "Colors", "Typography", "Layout", "Components", "Do's and Don'ts", "Open Questions"]
    }
  ],
  "system": {
    "assets": [
      {"id": "DA7-AS-001", "name": "Account identity and access records", "owner": "Identity and access logical component", "status": "Behavior required; storage and implementation proposed or unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-AS-002", "name": "Events, exact addresses, assignments, public URLs, dishes, recipes, and ingredients", "owner": "Events and recipes logical component", "status": "Behavior required; module boundary proposed", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-AS-003", "name": "Orders, food needs, consent, proposals, accepted recipes, holds, and bookings", "owner": "Orders and bookings logical component", "status": "Behavior required; module boundary proposed", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-AS-004", "name": "Connected-account, payment, refund, payout, fee, and reconciliation records", "owner": "Financial workflows logical component", "status": "Behavior required; provider and persistence unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-AS-005", "name": "Staff updates, account notices, delivery state, audit records, and pending work", "owner": "Updates/notices and durable-work logical components", "status": "Behavior required; implementation and nonfinancial retention unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-AS-006", "name": "Presentation and transient client state", "owner": "Web presentation; mobile ownership unresolved", "status": "ReactJS named; React Native named but native workflow scope unresolved", "evidence_ids": ["DA7-E-002", "DA7-E-004"]},
      {"id": "DA7-AS-007", "name": "Payment integration credentials and client configuration", "owner": "Payment outbound gateway", "status": "Logical isolation CONFIRMED; provider and implementation unresolved", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-AS-008", "name": "Email integration credentials and client configuration", "owner": "Email outbound gateway", "status": "Logical isolation CONFIRMED; provider and implementation unresolved", "evidence_ids": ["DA7-E-002", "DA7-E-003"]}
    ],
    "actors": [
      {"id": "DA7-ACT-001", "name": "Visitor", "status": "Required actor", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-002", "name": "Organizer", "status": "Required account role", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-003", "name": "Attendee", "status": "Required account role", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-004", "name": "Cook", "status": "Required event assignment, not a separate account role", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-005", "name": "Shopper", "status": "Required event assignment, not a separate account role", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-006", "name": "Admin", "status": "Required role; first provisioning unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-ACT-007", "name": "Payment service", "status": "Required external integration; provider unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-ACT-008", "name": "Email service", "status": "Required external integration; provider unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002"]}
    ],
    "data": [
      {"id": "DA7-D-001", "name": "Display name, email, verification, sign-in, session, role, suspension, and assignment data", "classification": "Personal/access data; detailed classification unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-D-002", "name": "Public event metadata", "fields": ["title", "description", "Organizer name", "menu", "schedule", "city", "country", "price", "cutoff", "availability", "cancellation notice"], "classification": "Required public data for launched events", "evidence_ids": ["DA7-E-001", "DA7-E-004"]},
      {"id": "DA7-D-003", "name": "Exact event address and access instructions", "classification": "Restricted to specified event audiences", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]},
      {"id": "DA7-D-004", "name": "Dietary labels, restrictions, exclusions, cross-contact concerns, special needs, preferences, omissions, private notes, recipes, and handling notes", "classification": "Private dietary data is an adopted ASSUMPTION; exact private-note boundary unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-D-005", "name": "Order, seat hold, booking, attendance, and ingredient-planning state", "classification": "Non-public operational and account data", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-D-006", "name": "Payment, refund, payout, fee, amount, state, receipt, and provider references", "classification": "Non-public financial records; specified subset retained for 24 months", "evidence_ids": ["DA7-E-001", "DA7-E-002"]},
      {"id": "DA7-D-007", "name": "Staff updates, cursors, account notices, email delivery state, audit records, and work metadata", "classification": "Audience-filtered records; post-event nonfinancial retention unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]}
    ],
    "zones": [
      {"id": "DA7-Z-001", "name": "Untrusted web client boundary", "status": "PROPOSED logical zone", "evidence_ids": ["DA7-E-002"]},
      {"id": "DA7-Z-002", "name": "Native client boundary", "status": "Framework named; platform and workflow scope TO BE DECIDED", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-Z-003", "name": "Trusted application boundary", "status": "PROPOSED logical zone", "evidence_ids": ["DA7-E-002"]},
      {"id": "DA7-Z-004", "name": "Database boundary", "status": "Logical persistence boundary; PostgreSQL is PROPOSED", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-Z-005", "name": "Isolated payment integration", "status": "Logical isolation CONFIRMED", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-Z-006", "name": "Separate email integration", "status": "Logical isolation CONFIRMED", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-Z-007", "name": "External provider boundary", "status": "Required boundary; providers unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002"]}
    ],
    "boundaries": [
      {"id": "DA7-B-001", "name": "Client to HTTP application", "status": "HTTP JSON and command/read endpoints PROPOSED", "from_zone_ids": ["DA7-Z-001", "DA7-Z-002"], "to_zone_ids": ["DA7-Z-003"], "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-B-002", "name": "Application to persistence", "status": "PROPOSED; interfaces and technology unresolved", "from_zone_ids": ["DA7-Z-003"], "to_zone_ids": ["DA7-Z-004"], "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-B-003", "name": "Application financial workflows to payment gateway and provider", "status": "Gateway separation CONFIRMED; provider contract unresolved", "from_zone_ids": ["DA7-Z-003", "DA7-Z-005"], "to_zone_ids": ["DA7-Z-007"], "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-B-004", "name": "Identity/notices to email gateway and provider", "status": "Gateway separation CONFIRMED; provider contract unresolved", "from_zone_ids": ["DA7-Z-003", "DA7-Z-006"], "to_zone_ids": ["DA7-Z-007"], "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-B-005", "name": "Public, Attendee, Organizer, cook, shopper, and Admin audience projections", "status": "Required audience restrictions with PROPOSED server projection enforcement", "from_zone_ids": ["DA7-Z-003"], "to_zone_ids": ["DA7-Z-001", "DA7-Z-002"], "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]}
    ],
    "flows": [
      {"id": "DA7-F-001", "name": "Publish and discover", "source_actor_ids": ["DA7-ACT-002"], "destination_actor_ids": ["DA7-ACT-001"], "data_ids": ["DA7-D-002"], "boundary_ids": ["DA7-B-001", "DA7-B-005"], "status": "Required behavior; implementation absent", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]},
      {"id": "DA7-F-002", "name": "Verify and sign in through email link", "source_actor_ids": ["DA7-ACT-003", "DA7-ACT-002"], "destination_actor_ids": ["DA7-ACT-008"], "data_ids": ["DA7-D-001"], "boundary_ids": ["DA7-B-001", "DA7-B-004"], "status": "Required behavior; provider and lifecycle unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-F-003", "name": "Create event and expose exact location to authorized audiences", "source_actor_ids": ["DA7-ACT-002"], "destination_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-004", "DA7-ACT-005", "DA7-ACT-006"], "data_ids": ["DA7-D-003"], "boundary_ids": ["DA7-B-001", "DA7-B-005"], "status": "Required behavior; implementation absent", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]},
      {"id": "DA7-F-004", "name": "Submit, review, accept, and prepare food requests", "source_actor_ids": ["DA7-ACT-003"], "destination_actor_ids": ["DA7-ACT-002", "DA7-ACT-004", "DA7-ACT-005"], "data_ids": ["DA7-D-004", "DA7-D-005"], "boundary_ids": ["DA7-B-001", "DA7-B-002", "DA7-B-005"], "status": "Required behavior; private-note classification and copy lifecycle unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003", "DA7-E-004"]},
      {"id": "DA7-F-005", "name": "Checkout, callback, validation, and booking confirmation", "source_actor_ids": ["DA7-ACT-003", "DA7-ACT-007"], "destination_actor_ids": ["DA7-ACT-007", "DA7-ACT-003"], "data_ids": ["DA7-D-005", "DA7-D-006"], "boundary_ids": ["DA7-B-001", "DA7-B-002", "DA7-B-003"], "status": "Required behavior; provider and implementation unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-F-006", "name": "Cancel, refund, reconcile, and pay out", "source_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-006", "DA7-ACT-007"], "destination_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-006", "DA7-ACT-007"], "data_ids": ["DA7-D-005", "DA7-D-006", "DA7-D-007"], "boundary_ids": ["DA7-B-001", "DA7-B-002", "DA7-B-003", "DA7-B-005"], "status": "Required behavior; durable execution, provider, and persistence unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
      {"id": "DA7-F-007", "name": "Staff update, polling, and reconnect replay", "source_actor_ids": ["DA7-ACT-002", "DA7-ACT-003"], "destination_actor_ids": ["DA7-ACT-004", "DA7-ACT-005"], "data_ids": ["DA7-D-004", "DA7-D-005", "DA7-D-007"], "boundary_ids": ["DA7-B-001", "DA7-B-002", "DA7-B-005"], "status": "Required behavior; two-second cursor polling PROPOSED and TO BE DECIDED", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003", "DA7-E-004"]},
      {"id": "DA7-F-008", "name": "Persist account notice and send filtered email", "source_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-006"], "destination_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-008"], "data_ids": ["DA7-D-001", "DA7-D-007"], "boundary_ids": ["DA7-B-002", "DA7-B-004", "DA7-B-005"], "status": "Required behavior; provider unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]},
      {"id": "DA7-F-009", "name": "Audit, delete private notes, and retain financial records", "source_actor_ids": ["DA7-ACT-002", "DA7-ACT-003", "DA7-ACT-004", "DA7-ACT-005", "DA7-ACT-006"], "destination_actor_ids": ["DA7-ACT-006"], "data_ids": ["DA7-D-004", "DA7-D-006", "DA7-D-007"], "boundary_ids": ["DA7-B-002", "DA7-B-005"], "status": "Required behavior; detailed classification, copies, backups, readers, and implementation unresolved", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]}
    ],
    "entry_points": [
      {"id": "DA7-EP-001", "name": "Public calendar, event page, and permanent QR URL", "status": "Required", "flow_ids": ["DA7-F-001"]},
      {"id": "DA7-EP-002", "name": "Email verification and sign-in link", "status": "Required; lifecycle unresolved", "flow_ids": ["DA7-F-002"]},
      {"id": "DA7-EP-003", "name": "Authenticated event, order, account, staff, Organizer, and Admin views/actions", "status": "Required; endpoint specification absent", "flow_ids": ["DA7-F-003", "DA7-F-004", "DA7-F-006", "DA7-F-007", "DA7-F-009"]},
      {"id": "DA7-EP-004", "name": "Checkout browser flow", "status": "Required; provider protocol unresolved", "flow_ids": ["DA7-F-005"]},
      {"id": "DA7-EP-005", "name": "Payment callback adapter and reconciliation reads", "status": "Logical boundary specified; provider protocol unresolved", "flow_ids": ["DA7-F-005", "DA7-F-006"]},
      {"id": "DA7-EP-006", "name": "Email delivery gateway", "status": "Logical boundary specified; provider protocol unresolved", "flow_ids": ["DA7-F-002", "DA7-F-008"]},
      {"id": "DA7-EP-007", "name": "Scheduled and retry work", "status": "PROPOSED durable-work mechanism", "flow_ids": ["DA7-F-006", "DA7-F-008", "DA7-F-009"]}
    ]
  },
  "methods": [
    {
      "id": "DA7-M-001",
      "name": "Document analysis",
      "categories": ["assets", "actors", "data", "flows", "trust boundaries", "threats", "controls", "assumptions", "requirements", "gaps"],
      "status_rules": [
        "Required or adopted product behavior is intent, not runtime evidence",
        "CONFIRMED architecture applies only to the stated logical gateway isolation",
        "PROPOSED architecture remains unapproved and unimplemented",
        "BLOCKED secure-coding rules do not supply active controls",
        "UNKNOWN and TO BE DECIDED facts remain gaps",
        "The supplied set contains no prior threat-model method to preserve"
      ]
    }
  ],
  "threats": [],
  "controls": [
    {"id": "DA7-C-001", "name": "Payment/email gateway isolation", "status": "CONFIRMED logical architecture constraint; implementation absent", "claim": "Separate ports, adapters, clients, credentials, configuration, retry state, failure state, and execution capacity; distinct inbound payment adapter.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-002", "name": "Ownership, role, suspension, and current-assignment authorization", "status": "Required behavior with PROPOSED server enforcement; implementation absent", "claim": "Protected reads and actions check current entitlement and reject unauthorized changes.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-003", "name": "Audience-specific server projections", "status": "PROPOSED; implementation absent", "claim": "Separate public, Attendee, Organizer, cook, shopper, and Admin responses filter private data before client/provider boundaries.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-004", "name": "Public, shopper, and email field exclusion", "status": "Required behavior and design rule; implementation absent", "claim": "Public pages exclude private records and exact addresses; shopper views exclude names and private notes; email excludes exact addresses and private notes.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-004"]},
    {"id": "DA7-C-005", "name": "Consent and food-request presentation", "status": "Required behavior and design rule; implementation absent", "claim": "Consent precedes food-needs sharing; consent is visually separate; labels are requests rather than certifications.", "evidence_ids": ["DA7-E-001", "DA7-E-004"]},
    {"id": "DA7-C-006", "name": "Payment evidence, capacity, refund, and payout integrity", "status": "Required behavior with PROPOSED transaction and deduplication mechanisms; implementation absent", "claim": "Provider evidence, amount, currency, hold, event, capacity, refund cap, and payout uniqueness are validated by authoritative workflows.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-007", "name": "Durable update and external work records", "status": "PROPOSED; implementation absent", "claim": "Updates, notices, expiry, payment, refund, payout, reconciliation, and retention work survive restarts and are deduplicated.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-008", "name": "Revocable server-side session", "status": "PROPOSED; exact lifecycle unresolved and implementation absent", "claim": "Browser holds an opaque identifier for server-stored revocable state.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-009", "name": "Audit, deletion, and retention", "status": "Required behavior; detailed coverage unresolved and implementation absent", "claim": "Record actor/time/outcome; delete private notes after 90 days or eligible withdrawal; retain specified financial records for 24 months without private notes.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-010", "name": "Reference-only private-note propagation", "status": "PROPOSED; implementation absent", "claim": "Updates, jobs, and audit records refer to owning food-note records instead of copying content.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-C-011", "name": "SC-001 Server boundary controls", "status": "BLOCKED", "claim": "Requires resolved runtime/framework roles, versions, baselines, and enforcement configuration.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-012", "name": "SC-002 Web rendering and browser controls", "status": "BLOCKED", "claim": "Requires resolved React/browser/rendering/session scope.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-013", "name": "SC-003 Identity and authorization", "status": "BLOCKED", "claim": "Requires resolved link/session lifecycle, Admin provisioning, implementation, and eligible guidance.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-014", "name": "SC-004 Native authentication and storage", "status": "BLOCKED", "claim": "Requires resolved native scope, platforms, versions, credential transport, and passkey decision.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-015", "name": "SC-005 Persistence and financial consistency", "status": "BLOCKED", "claim": "Requires persistence interfaces, transaction/deduplication mechanisms, provider contract, and eligible guidance.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-016", "name": "SC-006 Provider boundary implementation", "status": "BLOCKED", "claim": "Requires provider contracts and implementation guidance for callbacks, credentials, and independent execution.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-017", "name": "SC-007 Private data and audit lifecycle", "status": "BLOCKED", "claim": "Requires classification, deletion coverage, storage/logging implementation, and eligible sources.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-018", "name": "SC-008 Build and deployment controls", "status": "BLOCKED", "claim": "Requires deployment/build scope and versions.", "evidence_ids": ["DA7-E-003"]},
    {"id": "DA7-C-019", "name": "SC-009 Staff update authorization", "status": "BLOCKED", "claim": "Requires update transport and implementation guidance for assignment checks, replay, and private filtering.", "evidence_ids": ["DA7-E-003"]}
  ],
  "requirements": [
    {
      "id": "DA7-RQ-001",
      "name": "Public and exact-location behavior",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-1 and FR-2",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines private drafts, publication, preview, public fields, exact-address audience, QR content, and cancellation-page persistence.",
      "exact_statements": [
        {"source_id": "FR-1.6", "text": "The system MUST save a new event as a private Draft."},
        {"source_id": "FR-1.14", "text": "The system MUST let the event Organizer preview the public event details before launch."},
        {"source_id": "FR-2.8", "text": "The system MUST publish a launched event at a permanent public URL."},
        {"source_id": "FR-2.9", "text": "The system MUST encode only the public event URL in its QR code."},
        {"source_id": "FR-2.11", "text": "The system MUST show the title, description, Organizer name, menu, schedule, city, country, price, cutoff, and available seats on the public page."},
        {"source_id": "FR-2.12", "text": "The system MUST restrict the exact event address to its Organizer, assigned staff, confirmed Attendees, and Admin."},
        {"source_id": "FR-2.15", "text": "The system MUST retain a cancelled event's public URL with a cancellation notice."}
      ]
    },
    {
      "id": "DA7-RQ-002",
      "name": "Food-needs consent, review, and presentation",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-3",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines collected private food information, consent, human review, Attendee acceptance, payment blocking, and non-certification presentation.",
      "exact_statements": [
        {"source_id": "FR-3.7", "text": "The system MUST require explicit restrictions for each selected dietary label."},
        {"source_id": "FR-3.8", "text": "The system MUST let an Attendee record ingredient exclusions and cross-contact concerns for each dish."},
        {"source_id": "FR-3.10", "text": "The system MUST require consent before sharing food needs with the event Organizer and cook."},
        {"source_id": "FR-3.13", "text": "The system MUST show the event Organizer every request in an order awaiting review."},
        {"source_id": "FR-3.15", "text": "The system MUST require the Organizer to confirm that each proposed dish meets every recorded request before approval."},
        {"source_id": "FR-3.16", "text": "The system MUST show the Attendee the proposed ingredients, omissions, and handling notes before acceptance."},
        {"source_id": "FR-3.17", "text": "The system MUST move an approved order to Ready for Payment only after the Attendee accepts the proposed dishes."},
        {"source_id": "FR-3.19", "text": "The system MUST block payment for orders with unresolved or rejected requests."},
        {"source_id": "FR-3.22", "text": "The system MUST reject food changes after payment confirmation."},
        {"source_id": "FR-3.23", "text": "The system MUST show dietary labels as requests rather than medical or dietary certifications."}
      ]
    },
    {
      "id": "DA7-RQ-003",
      "name": "Staff updates and audience filtering",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-4",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines staff-update contents, role-specific privacy, persistence, reconnect behavior, notices, and email exclusions.",
      "exact_statements": [
        {"source_id": "FR-4.4", "text": "The system MUST show the order reference, state, change time, and paid-attendance effect in each staff update."},
        {"source_id": "FR-4.5", "text": "The system MUST show the cook the Attendee name, dish quantities, approved recipes, and food needs for confirmed orders."},
        {"source_id": "FR-4.7", "text": "The system MUST exclude Attendee names and private food notes from shopper views."},
        {"source_id": "FR-4.8", "text": "The system MUST mark unconfirmed orders as excluded from preparation and shopping totals."},
        {"source_id": "FR-4.9", "text": "The system MUST retain order updates while the event remains active."},
        {"source_id": "FR-4.10", "text": "The system MUST show the current event state and missed updates when staff reconnect."},
        {"source_id": "FR-4.11", "text": "The system MUST show a disconnected status with the last successful update time when a staff view loses its connection."},
        {"source_id": "FR-4.12", "text": "The system MUST send email notices for review decisions, booking confirmation, event cancellation, and refund results."},
        {"source_id": "FR-4.13", "text": "The system MUST keep notices available in the account if email delivery fails."},
        {"source_id": "FR-4.14", "text": "The system MUST exclude exact addresses and private food notes from email notices."}
      ]
    },
    {
      "id": "DA7-RQ-004",
      "name": "Identity, authorization, suspension, and staff assignment",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-6",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines verified-email access and all stated authorization relationships.",
      "exact_statements": [
        {"source_id": "FR-6.2", "text": "The system MUST require email verification before an account can place orders or create events."},
        {"source_id": "FR-6.3", "text": "The system MUST let a verified account sign in through an email link."},
        {"source_id": "FR-6.4", "text": "The system MUST let a signed-in account end its session."},
        {"source_id": "FR-6.6", "text": "The system MUST restrict changes to an event to its Organizer, except the Admin actions specified below."},
        {"source_id": "FR-6.7", "text": "The system MUST restrict order changes to the order's Attendee and the Organizer review actions specified above."},
        {"source_id": "FR-6.9", "text": "The system MUST let the event Organizer grant or remove cook and shopper assignments for verified accounts."},
        {"source_id": "FR-6.10", "text": "The system MUST restrict staff access to events with a current assignment."},
        {"source_id": "FR-6.11", "text": "The system MUST permit only an Admin to grant or remove the Admin role."},
        {"source_id": "FR-6.12", "text": "The system MUST let an Admin suspend an account from new events and orders."},
        {"source_id": "FR-6.13", "text": "The system MUST preserve cancellation and refund access for existing bookings when an account is suspended."},
        {"source_id": "FR-6.15", "text": "The system MUST let an Admin inspect payment and refund failures."},
        {"source_id": "FR-6.16", "text": "The system MUST reject an unauthorized action without changing the affected record."}
      ]
    },
    {
      "id": "DA7-RQ-005",
      "name": "Booking and payment integrity",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-8",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines capacity, holds, authoritative payment confirmation, deduplication, late or invalid payment handling, reconciliation, and connected-account status.",
      "exact_statements": [
        {"source_id": "FR-8.4", "text": "The system MUST reject checkout when confirmed bookings plus unexpired seat holds equal event capacity."},
        {"source_id": "FR-8.5", "text": "The system MUST prevent simultaneous checkout requests from reserving the same remaining seat."},
        {"source_id": "FR-8.9", "text": "The system MUST show the final USD price and cancellation terms before payment."},
        {"source_id": "FR-8.12", "text": "The system MUST confirm a booking only after the payment service confirms the correct amount and currency during a valid seat hold."},
        {"source_id": "FR-8.13", "text": "The system MUST record the payment reference and payment state against the order."},
        {"source_id": "FR-8.14", "text": "The system MUST create at most one confirmed booking from repeated payment confirmations for the same order."},
        {"source_id": "FR-8.15", "text": "The system MUST request a full refund for a payment received after hold expiry or event cancellation."},
        {"source_id": "FR-8.16", "text": "The system MUST request a full refund for an incorrect or duplicate payment."},
        {"source_id": "FR-8.17", "text": "The system MUST exclude payments awaiting validation from confirmed attendance."},
        {"source_id": "FR-8.19", "text": "The system MUST preserve a payment's Pending state while the payment service cannot determine its result."},
        {"source_id": "FR-8.20", "text": "The system MUST block another payment for an Attendee's event while that Attendee has an unresolved payment for the same event."},
        {"source_id": "FR-8.21", "text": "The system MUST let an Admin reconcile an unknown payment result against the payment service record."},
        {"source_id": "FR-8.24", "text": "The system MUST replace the seat hold with one confirmed booking when it confirms payment."}
      ]
    },
    {
      "id": "DA7-RQ-006",
      "name": "Cancellation, refund, and payout integrity",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-9",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines cancellation authorization, refund state and audience, retry bounds, financial views, payout eligibility, and duplicate prevention.",
      "exact_statements": [
        {"source_id": "FR-9.1", "text": "The system MUST let an Attendee cancel a confirmed booking before the booking cutoff."},
        {"source_id": "FR-9.2", "text": "The system MUST reject Attendee cancellation at or after the booking cutoff."},
        {"source_id": "FR-9.7", "text": "The system MUST request a full refund for each paid booking when an event is cancelled."},
        {"source_id": "FR-9.9", "text": "The system MUST show a failed refund to the affected Attendee, event Organizer, and Admin."},
        {"source_id": "FR-9.10", "text": "The system MUST let an Admin retry a failed refund without exceeding the amount originally paid."},
        {"source_id": "FR-9.12", "text": "The system MUST show the Organizer collected payments, refunds, payment service fees, and net proceeds for each event."},
        {"source_id": "FR-9.13", "text": "The system MUST request the Organizer's payout after event completion, excluding unresolved payments and amounts owed as refunds."},
        {"source_id": "FR-9.15", "text": "The system MUST notify the Organizer and Admin when a payout fails."},
        {"source_id": "FR-9.16", "text": "The system MUST cap total refunds for each payment at the amount received."},
        {"source_id": "FR-9.17", "text": "The system MUST let an Admin retry a failed payout."},
        {"source_id": "FR-9.18", "text": "The system MUST prevent repeated payout requests from paying the same event proceeds more than once."}
      ]
    },
    {
      "id": "DA7-RQ-007",
      "name": "Privacy and records",
      "authority": "REQUIREMENTS.md functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, FR-11",
      "document_status": "Adopted first-release behavior; not implementation evidence",
      "applicability_evidence": "Defines public and per-Attendee data boundaries, audit, deletion, retention, financial exclusion, and consent withdrawal.",
      "exact_statements": [
        {"source_id": "FR-11.1", "text": "The system MUST exclude orders, dietary requests, payment records, and staff updates from public event pages."},
        {"source_id": "FR-11.2", "text": "The system MUST show each Attendee only their own order and payment records."},
        {"source_id": "FR-11.3", "text": "The system MUST record the actor, time, and outcome of event, order, staff-assignment, and financial state changes."},
        {"source_id": "FR-11.4", "text": "The system MUST remove private food notes 90 days after event completion or cancellation."},
        {"source_id": "FR-11.5", "text": "The system MUST retain payment references, amounts, states, and financial action records for 24 months after their last change."},
        {"source_id": "FR-11.6", "text": "The system MUST exclude private food notes from retained financial records."},
        {"source_id": "FR-11.7", "text": "The system MUST let an Attendee withdraw consent for food notes by cancelling an eligible booking and deleting those notes."}
      ]
    },
    {
      "id": "DA7-RQ-008",
      "name": "Security-relevant quality requirements",
      "authority": "REQUIREMENTS.md non-functional requirements",
      "edition": "No edition stated",
      "source": "REQUIREMENTS.md, NFR-1-NFR-3",
      "document_status": "First-release acceptance targets; not measured results",
      "applicability_evidence": "Constrains refund independence, restart durability, capacity, availability, deterministic totals, and live-update focus.",
      "exact_statements": [
        {"source_id": "NFR-1.5", "text": "The system MUST submit an authorized refund request to an available payment service within one minute."},
        {"source_id": "NFR-2.1", "text": "The system MUST preserve acknowledged event and order changes across page reloads and service restarts."},
        {"source_id": "NFR-2.2", "text": "The system MUST keep confirmed bookings plus unexpired seat holds at or below event capacity under simultaneous requests."},
        {"source_id": "NFR-2.3", "text": "The system MUST produce identical ingredient totals for identical confirmed orders, recipes, and calculation rules."},
        {"source_id": "NFR-2.4", "text": "The system MUST provide public event reads and signed-in account reads for at least 99.5% of each calendar month."},
        {"source_id": "NFR-3.6", "text": "The system MUST preserve reading position and keyboard focus when a live update arrives."}
      ]
    },
    {
      "id": "DA7-RQ-009",
      "name": "Isolated provider gateways",
      "authority": "Confirmed architecture instruction",
      "edition": "No edition stated",
      "source": "ARCHITECTURE.md §2, §8 Isolated outbound gateways, DR-9, §9",
      "document_status": "CONFIRMED logical boundary; implementation absent",
      "applicability_evidence": "Governs all payment and email integration dependencies and execution isolation.",
      "exact_statements": [
        {"source_id": "ARCH-ISO-001", "text": "Payment outbound integration must be fully isolated from email integration, as explicitly required."},
        {"source_id": "DR-9", "text": "Only financial workflows may call the payment outbound port; only its dedicated gateway may make outbound payment-provider calls. Identity and notice workflows use the distinct email port and gateway. No dependency, invocation, shared provider client, credentials or mutable retry/failure state may cross between the two gateways. Inbound payment callbacks enter workflows through their separate adapter."}
      ]
    },
    {
      "id": "DA7-RQ-010",
      "name": "Security-relevant rendering constraints",
      "authority": "DESIGN.md interaction and rendering specification",
      "edition": "alpha",
      "source": "DESIGN.md, Components and Do's and Don'ts",
      "document_status": "ASSUMPTION-based design intent; implementation absent",
      "applicability_evidence": "Constrains how consent, private data, financial states, labels, errors, and live updates are presented.",
      "exact_statements": [
        {"source_id": "DESIGN-001", "text": "Keep consent separate."},
        {"source_id": "DESIGN-002", "text": "Reveal the exact address only to the allowed audience."},
        {"source_id": "DESIGN-003", "text": "Separate booking state from refund state. Keep a pending or failed refund visible after cancellation."},
        {"source_id": "DESIGN-004", "text": "Do not expose private food notes in public cards, shopper views, or email presentations."},
        {"source_id": "DESIGN-005", "text": "Do not use a diet label or the logo as proof that food is medically suitable."}
      ]
    }
  ],
  "risks": [
    {"id": "DA7-RISK-001", "statement": "Payment provider cannot support required refunds or payout timing.", "consequence": "Blocks the financial design; resolve capability fit before integration (AQ-3).", "rating": "Not supplied", "document_status": "Architecture risk", "evidence_ids": ["DA7-E-002"]},
    {"id": "DA7-RISK-002", "statement": "Polling or work dispatch misses required deadlines.", "consequence": "Proposed mechanisms remain unvalidated; test at the stated load before accepting them (AQ-5, AQ-6).", "rating": "Not supplied", "document_status": "Architecture risk", "evidence_ids": ["DA7-E-002"]},
    {"id": "DA7-RISK-003", "statement": "Private notes survive in snapshots or operational records.", "consequence": "Retention obligations may be violated; settle classification and deletion coverage (AQ-7).", "rating": "Not supplied", "document_status": "Architecture risk", "evidence_ids": ["DA7-E-002"]},
    {"id": "DA7-RISK-004", "statement": "Native scope and supplied technology labels remain ambiguous.", "consequence": "Implementation boundaries remain provisional (AQ-1, AQ-2).", "rating": "Not supplied", "document_status": "Architecture risk", "evidence_ids": ["DA7-E-002"]}
  ],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [
    {"id": "DA7-VIZ-001", "name": "Component and trust-boundary diagram", "type": "Mermaid flowchart", "source": "ARCHITECTURE.md §5", "document_status": "Payment/email gateway separation CONFIRMED; other internal boundaries PROPOSED; native scope unresolved", "depicts_record_ids": ["DA7-Z-001", "DA7-Z-003", "DA7-Z-004", "DA7-Z-005", "DA7-Z-006", "DA7-Z-007", "DA7-B-001", "DA7-B-002", "DA7-B-003", "DA7-B-004"]},
    {"id": "DA7-VIZ-002", "name": "Checkout and payment-result sequence", "type": "Mermaid sequence diagram", "source": "ARCHITECTURE.md §6", "document_status": "Logical runtime design; provider, persistence, and implementation unresolved", "depicts_record_ids": ["DA7-F-005", "DA7-F-007", "DA7-ACT-003", "DA7-ACT-007", "DA7-AS-003", "DA7-AS-004"]}
  ],
  "coverage": [
    {"id": "DA7-COV-001", "subject": "Document inventory", "status": "complete", "details": "Four supplied documents inventoried with type, author/date gaps, edition, authority, and state status."},
    {"id": "DA7-COV-002", "subject": "Ten extraction categories", "status": "complete", "details": "Assets, actors, data, flows, trust boundaries, threats, controls, assumptions, requirements, and gaps were evaluated for each document."},
    {"id": "DA7-COV-003", "subject": "Existing threats and prior threat methods", "status": "none supplied", "details": "No prior threat model or named prior threat-analysis method was supplied; four architecture risks were preserved without converting them into verified vulnerabilities."},
    {"id": "DA7-COV-004", "subject": "Implementation evidence", "status": "absent", "details": "No control is marked implemented or effective."},
    {"id": "DA7-COV-005", "subject": "Requirements extraction", "status": "security-relevant exact subset", "details": "Exact statements are retained for public/private data, consent, staff views, authorization, payment/financial integrity, records, quality, provider isolation, and rendering behavior; non-security business requirements remain available in DA7-E-001."}
  ],
  "conflicts": [
    {
      "id": "DA7-CON-001",
      "topic": "Node.js and Fastify technical roles",
      "source_values": [
        {"evidence_id": "DA7-E-002", "locator": "Required Architecture Inputs", "value": "Developer input names Fastify as the server runtime and Node.js as the server framework."},
        {"evidence_id": "DA7-E-002", "locator": "§4 and AQ-1", "value": "Node.js runtime with Fastify framework is a PROPOSED reinterpretation pending acceptance."},
        {"evidence_id": "DA7-E-003", "locator": "Secure-Coding Inputs and OD-001", "value": "The role conflict is unresolved; version scopes are UNKNOWN."}
      ],
      "resolution": "TO BE DECIDED; neither label is discarded or silently corrected."
    }
  ],
  "gaps": [
    {"id": "DA7-G-001", "topic": "Document metadata", "missing": "Authors and dates for all four files; editions for REQUIREMENTS.md, ARCHITECTURE.md, and SECURITY.md.", "needed_documentation": "Document ownership and revision metadata.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003", "DA7-E-004"]},
    {"id": "DA7-G-002", "topic": "Implementation and runtime evidence", "missing": "Source code, runtime/deployment configuration, tests, logs, control observations, and operational evidence.", "needed_documentation": "Implementation artifacts and control-verification results once implementation exists.", "evidence_ids": ["DA7-E-002", "DA7-E-003", "DA7-E-004"]},
    {"id": "DA7-G-003", "topic": "Technology, versions, and compatibility", "missing": "Resolved Node.js/Fastify roles and versions; React, React Native, language/toolchain, validation, authentication, data-access, policy-engine, and container decisions.", "needed_documentation": "Approved technology/version decision record resolving AQ-1, AQ-2, AQ-5 and OD-001, OD-002, OD-004, OD-005, OD-006, OD-007, OD-008, OD-012.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-004", "topic": "Identity and authorization", "missing": "Verification/sign-in link lifecycle, session lifetime and revocation, first Admin provisioning, authorization implementation, mobile credential transport, and passkey scope.", "needed_documentation": "Approved identity, session, Admin-bootstrap, and authorization contract.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-005", "topic": "Provider contracts", "missing": "Payment and email providers, exact data fields, authentication and callback verification, reconciliation, delivery, idempotency, retention, fees, refunds, payouts, and capability evidence.", "needed_documentation": "Provider selection ADRs and interface/data-lifecycle contracts.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-006", "topic": "API and native surface", "missing": "Approved API style and schemas, endpoint authorization declarations, request/response fields, native platforms, workflow parity, link handling, storage, printing, and accessibility mapping.", "needed_documentation": "Versioned API specification and approved native-scope specification.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-007", "topic": "Persistence and execution", "missing": "Accepted database/data-access choice, schema, record relationships, constraints, locking, transactions, durable-work retry/reconciliation, and execution settings.", "needed_documentation": "Database schema, transaction/consistency design, and durable-work runbook or ADR.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-008", "topic": "Deployment and operations", "missing": "Hosting, topology, network boundaries, secrets, operational identities and access, build/release controls, monitoring, incident response, backup, restore, and disaster recovery.", "needed_documentation": "Deployment/network diagram, operational access and secrets policy, build/release procedure, monitoring plan, incident-response runbook, and backup/restore specification.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-009", "topic": "Update transport", "missing": "Acceptance of polling, replay protocol, paging, cursor semantics, authorization enforcement, retry behavior, and evidence that timing targets are met.", "needed_documentation": "Approved update/replay protocol and load-test results.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-010", "topic": "Privacy lifecycle and legal scope", "missing": "Applicable jurisdictions and duties; private-note versus recipe/handling classification; complete data inventory; notice and consent details; derived/cached/exported/backup deletion; audit/update/notice/address retention and readers.", "needed_documentation": "Approved data inventory and classification, purpose/recipient map, notice and consent specification, retention/deletion matrix including backups, and authoritative legal-applicability record.", "evidence_ids": ["DA7-E-001", "DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-011", "topic": "Risk method and ownership", "missing": "Approved likelihood/impact method, risk acceptance rules, and owners for architecture/security decisions; SECURITY.md marks all OD owners UNKNOWN.", "needed_documentation": "Risk-method record and decision/control ownership register without inventing deadlines.", "evidence_ids": ["DA7-E-002", "DA7-E-003"]},
    {"id": "DA7-G-012", "topic": "Browser and design validation", "missing": "Browser support, rendering mode, responsive breakpoints, final brand assets, typeface rights, native equivalents, and rendered accessibility/security verification.", "needed_documentation": "Approved browser/rendering support matrix, resolved DQ-1-DQ-3, and rendered interaction/accessibility test evidence.", "evidence_ids": ["DA7-E-002", "DA7-E-003", "DA7-E-004"]}
  ]
}
```

## Summary

### Documents processed

- `REQUIREMENTS.md` is the current behavioral authority in the supplied set. It defines actors, data objects, workflows, state machines, audience restrictions, consent, audit, deletion, retention, and measurable acceptance requirements. Its ASSUMPTION entries are adopted first-release decisions, not observed facts. Provider selection and legal scope remain unknown (`DA7-E-001`).
- `ARCHITECTURE.md` is an undated arc42 logical design for a system with no implementation. Payment/email gateway isolation is CONFIRMED. The modular monolith, PostgreSQL, HTTP JSON API, server sessions, cursor polling, transactions, durable work, audience projections, and reference-only note propagation are PROPOSED. AQ-1 through AQ-8 remain unresolved (`DA7-E-002`).
- `SECURITY.md` records intake status and implementation blockers. SC-001 through SC-009 are all BLOCKED, candidate technology packs are TO BE DECIDED, and OD-001 through OD-012 have UNKNOWN owners. It supplies no implemented or tested security control (`DA7-E-003`).
- `DESIGN.md` is an alpha visual and interaction specification. It preserves requirement-driven state and audience distinctions, presents consent separately, prohibits private data in public/shopper/email presentations, and defines accessible state rendering. Its visual choices are assumptions; DQ-1 through DQ-3 remain open (`DA7-E-004`).

The normalized system model contains eight assets, eight actors, seven data groups, seven zones, five boundaries, nine flows, seven entry-point groups, nineteen control records, ten exact requirement groups, four existing architecture risks, and two source visualization records. No prior threat model or named prior threat-analysis method was supplied, so `threats`, `attack_trees`, and `attack_paths` are empty rather than inferred.

### Document status and extracted claims

Required behavior is preserved as intended product behavior, never as proof that a control exists. The one confirmed architecture decision is the logical separation of payment and email gateways (`DA7-C-001`, `DA7-RQ-009`). Authorization, filtering, consent, financial invariants, audit, deletion, retention, and rendering constraints are required but unimplemented (`DA7-C-002`, `DA7-C-004` through `DA7-C-006`, `DA7-C-009`). Server projections, durable work, server-side sessions, and private-note references are proposals (`DA7-C-003`, `DA7-C-007`, `DA7-C-008`, `DA7-C-010`). The nine secure-coding entries remain BLOCKED (`DA7-C-011` through `DA7-C-019`).

Exact security-relevant requirements are retained in `DA7-RQ-001` through `DA7-RQ-010` with authority, edition, source, applicability, and document status. They cover public and private event data, food-needs consent and review, staff updates, identity and authorization, booking/payment integrity, refunds/payouts, privacy records, quality constraints, confirmed gateway isolation, and rendering behavior. The complete product requirement set remains attributable to `DA7-E-001`; requirements unrelated to the modeled assets, boundaries, and controls were not duplicated into the compact fragment.

### Conflicts and contradictions

`DA7-CON-001` preserves the unresolved Node.js/Fastify role-label conflict. The developer input labels Fastify as runtime and Node.js as framework; the architecture proposes the conventional inverse interpretation, while `SECURITY.md` keeps the matter unresolved. No source is silently preferred. No other material contradiction was found: apparent differences between required behavior, proposed mechanisms, and blocked implementation rules are status distinctions rather than disagreements.

### Documentation gaps

The supplied set lacks document authors and most dates (`DA7-G-001`), all implementation and runtime evidence (`DA7-G-002`), resolved technology scope and versions (`DA7-G-003`), identity/session/Admin-bootstrap detail (`DA7-G-004`), provider contracts (`DA7-G-005`), API and native specifications (`DA7-G-006`), persistence and durable-execution design (`DA7-G-007`), deployment and operational material (`DA7-G-008`), an approved update protocol and validation (`DA7-G-009`), full privacy lifecycle and legal-scope evidence (`DA7-G-010`), a risk method and owners (`DA7-G-011`), and browser/design validation (`DA7-G-012`). Missing material is not treated as a vulnerability or as proof of non-compliance.

### Additional documentation needed

The gaps call for an approved decision record for technology and versions; identity, session, Admin-bootstrap, and authorization contracts; payment and email provider contracts; a versioned API and native-scope specification; a database schema and consistency design; durable-work and update/replay specifications; deployment, network, secrets, operational-access, incident-response, and backup/restore documentation; a complete data inventory, classification, notice/consent, recipient, and retention/deletion matrix; load and control-verification results; a risk method and ownership register; and a resolved browser/rendering support matrix with interaction and accessibility test evidence. These documentation needs carry no invented owner or deadline.
