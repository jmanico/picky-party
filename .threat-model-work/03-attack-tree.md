# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "AT3-SCOPE-001",
    "system": "Picky Party first-release cooking-event website specification",
    "analysis_method": "Evidence-traceable AND/OR attack trees",
    "analysis_date": "2026-10-19",
    "included_evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003", "AT3-E-004"],
    "limits": [
      "No implementation exists; control claims are not treated as implemented or effective",
      "Only roots and branches tied to supplied assets, adverse objectives, requirements, architecture risks, or explicit boundaries are included",
      "No approved likelihood, impact, cost, skill, detectability, access, or path-comparison method was supplied",
      "No CAPEC identifier is recorded because no identifier and name were verified against supplied authoritative CAPEC material",
      "Legal scope, providers, deployment, persistence, detailed session behavior, and native scope are unresolved"
    ]
  },
  "evidence": [
    {
      "id": "AT3-E-001",
      "artifact": "REQUIREMENTS.md",
      "revision": "No edition or date stated; repository state read 2026-10-19",
      "locators": ["FR-2.12", "FR-4.5", "FR-4.7", "FR-4.9-FR-4.14", "FR-6.7", "FR-6.10", "FR-6.16", "FR-8.4-FR-8.5", "FR-8.12-FR-8.24", "FR-9.10", "FR-9.16-FR-9.18", "FR-11.1-FR-11.7"],
      "covers": "Authoritative behavior for privacy audiences, authorization, capacity, payment confirmation, refund and payout bounds, audit, deletion, and retention.",
      "limits": "Specifies intended first-release behavior, not implementation evidence; provider and jurisdiction facts remain unknown."
    },
    {
      "id": "AT3-E-002",
      "artifact": "ARCHITECTURE.md",
      "revision": "No edition or date stated; repository state read 2026-10-19",
      "locators": ["§3 Context and Scope", "§5 Building Block View", "§6 Runtime View", "§7 Deployment View", "§8 Persistence and consistency", "§8 Isolated outbound gateways", "§8 Authentication and privacy boundaries", "DR-1-DR-9", "§11 Risks and Technical Debt", "AQ-1-AQ-8"],
      "covers": "Logical trust boundaries, entry paths, proposed server projections, payment evidence processing, callback/reconciliation flows, and explicit risk that private notes may survive in snapshots or operational records.",
      "limits": "The document describes a system with no implementation. Most mechanisms are PROPOSED or TO BE DECIDED."
    },
    {
      "id": "AT3-E-003",
      "artifact": "SECURITY.md",
      "revision": "No edition or date stated; repository state read 2026-10-19",
      "locators": ["Secure-Coding Inputs", "SC-001-SC-009", "OD-001-OD-012"],
      "covers": "Blocked secure-coding controls and unresolved identity, authorization, persistence, provider, deployment, privacy-lifecycle, update, and rendering decisions.",
      "limits": "All SC rules are BLOCKED, and no implementation or effective technical control is established."
    },
    {
      "id": "AT3-E-004",
      "artifact": "DESIGN.md",
      "revision": "version alpha; repository state read 2026-10-19",
      "locators": ["Overview", "Components", "Do's and Don'ts", "Open Questions"],
      "covers": "Specified public/private rendering, role-specific views, checkout state presentation, and prohibition on exposing private notes through public, shopper, or email presentations.",
      "limits": "No application implementation exists; visual arrangements and tokens are assumptions."
    }
  ],
  "system": {
    "assets": [
      {"id": "AT3-AS-001", "name": "Restricted personal, dietary, payment, staff-update, and exact-address data", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-AS-002", "name": "Booking, seat-capacity, and payment-confirmation integrity", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-AS-003", "name": "Refund and payout funds and accounting integrity", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-AS-004", "name": "Private food-note deletion and consent-withdrawal outcome", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]}
    ],
    "actors": [
      {"id": "AT3-ACT-001", "name": "Visitor", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-002", "name": "Attendee account", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-003", "name": "Organizer", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-004", "name": "Cook or shopper assignment", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-005", "name": "Admin", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-006", "name": "Payment service", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-ACT-007", "name": "Unauthorized requester", "description": "An actor lacking the audience entitlement required for the requested record or action; capability, motivation, and access are unknown.", "evidence_ids": ["AT3-E-001"]}
    ],
    "data": [
      {"id": "AT3-D-001", "name": "Exact event address", "evidence_ids": ["AT3-E-001"]},
      {"id": "AT3-D-002", "name": "Orders, dietary requests, private food notes, recipes, and handling notes", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-D-003", "name": "Payment records and staff updates", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-D-004", "name": "Seat holds, bookings, payment evidence, amount, currency, and provider references", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-D-005", "name": "Refund, payout, fee, reconciliation, and financial action records", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-D-006", "name": "Updates, jobs, audit records, snapshots, derived records, and backups that may reference or copy private notes", "evidence_ids": ["AT3-E-002", "AT3-E-003"]}
    ],
    "zones": [
      {"id": "AT3-Z-001", "name": "Public client zone", "status": "Specified logical zone"},
      {"id": "AT3-Z-002", "name": "Authenticated and role-specific client zone", "status": "Specified logical zone; implementation absent"},
      {"id": "AT3-Z-003", "name": "Application and authorized-read zone", "status": "Logical design; implementation absent"},
      {"id": "AT3-Z-004", "name": "Persistent record zone", "status": "Proposed; technology and deployment unresolved"},
      {"id": "AT3-Z-005", "name": "External payment-service zone", "status": "Required integration; provider unresolved"}
    ],
    "boundaries": [
      {"id": "AT3-B-001", "name": "Public client to application", "from_zone_ids": ["AT3-Z-001"], "to_zone_ids": ["AT3-Z-003"], "evidence_ids": ["AT3-E-002"]},
      {"id": "AT3-B-002", "name": "Authenticated audience to application", "from_zone_ids": ["AT3-Z-002"], "to_zone_ids": ["AT3-Z-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-B-003", "name": "Application to persistence", "from_zone_ids": ["AT3-Z-003"], "to_zone_ids": ["AT3-Z-004"], "evidence_ids": ["AT3-E-002"]},
      {"id": "AT3-B-004", "name": "Payment gateway and callback boundary", "from_zone_ids": ["AT3-Z-003"], "to_zone_ids": ["AT3-Z-005"], "evidence_ids": ["AT3-E-002"]}
    ],
    "flows": [
      {"id": "AT3-F-001", "name": "Public event and calendar read", "data_ids": ["AT3-D-001", "AT3-D-002", "AT3-D-003"], "boundary_ids": ["AT3-B-001"], "intended_result": "Return only approved public event fields", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-F-002", "name": "Attendee account order and payment read", "data_ids": ["AT3-D-002", "AT3-D-003"], "boundary_ids": ["AT3-B-002"], "intended_result": "Return only the Attendee's own records", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-F-003", "name": "Staff current-state and missed-update replay", "data_ids": ["AT3-D-001", "AT3-D-002", "AT3-D-003"], "boundary_ids": ["AT3-B-002", "AT3-B-003"], "intended_result": "Return the current role-specific projection only for a current assignment", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-F-004", "name": "Checkout, callback, and payment reconciliation", "data_ids": ["AT3-D-004"], "boundary_ids": ["AT3-B-002", "AT3-B-003", "AT3-B-004"], "intended_result": "Confirm at most one booking only after correct provider evidence during a valid hold", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-F-005", "name": "Refund and payout request or retry", "data_ids": ["AT3-D-005"], "boundary_ids": ["AT3-B-002", "AT3-B-003", "AT3-B-004"], "intended_result": "Do not refund more than received or pay the same proceeds twice", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
      {"id": "AT3-F-006", "name": "Private-note copy, withdrawal, scheduled deletion, and retention", "data_ids": ["AT3-D-002", "AT3-D-006"], "boundary_ids": ["AT3-B-003"], "intended_result": "Delete private food notes on eligible withdrawal and 90 days after event completion or cancellation, without retaining copies in financial records", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]}
    ],
    "entry_points": [
      {"id": "AT3-EP-001", "name": "Public event and calendar endpoints", "flow_ids": ["AT3-F-001"]},
      {"id": "AT3-EP-002", "name": "Authenticated account-read endpoints", "flow_ids": ["AT3-F-002"]},
      {"id": "AT3-EP-003", "name": "Staff polling or reconnect replay endpoint", "flow_ids": ["AT3-F-003"]},
      {"id": "AT3-EP-004", "name": "Checkout browser return, payment callback adapter, and reconciliation workflow", "flow_ids": ["AT3-F-004"]},
      {"id": "AT3-EP-005", "name": "Admin retry and scheduled payout workflows", "flow_ids": ["AT3-F-005"]},
      {"id": "AT3-EP-006", "name": "Retention and deletion work", "flow_ids": ["AT3-F-006"]}
    ]
  },
  "methods": [
    {
      "id": "AT3-M-001",
      "name": "Attack tree decomposition",
      "rules": [
        "Each root is an adverse objective supported by a specified asset, protection requirement, or explicit architecture risk",
        "OR means any child branch is sufficient; AND means every child is required",
        "Conditional paths include explicit control-failure or unresolved-design assumptions because no implementation evidence exists",
        "Paths are enumerated without ranking because no comparison method or supported estimates were supplied"
      ]
    }
  ],
  "threats": [
    {"id": "AT3-TH-001", "name": "Obtain restricted data without the required audience entitlement", "asset_ids": ["AT3-AS-001"], "actor_ids": ["AT3-ACT-007"], "tree_id": "AT3-TREE-001", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-004"], "risk_ids": ["AT3-RISK-001"]},
    {"id": "AT3-TH-002", "name": "Create a confirmed booking without acceptable payment evidence and a valid seat hold", "asset_ids": ["AT3-AS-002"], "actor_ids": ["AT3-ACT-002", "AT3-ACT-007"], "tree_id": "AT3-TREE-002", "evidence_ids": ["AT3-E-001", "AT3-E-002"], "risk_ids": ["AT3-RISK-002"]},
    {"id": "AT3-TH-003", "name": "Cause refunds above the amount received or pay the same event proceeds more than once", "asset_ids": ["AT3-AS-003"], "actor_ids": ["AT3-ACT-003", "AT3-ACT-005", "AT3-ACT-006", "AT3-ACT-007"], "tree_id": "AT3-TREE-003", "evidence_ids": ["AT3-E-001", "AT3-E-002"], "risk_ids": ["AT3-RISK-003"]},
    {"id": "AT3-TH-004", "name": "Keep private food-note content accessible after required deletion or eligible consent withdrawal", "asset_ids": ["AT3-AS-004"], "actor_ids": ["AT3-ACT-007"], "tree_id": "AT3-TREE-004", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"], "risk_ids": ["AT3-RISK-004"]}
  ],
  "controls": [
    {"id": "AT3-C-001", "name": "Public-field exclusion", "status": "Required; not implemented or tested", "addresses_node_ids": ["AT3-N-004"], "claim": "Public pages exclude exact addresses, orders, dietary requests, payment records, and staff updates.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-004"]},
    {"id": "AT3-C-002", "name": "Attendee record ownership", "status": "Required; not implemented or tested", "addresses_node_ids": ["AT3-N-008"], "claim": "Each Attendee sees only their own order and payment records.", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-C-003", "name": "Current staff-assignment authorization", "status": "Required; not implemented or tested", "addresses_node_ids": ["AT3-N-012"], "claim": "Staff reads, including subsequent replay reads, require a current assignment.", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-C-004", "name": "Server audience projections", "status": "PROPOSED; not confirmed, implemented, or tested", "addresses_node_ids": ["AT3-N-004", "AT3-N-008", "AT3-N-012"], "claim": "Separate server projections filter data for public, Attendee, Organizer, cook, shopper, and Admin audiences.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-C-005", "name": "Authoritative payment validation and deduplication", "status": "Required behavior with PROPOSED enforcement; not implemented or tested", "addresses_node_ids": ["AT3-N-024", "AT3-N-027", "AT3-N-031"], "claim": "A browser return cannot confirm payment; workflows validate provider evidence, amount, currency, hold, and event state and deduplicate repeated confirmations.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-C-006", "name": "Capacity and hold consistency", "status": "Required behavior with PROPOSED transactional enforcement; not implemented or tested", "addresses_node_ids": ["AT3-N-030", "AT3-N-031"], "claim": "Confirmed bookings plus unexpired holds cannot exceed capacity, and confirmation replaces a valid hold atomically.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-C-007", "name": "Refund cap", "status": "Required; not implemented or tested", "addresses_node_ids": ["AT3-N-043", "AT3-N-044"], "claim": "Total refunds for a payment cannot exceed the amount received.", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-C-008", "name": "Payout deduplication", "status": "Required; not implemented or tested", "addresses_node_ids": ["AT3-N-047", "AT3-N-048"], "claim": "Repeated payout requests cannot pay the same event proceeds more than once.", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-C-009", "name": "Private-note deletion and financial exclusion", "status": "Required; copy coverage unresolved and not implemented or tested", "addresses_node_ids": ["AT3-N-063", "AT3-N-064", "AT3-N-067", "AT3-N-068"], "claim": "Private notes are deleted on eligible withdrawal and 90 days after completion or cancellation and excluded from retained financial records.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-C-010", "name": "Reference-only private-note propagation", "status": "PROPOSED; not confirmed, implemented, or tested", "addresses_node_ids": ["AT3-N-061", "AT3-N-062", "AT3-N-064"], "claim": "Updates, jobs, and audit records refer to the owning note rather than copying its content.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]}
  ],
  "requirements": [
    {"id": "AT3-RQ-001", "source_id": "FR-11.1", "text": "The system MUST exclude orders, dietary requests, payment records, and staff updates from public event pages.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Selects and constrains AT3-TREE-001 public-read branch."},
    {"id": "AT3-RQ-002", "source_id": "FR-2.12", "text": "The system MUST restrict the exact event address to its Organizer, assigned staff, confirmed Attendees, and Admin.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Event Launch and Advertising", "applicability_evidence": "Defines restricted address data in AT3-TREE-001."},
    {"id": "AT3-RQ-003", "source_id": "FR-11.2", "text": "The system MUST show each Attendee only their own order and payment records.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Selects and constrains AT3-TREE-001 cross-Attendee branch."},
    {"id": "AT3-RQ-004", "source_id": "FR-6.10", "text": "The system MUST restrict staff access to events with a current assignment.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Accounts, Roles, and Staff", "applicability_evidence": "Selects and constrains AT3-TREE-001 former-staff replay branch."},
    {"id": "AT3-RQ-005", "source_id": "FR-6.16", "text": "The system MUST reject an unauthorized action without changing the affected record.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Accounts, Roles, and Staff", "applicability_evidence": "Supports the unauthorized-requester root framing."},
    {"id": "AT3-RQ-006", "source_id": "FR-8.12", "text": "The system MUST confirm a booking only after the payment service confirms the correct amount and currency during a valid seat hold.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Seats and Payments", "applicability_evidence": "Defines the adverse objective for AT3-TREE-002."},
    {"id": "AT3-RQ-007", "source_id": "FR-8.14", "text": "The system MUST create at most one confirmed booking from repeated payment confirmations for the same order.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Seats and Payments", "applicability_evidence": "Constrains the repeated-evidence branch in AT3-TREE-002."},
    {"id": "AT3-RQ-008", "source_id": "FR-8.24", "text": "The system MUST replace the seat hold with one confirmed booking when it confirms payment.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Seats and Payments", "applicability_evidence": "Constrains the invalid-hold branch in AT3-TREE-002."},
    {"id": "AT3-RQ-009", "source_id": "NFR-2.2", "text": "The system MUST keep confirmed bookings plus unexpired seat holds at or below event capacity under simultaneous requests.", "authority": "Project non-functional requirement", "source": "REQUIREMENTS.md, Reliability and Consistency", "applicability_evidence": "Constrains the simultaneous last-seat branch in AT3-TREE-002."},
    {"id": "AT3-RQ-010", "source_id": "FR-9.16", "text": "The system MUST cap total refunds for each payment at the amount received.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Cancellations, Refunds, and Payouts", "applicability_evidence": "Defines the excess-refund branch in AT3-TREE-003."},
    {"id": "AT3-RQ-011", "source_id": "FR-9.18", "text": "The system MUST prevent repeated payout requests from paying the same event proceeds more than once.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Cancellations, Refunds, and Payouts", "applicability_evidence": "Defines the duplicate-payout branch in AT3-TREE-003."},
    {"id": "AT3-RQ-012", "source_id": "FR-11.4", "text": "The system MUST remove private food notes 90 days after event completion or cancellation.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Defines the required lifecycle outcome for AT3-TREE-004."},
    {"id": "AT3-RQ-013", "source_id": "FR-11.6", "text": "The system MUST exclude private food notes from retained financial records.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Constrains retained-copy handling in AT3-TREE-004."},
    {"id": "AT3-RQ-014", "source_id": "FR-11.7", "text": "The system MUST let an Attendee withdraw consent for food notes by cancelling an eligible booking and deleting those notes.", "authority": "Project functional requirement", "source": "REQUIREMENTS.md, Privacy and Records", "applicability_evidence": "Defines the eligible-withdrawal deletion outcome for AT3-TREE-004."}
  ],
  "risks": [
    {"id": "AT3-RISK-001", "threat_ids": ["AT3-TH-001"], "statement": "A public requester, another Attendee, or a former staff assignee may receive records outside the required audience if the relevant projection or authorization check fails.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-RISK-002", "threat_ids": ["AT3-TH-002"], "statement": "A booking may be confirmed from an untrusted browser return, invalid or replayed provider evidence, or an invalid over-capacity hold if specified validation, deduplication, or capacity controls fail.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-RISK-003", "threat_ids": ["AT3-TH-003"], "statement": "Repeated refund or payout execution may cause transfers beyond the amount or proceeds authorized if caps or deduplication fail.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["AT3-E-001", "AT3-E-002"]},
    {"id": "AT3-RISK-004", "threat_ids": ["AT3-TH-004"], "statement": "Private food-note content may remain in operational copies or records classified as retained recipe or handling data after the source is deleted.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "score": "Not assigned", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]}
  ],
  "attack_trees": [
    {
      "id": "AT3-TREE-001",
      "threat_id": "AT3-TH-001",
      "root_node_id": "AT3-N-001",
      "selection_rationale": "Exact addresses and private event/order records have explicit audience restrictions, and unauthorized actions must be rejected.",
      "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-004"],
      "nodes": [
        {"id": "AT3-N-001", "name": "Obtain restricted data without the required audience entitlement", "operator": "OR", "child_ids": ["AT3-N-002", "AT3-N-005", "AT3-N-009"], "affected_record_ids": ["AT3-AS-001", "AT3-D-001", "AT3-D-002", "AT3-D-003"], "evidence_ids": ["AT3-E-001"], "control_ids": ["AT3-C-001", "AT3-C-002", "AT3-C-003", "AT3-C-004"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-002", "name": "Receive restricted fields through a public read", "operator": "AND", "child_ids": ["AT3-N-003", "AT3-N-004"], "affected_record_ids": ["AT3-F-001", "AT3-EP-001"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-001", "AT3-C-004"], "assumptions": ["A public endpoint exists as specified"], "estimates": {}},
        {"id": "AT3-N-003", "name": "Request a public event or calendar read", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-F-001", "AT3-EP-001", "AT3-ACT-001"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-004", "name": "Public response includes exact address, orders, dietary requests, payment records, or staff updates", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-001", "AT3-D-002", "AT3-D-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-004"], "control_ids": ["AT3-C-001", "AT3-C-004"], "assumptions": ["The required exclusion or proposed server projection is absent or fails"], "estimates": {}},
        {"id": "AT3-N-005", "name": "Receive another Attendee's order or payment record", "operator": "AND", "child_ids": ["AT3-N-006", "AT3-N-007", "AT3-N-008"], "affected_record_ids": ["AT3-F-002", "AT3-EP-002"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-002", "AT3-C-004"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-006", "name": "Use an authenticated Attendee account", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-002", "AT3-B-002"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["The requester has an authenticated account; how it was obtained is outside supplied evidence"], "estimates": {}},
        {"id": "AT3-N-007", "name": "Request an order or payment record owned by a different Attendee", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002", "AT3-D-003", "AT3-F-002"], "evidence_ids": ["AT3-E-001"], "control_ids": [], "assumptions": ["The endpoint accepts a record selector; its concrete form is unknown"], "estimates": {}},
        {"id": "AT3-N-008", "name": "Ownership authorization fails and the record is returned", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002", "AT3-D-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-002", "AT3-C-004"], "assumptions": ["The required ownership check or proposed projection is absent or fails"], "estimates": {}},
        {"id": "AT3-N-009", "name": "Receive staff state or replay after assignment removal", "operator": "AND", "child_ids": ["AT3-N-010", "AT3-N-011", "AT3-N-012"], "affected_record_ids": ["AT3-F-003", "AT3-EP-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-003", "AT3-C-004"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-010", "name": "Possess a staff client or cursor from a former cook or shopper assignment", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-004", "AT3-D-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["A prior assignment and retained client state exist"], "estimates": {}},
        {"id": "AT3-N-011", "name": "Request current state or missed updates after assignment removal", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-F-003", "AT3-EP-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-012", "name": "Current-assignment authorization fails for the read or replay", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-001", "AT3-D-002", "AT3-D-003"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-003", "AT3-C-004"], "assumptions": ["The required current-assignment check or proposed projection is absent or fails"], "estimates": {}}
      ]
    },
    {
      "id": "AT3-TREE-002",
      "threat_id": "AT3-TH-002",
      "root_node_id": "AT3-N-020",
      "selection_rationale": "Booking confirmation explicitly requires correct provider-confirmed amount and currency during a valid hold, deduplication, and capacity consistency.",
      "evidence_ids": ["AT3-E-001", "AT3-E-002"],
      "nodes": [
        {"id": "AT3-N-020", "name": "Create a confirmed booking without acceptable payment evidence and a valid seat hold", "operator": "OR", "child_ids": ["AT3-N-021", "AT3-N-025", "AT3-N-028"], "affected_record_ids": ["AT3-AS-002", "AT3-D-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005", "AT3-C-006"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-021", "name": "Use an untrusted browser return as confirmation", "operator": "AND", "child_ids": ["AT3-N-022", "AT3-N-023", "AT3-N-024"], "affected_record_ids": ["AT3-F-004", "AT3-EP-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-022", "name": "Enter checkout for an accepted order", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-002", "AT3-F-004"], "evidence_ids": ["AT3-E-001"], "control_ids": [], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-023", "name": "Return or submit browser-controlled payment-result data", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-EP-004", "AT3-D-004"], "evidence_ids": ["AT3-E-002"], "control_ids": [], "assumptions": ["The concrete browser-return protocol is unresolved"], "estimates": {}},
        {"id": "AT3-N-024", "name": "Workflow treats the browser return as authoritative payment evidence", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-004"], "evidence_ids": ["AT3-E-002"], "control_ids": ["AT3-C-005"], "assumptions": ["The specified server-side evidence rule is absent or fails"], "estimates": {}},
        {"id": "AT3-N-025", "name": "Use invalid or replayed provider evidence", "operator": "AND", "child_ids": ["AT3-N-026", "AT3-N-027"], "affected_record_ids": ["AT3-F-004", "AT3-EP-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-026", "name": "Deliver a repeated, late, incorrect-amount, wrong-currency, or cancelled-event payment result", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-004", "AT3-ACT-006"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["A provider message or reconciliation result with one of the specified non-confirming conditions reaches the workflow"], "estimates": {}},
        {"id": "AT3-N-027", "name": "Evidence validation or deduplication accepts the result for booking confirmation", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005"], "assumptions": ["Required validation or deduplication is absent or fails"], "estimates": {}},
        {"id": "AT3-N-028", "name": "Confirm from an invalid over-capacity hold", "operator": "AND", "child_ids": ["AT3-N-029", "AT3-N-030", "AT3-N-031"], "affected_record_ids": ["AT3-F-004", "AT3-EP-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005", "AT3-C-006"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-029", "name": "Submit simultaneous checkout requests for the remaining seat", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-002", "AT3-D-004"], "evidence_ids": ["AT3-E-001"], "control_ids": [], "assumptions": ["At least two eligible requests contend for the remaining capacity"], "estimates": {}},
        {"id": "AT3-N-030", "name": "Capacity enforcement creates an over-capacity or otherwise invalid hold", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-006"], "assumptions": ["Required capacity consistency or proposed serialization is absent or fails"], "estimates": {}},
        {"id": "AT3-N-031", "name": "Payment confirmation replaces the invalid hold with a booking", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-004"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-005", "AT3-C-006"], "assumptions": ["Confirmation does not reject the invalid hold"], "estimates": {}}
      ]
    },
    {
      "id": "AT3-TREE-003",
      "threat_id": "AT3-TH-003",
      "root_node_id": "AT3-N-040",
      "selection_rationale": "The requirements explicitly cap cumulative refunds and prohibit repeated payouts of the same event proceeds.",
      "evidence_ids": ["AT3-E-001", "AT3-E-002"],
      "nodes": [
        {"id": "AT3-N-040", "name": "Cause refunds above the amount received or pay the same event proceeds more than once", "operator": "OR", "child_ids": ["AT3-N-041", "AT3-N-045"], "affected_record_ids": ["AT3-AS-003", "AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-007", "AT3-C-008"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-041", "name": "Cause cumulative refunds to exceed the payment received", "operator": "AND", "child_ids": ["AT3-N-042", "AT3-N-043", "AT3-N-044"], "affected_record_ids": ["AT3-F-005", "AT3-EP-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-007"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-042", "name": "Repeat or overlap an eligible refund request or Admin retry", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-005", "AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["At least one paid transaction and refund workflow exist"], "estimates": {}},
        {"id": "AT3-N-043", "name": "Refund accounting or deduplication permits aggregate requested refunds above the receipt", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-007"], "assumptions": ["The required cap or proposed operation deduplication is absent or fails"], "estimates": {}},
        {"id": "AT3-N-044", "name": "Payment service accepts excess refund transfers", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-006", "AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-007"], "assumptions": ["The unresolved provider contract does not independently prevent the excess"], "estimates": {}},
        {"id": "AT3-N-045", "name": "Pay the same event proceeds more than once", "operator": "AND", "child_ids": ["AT3-N-046", "AT3-N-047", "AT3-N-048"], "affected_record_ids": ["AT3-F-005", "AT3-EP-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-008"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-046", "name": "Repeat or overlap a payout request or failed-payout retry for one event", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-003", "AT3-ACT-005", "AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["An event has eligible proceeds and payout processing exists"], "estimates": {}},
        {"id": "AT3-N-047", "name": "Payout accounting or deduplication treats repeated work as independently payable", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-008"], "assumptions": ["The required payout deduplication is absent or fails"], "estimates": {}},
        {"id": "AT3-N-048", "name": "Payment service completes more than one payout of the same proceeds", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-ACT-006", "AT3-D-005"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-008"], "assumptions": ["The unresolved provider contract does not independently prevent the duplicate"], "estimates": {}}
      ]
    },
    {
      "id": "AT3-TREE-004",
      "threat_id": "AT3-TH-004",
      "root_node_id": "AT3-N-060",
      "selection_rationale": "Deletion and withdrawal are required, and the architecture explicitly records a risk that private notes may survive in snapshots or operational records while classification and copy coverage remain unresolved.",
      "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"],
      "nodes": [
        {"id": "AT3-N-060", "name": "Keep private food-note content accessible after required deletion or eligible consent withdrawal", "operator": "OR", "child_ids": ["AT3-N-061", "AT3-N-065"], "affected_record_ids": ["AT3-AS-004", "AT3-D-002", "AT3-D-006"], "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-009", "AT3-C-010"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-061", "name": "Retain an operational copy after source-note deletion", "operator": "AND", "child_ids": ["AT3-N-062", "AT3-N-063", "AT3-N-064"], "affected_record_ids": ["AT3-F-006", "AT3-EP-006"], "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-009", "AT3-C-010"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-062", "name": "Private food-note content is copied into a snapshot, update, job, audit, derived, or backup record", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-006"], "evidence_ids": ["AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-010"], "assumptions": ["At least one unresolved copy mechanism stores note content rather than only a reference"], "estimates": {}},
        {"id": "AT3-N-063", "name": "The owning private-note record is deleted at the required time or on eligible withdrawal", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002", "AT3-F-006"], "evidence_ids": ["AT3-E-001"], "control_ids": ["AT3-C-009"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-064", "name": "The copied record remains readable after source deletion", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-006"], "evidence_ids": ["AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-009", "AT3-C-010"], "assumptions": ["Deletion coverage omits the copy and some reader can access it; reader identity is unknown"], "estimates": {}},
        {"id": "AT3-N-065", "name": "Retain private content as recipe or handling data outside the private-note lifecycle", "operator": "AND", "child_ids": ["AT3-N-066", "AT3-N-067", "AT3-N-068"], "affected_record_ids": ["AT3-F-006", "AT3-EP-006"], "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-009"], "assumptions": [], "estimates": {}},
        {"id": "AT3-N-066", "name": "Private food-note content is incorporated into accepted recipe or handling records", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": [], "assumptions": ["The unresolved classification permits private content in retained recipe or handling fields"], "estimates": {}},
        {"id": "AT3-N-067", "name": "Lifecycle processing classifies that record outside private food notes", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002", "AT3-D-006"], "evidence_ids": ["AT3-E-002", "AT3-E-003"], "control_ids": ["AT3-C-009"], "assumptions": ["Private-note versus recipe or handling classification remains unresolved"], "estimates": {}},
        {"id": "AT3-N-068", "name": "The record remains readable after the deletion point", "operator": null, "child_ids": [], "affected_record_ids": ["AT3-D-002", "AT3-D-006"], "evidence_ids": ["AT3-E-001", "AT3-E-002"], "control_ids": ["AT3-C-009"], "assumptions": ["The retained record is not covered by deletion and some reader can access it; reader identity is unknown"], "estimates": {}}
      ]
    }
  ],
  "attack_paths": [
    {"id": "AT3-PATH-001", "tree_id": "AT3-TREE-001", "node_ids": ["AT3-N-001", "AT3-N-002", "AT3-N-003", "AT3-N-004"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "A public request plus failed public-field exclusion satisfies the public disclosure branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "No implementation or response evidence; control failure is explicit assumption."},
    {"id": "AT3-PATH-002", "tree_id": "AT3-TREE-001", "node_ids": ["AT3-N-001", "AT3-N-005", "AT3-N-006", "AT3-N-007", "AT3-N-008"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Authenticated cross-record selection plus failed ownership enforcement satisfies the branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Record-selection interface and implementation are unknown."},
    {"id": "AT3-PATH-003", "tree_id": "AT3-TREE-001", "node_ids": ["AT3-N-001", "AT3-N-009", "AT3-N-010", "AT3-N-011", "AT3-N-012"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Retained former-staff state, a replay request, and failed current-assignment authorization satisfy the branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Update transport, cursor form, and implementation are unresolved."},
    {"id": "AT3-PATH-004", "tree_id": "AT3-TREE-002", "node_ids": ["AT3-N-020", "AT3-N-021", "AT3-N-022", "AT3-N-023", "AT3-N-024"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Checkout plus a browser-controlled result and failed authoritative-evidence enforcement satisfy the branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Provider and browser-return contracts are unresolved; no implementation exists."},
    {"id": "AT3-PATH-005", "tree_id": "AT3-TREE-002", "node_ids": ["AT3-N-020", "AT3-N-025", "AT3-N-026", "AT3-N-027"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Specified invalid or repeated provider evidence plus failed validation or deduplication satisfies the branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Callback authenticity, reconciliation, and implementation are unresolved."},
    {"id": "AT3-PATH-006", "tree_id": "AT3-TREE-002", "node_ids": ["AT3-N-020", "AT3-N-028", "AT3-N-029", "AT3-N-030", "AT3-N-031"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Simultaneous last-seat requests, failed capacity consistency, and confirmation of the invalid hold satisfy the branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Persistence and transaction design are TO BE DECIDED."},
    {"id": "AT3-PATH-007", "tree_id": "AT3-TREE-003", "node_ids": ["AT3-N-040", "AT3-N-041", "AT3-N-042", "AT3-N-043", "AT3-N-044"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Repeated refund work, failed aggregate cap, and provider acceptance satisfy the excess-refund branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Provider contract and implementation are unresolved."},
    {"id": "AT3-PATH-008", "tree_id": "AT3-TREE-003", "node_ids": ["AT3-N-040", "AT3-N-045", "AT3-N-046", "AT3-N-047", "AT3-N-048"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Repeated payout work, failed deduplication, and provider completion satisfy the duplicate-payout branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Provider contract and implementation are unresolved."},
    {"id": "AT3-PATH-009", "tree_id": "AT3-TREE-004", "node_ids": ["AT3-N-060", "AT3-N-061", "AT3-N-062", "AT3-N-063", "AT3-N-064"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "A copied note, source deletion, and surviving readable copy satisfy the operational-copy branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Copy inventory, deletion coverage, storage, backups, and readers are unresolved."},
    {"id": "AT3-PATH-010", "tree_id": "AT3-TREE-004", "node_ids": ["AT3-N-060", "AT3-N-065", "AT3-N-066", "AT3-N-067", "AT3-N-068"], "status": "Conditionally satisfiable", "method": "Logical AND/OR enumeration only; no comparison method supplied", "rationale": "Private content incorporated into a retained record, classified outside the deletion lifecycle, and remaining readable satisfies the classification branch.", "likelihood": "UNKNOWN", "impact": "UNKNOWN", "uncertainty": "Private-note versus recipe or handling classification is TO BE DECIDED."}
  ],
  "visualizations": [],
  "coverage": [
    {"id": "AT3-COV-001", "subject": "Artifacts", "status": "complete", "details": "All four supplied specifications were read and cataloged."},
    {"id": "AT3-COV-002", "subject": "Tree reachability and references", "status": "complete", "details": "All 42 nodes are reachable from one root; child, threat, tree, control, evidence, and modeled-record references resolve."},
    {"id": "AT3-COV-003", "subject": "Root selection", "status": "complete for supported adverse objectives", "details": "Four roots were selected from explicit audience restrictions, booking/payment invariants, refund/payout invariants, and the documented private-note survival risk."},
    {"id": "AT3-COV-004", "subject": "Path enumeration", "status": "complete", "details": "Ten root-to-branch paths are enumerated; all are conditional because the specifications provide no implementation evidence."},
    {"id": "AT3-COV-005", "subject": "CAPEC mapping", "status": "omitted", "details": "No CAPEC identifier and name were verified against supplied authoritative CAPEC material."},
    {"id": "AT3-COV-006", "subject": "Path comparison and estimates", "status": "not assessed", "details": "No approved method or evidence supports ranking likelihood, impact, cost, skill, detectability, or access."}
  ],
  "conflicts": [
    {
      "id": "AT3-CON-001",
      "topic": "Node.js and Fastify role labels",
      "source_values": [
        {"evidence_id": "AT3-E-002", "locator": "Required Architecture Inputs and AQ-1", "value": "Developer input names Fastify as runtime and Node.js as server framework."},
        {"evidence_id": "AT3-E-002", "locator": "§4 and AQ-1", "value": "Node.js runtime with Fastify framework is a proposed interpretation pending decision."}
      ],
      "effect": "No branch depends on a resolved runtime/framework interpretation; implementation controls remain blocked."
    }
  ],
  "gaps": [
    {"id": "AT3-G-001", "topic": "Implementation and effectiveness", "missing_evidence": "Application code, deployed topology, configuration, tests, logs, and operational evidence.", "effect": "All control-failure nodes and paths remain conditional; no vulnerability is declared.", "evidence_ids": ["AT3-E-002", "AT3-E-003", "AT3-E-004"]},
    {"id": "AT3-G-002", "topic": "Authorization interfaces", "missing_evidence": "Concrete endpoint selectors, projection implementation, access-decision interfaces, and staff replay transport.", "effect": "AT3-PATH-001 through AT3-PATH-003 cannot be validated or rejected.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-G-003", "topic": "Payment provider and evidence contract", "missing_evidence": "Provider selection, browser-return contract, callback authenticity, reconciliation semantics, provider idempotency, and provider-side refund or payout bounds.", "effect": "AT3-PATH-004, AT3-PATH-005, AT3-PATH-007, and AT3-PATH-008 remain conditional.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-G-004", "topic": "Persistence and concurrency", "missing_evidence": "Database choice, locking, transaction, uniqueness, operation-id, and durable-work implementation.", "effect": "Capacity, booking, refund, and payout consistency paths cannot be tested.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-G-005", "topic": "Private-note inventory and lifecycle", "missing_evidence": "Exact private-note classification, all copies and readers, derived-record and backup behavior, deletion execution, and post-event retention.", "effect": "AT3-PATH-009 and AT3-PATH-010 cannot be validated or rejected.", "evidence_ids": ["AT3-E-001", "AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-G-006", "topic": "Risk and path comparison method", "missing_evidence": "Approved scales or evidence for likelihood, impact, cost, skill, detectability, access, or path preference.", "effect": "No path is ranked or labeled easiest, most likely, or highest impact.", "evidence_ids": []},
    {"id": "AT3-G-007", "topic": "Identity and session attack surface", "missing_evidence": "Email-link lifecycle, session lifetime and revocation, first Admin provisioning, native credential transport, and implementation.", "effect": "No credential or privilege-escalation tree is created; generic branches were not invented.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]},
    {"id": "AT3-G-008", "topic": "Deployment and operational access", "missing_evidence": "Hosting, network boundaries, secret provisioning, operational identities, and administrator access paths.", "effect": "No infrastructure or operational-access branches are created.", "evidence_ids": ["AT3-E-002", "AT3-E-003"]}
  ]
}
```

## Summary

### Scope and evidence limits

The analysis uses all four supplied specifications (`AT3-E-001` through `AT3-E-004`) and includes only adverse goals grounded in protected data, explicit state invariants, or a documented architecture risk. There is no implementation, so all attack paths that depend on a failed required or proposed control are conditional. No supplied method supports likelihood, impact, cost, skill, detectability, access, or path ranking. CAPEC mappings are omitted because no identifier and name were verified against supplied authoritative CAPEC material.

### Text attack-tree diagrams

```text
AT3-N-001 [OR] Obtain restricted data without required audience entitlement
├── AT3-N-002 [AND] Receive restricted fields through a public read
│   ├── AT3-N-003 Request public event/calendar data
│   └── AT3-N-004 Public response contains excluded fields
├── AT3-N-005 [AND] Receive another Attendee's order/payment record
│   ├── AT3-N-006 Use an authenticated Attendee account
│   ├── AT3-N-007 Request a record owned by another Attendee
│   └── AT3-N-008 Ownership authorization fails and returns it
└── AT3-N-009 [AND] Receive staff data after assignment removal
    ├── AT3-N-010 Retain former-staff client state or cursor
    ├── AT3-N-011 Request current state or missed updates
    └── AT3-N-012 Current-assignment authorization fails
```

```text
AT3-N-020 [OR] Confirm a booking without acceptable payment evidence and valid hold
├── AT3-N-021 [AND] Use an untrusted browser return
│   ├── AT3-N-022 Enter checkout
│   ├── AT3-N-023 Return browser-controlled result data
│   └── AT3-N-024 Treat browser return as authoritative evidence
├── AT3-N-025 [AND] Use invalid or replayed provider evidence
│   ├── AT3-N-026 Deliver repeated/late/incorrect/cancelled-event result
│   └── AT3-N-027 Validation or deduplication accepts it
└── AT3-N-028 [AND] Confirm from an invalid over-capacity hold
    ├── AT3-N-029 Submit simultaneous last-seat requests
    ├── AT3-N-030 Capacity enforcement creates an invalid hold
    └── AT3-N-031 Confirmation replaces it with a booking
```

```text
AT3-N-040 [OR] Exceed authorized refund or payout amounts
├── AT3-N-041 [AND] Refund more than the payment received
│   ├── AT3-N-042 Repeat/overlap a refund or Admin retry
│   ├── AT3-N-043 Aggregate cap or deduplication fails
│   └── AT3-N-044 Payment service accepts the excess
└── AT3-N-045 [AND] Pay the same proceeds more than once
    ├── AT3-N-046 Repeat/overlap payout work or retry
    ├── AT3-N-047 Payout deduplication fails
    └── AT3-N-048 Payment service completes the duplicate
```

```text
AT3-N-060 [OR] Keep private food-note content accessible after deletion/withdrawal
├── AT3-N-061 [AND] Retain an operational copy
│   ├── AT3-N-062 Copy note content into another record
│   ├── AT3-N-063 Delete the owning source note
│   └── AT3-N-064 Leave the copy readable
└── AT3-N-065 [AND] Retain private content as recipe/handling data
    ├── AT3-N-066 Incorporate private content into that record
    ├── AT3-N-067 Classify it outside the private-note lifecycle
    └── AT3-N-068 Leave the retained record readable
```

### Path analysis and shared defensive nodes

Ten conditional paths are enumerated as `AT3-PATH-001` through `AT3-PATH-010`: three audience-bypass paths, three invalid-booking paths, two excess-transfer paths, and two private-note-survival paths. They are logical alternatives only. The model does not rank them.

The public, cross-Attendee, and former-staff paths converge on server-side audience projection and authorization (`AT3-C-001` through `AT3-C-004`). Browser-return and invalid-provider-result paths converge on authoritative payment validation and deduplication (`AT3-C-005`). The invalid-hold path additionally depends on capacity consistency (`AT3-C-006`). Excess refund and duplicate payout paths depend on separate caps and deduplication requirements (`AT3-C-007`, `AT3-C-008`). Both private-note paths depend on complete lifecycle coverage (`AT3-C-009`); avoiding copied content through references is only proposed (`AT3-C-010`).

### Control status, conflicts, and gaps

All ten control records are unimplemented and untested. Eight describe required behavior, while server audience projections and reference-only private-note propagation are proposals. `SECURITY.md` keeps the corresponding secure-coding rules blocked. The Node.js/Fastify role-label conflict is retained as `AT3-CON-001`, but no attack branch depends on its resolution.

Material gaps are implementation evidence (`AT3-G-001`), concrete authorization interfaces (`AT3-G-002`), payment-provider evidence and idempotency contracts (`AT3-G-003`), persistence and concurrency mechanisms (`AT3-G-004`), the private-note inventory and lifecycle (`AT3-G-005`), an approved path-comparison method (`AT3-G-006`), identity/session attack-surface details (`AT3-G-007`), and deployment or operational access (`AT3-G-008`). Generic credential, infrastructure, and operational branches were not added from these gaps.
