# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": [
    {
      "id": "SCP-01",
      "name": "Picky Party specification-level FMEA",
      "status": "completed with evidence gaps",
      "in_scope": ["First-release website behavior", "Documented logical components, flows, boundaries, dependencies, controls, and rendering behavior"],
      "limits": ["No implementation exists", "No operational history, tests, telemetry, incidents, or control-effectiveness evidence", "No FMEA rating method", "Native workflows and deployment topology unresolved"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    }
  ],
  "evidence": [
    {"id": "E-01", "artifact": "REQUIREMENTS.md", "kind": "requirements", "revision": "not supplied", "date": "not supplied", "locators": ["Required Requirement Inputs", "Product Rules and Terms", "FR-1 through FR-11", "NFR-1 through NFR-3"], "coverage": "Functions, states, dependencies, controls, acceptance targets, load assumptions, and exclusions.", "limits": "Requirements marked ASSUMPTION are adopted decisions, not measured results; provider and jurisdiction facts remain unknown."},
    {"id": "E-02", "artifact": "ARCHITECTURE.md", "kind": "architecture specification", "revision": "not supplied", "date": "not supplied", "locators": ["§1 through §11", "Required Architecture Inputs", "AQ-1 through AQ-8"], "coverage": "Logical components, flows, boundaries, dependencies, quality scenarios, proposed mechanisms, confirmed gateway isolation, and architecture risks.", "limits": "The system has no implementation; most mechanisms are proposed or unresolved."},
    {"id": "E-03", "artifact": "SECURITY.md", "kind": "security specification", "revision": "not supplied", "date": "not supplied", "locators": ["Secure-Coding Inputs", "SC-001 through SC-009", "OD-001 through OD-012"], "coverage": "Confirmed boundaries and unresolved implementation, provider, session, persistence, privacy, deployment, and update decisions.", "limits": "All secure-coding rules are BLOCKED; none is implemented or effective evidence."},
    {"id": "E-04", "artifact": "DESIGN.md", "kind": "interaction and rendering specification", "revision": "alpha", "date": "not supplied", "locators": ["Overview", "Layout", "Components", "Do's and Don'ts", "DQ-1 through DQ-3"], "coverage": "Canonical states, errors, staleness, private fields, prices, deadlines, accessibility, and live-update rendering.", "limits": "No application exists; tokens/layouts are assumptions and browser scope is unresolved."}
  ],
  "system": {
    "assets": [
      {"id": "FN-01", "name": "Web presentation", "status": "specified; not implemented", "evidence_ids": ["E-01", "E-02", "E-04"]},
      {"id": "FN-02", "name": "Mobile presentation", "status": "scope unresolved", "evidence_ids": ["E-02", "E-03"]},
      {"id": "FN-03", "name": "Identity and access", "status": "partly specified; mechanisms unresolved", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FN-04", "name": "Events and recipes", "status": "specified; not implemented", "evidence_ids": ["E-01", "E-02"]},
      {"id": "FN-05", "name": "Orders and bookings", "status": "specified; not implemented", "evidence_ids": ["E-01", "E-02", "E-04"]},
      {"id": "FN-06", "name": "Financial workflows", "status": "partly specified; provider/mechanisms unresolved", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FN-07", "name": "Payment outbound gateway and callback adapter", "status": "logical isolation confirmed; implementation unresolved", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FN-08", "name": "Email outbound gateway", "status": "logical isolation confirmed; implementation unresolved", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FN-09", "name": "Preparation and shopping reads", "status": "specified; not implemented", "evidence_ids": ["E-01", "E-02", "E-04"]},
      {"id": "FN-10", "name": "Updates and notices", "status": "partly specified; transport unresolved", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
      {"id": "FN-11", "name": "Durable work and records", "status": "outcomes specified; mechanism proposed", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "AS-01", "name": "Capacity and booking integrity", "evidence_ids": ["E-01", "E-02"]},
      {"id": "AS-02", "name": "Financial integrity and Organizer proceeds", "evidence_ids": ["E-01", "E-02"]},
      {"id": "AS-03", "name": "Private and audience-specific records", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
      {"id": "AS-04", "name": "Accurate preparation and shopping information", "evidence_ids": ["E-01", "E-02"]},
      {"id": "AS-05", "name": "Account, role, assignment, and session integrity", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "AS-06", "name": "Audit, update, notice, and retention records", "evidence_ids": ["E-01", "E-02", "E-03"]}
    ],
    "actors": [
      {"id": "ACT-01", "name": "Visitor", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-02", "name": "Attendee", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-03", "name": "Organizer", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-04", "name": "Cook", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-05", "name": "Shopper", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-06", "name": "Admin", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-07", "name": "Payment service", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-08", "name": "Email service", "evidence_ids": ["E-01", "E-02"]},
      {"id": "ACT-09", "name": "Durable work dispatcher", "status": "proposed", "evidence_ids": ["E-02"]}
    ],
    "data": [
      {"id": "D-01", "name": "Account, role, assignment, suspension, and session data", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "D-02", "name": "Event, capacity, recipe snapshot, and address data", "evidence_ids": ["E-01", "E-02"]},
      {"id": "D-03", "name": "Food needs, consent, proposals, recipes, and private notes", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
      {"id": "D-04", "name": "Order, hold, booking, and attendance state", "evidence_ids": ["E-01", "E-02"]},
      {"id": "D-05", "name": "Payment, refund, payout, fee, receipt, and operation data", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "D-06", "name": "Ingredient totals, variants, and calculation time", "evidence_ids": ["E-01", "E-02"]},
      {"id": "D-07", "name": "Staff updates, notices, delivery status, and cursors", "evidence_ids": ["E-01", "E-02"]},
      {"id": "D-08", "name": "Audit, pending work, and retention metadata", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "D-09", "name": "Provider credentials and configuration", "status": "storage/provisioning unknown", "evidence_ids": ["E-02", "E-03"]}
    ],
    "zones": [
      {"id": "Z-01", "name": "Untrusted clients", "evidence_ids": ["E-02"]},
      {"id": "Z-02", "name": "Trusted application", "evidence_ids": ["E-02"]},
      {"id": "Z-03", "name": "Persistence", "status": "technology/deployment unresolved", "evidence_ids": ["E-02", "E-03"]},
      {"id": "Z-04", "name": "Isolated payment integration", "evidence_ids": ["E-02", "E-03"]},
      {"id": "Z-05", "name": "Separate email integration", "evidence_ids": ["E-02", "E-03"]},
      {"id": "Z-06", "name": "External providers", "evidence_ids": ["E-02"]}
    ],
    "boundaries": [
      {"id": "B-01", "name": "Client to application", "evidence_ids": ["E-02"]},
      {"id": "B-02", "name": "Application to persistence", "evidence_ids": ["E-02"]},
      {"id": "B-03", "name": "Financial workflow to payment integration", "evidence_ids": ["E-02", "E-03"]},
      {"id": "B-04", "name": "Identity/notice workflows to email integration", "evidence_ids": ["E-02", "E-03"]},
      {"id": "B-05", "name": "Payment callback/provider boundary", "evidence_ids": ["E-02", "E-03"]}
    ],
    "flows": [
      {"id": "FL-01", "name": "Public and authenticated commands/reads", "evidence_ids": ["E-01", "E-02", "E-04"]},
      {"id": "FL-02", "name": "Persistence and transactional state changes", "evidence_ids": ["E-02"]},
      {"id": "FL-03", "name": "Payment operation, callback, and reconciliation", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FL-04", "name": "Email access and notice delivery", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "FL-05", "name": "Update replay, scheduled work, and retention", "evidence_ids": ["E-01", "E-02"]}
    ],
    "entry_points": [
      {"id": "EP-01", "name": "Public event/calendar/QR reads", "evidence_ids": ["E-01", "E-02"]},
      {"id": "EP-02", "name": "Email verification/sign-in links", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "EP-03", "name": "Authenticated commands and reads", "evidence_ids": ["E-01", "E-02"]},
      {"id": "EP-04", "name": "Staff polling and reconnect replay", "evidence_ids": ["E-01", "E-02"]},
      {"id": "EP-05", "name": "Payment callbacks/reconciliation results", "evidence_ids": ["E-01", "E-02", "E-03"]},
      {"id": "EP-06", "name": "Scheduled and retry work", "evidence_ids": ["E-02"]}
    ]
  },
  "methods": [
    {
      "id": "M-01",
      "name": "FMEA",
      "completion_state": "completed with unranked failure modes",
      "supplied_method": "None",
      "factors": [],
      "scales": [],
      "directions": [],
      "thresholds": [],
      "calculations": [],
      "ranking_disposition": "All failure modes remain unranked; requirement and architecture priority language is not converted into ratings.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "passes": [
        {"pass": 1, "name": "Catalog evidence and scope", "state": "completed", "gap_ids": ["G-01", "G-02"]},
        {"pass": 2, "name": "Decompose system", "state": "completed at logical level", "gap_ids": ["G-03", "G-04", "G-05"]},
        {"pass": 3, "name": "Identify failure modes", "state": "completed from supported functions and prohibited outcomes", "gap_ids": ["G-01", "G-02"]},
        {"pass": 4, "name": "Trace controls", "state": "completed; document controls are not treated as effective", "gap_ids": ["G-06"]},
        {"pass": 5, "name": "Apply supplied rating method", "state": "not applicable; no method supplied", "gap_ids": ["G-07"]},
        {"pass": 6, "name": "Identify interactions", "state": "completed", "gap_ids": ["G-03"]},
        {"pass": 7, "name": "Evaluate treatments", "state": "documented proposals preserved; no target ratings/residual reassessment", "gap_ids": ["G-06", "G-07"]},
        {"pass": 8, "name": "Check coverage", "state": "completed", "gap_ids": []}
      ],
      "interactions": [
        {"id": "INT-01", "type": "cascade", "description": "Invalid payment state can cascade into booking, attendance, updates, ingredient totals, refunds, and payouts.", "failure_mode_ids": ["FM-04", "FM-05", "FM-07", "FM-08"], "evidence_ids": ["E-01", "E-02"]},
        {"id": "INT-02", "type": "common cause", "description": "If selected, the proposed shared persistence/durable-work mechanism can jointly affect capacity, finance, updates, audit, expiry, completion, and retention.", "failure_mode_ids": ["FM-04", "FM-05", "FM-06", "FM-08", "FM-09"], "assumptions": ["The proposed shared mechanism is selected."], "evidence_ids": ["E-02", "E-03"]},
        {"id": "INT-03", "type": "shared control", "description": "Authorization and audience projections jointly govern protected commands, reads, and replay.", "failure_mode_ids": ["FM-01", "FM-03", "FM-08", "FM-09"], "evidence_ids": ["E-01", "E-02", "E-03"]},
        {"id": "INT-04", "type": "dependency cascade", "description": "Email backlog can affect financial timing only if confirmed gateway and execution isolation is not preserved.", "failure_mode_ids": ["FM-06", "FM-10"], "assumptions": ["Isolation is implemented incorrectly."], "evidence_ids": ["E-01", "E-02", "E-03"]},
        {"id": "INT-05", "type": "time dependency", "description": "Cutoff, holds, completion, payout, update timing, and retention depend on server time/scheduled execution; scheduler delay must not extend eligibility.", "failure_mode_ids": ["FM-02", "FM-03", "FM-04", "FM-06", "FM-08", "FM-09"], "evidence_ids": ["E-01", "E-02"]}
      ]
    }
  ],
  "threats": [
    {
      "id": "FM-01", "title": "Identity or authorization returns the wrong decision", "function_ids": ["FN-03"],
      "failure_mode": "Email/session, role, ownership, suspension, Admin-grant, or current-assignment enforcement admits an unauthorized action/read or rejects required suspended-account cancellation/refund access.",
      "causes": ["Link/session lifecycle and first Admin provisioning unresolved", "Authorization implementation unresolved", "Assumption: a check is missing, stale, or applied to the wrong audience"],
      "local_effect": "Incorrect authorization result.", "downstream_effect": "Restricted data/state is exposed or changed, or required access is denied.",
      "affected_record_ids": ["FN-03", "AS-03", "AS-05", "D-01", "D-02", "D-03", "D-04", "D-05", "EP-02", "EP-03", "EP-04"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"], "control_ids": ["C-01", "C-02"], "assumptions": ["No defect is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes revocable server sessions and current ownership/assignment/role/suspension checks; SECURITY.md keeps implementation controls BLOCKED."], "risk_ids": ["R-01"]
    },
    {
      "id": "FM-02", "title": "Event publication or recipe snapshot is invalid", "function_ids": ["FN-04"],
      "failure_mode": "An event launches without required data/capability/time validity; fixed published data changes; visibility/completion is wrong; or dish edits alter launched recipes.",
      "causes": ["Assumption: validation is incomplete/non-atomic", "Assumption: snapshot enforcement is absent", "Time behavior untested"],
      "local_effect": "Invalid event or recipe state.", "downstream_effect": "Incorrect public facts, unintended recipes, or actions outside permitted state/time.",
      "affected_record_ids": ["FN-04", "AS-01", "AS-04", "D-02", "D-03", "EP-01", "EP-03", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-04"], "control_ids": ["C-03", "C-04"], "assumptions": ["No defect is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes explicit commands, server-owned rules, snapshots, time-zone identifiers, and server-clock deadline checks."], "risk_ids": ["R-02"]
    },
    {
      "id": "FM-03", "title": "Food request, consent, acceptance, or order state advances incorrectly", "function_ids": ["FN-05"],
      "failure_mode": "Food needs are shared without consent; unresolved/rejected changes become payable; acceptance is skipped; paid changes occur; or cutoff/cancellation is wrong.",
      "causes": ["Assumption: state gates or ownership checks are bypassed", "Assumption: consent/accepted-recipe evidence is not preserved", "Private-note classification unresolved"],
      "local_effect": "Order state conflicts with review, consent, acceptance, payment, or cutoff facts.", "downstream_effect": "Unresolved needs become payable, an unaccepted recipe is prepared, private data is disclosed, or eligibility is wrong.",
      "affected_record_ids": ["FN-05", "AS-03", "AS-04", "D-03", "D-04", "EP-03", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"], "control_ids": ["C-01", "C-05", "C-06"], "assumptions": ["No failure is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes command workflows, server-owned transitions, audience projections, and accepted-recipe snapshots."], "risk_ids": ["R-03"]
    },
    {
      "id": "FM-04", "title": "Seat hold or capacity accounting becomes inconsistent", "function_ids": ["FN-05", "FN-11"],
      "failure_mode": "Overlapping checkout, confirmation, expiry, cancellation, or capacity edits oversubscribe, retain/release the wrong hold, or create duplicate bookings.",
      "causes": ["Transactions/locking/deduplication unresolved", "Assumption: operations lack one atomic rule", "Assumption: scheduler delay extends eligibility"],
      "local_effect": "Hold, booking, and capacity records disagree.", "downstream_effect": "Oversubscription, wrong seat/payment mapping, or wrong attendance/totals.",
      "affected_record_ids": ["FN-05", "FN-11", "AS-01", "AS-04", "D-02", "D-04", "D-06", "FL-02", "FL-03", "FL-05"],
      "evidence_ids": ["E-01", "E-02", "E-03"], "control_ids": ["C-07", "C-08"], "assumptions": ["Operations overlap and eventual consistency is ineffective; neither is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes serializing capacity changes, atomic hold-to-booking replacement, constraints, and server-time checks."], "risk_ids": ["R-04"]
    },
    {
      "id": "FM-05", "title": "Payment result is validated, reconciled, or deduplicated incorrectly", "function_ids": ["FN-06", "FN-07"],
      "failure_mode": "A return/callback/reconciliation result changes state without valid provider evidence, amount/currency, hold, event state, or operation identity; or unknown state is mishandled.",
      "causes": ["Provider/authenticity contract unresolved", "Persistence/idempotency unresolved", "Assumption: evidence is incomplete/stale/replayed and validation fails"],
      "local_effect": "Incorrect payment or booking decision.", "downstream_effect": "Wrong attendance, duplicate booking, wrong refund/notices/totals/payout.",
      "affected_record_ids": ["FN-06", "FN-07", "AS-01", "AS-02", "D-04", "D-05", "D-07", "FL-03", "EP-05"],
      "evidence_ids": ["E-01", "E-02", "E-03"], "control_ids": ["C-08", "C-09", "C-10"], "assumptions": ["No provider or implementation defect is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes a payment inbound adapter, normalized evidence, server validation, operation IDs, deduplication, Pending unknown state, and reconciliation."], "risk_ids": ["R-05"]
    },
    {
      "id": "FM-06", "title": "Refund or payout is late, excessive, duplicated, or blocked by email", "function_ids": ["FN-06", "FN-07", "FN-08", "FN-11"],
      "failure_mode": "Refund exceeds receipt, payout repeats/includes unresolved obligations, authorized refund misses its deadline, or email backlog delays payment work.",
      "causes": ["Provider/retry contracts unresolved", "Durable execution unresolved", "Assumption: cap, eligibility, identity, or isolation fails"],
      "local_effect": "Wrong financial amount, eligibility, identity, or timing.", "downstream_effect": "Financial loss, wrong proceeds, unresolved refund, or missed one-minute target.",
      "affected_record_ids": ["FN-06", "FN-07", "FN-08", "FN-11", "AS-02", "D-05", "D-08", "D-09", "FL-03", "FL-04", "FL-05"],
      "evidence_ids": ["E-01", "E-02", "E-03"], "control_ids": ["C-10", "C-11", "C-12"], "assumptions": ["No duplication, excessive amount, or delay is observed."],
      "proposed_treatment": ["Confirmed: separate payment/email ports, clients, credentials, retry/failure state, handlers, and capacity. Proposed: durable work, operation IDs, refund caps, payout eligibility, and deduplication."], "risk_ids": ["R-06"]
    },
    {
      "id": "FM-07", "title": "Preparation or shopping output is wrong or exposes private data", "function_ids": ["FN-09"],
      "failure_mode": "Totals include wrong orders, omit variants, merge unlike records/units, miscalculate, vary for identical inputs, or shopper output includes identity/private notes.",
      "causes": ["Assumption: filtering/arithmetic is wrong", "Assumption: cook/shopper projections are confused", "No tests"],
      "local_effect": "Incorrect quantities, recipes, notes, or audience fields.", "downstream_effect": "Wrong purchase/preparation or shopper privacy disclosure.",
      "affected_record_ids": ["FN-09", "AS-03", "AS-04", "D-03", "D-04", "D-06", "D-07"],
      "evidence_ids": ["E-01", "E-02", "E-04"], "control_ids": ["C-02", "C-13"], "assumptions": ["No defect is demonstrated."],
      "proposed_treatment": ["ARCHITECTURE.md proposes exact arithmetic, canonical conversions/rounding, accepted-recipe snapshots, and separate server projections."], "risk_ids": ["R-07"]
    },
    {
      "id": "FM-08", "title": "Staff update/reconnect state is lost, delayed, stale, duplicated, or mis-scoped", "function_ids": ["FN-01", "FN-10", "FN-11"],
      "failure_mode": "An update misses deadlines; reconnect omits state/history; cursor skips/duplicates; stale data looks current; focus moves; or replay ignores assignment/privacy.",
      "causes": ["Transport unresolved", "Cursor/durable work proposed and untested", "Assumption: delivery, authorization, consistency, or rendering fails"],
      "local_effect": "Staff view differs from current authorized state.", "downstream_effect": "Stale/incomplete preparation, removed-staff access, or inaccessible updates.",
      "affected_record_ids": ["FN-01", "FN-10", "FN-11", "AS-03", "AS-04", "AS-06", "D-01", "D-03", "D-06", "D-07", "FL-05", "EP-04"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"], "control_ids": ["C-01", "C-02", "C-14", "C-15"], "assumptions": ["No update failure is observed."],
      "proposed_treatment": ["ARCHITECTURE.md proposes durable cursors, paging/revisions, current state plus history, and assignment checks; DESIGN.md requires staleness and focus behavior."], "risk_ids": ["R-08"]
    },
    {
      "id": "FM-09", "title": "Durable work, audit, or retention is incomplete", "function_ids": ["FN-11"],
      "failure_mode": "Restart loses changes/work; expiry/completion/refund/payout/retention fails; audit fields are absent; or private notes survive deletion or enter financial records.",
      "causes": ["Durability/audit/backup/deletion unresolved", "Private-note boundary unresolved", "Assumption: work is not committed with state or deletion misses copies"],
      "local_effect": "Work, history, or lifecycle diverges from source state.", "downstream_effect": "Lost changes, missed actions, incomplete accountability, or retained private data.",
      "affected_record_ids": ["FN-11", "AS-02", "AS-03", "AS-06", "D-03", "D-04", "D-05", "D-07", "D-08", "FL-02", "FL-05", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-03"], "control_ids": ["C-06", "C-12", "C-16"], "assumptions": ["No failure is observed."],
      "proposed_treatment": ["ARCHITECTURE.md proposes transactional work/update references, restart recovery, and reference-only jobs/audits; SECURITY.md leaves lifecycle controls BLOCKED."], "risk_ids": ["R-09"]
    },
    {
      "id": "FM-10", "title": "Email access or notice delivery fails without safe fallback", "function_ids": ["FN-08", "FN-10"],
      "failure_mode": "Access links or required notices fail; failed email is absent from account notices; or email includes exact address/private notes.",
      "causes": ["Email/link contracts unresolved", "Assumption: notice persistence or email projection fails"],
      "local_effect": "Email access/notice is unavailable, misleading, or unsafe.", "downstream_effect": "Lost access/notice, missing fallback, disclosure, or FM-06 cascade if isolation fails.",
      "affected_record_ids": ["FN-08", "FN-10", "AS-03", "AS-05", "AS-06", "D-01", "D-03", "D-07", "D-09", "FL-04", "EP-02"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"], "control_ids": ["C-02", "C-11", "C-17"], "assumptions": ["No failure is observed."],
      "proposed_treatment": ["Requirements mandate persistent account notices and private-field filtering; architecture separates email delivery from persistence/payment."], "risk_ids": ["R-10"]
    },
    {
      "id": "FM-11", "title": "Web presentation misstates state, price, deadline, error, or staleness", "function_ids": ["FN-01"],
      "failure_mode": "UI conflates states, hides price/cutoff/hold, truncates needs, loses inputs, omits text errors/staleness, or breaks keyboard/focus/reflow.",
      "causes": ["Browser/rendering scope unresolved", "No rendered/test evidence", "Assumption: UI violates canonical requirements"],
      "local_effect": "Presentation disagrees with authoritative state or blocks operation.", "downstream_effect": "Misled/blocked user or stale/current preparation data cannot be distinguished.",
      "affected_record_ids": ["FN-01", "AS-01", "AS-02", "AS-03", "AS-04", "D-02", "D-03", "D-04", "D-05", "D-07"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"], "control_ids": ["C-04", "C-15", "C-18"], "assumptions": ["No rendering/accessibility failure is observed."],
      "proposed_treatment": ["Requirements/DESIGN.md mandate canonical labels, explicit values, retained inputs, text errors, staleness, keyboard access, reflow, and focus; browser controls remain BLOCKED."], "risk_ids": ["R-11"]
    }
  ],
  "controls": [
    {"id": "C-01", "type": "prevention", "name": "Ownership, role, suspension, Admin-grant, and assignment authorization", "status": "required; proposed server enforcement; untested", "failure_mode_ids": ["FM-01", "FM-03", "FM-08"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-02", "type": "prevention", "name": "Audience projections, consent, and shopper/email/public filtering", "status": "required; proposed server placement; untested", "failure_mode_ids": ["FM-01", "FM-07", "FM-08", "FM-10"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "C-03", "type": "prevention", "name": "Launch, capability, cutoff, schedule, and immutable-field validation", "status": "required; untested", "failure_mode_ids": ["FM-02"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "C-04", "type": "prevention/detection", "name": "Field errors, retained values, preview, canonical states, and visibility", "status": "required; unrendered/untested", "failure_mode_ids": ["FM-02", "FM-11"], "evidence_ids": ["E-01", "E-04"]},
    {"id": "C-05", "type": "prevention", "name": "Consent, review, acceptance, payment gate, and paid-state immutability", "status": "required; untested", "failure_mode_ids": ["FM-03"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "C-06", "type": "recovery", "name": "Eligible cancellation and consent-withdrawal note deletion", "status": "required; deletion coverage unresolved", "failure_mode_ids": ["FM-03", "FM-09"], "evidence_ids": ["E-01", "E-03"]},
    {"id": "C-07", "type": "prevention", "name": "Capacity/hold/order/booking invariants", "status": "required; mechanism unresolved", "failure_mode_ids": ["FM-04"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-08", "type": "prevention", "name": "Short transactions, shared locking, constraints, atomic replacement, operation IDs", "status": "proposed; untested", "failure_mode_ids": ["FM-04", "FM-05"], "evidence_ids": ["E-02", "E-03"]},
    {"id": "C-09", "type": "prevention", "name": "Payment evidence/amount/currency/hold/event validation", "status": "required with proposed placement; provider unresolved", "failure_mode_ids": ["FM-05"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-10", "type": "detection/recovery", "name": "Pending unknown payment, payment block, reconciliation, invalid-payment refund", "status": "required; mechanisms unresolved", "failure_mode_ids": ["FM-05", "FM-06"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-11", "type": "prevention", "name": "Separate payment/email clients, credentials, retry/failure state, and capacity", "status": "confirmed logical requirement; untested", "failure_mode_ids": ["FM-06", "FM-10"], "evidence_ids": ["E-02", "E-03"]},
    {"id": "C-12", "type": "prevention/recovery", "name": "Refund caps, payout eligibility/deduplication, persistent work, Admin retry", "status": "required outcomes/proposed mechanism; untested", "failure_mode_ids": ["FM-06", "FM-09"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-13", "type": "prevention/detection", "name": "Confirmed-order filtering, recipe snapshots, exact conversions/rounding, visible calculation time", "status": "required/proposed; untested", "failure_mode_ids": ["FM-07"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "C-14", "type": "prevention/recovery", "name": "Durable history, consistent cursor/revision, current state plus missed updates, replay authorization", "status": "required outcomes/proposed transport; unresolved", "failure_mode_ids": ["FM-08"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-15", "type": "detection/response", "name": "Stale status, last update time, canonical labels, stable reading position/focus", "status": "required; unrendered/untested", "failure_mode_ids": ["FM-08", "FM-11"], "evidence_ids": ["E-01", "E-04"]},
    {"id": "C-16", "type": "prevention/recovery", "name": "Audit, private-note deletion, financial retention, note references, restart recovery", "status": "required/proposed; classification/coverage unresolved", "failure_mode_ids": ["FM-09"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "C-17", "type": "response/recovery", "name": "Persistent account notices on email failure", "status": "required; untested", "failure_mode_ids": ["FM-10"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "C-18", "type": "prevention/detection", "name": "Explicit values/errors/state distinctions and accessible interaction", "status": "required; unrendered/untested", "failure_mode_ids": ["FM-11"], "evidence_ids": ["E-01", "E-04"]}
  ],
  "requirements": [
    {"id": "RQ-01", "source_ids": ["FR-6", "FR-11.1", "FR-11.2"], "statement": "Authorize protected actions/reads by current role, ownership, suspension, and assignment.", "failure_mode_ids": ["FM-01", "FM-08"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "RQ-02", "source_ids": ["FR-1", "FR-2", "FR-5", "FR-7.8", "FR-7.9"], "statement": "Validate lifecycle, visibility, time, and immutable snapshots.", "failure_mode_ids": ["FM-02"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "RQ-03", "source_ids": ["FR-3", "FR-8.1", "FR-8.2", "FR-9.1", "FR-9.2", "FR-11.7"], "statement": "Enforce consent, review, acceptance, payment, cutoff, cancellation, and withdrawal transitions.", "failure_mode_ids": ["FM-03"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "RQ-04", "source_ids": ["FR-8.3 through FR-8.8", "FR-8.24", "NFR-2.2"], "statement": "Keep holds/bookings within capacity under concurrency.", "failure_mode_ids": ["FM-04"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "RQ-05", "source_ids": ["FR-8.10 through FR-8.23"], "statement": "Validate/reconcile payment and deduplicate confirmation.", "failure_mode_ids": ["FM-05"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "RQ-06", "source_ids": ["FR-9", "NFR-1.5", "ARCHITECTURE DR-9"], "statement": "Cap/deduplicate/timely dispatch finance while isolating payment from email.", "failure_mode_ids": ["FM-06"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "RQ-07", "source_ids": ["FR-4.5 through FR-4.8", "FR-10", "NFR-2.3"], "statement": "Produce deterministic audience-filtered preparation/shopping reads.", "failure_mode_ids": ["FM-07"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "RQ-08", "source_ids": ["FR-4.1 through FR-4.11", "FR-6.10", "NFR-1.1 through NFR-1.3", "NFR-3.6"], "statement": "Persist, authorize, replay, and display current staff updates within targets.", "failure_mode_ids": ["FM-08"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "RQ-09", "source_ids": ["FR-11.3 through FR-11.7", "NFR-2.1"], "statement": "Preserve changes, audit outcomes, and apply retention/deletion.", "failure_mode_ids": ["FM-09"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "RQ-10", "source_ids": ["FR-4.12 through FR-4.14", "FR-6.2", "FR-6.3"], "statement": "Deliver access/notices with account fallback and private filtering.", "failure_mode_ids": ["FM-10"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "RQ-11", "source_ids": ["FR-1.12", "FR-1.13", "FR-4.11", "FR-8.6", "FR-8.9", "NFR-3", "DESIGN Components"], "statement": "Present states, values, errors, staleness, and accessible interactions accurately.", "failure_mode_ids": ["FM-11"], "evidence_ids": ["E-01", "E-04"]}
  ],
  "risks": [
    {"id": "R-01", "failure_mode_id": "FM-01", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "R-02", "failure_mode_id": "FM-02", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02"]},
    {"id": "R-03", "failure_mode_id": "FM-03", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "R-04", "failure_mode_id": "FM-04", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "R-05", "failure_mode_id": "FM-05", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "R-06", "failure_mode_id": "FM-06", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "R-07", "failure_mode_id": "FM-07", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "R-08", "failure_mode_id": "FM-08", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "R-09", "failure_mode_id": "FM-09", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "R-10", "failure_mode_id": "FM-10", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "R-11", "failure_mode_id": "FM-11", "priority": "unranked", "factors": {}, "result": null, "residual_risk": "not assessed", "rationale": "No method or values supplied.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]}
  ],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [],
  "coverage": [
    {"id": "CV-01", "component_id": "FN-01", "disposition": "assessed", "failure_mode_ids": ["FM-08", "FM-11"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "CV-02", "component_id": "FN-02", "disposition": "not assessed", "reason": "Native platforms/workflows unresolved; a technology name cannot ground failure modes.", "gap_ids": ["G-05"], "evidence_ids": ["E-02", "E-03"]},
    {"id": "CV-03", "component_id": "FN-03", "disposition": "assessed", "failure_mode_ids": ["FM-01"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "CV-04", "component_id": "FN-04", "disposition": "assessed", "failure_mode_ids": ["FM-02"], "evidence_ids": ["E-01", "E-02"]},
    {"id": "CV-05", "component_id": "FN-05", "disposition": "assessed", "failure_mode_ids": ["FM-03", "FM-04"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "CV-06", "component_id": "FN-06", "disposition": "assessed", "failure_mode_ids": ["FM-05", "FM-06"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "CV-07", "component_id": "FN-07", "disposition": "assessed", "failure_mode_ids": ["FM-05", "FM-06"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "CV-08", "component_id": "FN-08", "disposition": "assessed", "failure_mode_ids": ["FM-06", "FM-10"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "CV-09", "component_id": "FN-09", "disposition": "assessed", "failure_mode_ids": ["FM-07"], "evidence_ids": ["E-01", "E-02", "E-04"]},
    {"id": "CV-10", "component_id": "FN-10", "disposition": "assessed", "failure_mode_ids": ["FM-08", "FM-10"], "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "CV-11", "component_id": "FN-11", "disposition": "assessed", "failure_mode_ids": ["FM-04", "FM-06", "FM-08", "FM-09"], "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "CV-12", "topic": "Prioritization", "disposition": "not applicable", "reason": "No method supplied; all risks unranked.", "gap_ids": ["G-07"], "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "CV-13", "topic": "Traceability", "disposition": "covered", "reason": "Every conclusion is evidenced or marked as assumption.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]}
  ],
  "conflicts": [
    {"id": "CF-01", "topic": "Node.js/Fastify roles", "description": "Input labels Fastify as runtime and Node.js as framework; proposed correction remains undecided.", "status": "unresolved", "evidence_ids": ["E-02", "E-03"], "gap_ids": ["G-04"]},
    {"id": "CF-02", "topic": "Candidate Node.js versions", "description": "Direct Node.js 26 and transitive Node.js 24 candidates lack a selected project version or active composition.", "status": "unresolved", "evidence_ids": ["E-03"], "gap_ids": ["G-04"]}
  ],
  "gaps": [
    {"id": "G-01", "name": "Operational history", "description": "No incidents, failures, abuse cases, production observations, or maintenance history.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "G-02", "name": "Verification evidence", "description": "No implementation, tests, telemetry, load/accessibility results, fault injection, or scanner/provider findings.", "evidence_ids": ["E-02", "E-03", "E-04"]},
    {"id": "G-03", "name": "Persistence and durable execution", "description": "Database, transactions, locking, constraints, retries, reconciliation, scheduler, backup, and deletion unresolved.", "evidence_ids": ["E-02", "E-03"]},
    {"id": "G-04", "name": "Technology and deployment", "description": "Roles/versions/composition, hosting, network, secrets, build, and operational access unresolved.", "evidence_ids": ["E-02", "E-03"]},
    {"id": "G-05", "name": "Native and browser scope", "description": "Native platforms/workflows and browser/rendering scope unresolved.", "evidence_ids": ["E-02", "E-03", "E-04"]},
    {"id": "G-06", "name": "Control implementation/effectiveness", "description": "Document-only requirements, boundaries, and proposals have no implementation/effectiveness evidence.", "evidence_ids": ["E-02", "E-03", "E-04"]},
    {"id": "G-07", "name": "FMEA prioritization", "description": "No factors, scales, directions, anchors, values, thresholds, calculation, owners, dates, targets, or residual reassessment.", "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]},
    {"id": "G-08", "name": "Provider and session contracts", "description": "Providers, callback authenticity, retry semantics, link/session lifecycle, and first Admin provisioning unresolved.", "evidence_ids": ["E-02", "E-03"]},
    {"id": "G-09", "name": "Privacy lifecycle", "description": "Jurisdictions, private-note boundary, derived/backup deletion, and nonfinancial retention unresolved.", "evidence_ids": ["E-01", "E-02", "E-03"]},
    {"id": "G-10", "name": "Update transport/replay", "description": "Transport, cursor/revision, replay authorization, paging, and measured timing unresolved.", "evidence_ids": ["E-01", "E-02", "E-03"]}
  ]
}
```

## Summary

### Scope and material limits

This FMEA covers the first-release website functions, logical architecture, security decisions, and security-relevant rendering behavior in the four supplied specifications. No implementation, operational history, incidents, telemetry, tests, or control-effectiveness evidence exists. Native workflows and deployment topology are unresolved.

### FMEA table

| ID | Function | Failure mode | Local effect | Downstream effect | Controls/status | Priority |
| --- | --- | --- | --- | --- | --- | --- |
| FM-01 | Identity/access | Wrong email/session/role/ownership/suspension/assignment decision | Incorrect authorization | Restricted data/state changed or required access denied | C-01/C-02 required/proposed; untested | Unranked |
| FM-02 | Events/recipes | Invalid launch, lifecycle, visibility, time, immutability, or snapshot | Invalid event/recipe state | Wrong public facts, recipes, or eligibility | C-03/C-04 required; untested | Unranked |
| FM-03 | Orders/bookings | Consent, review, acceptance, payment, cutoff, or cancellation gate fails | Invalid order state | Unresolved needs paid, unaccepted recipe, disclosure, or wrong eligibility | C-01/C-05/C-06 required; unresolved | Unranked |
| FM-04 | Orders/durable work | Holds/capacity diverge under overlap | Capacity records disagree | Oversubscription, wrong seat/payment, wrong totals | C-07 required; C-08 proposed | Unranked |
| FM-05 | Finance/payment | Payment evidence/state/deduplication wrong | Wrong payment/booking decision | Wrong attendance, refund, notices, totals, payout | C-08/C-09/C-10 required/proposed | Unranked |
| FM-06 | Finance/payment/email/work | Refund/payout late, excessive, duplicate, or email-blocked | Wrong amount/eligibility/identity/timing | Loss, wrong proceeds, unresolved refund, missed target | C-11 isolation confirmed; C-10/C-12 required/proposed | Unranked |
| FM-07 | Preparation/shopping | Totals/recipes/audience filtering wrong | Incorrect read model | Wrong purchase/preparation or disclosure | C-02/C-13 required/proposed | Unranked |
| FM-08 | Web/updates/work | Update/reconnect lost, delayed, stale, duplicate, or mis-scoped | Staff view differs from current authorized state | Stale preparation, disclosure, inaccessible update | C-01/C-02/C-14/C-15 required/proposed | Unranked |
| FM-09 | Durable work/records | Restart, audit, or retention incomplete | Work/history/lifecycle diverges | Lost changes, missed action, incomplete audit, retained private data | C-06/C-12/C-16 required/proposed | Unranked |
| FM-10 | Email/notices | Access/notice/fallback fails or email leaks | Unavailable/unsafe email result | Lost access/notice, disclosure, possible finance cascade | C-02/C-11/C-17 required/confirmed | Unranked |
| FM-11 | Web presentation | State/value/error/staleness/accessibility misrendered | UI disagrees or blocks use | Misled/blocked user; stale/current indistinguishable | C-04/C-15/C-18 required | Unranked |

### Common causes and cascades

Invalid payment state can cascade into booking, attendance, updates, totals, refunds, and payouts. If selected, shared persistence/durable work can become a common dependency for capacity, finance, updates, audit, expiry, completion, and retention. Authorization and projections are shared controls. Email backlog can affect finance only if confirmed isolation is not preserved. Server time and scheduling are shared dependencies for cutoffs, holds, completion, payouts, updates, and retention.

### Controls, priorities, treatments, conflicts, and gaps

Controls are required, confirmed logical boundaries, proposed, or BLOCKED; none is treated as implemented or effective. Documented treatments are preserved without adding owners, dates, products, settings, target ratings, or residual-risk claims. No rating method was supplied, so every failure mode remains unranked and no comparable priority is asserted.

The unresolved conflicts are Node.js/Fastify role labels and candidate Node.js baselines. Gaps cover operational/verification evidence, persistence/durable execution, technology/deployment, native/browser scope, control effectiveness, the full FMEA rating method, provider/session contracts, privacy lifecycle, and update transport/replay. Missing evidence is not proof that a failure occurred.
