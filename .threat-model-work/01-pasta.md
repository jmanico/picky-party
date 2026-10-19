# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": [
    {
      "id": "SCP-01",
      "name": "Picky Party first-release cooking-event website",
      "status": "documented",
      "purpose": "Support paid cooking events, reviewed food needs, confirmed attendance, ingredient planning, staff updates, cancellations, refunds, payouts, and public event discovery.",
      "objectives": [
        "Keep capacity and financial state consistent.",
        "Limit private and audience-specific data to its authorized audiences.",
        "Preserve acknowledged changes and deliver timely, accessible staff views.",
        "Keep payment outbound integration isolated from email integration."
      ],
      "in_scope": [
        "Public and authenticated website workflows defined by REQUIREMENTS.md",
        "Logical application components and provider boundaries defined or proposed in ARCHITECTURE.md",
        "Security decisions and blocked secure-coding rules in SECURITY.md",
        "Security-relevant rendering and interaction constraints in DESIGN.md",
        "External payment and email interactions at the documented logical boundaries"
      ],
      "exclusions": [
        "Group bookings",
        "Extra portions",
        "Offline payments",
        "Waitlists",
        "Discounts",
        "Automatic dietary certification",
        "Unspecified native application workflows",
        "Unspecified deployment topology"
      ],
      "risk_appetite": "unknown",
      "impact_scale": "unknown",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    }
  ],
  "evidence": [
    {
      "id": "E-01",
      "artifact": "REQUIREMENTS.md",
      "kind": "requirements",
      "revision": "not supplied",
      "date": "not supplied",
      "locators": [
        "Required Requirement Inputs",
        "Product Rules and Terms",
        "FR-1 through FR-11",
        "NFR-1 through NFR-3",
        "Open Questions"
      ],
      "observations": "Defines adopted first-release behavior, actors, records, state transitions, privacy restrictions, financial consistency rules, performance targets, load assumptions, and explicit exclusions. Requirements labelled ASSUMPTION are adopted product decisions, not measured results."
    },
    {
      "id": "E-02",
      "artifact": "ARCHITECTURE.md",
      "kind": "architecture specification",
      "revision": "not supplied",
      "date": "not supplied",
      "locators": [
        "§1 Introduction and Goals",
        "§3 Context and Scope",
        "§4 Solution Strategy",
        "§5 Building Block View",
        "§6 Runtime View",
        "§8 Crosscutting Concepts",
        "§9 Architectural Decisions",
        "§10 Quality Requirements",
        "§11 Risks and Technical Debt",
        "Required Architecture Inputs",
        "AQ-1 through AQ-8"
      ],
      "observations": "Describes a system with no implementation. Confirms logical isolation of payment and email outbound gateways; proposes the remaining modular-monolith, persistence, session, polling, and durable-work mechanisms; identifies provider, deployment, privacy-lifecycle, session, transport, and technology gaps."
    },
    {
      "id": "E-03",
      "artifact": "SECURITY.md",
      "kind": "security specification",
      "revision": "not supplied",
      "date": "not supplied",
      "locators": [
        "Secure-Coding Inputs",
        "Secure-Coding Rules SC-001 through SC-009",
        "Open Security Decisions OD-001 through OD-012"
      ],
      "observations": "Records confirmed behavioral and integration boundaries, states that no application implementation exists, and keeps every secure-coding rule BLOCKED because implementation, version, provider, session, deployment, persistence, privacy, and transport evidence is unresolved."
    },
    {
      "id": "E-04",
      "artifact": "DESIGN.md",
      "kind": "interaction and rendering specification",
      "revision": "alpha",
      "date": "not supplied",
      "locators": [
        "Overview",
        "Typography",
        "Layout",
        "Components",
        "Do's and Don'ts",
        "Open Questions DQ-1 through DQ-3"
      ],
      "observations": "States that no application implementation exists and defines presentation rules for exact states, private-field visibility, payment and booking distinctions, staleness, retained input, and accessible updates. Visual tokens are proposed assumptions."
    }
  ],
  "system": {
    "assets": [
      {
        "id": "A-01",
        "name": "Event, capacity, hold, order, and booking state",
        "importance": "Architecture identifies consistent capacity and durable changes as priorities; requirements prohibit oversubscription and unauthorized state changes.",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "A-02",
        "name": "Food needs, private notes, consent, proposals, and accepted recipes",
        "importance": "These records affect preparation and are subject to consent, audience filtering, and deletion requirements.",
        "evidence_ids": ["E-01", "E-02", "E-04"]
      },
      {
        "id": "A-03",
        "name": "Payment, refund, fee, payout, and receipt records",
        "importance": "These records determine paid attendance, refunds, and organizer proceeds and have deduplication, cap, and retention requirements.",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "A-04",
        "name": "Account identity, roles, ownership, staff assignments, suspension, and sessions",
        "importance": "These facts govern every protected action and private read.",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "A-05",
        "name": "Exact event addresses and access instructions",
        "importance": "Exact addresses are explicitly restricted to the Organizer, assigned staff, confirmed Attendees, and Admin.",
        "evidence_ids": ["E-01", "E-02", "E-04"]
      },
      {
        "id": "A-06",
        "name": "Staff updates, current preparation views, notices, and update cursors",
        "importance": "These records must be durable, timely, privacy-filtered, and re-authorized after reconnection or assignment changes.",
        "evidence_ids": ["E-01", "E-02", "E-04"]
      },
      {
        "id": "A-07",
        "name": "Audit and retention records",
        "importance": "Actor, time, and outcome must be recorded for specified changes while private food notes are excluded from retained financial records and removed on schedule.",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "A-08",
        "name": "Provider credentials, configuration, operation identifiers, and retry state",
        "importance": "Payment and email integration material must remain isolated, and financial operations must be deduplicated.",
        "evidence_ids": ["E-02", "E-03"]
      }
    ],
    "actors": [
      {
        "id": "ACT-01",
        "name": "Visitor",
        "trust": "untrusted external actor",
        "documented_capabilities": ["Browse public calendar and event information", "Follow public QR URLs"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-02",
        "name": "Attendee",
        "trust": "authenticated account actor for owned orders and bookings",
        "documented_capabilities": ["Submit food requests", "Accept proposals", "Enter checkout", "Inspect and cancel eligible owned bookings"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-03",
        "name": "Organizer",
        "trust": "authenticated event owner",
        "documented_capabilities": ["Manage owned events and recipes", "Review food requests", "Assign staff", "Read event financial records", "Cancel an owned event"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-04",
        "name": "Cook",
        "trust": "authenticated account with a current event assignment",
        "documented_capabilities": ["Read assigned-event confirmed preparation details and food needs", "Receive persistent updates"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-05",
        "name": "Shopper",
        "trust": "authenticated account with a current event assignment",
        "documented_capabilities": ["Read assigned-event ingredient changes and totals without Attendee names or private notes", "Receive persistent updates"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-06",
        "name": "Admin",
        "trust": "privileged authenticated actor",
        "documented_capabilities": ["Manage Admin grants", "Suspend accounts", "Cancel events", "Inspect, reconcile, and retry specified financial actions"],
        "motive": "not supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-07",
        "name": "Payment service",
        "trust": "external provider",
        "documented_capabilities": ["Return account capabilities", "Process checkout, refunds, fees, and payouts", "Send payment results or answer reconciliation queries"],
        "motive": "not applicable; no hostile-provider claim is supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-08",
        "name": "Email service",
        "trust": "external provider",
        "documented_capabilities": ["Deliver verification and sign-in links", "Deliver required notices"],
        "motive": "not applicable; no hostile-provider claim is supplied",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "ACT-09",
        "name": "Untrusted client",
        "trust": "untrusted source of client requests",
        "documented_capabilities": ["Send requests across the client boundary", "Supply identifiers and command inputs"],
        "motive": "unknown",
        "evidence_ids": ["E-02"]
      },
      {
        "id": "ACT-10",
        "name": "Durable work dispatcher",
        "trust": "proposed internal logical actor",
        "documented_capabilities": ["Resume scheduled and retry work", "Invoke owning workflows for expiration, completion, refunds, payouts, email, reconciliation, and retention"],
        "motive": "not applicable",
        "evidence_ids": ["E-02"]
      }
    ],
    "data": [
      {
        "id": "D-01",
        "name": "Public event and calendar fields",
        "classification": "public by requirement for launched, eligible events",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "D-02",
        "name": "Exact event address and access instructions",
        "classification": "restricted audience",
        "evidence_ids": ["E-01", "E-02", "E-04"]
      },
      {
        "id": "D-03",
        "name": "Food needs, restrictions, exclusions, cross-contact concerns, preferences, and private notes",
        "classification": "private; sharing requires consent; exact classification and copy lifecycle unresolved",
        "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
      },
      {
        "id": "D-04",
        "name": "Recipes, accepted replacements, omissions, and handling notes",
        "classification": "audience-specific; private-note boundary unresolved",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "D-05",
        "name": "Account, email, role, assignment, suspension, verification, and session data",
        "classification": "protected identity and authorization data",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "D-06",
        "name": "Order, hold, booking, cutoff, capacity, and attendance state",
        "classification": "protected business state",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "D-07",
        "name": "Payment references, amounts, currency, states, refunds, fees, payouts, and receipts",
        "classification": "protected financial records",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "D-08",
        "name": "Staff updates, notice records, delivery status, and cursors",
        "classification": "audience-specific operational records",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "D-09",
        "name": "Audit records and pending-work metadata",
        "classification": "protected operational records; required content and some retention defined",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "D-10",
        "name": "Payment and email provider credentials and configuration",
        "classification": "sensitive integration data; exact storage and provisioning unknown",
        "evidence_ids": ["E-02", "E-03"]
      }
    ],
    "zones": [
      {
        "id": "Z-01",
        "name": "Untrusted client zone",
        "status": "documented logical zone",
        "evidence_ids": ["E-02"]
      },
      {
        "id": "Z-02",
        "name": "Trusted application zone",
        "status": "documented logical zone; implementation absent",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "Z-03",
        "name": "Persistence zone",
        "status": "logical database boundary documented; database technology and deployment unconfirmed",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "Z-04",
        "name": "Isolated payment integration zone",
        "status": "confirmed logical boundary; provider and implementation unknown",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "Z-05",
        "name": "Separate email integration zone",
        "status": "confirmed logical boundary; provider and implementation unknown",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "Z-06",
        "name": "External provider zone",
        "status": "documented logical zone",
        "evidence_ids": ["E-02"]
      }
    ],
    "boundaries": [
      {
        "id": "B-01",
        "name": "Client-to-application trust boundary",
        "from_zone_id": "Z-01",
        "to_zone_id": "Z-02",
        "evidence_ids": ["E-02"]
      },
      {
        "id": "B-02",
        "name": "Application-to-persistence boundary",
        "from_zone_id": "Z-02",
        "to_zone_id": "Z-03",
        "evidence_ids": ["E-02"]
      },
      {
        "id": "B-03",
        "name": "Financial-workflow-to-payment-gateway boundary",
        "from_zone_id": "Z-02",
        "to_zone_id": "Z-04",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "B-04",
        "name": "Identity/notice-to-email-gateway boundary",
        "from_zone_id": "Z-02",
        "to_zone_id": "Z-05",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "B-05",
        "name": "Payment provider callback boundary",
        "from_zone_id": "Z-06",
        "to_zone_id": "Z-04",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "B-06",
        "name": "Payment outbound provider boundary",
        "from_zone_id": "Z-04",
        "to_zone_id": "Z-06",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "B-07",
        "name": "Email outbound provider boundary",
        "from_zone_id": "Z-05",
        "to_zone_id": "Z-06",
        "evidence_ids": ["E-02", "E-03"]
      }
    ],
    "flows": [
      {
        "id": "F-01",
        "name": "Public discovery and QR navigation",
        "source_ids": ["ACT-01"],
        "destination_ids": ["Z-02"],
        "data_ids": ["D-01"],
        "boundary_ids": ["B-01"],
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "F-02",
        "name": "Authenticated event, order, staff, and administration commands and reads",
        "source_ids": ["ACT-02", "ACT-03", "ACT-04", "ACT-05", "ACT-06"],
        "destination_ids": ["Z-02"],
        "data_ids": ["D-02", "D-03", "D-04", "D-05", "D-06", "D-07", "D-08"],
        "boundary_ids": ["B-01"],
        "evidence_ids": ["E-01", "E-02", "E-04"]
      },
      {
        "id": "F-03",
        "name": "Application persistence",
        "source_ids": ["Z-02"],
        "destination_ids": ["Z-03"],
        "data_ids": ["D-02", "D-03", "D-04", "D-05", "D-06", "D-07", "D-08", "D-09"],
        "boundary_ids": ["B-02"],
        "evidence_ids": ["E-02"]
      },
      {
        "id": "F-04",
        "name": "Payment checkout, capability, reconciliation, refund, fee, and payout operations",
        "source_ids": ["Z-02", "ACT-07"],
        "destination_ids": ["Z-04", "Z-06"],
        "data_ids": ["D-07", "D-10"],
        "boundary_ids": ["B-03", "B-05", "B-06"],
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "F-05",
        "name": "Email-link and notice delivery",
        "source_ids": ["Z-02"],
        "destination_ids": ["Z-05", "ACT-08"],
        "data_ids": ["D-05", "D-08", "D-10"],
        "boundary_ids": ["B-04", "B-07"],
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "F-06",
        "name": "Durable work, update replay, and retention execution",
        "source_ids": ["ACT-10"],
        "destination_ids": ["Z-02", "Z-03"],
        "data_ids": ["D-03", "D-06", "D-07", "D-08", "D-09"],
        "boundary_ids": ["B-02"],
        "evidence_ids": ["E-01", "E-02"]
      }
    ],
    "entry_points": [
      {
        "id": "EP-01",
        "name": "Public event and calendar reads, including permanent QR URLs",
        "zone_id": "Z-02",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "EP-02",
        "name": "Email verification and sign-in links",
        "zone_id": "Z-02",
        "evidence_ids": ["E-01", "E-02", "E-03"]
      },
      {
        "id": "EP-03",
        "name": "Authenticated command and read API",
        "zone_id": "Z-02",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "EP-04",
        "name": "Staff update and reconnect reads",
        "zone_id": "Z-02",
        "evidence_ids": ["E-01", "E-02"]
      },
      {
        "id": "EP-05",
        "name": "Payment provider callbacks",
        "zone_id": "Z-04",
        "evidence_ids": ["E-02", "E-03"]
      },
      {
        "id": "EP-06",
        "name": "Durable scheduled, retry, reconciliation, and retention work",
        "zone_id": "Z-02",
        "evidence_ids": ["E-02"]
      }
    ]
  },
  "methods": [
    {
      "id": "M-01",
      "name": "PASTA",
      "completion_state": "completed with evidence gaps",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "stages": [
        {
          "stage": 1,
          "name": "Objectives",
          "state": "completed",
          "evidence_ids": ["E-01", "E-02"],
          "gap_ids": ["G-01", "G-02"]
        },
        {
          "stage": 2,
          "name": "Technical scope",
          "state": "completed",
          "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
          "gap_ids": ["G-03", "G-04", "G-05", "G-06", "G-07"]
        },
        {
          "stage": 3,
          "name": "Decomposition",
          "state": "completed using logical and proposed architecture",
          "evidence_ids": ["E-02", "E-03"],
          "gap_ids": ["G-03", "G-04"]
        },
        {
          "stage": 4,
          "name": "Threat analysis",
          "state": "completed with no supplied threat intelligence, incidents, or hostile-actor profiles",
          "evidence_ids": ["E-01", "E-02", "E-03"],
          "gap_ids": ["G-08", "G-09"]
        },
        {
          "stage": 5,
          "name": "Weakness analysis",
          "state": "completed; no demonstrated implementation weakness because no implementation or test evidence exists",
          "evidence_ids": ["E-02", "E-03", "E-04"],
          "gap_ids": ["G-10", "G-11"]
        },
        {
          "stage": 6,
          "name": "Attack modeling",
          "state": "completed with assumption-marked success conditions",
          "evidence_ids": ["E-01", "E-02", "E-03"],
          "gap_ids": ["G-08", "G-10"]
        },
        {
          "stage": 7,
          "name": "Risk and impact analysis",
          "state": "completed; qualitative affected objectives recorded and ratings left unresolved",
          "evidence_ids": ["E-01", "E-02"],
          "gap_ids": ["G-01", "G-02", "G-12"]
        }
      ]
    }
  ],
  "threats": [
    {
      "id": "P-T01",
      "title": "Unauthorized actor reads or changes audience-restricted records",
      "method": "PASTA",
      "description": "A client request could seek exact addresses, another Attendee's order or payment data, Organizer/Admin actions, or assigned-staff data outside the actor's ownership, role, suspension state, or current assignment. The specifications require rejection and server-filtered projections, but no implementation evidence demonstrates enforcement.",
      "threat_actor_ids": ["ACT-01", "ACT-02", "ACT-03", "ACT-04", "ACT-05", "ACT-09"],
      "affected_record_ids": ["A-01", "A-02", "A-03", "A-04", "A-05", "A-06", "D-02", "D-03", "D-05", "D-06", "D-07", "D-08", "B-01", "EP-01", "EP-03", "EP-04"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["Successful exploitation would require absent or defective authorization or projection enforcement; no such defect is evidenced."],
      "control_ids": ["C-01", "C-02", "C-08"],
      "risk_ids": ["R-01"]
    },
    {
      "id": "P-T02",
      "title": "Untrusted or repeated payment evidence corrupts booking or financial state",
      "method": "PASTA",
      "description": "Provider callbacks, reconciliation results, retries, or browser-return information could be accepted without sufficient authenticity, amount, currency, hold, event-state, or operation-identity validation, producing an invalid booking or inconsistent payment state. The provider contract and callback verification mechanism are unresolved.",
      "threat_actor_ids": ["ACT-07", "ACT-09"],
      "affected_record_ids": ["A-01", "A-03", "A-08", "D-06", "D-07", "D-10", "B-05", "EP-05"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["An untrusted source can deliver or replay payment-like input at a provider-facing or client-facing entry point.", "Successful exploitation requires validation or deduplication to fail; no implementation result is supplied."],
      "control_ids": ["C-03", "C-04", "C-06"],
      "risk_ids": ["R-02"]
    },
    {
      "id": "P-T03",
      "title": "Concurrent capacity changes exceed event capacity or misallocate the final seat",
      "method": "PASTA",
      "description": "Simultaneous checkout, confirmation, cancellation, expiration, or capacity-edit operations could observe inconsistent occupancy and violate the requirement that confirmed bookings plus unexpired holds never exceed capacity. Transaction and locking details remain undecided.",
      "threat_actor_ids": ["ACT-02", "ACT-03", "ACT-07", "ACT-10"],
      "affected_record_ids": ["A-01", "D-06", "F-02", "F-04", "F-06", "EP-03", "EP-05", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["Relevant operations overlap in time.", "Successful failure requires the eventual consistency mechanism not to serialize or atomically constrain capacity-changing operations; no implementation result is supplied."],
      "control_ids": ["C-04"],
      "risk_ids": ["R-03"]
    },
    {
      "id": "P-T04",
      "title": "Repeated refund or payout execution exceeds authorized financial value",
      "method": "PASTA",
      "description": "Callback duplication, Admin retries, background retries, or reconciliation could initiate excessive refunds or pay the same event proceeds more than once unless operation identity, receipt caps, unresolved obligations, and payout eligibility are enforced consistently.",
      "threat_actor_ids": ["ACT-06", "ACT-07", "ACT-10"],
      "affected_record_ids": ["A-03", "A-08", "D-07", "D-09", "F-04", "F-06", "EP-05", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["A financial operation is delivered or invoked more than once.", "Successful loss requires cap, eligibility, or deduplication enforcement to fail; no implementation result is supplied."],
      "control_ids": ["C-03", "C-05", "C-06"],
      "risk_ids": ["R-04"]
    },
    {
      "id": "P-T05",
      "title": "Private food notes or exact addresses leak through a secondary projection or retained copy",
      "method": "PASTA",
      "description": "Public pages, shopper views, email notices, staff replay, jobs, audit records, financial records, derived results, or backups could expose or retain private food notes or exact addresses beyond their authorized audience or deletion period. The architecture proposes references instead of copied notes, but classification and complete deletion coverage are unresolved.",
      "threat_actor_ids": ["ACT-01", "ACT-05", "ACT-08", "ACT-09", "ACT-10"],
      "affected_record_ids": ["A-02", "A-05", "A-06", "A-07", "D-02", "D-03", "D-04", "D-08", "D-09", "F-01", "F-02", "F-05", "F-06"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["A secondary record or projection includes restricted content.", "The existence of such a copy is not demonstrated; the architecture records it as a risk and the lifecycle remains undecided."],
      "control_ids": ["C-01", "C-02", "C-07", "C-08"],
      "risk_ids": ["R-05"]
    },
    {
      "id": "P-T06",
      "title": "Email integration failure delays or controls required financial work",
      "method": "PASTA",
      "description": "Shared clients, credentials, retry state, execution capacity, or a combined external-services path could let an email outage or backlog delay payment, refund, or payout operations, including the one-minute authorized-refund submission target. Logical gateway separation is confirmed, but execution settings and implementation are absent.",
      "threat_actor_ids": ["ACT-08", "ACT-10"],
      "affected_record_ids": ["A-03", "A-08", "D-07", "D-09", "D-10", "B-03", "B-04", "B-06", "B-07", "F-04", "F-05", "F-06"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["Email delivery becomes unavailable or backlogged.", "Successful interference requires the confirmed separation and independent execution requirement not to be implemented; no implementation evidence is supplied."],
      "control_ids": ["C-06"],
      "risk_ids": ["R-06"]
    },
    {
      "id": "P-T07",
      "title": "Lost, delayed, replayed, or stale staff updates misstate preparation information",
      "method": "PASTA",
      "description": "An update cursor, reconnection, polling, or durable-work failure could omit accepted changes, replay obsolete content as current, or continue serving a removed staff member. This could leave cook or shopper views stale or incorrectly scoped. Transport and replay implementation remain undecided and the timing targets are unvalidated.",
      "threat_actor_ids": ["ACT-04", "ACT-05", "ACT-10"],
      "affected_record_ids": ["A-02", "A-04", "A-06", "D-03", "D-04", "D-05", "D-08", "F-02", "F-06", "EP-04", "EP-06"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["A delivery, cursor, revision, or current-assignment check fails; no such implementation failure is demonstrated."],
      "control_ids": ["C-01", "C-08", "C-09"],
      "risk_ids": ["R-07"]
    },
    {
      "id": "P-T08",
      "title": "Email sign-in or session misuse permits account impersonation",
      "method": "PASTA",
      "description": "Email verification/sign-in links and later sessions are account-access entry points. Link lifecycle, session lifetime and revocation, native credential transport, and first Admin provisioning are unresolved, so misuse scenarios cannot be decomposed beyond the documented entry point without assumptions.",
      "threat_actor_ids": ["ACT-08", "ACT-09"],
      "affected_record_ids": ["A-04", "D-05", "D-10", "F-05", "EP-02"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["An unauthorized party obtains or reuses a valid access artifact.", "The specifications do not establish a delivery compromise, link weakness, or session defect."],
      "control_ids": ["C-10"],
      "risk_ids": ["R-08"]
    }
  ],
  "controls": [
    {
      "id": "C-01",
      "name": "Server-side ownership, role, suspension, and current-assignment authorization",
      "status": "required; enforcement placement proposed; not implemented or tested",
      "addresses_threat_ids": ["P-T01", "P-T05", "P-T07"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "C-02",
      "name": "Audience-specific projections and consent-based food-note sharing",
      "status": "required; server projection placement proposed; not implemented or tested",
      "addresses_threat_ids": ["P-T01", "P-T05"],
      "evidence_ids": ["E-01", "E-02", "E-04"]
    },
    {
      "id": "C-03",
      "name": "Payment evidence, amount, currency, hold, and event-state validation",
      "status": "required; callback/provider mechanism unresolved; not implemented or tested",
      "addresses_threat_ids": ["P-T02", "P-T04"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "C-04",
      "name": "Atomic seat allocation and repeated-confirmation deduplication",
      "status": "required; transaction and locking design proposed or undecided; not implemented or tested",
      "addresses_threat_ids": ["P-T02", "P-T03"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "C-05",
      "name": "Refund caps, payout eligibility, and financial-operation deduplication",
      "status": "required; persistence/provider mechanisms unresolved; not implemented or tested",
      "addresses_threat_ids": ["P-T04"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "C-06",
      "name": "Isolated payment and email gateways with separate credentials, retry state, and execution capacity",
      "status": "confirmed logical architecture requirement; implementation and execution settings absent",
      "addresses_threat_ids": ["P-T02", "P-T04", "P-T06"],
      "evidence_ids": ["E-02", "E-03"]
    },
    {
      "id": "C-07",
      "name": "Private-note deletion, financial-record exclusion, audit content, and retention",
      "status": "required; classification, backups, derived-copy coverage, and implementation unresolved",
      "addresses_threat_ids": ["P-T05"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "C-08",
      "name": "Privacy-filtered durable staff updates with current-assignment checks on replay",
      "status": "required; transport, replay, and implementation unresolved",
      "addresses_threat_ids": ["P-T01", "P-T05", "P-T07"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "C-09",
      "name": "Visible staleness, canonical states, and preserved focus for live updates",
      "status": "required design and behavior; not rendered or tested",
      "addresses_threat_ids": ["P-T07"],
      "evidence_ids": ["E-01", "E-02", "E-04"]
    },
    {
      "id": "C-10",
      "name": "Verified email access, sign-out, and proposed revocable server-side sessions",
      "status": "verified-email behavior required; session mechanism proposed; lifecycle and first Admin provisioning unresolved",
      "addresses_threat_ids": ["P-T08"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    }
  ],
  "requirements": [
    {
      "id": "PR-01",
      "source_ids": ["FR-2.12", "FR-6.6", "FR-6.7", "FR-6.10", "FR-6.11", "FR-6.16", "FR-11.1", "FR-11.2"],
      "statement": "Enforce ownership, role, current assignment, and audience restrictions for actions and reads; unauthorized actions change no record.",
      "control_ids": ["C-01", "C-02", "C-08"],
      "threat_ids": ["P-T01", "P-T05", "P-T07"],
      "evidence_ids": ["E-01", "E-02", "E-04"]
    },
    {
      "id": "PR-02",
      "source_ids": ["FR-3.10", "FR-4.7", "FR-4.14", "FR-11.4", "FR-11.6", "FR-11.7"],
      "statement": "Require consent for food-note sharing, filter shopper and email views, remove private notes on schedule or eligible withdrawal, and exclude them from retained financial records.",
      "control_ids": ["C-02", "C-07", "C-08"],
      "threat_ids": ["P-T05"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "PR-03",
      "source_ids": ["FR-8.5", "FR-8.12", "FR-8.14", "FR-8.15", "FR-8.16", "FR-8.17", "FR-8.19", "FR-8.20", "FR-8.24", "NFR-2.2"],
      "statement": "Validate payment evidence and booking eligibility, deduplicate confirmations, preserve unresolved state, refund invalid payments, and keep occupancy within capacity.",
      "control_ids": ["C-03", "C-04"],
      "threat_ids": ["P-T02", "P-T03"],
      "evidence_ids": ["E-01", "E-02"]
    },
    {
      "id": "PR-04",
      "source_ids": ["FR-9.10", "FR-9.13", "FR-9.16", "FR-9.17", "FR-9.18"],
      "statement": "Cap refunds, exclude unresolved obligations from payout, and prevent duplicate payout of event proceeds.",
      "control_ids": ["C-05"],
      "threat_ids": ["P-T04"],
      "evidence_ids": ["E-01", "E-02"]
    },
    {
      "id": "PR-05",
      "source_ids": ["NFR-1.5", "ARCHITECTURE §2", "ARCHITECTURE §8 DR-9"],
      "statement": "Keep payment and email outbound integration isolated and ensure email failure cannot delay required financial work.",
      "control_ids": ["C-06"],
      "threat_ids": ["P-T06"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "PR-06",
      "source_ids": ["FR-4.9", "FR-4.10", "FR-4.11", "NFR-1.1", "NFR-1.2", "NFR-1.3", "NFR-3.6"],
      "statement": "Retain and replay staff updates, show current and stale connection state, meet update timing targets, and preserve reading position and focus.",
      "control_ids": ["C-08", "C-09"],
      "threat_ids": ["P-T07"],
      "evidence_ids": ["E-01", "E-02", "E-04"]
    },
    {
      "id": "PR-07",
      "source_ids": ["FR-6.2", "FR-6.3", "FR-6.4", "FR-6.11"],
      "statement": "Require verified email access, email-link sign-in, sign-out, and Admin-controlled Admin grants.",
      "control_ids": ["C-10"],
      "threat_ids": ["P-T08"],
      "evidence_ids": ["E-01", "E-02", "E-03"]
    }
  ],
  "risks": [
    {
      "id": "R-01",
      "threat_id": "P-T01",
      "affected_objectives": ["Private audience-specific data", "Authorized business-state changes"],
      "potential_impact": "Disclosure of restricted data or unauthorized modification of event, order, assignment, or financial state.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "No implementation, test, incident, attacker-capability, or prevalence evidence.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "R-02",
      "threat_id": "P-T02",
      "affected_objectives": ["Consistent booking and financial state", "Correct paid attendance"],
      "potential_impact": "Invalid booking confirmation, incorrect payment state, or avoidable refund work.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Provider and callback contracts, authenticity mechanism, implementation, and tests are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "R-03",
      "threat_id": "P-T03",
      "affected_objectives": ["Capacity consistency", "Correct attendance"],
      "potential_impact": "Oversubscribed event or inconsistent hold and booking state.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Persistence, transaction, locking, and load-test evidence are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "R-04",
      "threat_id": "P-T04",
      "affected_objectives": ["Consistent financial state", "Correct Organizer proceeds"],
      "potential_impact": "Refunds exceeding receipts or duplicate payout of event proceeds.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Provider retry semantics, persistence mechanisms, and tests are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "R-05",
      "threat_id": "P-T05",
      "affected_objectives": ["Private audience-specific data", "Required deletion and retention behavior"],
      "potential_impact": "Unauthorized disclosure or retention of food notes or event location data.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Data classification, full copy inventory, backup behavior, storage, and tests are absent; jurisdictions are unknown.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "R-06",
      "threat_id": "P-T06",
      "affected_objectives": ["Payment/email isolation", "Timely authorized refunds"],
      "potential_impact": "A required financial operation is delayed by unrelated email failure or backlog.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Execution configuration and failure-injection evidence are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "R-07",
      "threat_id": "P-T07",
      "affected_objectives": ["Timely accurate staff views", "Audience-specific data"],
      "potential_impact": "Preparation or shopping uses stale or incomplete information, or removed staff retain access to replayed data.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Transport, cursor, replay, implementation, and end-to-end timing evidence are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "R-08",
      "threat_id": "P-T08",
      "affected_objectives": ["Authenticated access", "Role and account integrity"],
      "potential_impact": "Unauthorized use of an account and its permitted event, order, staff, or administration actions.",
      "likelihood": "unresolved",
      "impact_rating": "unresolved",
      "overall_rating": "unresolved",
      "method": "No risk scale or likelihood inputs supplied.",
      "uncertainty": "Link/session lifecycle, provider contract, first Admin provisioning, implementation, and incidents are absent.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    }
  ],
  "attack_trees": [],
  "attack_paths": [
    {
      "id": "AP-01",
      "threat_id": "P-T01",
      "title": "Cross-audience read or command",
      "prerequisites": ["An entry point accepts an identifier for a record outside the requester's authorized audience."],
      "steps": [
        {"order": 1, "action": "Send a public or authenticated request carrying another record or event identifier.", "support": "supported entry point and identifier-based domain model", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Ownership, role, suspension, current assignment, or projection filtering fails.", "support": "assumption; no implementation weakness is evidenced", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Receive restricted data or cause an unauthorized state change.", "support": "modeled adverse outcome constrained by explicit requirements", "evidence_ids": ["E-01", "E-04"]}
      ],
      "affected_record_ids": ["A-01", "A-02", "A-03", "A-05", "D-02", "D-03", "D-06", "D-07", "D-08"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["A route accepts a caller-supplied record identifier.", "A required authorization or projection check is absent or defective."],
      "control_ids": ["C-01", "C-02", "C-08"],
      "risk_ids": ["R-01"]
    },
    {
      "id": "AP-02",
      "threat_id": "P-T02",
      "title": "Replay or misclassification of payment evidence",
      "prerequisites": ["Payment-result input reaches a callback, reconciliation, or client-return handling path."],
      "steps": [
        {"order": 1, "action": "Deliver payment-result input or repeat a prior result.", "support": "provider callback and repeated confirmation flows are documented", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Authenticity, amount, currency, hold, event state, or operation identity is not validated correctly.", "support": "assumption; provider contract and implementation are unresolved", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Create or preserve an invalid booking or financial state.", "support": "modeled adverse outcome constrained by FR-8", "evidence_ids": ["E-01"]}
      ],
      "affected_record_ids": ["A-01", "A-03", "D-06", "D-07", "EP-05"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["An untrusted or repeated result reaches the handler.", "Required validation or deduplication fails."],
      "control_ids": ["C-03", "C-04", "C-06"],
      "risk_ids": ["R-02"]
    },
    {
      "id": "AP-03",
      "threat_id": "P-T03",
      "title": "Concurrent final-seat allocation",
      "prerequisites": ["At least two capacity-changing operations overlap when one seat remains or capacity is being reduced."],
      "steps": [
        {"order": 1, "action": "Issue overlapping checkout, confirmation, cancellation, expiry, or capacity-edit operations.", "support": "simultaneous requests are an explicit requirement scenario", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Operations observe or commit without one shared atomic capacity rule.", "support": "assumption; transaction and locking details are undecided", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Confirmed bookings plus unexpired holds exceed capacity or the same seat is allocated inconsistently.", "support": "modeled adverse outcome explicitly prohibited by FR-8.5 and NFR-2.2", "evidence_ids": ["E-01"]}
      ],
      "affected_record_ids": ["A-01", "D-06"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["Operations overlap.", "The eventual implementation lacks effective atomic consistency."],
      "control_ids": ["C-04"],
      "risk_ids": ["R-03"]
    },
    {
      "id": "AP-04",
      "threat_id": "P-T04",
      "title": "Duplicate financial execution",
      "prerequisites": ["A refund or payout can be retried, reconciled, or redelivered."],
      "steps": [
        {"order": 1, "action": "Repeat an Admin, background, callback, or reconciliation invocation for one financial operation.", "support": "retry and repeated-result workflows are documented", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Operation identity, refund cap, payout obligations, or prior completion is not enforced atomically.", "support": "assumption; persistence and provider mechanisms are unresolved", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Refund more than received or request the same event proceeds more than once.", "support": "modeled adverse outcome explicitly prohibited by FR-9.16 and FR-9.18", "evidence_ids": ["E-01"]}
      ],
      "affected_record_ids": ["A-03", "A-08", "D-07", "D-09"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["A duplicate invocation occurs.", "Required cap or deduplication enforcement fails."],
      "control_ids": ["C-03", "C-05", "C-06"],
      "risk_ids": ["R-04"]
    },
    {
      "id": "AP-05",
      "threat_id": "P-T05",
      "title": "Restricted-data copy escapes audience or retention controls",
      "prerequisites": ["A projection, update, job, audit record, financial record, derived result, or backup processes restricted content."],
      "steps": [
        {"order": 1, "action": "Copy exact address or private food-note content into a secondary representation.", "support": "assumption; architecture identifies surviving snapshot or operational copies as a risk", "evidence_ids": ["E-02", "E-03"]},
        {"order": 2, "action": "Serve the secondary copy to a public, shopper, email, removed-staff, or other unauthorized audience, or omit it from deletion.", "support": "assumption; the relevant audiences and deletion requirements are explicit", "evidence_ids": ["E-01", "E-04"]},
        {"order": 3, "action": "Restricted content is disclosed or retained beyond the required lifecycle.", "support": "modeled adverse outcome constrained by FR-2.12, FR-4.7, FR-4.14, and FR-11", "evidence_ids": ["E-01"]}
      ],
      "affected_record_ids": ["A-02", "A-05", "A-06", "A-07", "D-02", "D-03", "D-08", "D-09"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["A secondary copy contains restricted content.", "Audience filtering or lifecycle deletion misses that copy."],
      "control_ids": ["C-01", "C-02", "C-07", "C-08"],
      "risk_ids": ["R-05"]
    },
    {
      "id": "AP-06",
      "threat_id": "P-T06",
      "title": "Email backlog consumes financial execution capacity",
      "prerequisites": ["Email delivery is unavailable or backlogged."],
      "steps": [
        {"order": 1, "action": "Accumulate email delivery retries or failures.", "support": "email failure and backlog are explicit quality scenarios", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Email and payment paths share mutable client, credentials, retry state, failure state, or constrained execution capacity.", "support": "assumption contrary to the confirmed separation requirement; implementation evidence is absent", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Delay an authorized refund or other financial operation.", "support": "modeled adverse outcome explicitly addressed by NFR-1.5 and the architecture quality scenario", "evidence_ids": ["E-01", "E-02"]}
      ],
      "affected_record_ids": ["A-03", "A-08", "D-07", "D-09", "D-10"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["Email delivery fails or is backlogged.", "The confirmed logical and execution separation is not implemented."],
      "control_ids": ["C-06"],
      "risk_ids": ["R-06"]
    },
    {
      "id": "AP-07",
      "threat_id": "P-T07",
      "title": "Stale or mis-scoped staff replay",
      "prerequisites": ["A cook or shopper reconnects with a saved cursor, or an assignment changes while updates exist."],
      "steps": [
        {"order": 1, "action": "Request current state and missed updates after disconnection or assignment change.", "support": "required reconnect and replay workflow", "evidence_ids": ["E-01", "E-02"]},
        {"order": 2, "action": "Cursor consistency, current-assignment authorization, privacy projection, or durable history fails.", "support": "assumption; transport and replay implementation are unresolved", "evidence_ids": ["E-02", "E-03"]},
        {"order": 3, "action": "Display stale, incomplete, or unauthorized preparation data.", "support": "modeled adverse outcome constrained by FR-4, FR-6.10, and NFR-1", "evidence_ids": ["E-01", "E-04"]}
      ],
      "affected_record_ids": ["A-02", "A-04", "A-06", "D-03", "D-04", "D-05", "D-08"],
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "assumptions": ["A replay, authorization, projection, or durability mechanism fails."],
      "control_ids": ["C-01", "C-08", "C-09"],
      "risk_ids": ["R-07"]
    },
    {
      "id": "AP-08",
      "threat_id": "P-T08",
      "title": "Reuse of an email access artifact",
      "prerequisites": ["An unauthorized party obtains a valid email verification or sign-in artifact."],
      "steps": [
        {"order": 1, "action": "Obtain a valid access artifact.", "support": "assumption; no compromise path is supplied", "evidence_ids": ["E-03"]},
        {"order": 2, "action": "Present the artifact to the email-link entry point after issuance or reuse it after intended use.", "support": "email-link entry point is required; lifecycle behavior is unresolved", "evidence_ids": ["E-01", "E-02", "E-03"]},
        {"order": 3, "action": "Receive or retain an authenticated session as the account.", "support": "assumption; exact session and revocation behavior is unresolved", "evidence_ids": ["E-02", "E-03"]}
      ],
      "affected_record_ids": ["A-04", "D-05", "EP-02"],
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "assumptions": ["An unauthorized party obtains a valid artifact.", "Artifact or session lifecycle permits the attempted use."],
      "control_ids": ["C-10"],
      "risk_ids": ["R-08"]
    }
  ],
  "visualizations": [],
  "coverage": [
    {
      "id": "CV-01",
      "method": "PASTA stage 1",
      "topic": "Objectives",
      "disposition": "covered",
      "notes": "Purpose, workflows, architecture priorities, load assumptions, first-release scope, and exclusions are documented. Risk appetite and quantified business impact are not supplied.",
      "evidence_ids": ["E-01", "E-02"],
      "gap_ids": ["G-01", "G-02"]
    },
    {
      "id": "CV-02",
      "method": "PASTA stage 2",
      "topic": "Technical scope",
      "disposition": "partially covered",
      "notes": "Logical actors, components, data, boundaries, providers, and entry points are documented. Deployment, provider selections, native scope, exact versions, persistence, and session implementation remain unresolved.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "gap_ids": ["G-03", "G-04", "G-05", "G-06", "G-07"]
    },
    {
      "id": "CV-03",
      "method": "PASTA stage 3",
      "topic": "Decomposition",
      "disposition": "covered at logical design level",
      "notes": "Trust boundaries and flows are represented from architecture claims. Proposed components are not treated as implemented, and deployment topology is not inferred.",
      "evidence_ids": ["E-02", "E-03"],
      "gap_ids": ["G-03", "G-04"]
    },
    {
      "id": "CV-04",
      "method": "PASTA stage 4",
      "topic": "Threat analysis",
      "disposition": "partially covered",
      "notes": "Threat events are derived from explicit protected assets, boundary rules, prohibited outcomes, and architecture risks. No threat intelligence, incidents, hostile actor profiles, motives, capability assessment, or time-bounded external intelligence is supplied.",
      "evidence_ids": ["E-01", "E-02", "E-03"],
      "gap_ids": ["G-08", "G-09"]
    },
    {
      "id": "CV-05",
      "method": "PASTA stage 5",
      "topic": "Weakness analysis",
      "disposition": "no demonstrated weaknesses",
      "notes": "No application implementation, test result, scanner result, incident, or control-effectiveness evidence exists. BLOCKED security rules and open decisions are evidence gaps, not proof of defects.",
      "evidence_ids": ["E-02", "E-03", "E-04"],
      "gap_ids": ["G-10", "G-11"]
    },
    {
      "id": "CV-06",
      "method": "PASTA stage 6",
      "topic": "Attack modeling",
      "disposition": "covered with assumptions",
      "notes": "Eight paths trace documented entry points and prohibited outcomes. Every successful-control-failure step and any unavailable acquisition step is marked as an assumption.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "gap_ids": ["G-08", "G-10"]
    },
    {
      "id": "CV-07",
      "method": "PASTA stage 7",
      "topic": "Risk and impact analysis",
      "disposition": "qualitative impacts only",
      "notes": "Risks link threats to documented objectives and prohibited outcomes. Likelihood, impact rating, and overall rating remain unresolved because no approved risk method, appetite, loss data, or scoring inputs are supplied.",
      "evidence_ids": ["E-01", "E-02"],
      "gap_ids": ["G-01", "G-02", "G-12"]
    },
    {
      "id": "CV-08",
      "method": "PASTA traceability check",
      "topic": "Threat, path, control, and risk provenance",
      "disposition": "covered",
      "notes": "Every threat, attack path, control, requirement group, and risk cites evidence IDs. Proposed and required controls remain distinguished from implemented or tested controls.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"],
      "gap_ids": []
    }
  ],
  "conflicts": [
    {
      "id": "CF-01",
      "topic": "Node.js and Fastify technical roles",
      "description": "Developer input labels Fastify as the runtime and Node.js as the server framework; architecture proposes the reverse interpretation but leaves acceptance undecided.",
      "status": "unresolved",
      "evidence_ids": ["E-02", "E-03"],
      "related_gap_ids": ["G-05"]
    },
    {
      "id": "CF-02",
      "topic": "Candidate Node.js baselines",
      "description": "SECURITY.md records a direct Node.js 26 candidate and Node.js 24 transitively included by several candidate packs, while no project version establishes precedence.",
      "status": "unresolved and not an active secure-coding composition",
      "evidence_ids": ["E-03"],
      "related_gap_ids": ["G-05"]
    }
  ],
  "gaps": [
    {
      "id": "G-01",
      "name": "Risk appetite",
      "description": "No acceptable-loss, tolerance, or risk-acceptance criteria are supplied.",
      "needed_evidence": "Approved business risk appetite or explicit acceptance criteria.",
      "evidence_ids": ["E-01", "E-02"]
    },
    {
      "id": "G-02",
      "name": "Quantified business impact",
      "description": "The specifications define protected outcomes and quality targets but do not quantify financial, operational, safety, or reputational impact.",
      "needed_evidence": "Approved impact categories, thresholds, or loss estimates.",
      "evidence_ids": ["E-01", "E-02"]
    },
    {
      "id": "G-03",
      "name": "Deployment and operational topology",
      "description": "Hosting, network boundaries, secret provisioning, operational access, build scope, and deployment topology are unknown.",
      "needed_evidence": "Approved deployment and operational architecture.",
      "evidence_ids": ["E-02", "E-03"]
    },
    {
      "id": "G-04",
      "name": "Persistence and durable execution design",
      "description": "Database selection, data-access technology, transactional locking, deduplication implementation, retry policy, reconciliation, and backup behavior are unresolved.",
      "needed_evidence": "Accepted persistence, consistency, durable-work, retry, reconciliation, and backup contracts.",
      "evidence_ids": ["E-02", "E-03"]
    },
    {
      "id": "G-05",
      "name": "Runtime, framework, language, and library versions",
      "description": "Technology roles conflict and versions or composition eligibility are not established.",
      "needed_evidence": "Authoritative technology roles, versions, compatibility results, and selected secure-coding provenance.",
      "evidence_ids": ["E-02", "E-03"]
    },
    {
      "id": "G-06",
      "name": "Provider and identity/session contracts",
      "description": "Payment and email providers, callback authenticity, sign-in-link lifecycle, session lifetime/revocation, native credential transport, and first Admin provisioning are unresolved.",
      "needed_evidence": "Selected provider contracts and approved identity/session lifecycle.",
      "evidence_ids": ["E-02", "E-03"]
    },
    {
      "id": "G-07",
      "name": "Native and browser scope",
      "description": "React Native is named, but native platforms, workflow parity, versions, link handling, and browser/rendering support are unresolved.",
      "needed_evidence": "Approved target surfaces, platforms, versions, browsers, and security-relevant rendering model.",
      "evidence_ids": ["E-02", "E-03", "E-04"]
    },
    {
      "id": "G-08",
      "name": "Threat actors, motives, and capabilities",
      "description": "No hostile actor profiles, motives, resource levels, access assumptions, or capability assessments are supplied.",
      "needed_evidence": "Approved threat-actor model tied to the system context.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "G-09",
      "name": "Threat intelligence and incident history",
      "description": "No time-bounded threat intelligence, abuse history, fraud history, operational incidents, or comparable-system evidence is supplied.",
      "needed_evidence": "Relevant, dated intelligence or incident evidence with provenance.",
      "evidence_ids": ["E-01", "E-02", "E-03", "E-04"]
    },
    {
      "id": "G-10",
      "name": "Implementation and weakness evidence",
      "description": "The specifications state that no application implementation exists; therefore code, configuration, dependency, deployment, test, and scanner findings are unavailable.",
      "needed_evidence": "Implementation artifacts and scoped verification results when implementation exists.",
      "evidence_ids": ["E-02", "E-03", "E-04"]
    },
    {
      "id": "G-11",
      "name": "Control effectiveness",
      "description": "Required, confirmed, and proposed controls have not been implemented or tested, so their effectiveness is unknown.",
      "needed_evidence": "Design verification and implementation test results for each control and boundary.",
      "evidence_ids": ["E-02", "E-03", "E-04"]
    },
    {
      "id": "G-12",
      "name": "Risk method and scoring inputs",
      "description": "No approved likelihood scale, impact scale, scoring formula, mapping, or risk owner is supplied.",
      "needed_evidence": "Approved risk method, mappings, input data, and ownership.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "G-13",
      "name": "Privacy classification and copy lifecycle",
      "description": "Jurisdictions, statutory duties, the private-note boundary around recipes and handling data, derived-copy and backup deletion, and post-event nonfinancial retention are unresolved.",
      "needed_evidence": "Approved data classification, jurisdictional inputs, storage/copy inventory, deletion coverage, and retention decisions.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    },
    {
      "id": "G-14",
      "name": "Staff update transport and validation",
      "description": "Polling acceptance, cursor/revision implementation, replay authorization, and end-to-end timing evidence are unresolved.",
      "needed_evidence": "Accepted transport contract and test evidence under the stated load and reconnect conditions.",
      "evidence_ids": ["E-01", "E-02", "E-03"]
    }
  ]
}
```

## Summary

### Objectives and scope

The reviewed system is the specified first-release Picky Party cooking-event website. Its supported objectives are consistent capacity and financial state, protected audience-specific data, durable state changes, timely accessible staff views, and logical isolation of payment outbound integration from email integration. Public and authenticated web workflows, logical application and provider boundaries, and security-relevant rendering behavior are in scope. The explicitly excluded first-release features, unresolved native workflows, and unspecified deployment topology are outside the modeled scope. No risk appetite, quantified impact scale, or approved risk-scoring method is supplied.

### Technical decomposition

The evidence identifies Visitor, Attendee, Organizer, cook, shopper, Admin, payment service, email service, untrusted client, and proposed durable-work actors. Protected assets include event/capacity state, food needs and accepted recipes, account and authorization facts, exact addresses, financial records, staff updates, audit records, and isolated provider material. Documented logical boundaries separate untrusted clients, the application, persistence, payment integration, email integration, and external providers. The database technology, deployment topology, provider contracts, session lifecycle, update transport, and most component mechanisms are proposed or unresolved rather than implemented facts.

### Threat and weakness evidence

The model records eight scenarios grounded in explicit protected outcomes and boundaries: cross-audience access or mutation; untrusted or repeated payment evidence; concurrent capacity corruption; duplicate refund or payout execution; restricted-data leakage or retention through secondary copies; email failure interfering with financial work; stale or mis-scoped staff replay; and misuse of email access artifacts. The supplied material contains no threat intelligence, hostile-actor profiles, motives, incident history, or time-bounded external observations. It also states that no application implementation exists. Consequently, no implementation weakness or ineffective control is claimed. BLOCKED security rules and open decisions are evidence gaps, not demonstrated vulnerabilities.

### Supported attack paths

Eight paths connect documented entry points or retry flows to explicitly prohibited outcomes. Their supported steps include identifier-bearing client requests, payment callbacks and reconciliation, simultaneous checkout, Admin/background retries, staff reconnect replay, email failure, and email-link account access. Each step that depends on a failed control, a copied private record, a compromised link, shared execution capacity, or another unavailable implementation fact is explicitly marked as an assumption.

### Risk results

Each scenario is linked to affected objectives and a qualitative potential impact: unauthorized disclosure or mutation, invalid bookings or payment state, oversubscription, excessive refunds or duplicate payouts, retention or disclosure of restricted data, delayed financial operations, stale preparation information, or account impersonation. Likelihood, impact rating, and overall risk rating remain unresolved for every scenario because the evidence supplies no risk scale, appetite, loss data, actor capability assessment, implementation result, or effectiveness test.

### Conflicts and gaps

The unresolved technology conflicts are the supplied Node.js/Fastify role labels and incompatible candidate Node.js baselines without a selected project version. Major gaps cover risk appetite and quantified impacts; deployment and persistence; technology versions; provider and identity/session contracts; native/browser scope; threat actors and intelligence; implementation and control effectiveness; risk scoring; privacy classification and deletion coverage; and staff-update transport and testing. These gaps do not establish vulnerabilities.
