# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "L2-SCOPE-001",
    "system": "Picky Party first-release cooking-event website specification",
    "analysis_method": "LINDDUN",
    "analysis_date": "2026-10-19",
    "included_artifacts": [
      "L2-E-001",
      "L2-E-002",
      "L2-E-003",
      "L2-E-004"
    ],
    "included_surfaces": [
      "Public event and calendar views and permanent QR URLs",
      "Authenticated event, order, staff, account, and administration workflows",
      "Email-link identity and notice flows",
      "Payment, refund, payout, and payment-callback boundaries",
      "Specified records, updates, audit data, retention, consent, and deletion behavior"
    ],
    "excluded_or_unresolved": [
      "No implementation exists, so control implementation or effectiveness was not assessed",
      "Native application workflows and platforms are unresolved",
      "Providers, deployment topology, persistence choice, operational access, and detailed session behavior are unresolved",
      "Applicable jurisdictions and statutory duties are unknown; this is not a legal or compliance assessment"
    ]
  },
  "evidence": [
    {
      "id": "L2-E-001",
      "artifact": "REQUIREMENTS.md",
      "revision": "No document edition or date stated; repository state read 2026-10-19",
      "locators": [
        "Required Requirement Inputs",
        "Product Rules and Terms",
        "FR-1.14",
        "FR-2.8-FR-2.12",
        "FR-2.15",
        "FR-3.2-FR-3.10",
        "FR-3.13-FR-3.23",
        "FR-4.1-FR-4.14",
        "FR-5.1-FR-5.10",
        "FR-6.1-FR-6.17",
        "FR-7.9-FR-7.10",
        "FR-8.10-FR-8.23",
        "FR-9.1-FR-9.18",
        "FR-11.1-FR-11.7"
      ],
      "covers": "Authoritative first-release behavior, actors, data objects, audience restrictions, consent, public presentation, financial records, audit, retention, and deletion requirements.",
      "limits": "Requirements marked ASSUMPTION are adopted product decisions rather than measured facts. Providers and legal scope remain unknown. The file specifies intended behavior, not implemented controls."
    },
    {
      "id": "L2-E-002",
      "artifact": "ARCHITECTURE.md",
      "revision": "No document edition or date stated; repository state read 2026-10-19",
      "locators": [
        "§1 Introduction and Goals",
        "§3 Context and Scope",
        "§5 Building Block View",
        "§6 Runtime View",
        "§7 Deployment View",
        "§8 API and frontend",
        "§8 Persistence and consistency",
        "§8 Isolated outbound gateways",
        "§8 Authentication and privacy boundaries",
        "§11 Risks and Technical Debt",
        "AQ-2-AQ-8"
      ],
      "covers": "Logical actors, components, trust boundaries, proposed records and flows, confirmed payment/email gateway isolation, server projections, and architecture risks and gaps.",
      "limits": "The architecture explicitly describes a system with no implementation. Most component, persistence, session, polling, and retention-copy mechanisms are PROPOSED or TO BE DECIDED and are not treated as implemented or effective."
    },
    {
      "id": "L2-E-003",
      "artifact": "SECURITY.md",
      "revision": "No document edition or date stated; repository state read 2026-10-19",
      "locators": [
        "Secure-Coding Inputs",
        "Secure-Coding Rules SC-001-SC-009",
        "OD-001-OD-012"
      ],
      "covers": "Security evidence status, blocked secure-coding rules, and unresolved identity, authorization, provider, persistence, deployment, privacy-lifecycle, update, and rendering decisions.",
      "limits": "All secure-coding rules are BLOCKED. Candidate technology notes are not project facts, and no implementation control is established."
    },
    {
      "id": "L2-E-004",
      "artifact": "DESIGN.md",
      "revision": "version alpha; repository state read 2026-10-19",
      "locators": [
        "Overview",
        "Typography",
        "Layout",
        "Components",
        "Do's and Don'ts",
        "Open Questions"
      ],
      "covers": "Specified rendering of account, event, food-request, review, checkout, staff, and administration views; separate consent presentation; public/private field presentation rules.",
      "limits": "No application implementation exists. Visual arrangements and tokens are assumptions, and brand/browser/native details remain unresolved."
    }
  ],
  "system": {
    "assets": [
      {
        "id": "L2-AS-001",
        "name": "Account identity and access",
        "data_ids": ["L2-D-001", "L2-D-002"]
      },
      {
        "id": "L2-AS-002",
        "name": "Event location and participation privacy",
        "data_ids": ["L2-D-003", "L2-D-004", "L2-D-006"]
      },
      {
        "id": "L2-AS-003",
        "name": "Food-needs confidentiality and consent",
        "data_ids": ["L2-D-005", "L2-D-006", "L2-D-010"]
      },
      {
        "id": "L2-AS-004",
        "name": "Financial and booking privacy",
        "data_ids": ["L2-D-007", "L2-D-008"]
      },
      {
        "id": "L2-AS-005",
        "name": "Activity and audit privacy",
        "data_ids": ["L2-D-009", "L2-D-011"]
      }
    ],
    "actors": [
      {"id": "L2-ACT-001", "name": "Visitor", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-002", "name": "Account holder", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-003", "name": "Organizer", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-004", "name": "Attendee", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-005", "name": "Cook assignment", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-006", "name": "Shopper assignment", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-007", "name": "Admin", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-008", "name": "Payment service", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-ACT-009", "name": "Email service", "evidence_ids": ["L2-E-001", "L2-E-002"]}
    ],
    "data": [
      {"id": "L2-D-001", "name": "Account display name and email address", "classification": "Personal data; finer classification not supplied", "evidence_ids": ["L2-E-001"]},
      {"id": "L2-D-002", "name": "Verification records, sign-in links, and sessions", "classification": "Access data; implementation and lifecycle unresolved", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
      {"id": "L2-D-003", "name": "Public event metadata", "fields": ["title", "description", "Organizer name", "menu", "schedule", "city", "country", "price", "cutoff", "available seats", "calendar booking state", "cancellation notice"], "evidence_ids": ["L2-E-001"]},
      {"id": "L2-D-004", "name": "Exact event address and optional access instructions", "classification": "Restricted by audience requirement", "evidence_ids": ["L2-E-001"]},
      {"id": "L2-D-005", "name": "Dietary labels, explicit restrictions, ingredient exclusions, cross-contact concerns, special needs, preferences, omissions, and private food notes", "classification": "Private dietary data by adopted requirement input; exact private-note boundary unresolved", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
      {"id": "L2-D-006", "name": "Orders, proposals, accepted recipes, handling notes, bookings, and attendance state", "classification": "Non-public personal and event data; finer classification unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-D-007", "name": "Payment, refund, payout, fee, amount, state, and provider references", "classification": "Non-public financial records; retained fields specified", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-D-008", "name": "Seat holds, checkout state, booking references, and receipts", "classification": "Non-public account and transaction data", "evidence_ids": ["L2-E-001"]},
      {"id": "L2-D-009", "name": "Staff update history, cursors, account notices, and delivery state", "classification": "Audience-filtered operational records; post-event retention unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-D-010", "name": "Consent and withdrawal state for food-note sharing", "classification": "Consent record; detailed notice and lifecycle unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-D-011", "name": "Actor, time, and outcome audit records", "classification": "Attributable activity records; nonfinancial retention and audiences unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]}
    ],
    "zones": [
      {"id": "L2-Z-001", "name": "Public client zone", "status": "Specified logical audience", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-Z-002", "name": "Authenticated client and role-specific view zone", "status": "Specified logical audience; client implementation absent", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-Z-003", "name": "Application boundary", "status": "Logical design; implementation absent", "evidence_ids": ["L2-E-002"]},
      {"id": "L2-Z-004", "name": "Persistent records boundary", "status": "Proposed logical store; technology and deployment unresolved", "evidence_ids": ["L2-E-002", "L2-E-003"]},
      {"id": "L2-Z-005", "name": "External payment provider zone", "status": "Required integration; provider unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-Z-006", "name": "External email provider zone", "status": "Required integration; provider unresolved", "evidence_ids": ["L2-E-001", "L2-E-002"]}
    ],
    "boundaries": [
      {"id": "L2-B-001", "name": "Public client to application", "from_zone_ids": ["L2-Z-001"], "to_zone_ids": ["L2-Z-003"], "evidence_ids": ["L2-E-002"]},
      {"id": "L2-B-002", "name": "Authenticated client to application and audience projection", "from_zone_ids": ["L2-Z-002"], "to_zone_ids": ["L2-Z-003"], "evidence_ids": ["L2-E-001", "L2-E-002"]},
      {"id": "L2-B-003", "name": "Application to persistence", "from_zone_ids": ["L2-Z-003"], "to_zone_ids": ["L2-Z-004"], "evidence_ids": ["L2-E-002"]},
      {"id": "L2-B-004", "name": "Isolated payment integration", "from_zone_ids": ["L2-Z-003"], "to_zone_ids": ["L2-Z-005"], "evidence_ids": ["L2-E-002"]},
      {"id": "L2-B-005", "name": "Separate email integration", "from_zone_ids": ["L2-Z-003"], "to_zone_ids": ["L2-Z-006"], "evidence_ids": ["L2-E-002"]},
      {"id": "L2-B-006", "name": "Public, Attendee, Organizer, cook, shopper, and Admin audience boundaries", "from_zone_ids": ["L2-Z-003"], "to_zone_ids": ["L2-Z-001", "L2-Z-002"], "evidence_ids": ["L2-E-001", "L2-E-002"]}
    ],
    "flows": [
      {
        "id": "L2-F-001",
        "name": "Publish and discover events",
        "source_actor_ids": ["L2-ACT-003"],
        "destination_actor_ids": ["L2-ACT-001"],
        "data_ids": ["L2-D-003"],
        "purpose": "Advertise launched events and support calendar discovery through permanent public URLs and QR codes.",
        "boundary_ids": ["L2-B-001", "L2-B-006"],
        "control_ids": ["L2-C-001", "L2-C-002"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
        "unresolved_facts": ["No public-profile or display-name privacy choices are specified", "Public URL identifier characteristics are not specified"]
      },
      {
        "id": "L2-F-002",
        "name": "Create account, verify email, and sign in through email link",
        "source_actor_ids": ["L2-ACT-002"],
        "destination_actor_ids": ["L2-ACT-009"],
        "data_ids": ["L2-D-001", "L2-D-002"],
        "purpose": "Create and verify an account and provide email-link access.",
        "boundary_ids": ["L2-B-002", "L2-B-005"],
        "control_ids": ["L2-C-004", "L2-C-010"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"],
        "unresolved_facts": ["Email provider", "Link contents and lifecycle", "Session lifetime and revocation behavior", "First Admin provisioning", "Native credential transport"]
      },
      {
        "id": "L2-F-003",
        "name": "Create and expose event location",
        "source_actor_ids": ["L2-ACT-003"],
        "destination_actor_ids": ["L2-ACT-003", "L2-ACT-004", "L2-ACT-005", "L2-ACT-006", "L2-ACT-007"],
        "data_ids": ["L2-D-004"],
        "purpose": "Create the event and provide its exact location to the Organizer, assigned staff, confirmed Attendees, and Admin.",
        "boundary_ids": ["L2-B-002", "L2-B-006"],
        "control_ids": ["L2-C-002", "L2-C-004"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
        "unresolved_facts": ["Address visibility timing within each permitted audience", "Post-event address retention", "Download, print, cache, and notification handling"]
      },
      {
        "id": "L2-F-004",
        "name": "Submit, review, accept, and preserve food needs",
        "source_actor_ids": ["L2-ACT-004"],
        "destination_actor_ids": ["L2-ACT-003", "L2-ACT-005", "L2-ACT-004"],
        "data_ids": ["L2-D-005", "L2-D-006", "L2-D-010"],
        "purpose": "Collect food needs, enable Organizer review and Attendee acceptance, and prepare an accepted recipe for a paid booking.",
        "boundary_ids": ["L2-B-002", "L2-B-003", "L2-B-006"],
        "control_ids": ["L2-C-003", "L2-C-004", "L2-C-008", "L2-C-009"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
        "unresolved_facts": ["Exact boundary between private food notes and retained recipes or handling notes", "Consent notice contents, purpose granularity, and consent record details", "Withdrawal handling when a booking is no longer eligible for cancellation"]
      },
      {
        "id": "L2-F-005",
        "name": "Deliver staff updates and preparation or shopping views",
        "source_actor_ids": ["L2-ACT-004", "L2-ACT-003"],
        "destination_actor_ids": ["L2-ACT-005", "L2-ACT-006"],
        "data_ids": ["L2-D-005", "L2-D-006", "L2-D-009"],
        "purpose": "Give currently assigned staff current preparation information and durable updates.",
        "boundary_ids": ["L2-B-002", "L2-B-003", "L2-B-006"],
        "control_ids": ["L2-C-004", "L2-C-005", "L2-C-009"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
        "unresolved_facts": ["Update transport", "Replay and paging implementation", "Whether initial cook updates before confirmation contain food-need details", "Post-event update retention"]
      },
      {
        "id": "L2-F-006",
        "name": "Checkout and validate payment",
        "source_actor_ids": ["L2-ACT-004"],
        "destination_actor_ids": ["L2-ACT-008"],
        "data_ids": ["L2-D-006", "L2-D-007", "L2-D-008"],
        "purpose": "Collect the event price for one seat and confirm a booking from validated payment evidence.",
        "boundary_ids": ["L2-B-002", "L2-B-003", "L2-B-004"],
        "control_ids": ["L2-C-004", "L2-C-006", "L2-C-011"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003", "L2-E-004"],
        "unresolved_facts": ["Payment provider", "Provider data fields and purposes", "Callback authenticity contract", "Provider retention"]
      },
      {
        "id": "L2-F-007",
        "name": "Cancel, refund, reconcile, and pay out",
        "source_actor_ids": ["L2-ACT-004", "L2-ACT-003", "L2-ACT-007", "L2-ACT-008"],
        "destination_actor_ids": ["L2-ACT-004", "L2-ACT-003", "L2-ACT-007", "L2-ACT-008"],
        "data_ids": ["L2-D-006", "L2-D-007", "L2-D-008", "L2-D-011"],
        "purpose": "Cancel eligible bookings or events, refund payments, reconcile unknown results, and pay event proceeds.",
        "boundary_ids": ["L2-B-002", "L2-B-003", "L2-B-004", "L2-B-006"],
        "control_ids": ["L2-C-004", "L2-C-006", "L2-C-007", "L2-C-011"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"],
        "unresolved_facts": ["Provider contract and provider-side data lifecycle", "Detailed Admin financial-view fields", "Operational access"]
      },
      {
        "id": "L2-F-008",
        "name": "Persist account notices and send email notices",
        "source_actor_ids": ["L2-ACT-003", "L2-ACT-004", "L2-ACT-007"],
        "destination_actor_ids": ["L2-ACT-002", "L2-ACT-009"],
        "data_ids": ["L2-D-001", "L2-D-006", "L2-D-007", "L2-D-009"],
        "purpose": "Notify affected account holders of review decisions, booking confirmations, event cancellations, refund results, and payout failures.",
        "boundary_ids": ["L2-B-003", "L2-B-005", "L2-B-006"],
        "control_ids": ["L2-C-005", "L2-C-011"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
        "unresolved_facts": ["Email provider", "Complete notice field sets", "Account-notice retention", "Email-provider retention and secondary processing"]
      },
      {
        "id": "L2-F-009",
        "name": "Audit state changes and apply record lifecycle",
        "source_actor_ids": ["L2-ACT-002", "L2-ACT-003", "L2-ACT-004", "L2-ACT-005", "L2-ACT-006", "L2-ACT-007"],
        "destination_actor_ids": ["L2-ACT-007"],
        "data_ids": ["L2-D-005", "L2-D-007", "L2-D-009", "L2-D-010", "L2-D-011"],
        "purpose": "Record actor, time, and outcome for required state changes; remove private food notes; retain specified financial records.",
        "boundary_ids": ["L2-B-003", "L2-B-006"],
        "control_ids": ["L2-C-007", "L2-C-008", "L2-C-009"],
        "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"],
        "unresolved_facts": ["Audit readers", "Nonfinancial audit retention", "Derived-record and backup deletion coverage", "Private-note classification", "Post-event notice and update retention"]
      }
    ],
    "entry_points": [
      {"id": "L2-EP-001", "name": "Public calendar, event page, and permanent QR URL", "flow_ids": ["L2-F-001"]},
      {"id": "L2-EP-002", "name": "Account creation, verification, and email-link sign-in", "flow_ids": ["L2-F-002"]},
      {"id": "L2-EP-003", "name": "Authenticated event, order, consent, review, and account interactions", "flow_ids": ["L2-F-003", "L2-F-004"]},
      {"id": "L2-EP-004", "name": "Cook and shopper views, reconnect, and update replay", "flow_ids": ["L2-F-005"]},
      {"id": "L2-EP-005", "name": "Checkout browser flow and payment callback adapter", "flow_ids": ["L2-F-006"]},
      {"id": "L2-EP-006", "name": "Organizer and Admin financial actions", "flow_ids": ["L2-F-007"]},
      {"id": "L2-EP-007", "name": "Account notices and external email delivery", "flow_ids": ["L2-F-008"]},
      {"id": "L2-EP-008", "name": "Scheduled retention and authorized audit access", "flow_ids": ["L2-F-009"]}
    ]
  },
  "methods": [
    {
      "id": "L2-M-001",
      "name": "LINDDUN",
      "threat_types": [
        "Linking",
        "Identifying",
        "Non-repudiation",
        "Detecting",
        "Data disclosure",
        "Unawareness and unintervenability",
        "Non-compliance"
      ],
      "disposition_rule": "finding means a system-specific scenario is supported; assessed-no-additional-finding means the evidence was examined but did not support a separate threat; evidence-gap means required facts are missing; not-applicable includes a rationale.",
      "flow_assessments": [
        {"flow_id": "L2-F-001", "Linking": "finding:L2-TH-001", "Identifying": "finding:L2-TH-002", "Non-repudiation": "assessed-no-additional-finding", "Detecting": "finding:L2-TH-004", "Data disclosure": "assessed-no-additional-finding; public fields are the intended flow", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-002", "Linking": "assessed-no-additional-finding", "Identifying": "assessed-no-additional-finding; account identification is explicit", "Non-repudiation": "assessed-no-additional-finding", "Detecting": "assessed-no-additional-finding", "Data disclosure": "evidence-gap:L2-G-002", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-003", "Linking": "assessed-no-additional-finding", "Identifying": "assessed-no-additional-finding", "Non-repudiation": "assessed-no-additional-finding", "Detecting": "assessed-no-additional-finding", "Data disclosure": "finding:L2-TH-005", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-004", "Linking": "finding:L2-TH-003", "Identifying": "finding:L2-TH-003", "Non-repudiation": "assessed-no-additional-finding; attributable audit is assessed in L2-F-009", "Detecting": "assessed-no-additional-finding", "Data disclosure": "finding:L2-TH-006", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-005", "Linking": "finding:L2-TH-003", "Identifying": "finding:L2-TH-003", "Non-repudiation": "assessed-no-additional-finding; attributable audit is assessed in L2-F-009", "Detecting": "assessed-no-additional-finding; current-assignment restriction is specified", "Data disclosure": "finding:L2-TH-006", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-006", "Linking": "assessed-no-additional-finding", "Identifying": "assessed-no-additional-finding", "Non-repudiation": "finding:L2-TH-007", "Detecting": "assessed-no-additional-finding", "Data disclosure": "evidence-gap:L2-G-002", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-007", "Linking": "assessed-no-additional-finding", "Identifying": "assessed-no-additional-finding", "Non-repudiation": "finding:L2-TH-007", "Detecting": "assessed-no-additional-finding", "Data disclosure": "evidence-gap:L2-G-002", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-008", "Linking": "assessed-no-additional-finding", "Identifying": "assessed-no-additional-finding", "Non-repudiation": "assessed-no-additional-finding", "Detecting": "assessed-no-additional-finding", "Data disclosure": "evidence-gap:L2-G-002", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"},
        {"flow_id": "L2-F-009", "Linking": "finding:L2-TH-007", "Identifying": "finding:L2-TH-007", "Non-repudiation": "finding:L2-TH-007", "Detecting": "assessed-no-additional-finding", "Data disclosure": "finding:L2-TH-008", "Unawareness and unintervenability": "evidence-gap:L2-G-003", "Non-compliance": "evidence-gap:L2-G-001"}
      ]
    }
  ],
  "threats": [
    {
      "id": "L2-TH-001",
      "linddun_type": "Linking",
      "scenario": "A visitor can use a permanent public event URL and its retained cancellation notice to correlate the same event over time with its public Organizer name, city, schedule, menu, price, availability, and state.",
      "affected_record_ids": ["L2-AS-002", "L2-ACT-001", "L2-ACT-003", "L2-D-003", "L2-F-001", "L2-EP-001"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-001", "L2-RQ-002", "L2-RQ-003"],
      "evidence_ids": ["L2-E-001", "L2-E-002"],
      "control_ids": ["L2-C-001"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-001"]
    },
    {
      "id": "L2-TH-002",
      "linddun_type": "Identifying",
      "scenario": "The public event page directly publishes the Organizer name together with event details, allowing visitors to identify the named Organizer's association with the event.",
      "affected_record_ids": ["L2-AS-001", "L2-AS-002", "L2-ACT-001", "L2-ACT-003", "L2-D-001", "L2-D-003", "L2-F-001"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-001", "L2-RQ-003"],
      "evidence_ids": ["L2-E-001"],
      "control_ids": ["L2-C-001"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-002"]
    },
    {
      "id": "L2-TH-003",
      "linddun_type": "Identifying",
      "scenario": "The cook view combines an Attendee name with confirmed-order food needs, quantities, approved recipes, and handling information, directly identifying whose food requirements are represented. Food-note sharing is consent-gated, but implementation and effectiveness are not established.",
      "affected_record_ids": ["L2-AS-003", "L2-ACT-004", "L2-ACT-005", "L2-D-001", "L2-D-005", "L2-D-006", "L2-F-004", "L2-F-005"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-004", "L2-RQ-005", "L2-RQ-006"],
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
      "control_ids": ["L2-C-003", "L2-C-004"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-003"]
    },
    {
      "id": "L2-TH-004",
      "linddun_type": "Detecting",
      "scenario": "Any visitor can detect that a launched event exists and observe its time, city, price, booking availability, and later cancellation state through the public calendar and permanent event URL.",
      "affected_record_ids": ["L2-AS-002", "L2-ACT-001", "L2-D-003", "L2-F-001", "L2-EP-001"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-001", "L2-RQ-002", "L2-RQ-003"],
      "evidence_ids": ["L2-E-001"],
      "control_ids": ["L2-C-001"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-004"]
    },
    {
      "id": "L2-TH-005",
      "linddun_type": "Data disclosure",
      "scenario": "The system discloses the exact event address to each confirmed Attendee, current assigned staff member, the Organizer, and Admin. This is required access, but it exposes precise location information to multiple account and assignment audiences.",
      "affected_record_ids": ["L2-AS-002", "L2-ACT-003", "L2-ACT-004", "L2-ACT-005", "L2-ACT-006", "L2-ACT-007", "L2-D-004", "L2-F-003"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-007", "L2-RQ-008"],
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
      "control_ids": ["L2-C-002", "L2-C-004"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-005"]
    },
    {
      "id": "L2-TH-006",
      "linddun_type": "Data disclosure",
      "scenario": "Private food information crosses from the Attendee to the Organizer and cook, and confirmed cook views display it with identity and handling details. The intended sharing is consent-gated, while shopper and email outputs have explicit exclusions.",
      "affected_record_ids": ["L2-AS-003", "L2-ACT-003", "L2-ACT-004", "L2-ACT-005", "L2-D-005", "L2-D-006", "L2-D-010", "L2-F-004", "L2-F-005"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-004", "L2-RQ-005", "L2-RQ-006", "L2-RQ-009", "L2-RQ-010"],
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"],
      "control_ids": ["L2-C-003", "L2-C-004", "L2-C-005"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-006"]
    },
    {
      "id": "L2-TH-007",
      "linddun_type": "Non-repudiation",
      "scenario": "Required audit records bind an actor, time, and outcome to event, order, staff-assignment, and financial state changes; retained payment references, amounts, states, and financial action records preserve attributable evidence for 24 months after their last change.",
      "affected_record_ids": ["L2-AS-004", "L2-AS-005", "L2-ACT-002", "L2-ACT-003", "L2-ACT-004", "L2-ACT-005", "L2-ACT-006", "L2-ACT-007", "L2-D-007", "L2-D-011", "L2-F-006", "L2-F-007", "L2-F-009"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-011", "L2-RQ-012", "L2-RQ-013"],
      "evidence_ids": ["L2-E-001", "L2-E-002"],
      "control_ids": ["L2-C-007", "L2-C-008"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-007"]
    },
    {
      "id": "L2-TH-008",
      "linddun_type": "Data disclosure",
      "scenario": "The architecture records a risk that private food notes may survive in snapshots or operational records, while the exact private-note classification and deletion coverage across derived records and backups remain unresolved. A proposed reference-only design is not a confirmed or implemented control.",
      "affected_record_ids": ["L2-AS-003", "L2-AS-005", "L2-D-005", "L2-D-006", "L2-D-009", "L2-D-011", "L2-F-009"],
      "implicated_interests_or_requirement_ids": ["L2-RQ-014", "L2-RQ-015", "L2-RQ-016"],
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"],
      "control_ids": ["L2-C-008", "L2-C-009"],
      "assumptions": [],
      "risk_ids": ["L2-RISK-008"]
    }
  ],
  "controls": [
    {
      "id": "L2-C-001",
      "name": "Public projection minimization",
      "claim": "Public views show the specified event and calendar fields and exclude orders, dietary requests, payment records, staff updates, and exact addresses.",
      "status": "Required design behavior; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"]
    },
    {
      "id": "L2-C-002",
      "name": "Exact-address audience restriction",
      "claim": "Exact event addresses are restricted to the Organizer, assigned staff, confirmed Attendees, and Admin.",
      "status": "Required design behavior; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002"]
    },
    {
      "id": "L2-C-003",
      "name": "Consent before food-needs sharing",
      "claim": "Consent is required before sharing food needs with the event Organizer and cook, and the design presents consent separately.",
      "status": "Required design behavior; notice details and implementation unresolved",
      "evidence_ids": ["L2-E-001", "L2-E-004"]
    },
    {
      "id": "L2-C-004",
      "name": "Ownership, role, and current-assignment checks",
      "claim": "Protected actions and reads are restricted by order ownership, event ownership, role, suspension, and current event assignment; unauthorized actions must not change records.",
      "status": "Required behavior with proposed server enforcement; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]
    },
    {
      "id": "L2-C-005",
      "name": "Audience-specific field filtering",
      "claim": "Shopper views exclude Attendee names and private food notes; email notices exclude exact addresses and private food notes.",
      "status": "Required design behavior; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"]
    },
    {
      "id": "L2-C-006",
      "name": "Attendee record isolation",
      "claim": "Each Attendee sees only their own order and payment records.",
      "status": "Required design behavior; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002"]
    },
    {
      "id": "L2-C-007",
      "name": "Attributable state-change audit",
      "claim": "Actor, time, and outcome are recorded for event, order, staff-assignment, and financial state changes.",
      "status": "Required behavior; audit audience, nonfinancial retention, and implementation unresolved",
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]
    },
    {
      "id": "L2-C-008",
      "name": "Specified deletion and financial retention",
      "claim": "Private food notes are removed 90 days after event completion or cancellation; specified financial records are retained for 24 months after last change without private food notes; eligible cancellation withdraws consent and deletes notes.",
      "status": "Required behavior; classification, derived-copy, backup, and withdrawal coverage unresolved; not implemented or tested",
      "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]
    },
    {
      "id": "L2-C-009",
      "name": "Reference-only private-note propagation",
      "claim": "Updates, jobs, and audit records refer to owning private-note records instead of copying note content.",
      "status": "PROPOSED architecture control; unconfirmed and not implemented",
      "evidence_ids": ["L2-E-002", "L2-E-003"]
    },
    {
      "id": "L2-C-010",
      "name": "Revocable server-side sessions",
      "claim": "The browser holds only an opaque identifier for a server-stored revocable session.",
      "status": "PROPOSED; exact link and session lifecycle unresolved; not implemented",
      "evidence_ids": ["L2-E-002", "L2-E-003"]
    },
    {
      "id": "L2-C-011",
      "name": "Payment and email gateway isolation",
      "claim": "Payment and email use separate gateways, clients, credentials, configuration, retry state, and execution capacity; payment callbacks enter through a distinct adapter.",
      "status": "Confirmed architecture boundary; provider contracts and implementation unresolved",
      "evidence_ids": ["L2-E-002", "L2-E-003"]
    }
  ],
  "requirements": [
    {"id": "L2-RQ-001", "source_id": "FR-2.8", "text": "The system MUST publish a launched event at a permanent public URL.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Event Launch and Advertising", "applicability_evidence": "Defines the public flow in L2-F-001."},
    {"id": "L2-RQ-002", "source_id": "FR-2.15", "text": "The system MUST retain a cancelled event's public URL with a cancellation notice.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Event Launch and Advertising", "applicability_evidence": "Defines persistent public event-state visibility in L2-F-001."},
    {"id": "L2-RQ-003", "source_id": "FR-2.11", "text": "The system MUST show the title, description, Organizer name, menu, schedule, city, country, price, cutoff, and available seats on the public page.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Event Launch and Advertising", "applicability_evidence": "Enumerates public fields implicated by L2-TH-001, L2-TH-002, and L2-TH-004."},
    {"id": "L2-RQ-004", "source_id": "FR-3.10", "text": "The system MUST require consent before sharing food needs with the event Organizer and cook.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Food Orders and Guest Needs", "applicability_evidence": "Governs L2-F-004 and the consent control for named food-needs sharing."},
    {"id": "L2-RQ-005", "source_id": "FR-4.5", "text": "The system MUST show the cook the Attendee name, dish quantities, approved recipes, and food needs for confirmed orders.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Order Updates", "applicability_evidence": "Directly establishes L2-TH-003 and part of L2-TH-006."},
    {"id": "L2-RQ-006", "source_id": "FR-6.10", "text": "The system MUST restrict staff access to events with a current assignment.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Accounts, Roles, and Staff", "applicability_evidence": "Limits the staff audience in L2-F-003 and L2-F-005."},
    {"id": "L2-RQ-007", "source_id": "FR-2.12", "text": "The system MUST restrict the exact event address to its Organizer, assigned staff, confirmed Attendees, and Admin.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Event Launch and Advertising", "applicability_evidence": "Establishes the audience and restriction for L2-TH-005."},
    {"id": "L2-RQ-008", "source_id": "FR-11.1", "text": "The system MUST exclude orders, dietary requests, payment records, and staff updates from public event pages.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Constrains the public projection in L2-F-001."},
    {"id": "L2-RQ-009", "source_id": "FR-4.7", "text": "The system MUST exclude Attendee names and private food notes from shopper views.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Order Updates", "applicability_evidence": "Limits food-needs disclosure in L2-F-005."},
    {"id": "L2-RQ-010", "source_id": "FR-4.14", "text": "The system MUST exclude exact addresses and private food notes from email notices.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Order Updates", "applicability_evidence": "Limits external-email disclosure in L2-F-008."},
    {"id": "L2-RQ-011", "source_id": "FR-11.3", "text": "The system MUST record the actor, time, and outcome of event, order, staff-assignment, and financial state changes.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Directly establishes attributable records in L2-TH-007."},
    {"id": "L2-RQ-012", "source_id": "FR-11.5", "text": "The system MUST retain payment references, amounts, states, and financial action records for 24 months after their last change.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Defines duration for financial evidence implicated by L2-TH-007."},
    {"id": "L2-RQ-013", "source_id": "FR-11.6", "text": "The system MUST exclude private food notes from retained financial records.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Constrains retained financial records in L2-F-009."},
    {"id": "L2-RQ-014", "source_id": "FR-11.4", "text": "The system MUST remove private food notes 90 days after event completion or cancellation.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Defines the deletion outcome whose copy coverage is unresolved in L2-TH-008."},
    {"id": "L2-RQ-015", "source_id": "FR-11.7", "text": "The system MUST let an Attendee withdraw consent for food notes by cancelling an eligible booking and deleting those notes.", "authority": "Project functional requirement", "edition": "Not stated", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Defines the supplied withdrawal interaction and deletion behavior in L2-F-004 and L2-F-009."},
    {"id": "L2-RQ-016", "source_id": "AQ-7", "text": "Jurisdictions are UNKNOWN. Exact classification of private food notes versus retained recipe/handling data, deletion across derived records/backups, and post-event retention of nonfinancial notices/updates are TO BE DECIDED in coordination with SECURITY.md. Required 90-day deletion, consent withdrawal, financial exclusion and 24-month retention remain binding.", "authority": "Project architecture open question", "edition": "Not stated", "source": "ARCHITECTURE.md, Open Questions", "applicability_evidence": "Explicitly establishes the unresolved lifecycle facts in L2-TH-008 and L2-G-004."}
  ],
  "risks": [
    {"id": "L2-RISK-001", "threat_ids": ["L2-TH-001"], "statement": "Persistent public correlation can reveal an Organizer's event activity and changes over time.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-002", "threat_ids": ["L2-TH-002"], "statement": "Publishing the Organizer name exposes the named person's association with a particular event to any visitor.", "likelihood": "The disclosure is required for launched events; observation likelihood beyond that is UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-003", "threat_ids": ["L2-TH-003"], "statement": "A cook can associate an identified Attendee with detailed food needs and handling information.", "likelihood": "The view is required for current cooks on confirmed orders; misuse likelihood is UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-004", "threat_ids": ["L2-TH-004"], "statement": "Public discovery reveals event existence, coarse location, schedule, availability, and cancellation state.", "likelihood": "The disclosure is required for launched events; observation likelihood beyond that is UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-005", "threat_ids": ["L2-TH-005"], "statement": "Members of the permitted event audience learn the precise event location and may retain it outside the system; the specifications do not define downstream handling.", "likelihood": "The disclosure to permitted audiences is required; downstream retention is UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001", "L2-E-002"]},
    {"id": "L2-RISK-006", "threat_ids": ["L2-TH-006"], "statement": "Food-needs disclosure can reveal potentially sensitive personal circumstances to the Organizer and cook.", "likelihood": "The disclosure occurs for consented food-needs workflows; misuse likelihood is UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-007", "threat_ids": ["L2-TH-007"], "statement": "Attributable audit and financial histories reduce actors' ability to deny recorded actions and retain linkages between people and event or financial activity.", "likelihood": "Required record creation is specified; access and use likelihood are UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-RISK-008", "threat_ids": ["L2-TH-008"], "statement": "Private food-note copies may remain in derived records, operational records, or backups beyond withdrawal or the 90-day deletion point if lifecycle coverage is incomplete.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]}
  ],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [],
  "coverage": [
    {"id": "L2-COV-001", "subject": "Evidence artifacts", "status": "complete", "details": "All four supplied specifications were read and cataloged as L2-E-001 through L2-E-004."},
    {"id": "L2-COV-002", "subject": "Modeled flows", "status": "complete for specified logical flows", "details": "L2-F-001 through L2-F-009 cover public discovery, identity/email access, event address, food needs, staff views, payment, settlement, notices, and audit/lifecycle."},
    {"id": "L2-COV-003", "subject": "All seven LINDDUN threat types", "status": "complete", "details": "Every type was dispositioned for every modeled flow in L2-M-001."},
    {"id": "L2-COV-004", "subject": "Implementation controls", "status": "not assessed", "details": "No implementation exists; requirements and architecture claims are not treated as implemented or effective."},
    {"id": "L2-COV-005", "subject": "Native application", "status": "not assessed", "details": "React Native is a named choice, but native workflow and platform scope are unresolved."},
    {"id": "L2-COV-006", "subject": "Legal compliance", "status": "not assessed", "details": "Jurisdictions, statutory duties, and applicability evidence are unknown; no compliance conclusion is made."}
  ],
  "conflicts": [
    {
      "id": "L2-CON-001",
      "topic": "Node.js and Fastify role labels",
      "source_values": [
        {"evidence_id": "L2-E-002", "locator": "Required Architecture Inputs and AQ-1", "value": "Developer input names Fastify as runtime and Node.js as server framework."},
        {"evidence_id": "L2-E-002", "locator": "§4 and AQ-1", "value": "The architecture proposes interpreting Node.js as runtime and Fastify as framework, pending a decision."}
      ],
      "privacy_effect": "No direct privacy finding is inferred; unresolved implementation scope contributes to blocked server and update controls in SECURITY.md."
    }
  ],
  "gaps": [
    {"id": "L2-G-001", "topic": "Legal scope and compliance", "missing_evidence": "Applicable jurisdictions, statutory duties, legal bases, rights, and authoritative applicability evidence.", "effect": "Non-compliance cannot be assessed, and no compliance or non-compliance finding is made.", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
    {"id": "L2-G-002", "topic": "Provider data scope and lifecycle", "missing_evidence": "Selected payment and email providers; exact transferred fields; provider purposes, recipients, retention, callback authenticity, reconciliation, and delivery contracts.", "effect": "Provider-bound disclosure, linking, identifying, and retention risk cannot be determined beyond the existence and purpose of the specified flows.", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
    {"id": "L2-G-003", "topic": "Transparency, choice, and intervention", "missing_evidence": "Notice content and timing for account, public Organizer, address, financial, audit, provider, and retention processing; consent purpose granularity and record details; correction/export mechanisms; food-note withdrawal behavior when cancellation is no longer eligible.", "effect": "Unawareness and unintervenability cannot be resolved beyond the explicit food-note consent, separate consent presentation, request-label wording, and eligible-cancellation withdrawal requirements.", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-004"]},
    {"id": "L2-G-004", "topic": "Private food-note classification and deletion coverage", "missing_evidence": "Exact boundary between private notes and retained recipes or handling notes; all stores, derived data, updates, audit records, jobs, caches, exports, and backups; deletion and restoration behavior.", "effect": "The 90-day deletion and eligible-withdrawal outcomes cannot be shown to cover every copy.", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
    {"id": "L2-G-005", "topic": "Access and retention for operational records", "missing_evidence": "Readers and retention for nonfinancial audit records, notices, staff updates, and event addresses after event completion or cancellation; operational-administrator access.", "effect": "The duration and audience of linkable and attributable records cannot be fully assessed.", "evidence_ids": ["L2-E-001", "L2-E-002", "L2-E-003"]},
    {"id": "L2-G-006", "topic": "Identity and session lifecycle", "missing_evidence": "Email-link contents, expiry, reuse, revocation, session lifetime, session revocation behavior, first Admin provisioning, and native credential transport.", "effect": "Privacy properties of identity correlation and access to account data cannot be fully assessed.", "evidence_ids": ["L2-E-002", "L2-E-003"]},
    {"id": "L2-G-007", "topic": "Staff update contents before confirmation", "missing_evidence": "FR-4.1 requires an update to the cook when an order is placed, while FR-4.5 enumerates named food-needs content for confirmed orders; the exact pre-confirmation cook-update fields are not specified.", "effect": "Pre-confirmation food-needs disclosure to the cook cannot be determined.", "evidence_ids": ["L2-E-001"]},
    {"id": "L2-G-008", "topic": "Implementation and effectiveness", "missing_evidence": "Application code, deployed topology, runtime configuration, tests, logs, and operational evidence.", "effect": "No specified or proposed control can be treated as implemented or effective.", "evidence_ids": ["L2-E-002", "L2-E-003", "L2-E-004"]},
    {"id": "L2-G-009", "topic": "Native application scope", "missing_evidence": "Native workflows, platforms, parity, link handling, printing, storage, and accessibility mapping.", "effect": "Native privacy flows and threats are not assessed.", "evidence_ids": ["L2-E-002", "L2-E-003"]}
  ]
}
```

## Summary

### Scope and evidence limits

This LINDDUN analysis covers the specified first-release website flows in `REQUIREMENTS.md`, the logical architecture in `ARCHITECTURE.md`, the blocked security decisions in `SECURITY.md`, and the alpha interaction specification in `DESIGN.md` (`L2-E-001` through `L2-E-004`). No implementation exists. Required behaviors, confirmed logical gateway separation, and proposed controls were modeled as document claims with their stated status; none was treated as implemented or effective. Native scope, providers, deployment, persistence, operational access, detailed identity/session behavior, and legal scope remain unresolved. This is not a legal or compliance assessment.

### Personal-data-flow overview

The model contains nine flows. Launched-event metadata passes from an Organizer to every visitor through public calendar entries, permanent URLs, and QR codes (`L2-F-001`). Account display names, email addresses, verification records, sign-in links, and sessions cross the application and external email boundary (`L2-F-002`). Exact event addresses pass to Organizers, current assigned staff, confirmed Attendees, and Admin (`L2-F-003`). Attendee food needs, consent, proposals, accepted recipes, and handling information move through review and then into cook and shopper projections with different field sets (`L2-F-004`, `L2-F-005`). Booking and financial data cross the payment boundary for checkout, confirmation, refunds, reconciliation, and payouts (`L2-F-006`, `L2-F-007`). Required notices cross the email boundary (`L2-F-008`). Audit, deletion, and retention processing acts on attributable state changes, private food notes, operational records, and retained financial records (`L2-F-009`).

### LINDDUN coverage matrix

Codes: `F` = evidenced finding, `A` = assessed with no separate supported finding, `G` = evidence gap. The identifiers point to the JSON records above.

| Type | F-001 public | F-002 identity | F-003 address | F-004 food review | F-005 staff views | F-006 payment | F-007 settlement | F-008 notices | F-009 records |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Linking | F `L2-TH-001` | A | A | F `L2-TH-003` | F `L2-TH-003` | A | A | A | F `L2-TH-007` |
| Identifying | F `L2-TH-002` | A | A | F `L2-TH-003` | F `L2-TH-003` | A | A | A | F `L2-TH-007` |
| Non-repudiation | A | A | A | A | A | F `L2-TH-007` | F `L2-TH-007` | A | F `L2-TH-007` |
| Detecting | F `L2-TH-004` | A | A | A | A | A | A | A | A |
| Data disclosure | A | G `L2-G-002` | F `L2-TH-005` | F `L2-TH-006` | F `L2-TH-006` | G `L2-G-002` | G `L2-G-002` | G `L2-G-002` | F `L2-TH-008` |
| Unawareness and unintervenability | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` | G `L2-G-003` |
| Non-compliance | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` | G `L2-G-001` |

Every current LINDDUN type was dispositioned for every modeled flow in `L2-M-001`. Non-compliance was not assessed because no jurisdiction, statutory duty, legal basis, rights regime, or authoritative applicability evidence was supplied.

### Evidenced threats and risks

Eight system-specific privacy threats are supported. Permanent URLs and retained cancellation pages let visitors link an event and its public metadata over time (`L2-TH-001`), while the required Organizer name directly identifies the named Organizer's association with that event (`L2-TH-002`). Cook views identify an Attendee alongside food needs, recipes, quantities, and handling information (`L2-TH-003`). Public calendar and event pages reveal the existence, city, schedule, availability, and cancellation state of launched events (`L2-TH-004`). Exact addresses are disclosed to the specified multi-role audience (`L2-TH-005`). Food needs are disclosed to the Organizer and cook under the specified consent and assignment controls (`L2-TH-006`). Required audit and retained financial records create attributable histories that reduce repudiability (`L2-TH-007`). Finally, the architecture itself records the risk that private notes may survive in snapshots or operational records while deletion coverage and classification remain unresolved (`L2-TH-008`).

Each threat has a corresponding risk record (`L2-RISK-001` through `L2-RISK-008`). No likelihood score, impact score, owner, deadline, or overall risk rating was supplied, so none was invented.

### Requirement traceability and control status

Exact project requirements implicated by the findings are recorded as `L2-RQ-001` through `L2-RQ-016`, including public URL and field requirements, consent, named cook views, staff assignment limits, address restrictions, shopper/email exclusions, audit, deletion, retention, consent withdrawal, and architecture privacy-lifecycle uncertainty. These are project requirements and an architecture open question; no external legal requirement was asserted.

The model records eleven control claims. Public-field minimization, exact-address audience restriction, consent, ownership and current-assignment checks, shopper/email filtering, Attendee record isolation, audit, and deletion/retention are required design behavior (`L2-C-001` through `L2-C-008`). Reference-only propagation of private notes and revocable server-side sessions are proposals (`L2-C-009`, `L2-C-010`). Payment/email gateway isolation is a confirmed architecture boundary (`L2-C-011`). None is implemented or tested, and `SECURITY.md` keeps all secure-coding rules blocked.

### Conflicts and open gaps

The only retained source conflict is the Node.js/Fastify role-label conflict and its pending proposed reinterpretation (`L2-CON-001`); no privacy finding was inferred from it. Material privacy gaps are legal scope (`L2-G-001`), provider data and lifecycle contracts (`L2-G-002`), transparency and intervention details (`L2-G-003`), private-note classification and deletion coverage (`L2-G-004`), operational-record access and retention (`L2-G-005`), identity and session lifecycle (`L2-G-006`), pre-confirmation cook-update fields (`L2-G-007`), all implementation and effectiveness evidence (`L2-G-008`), and native scope (`L2-G-009`). These gaps are not treated as proof of a vulnerability or non-compliance.
