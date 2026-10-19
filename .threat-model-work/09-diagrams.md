# THREAT_MODEL_DIAGRAM

## Model

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

## Picky Party System Context

**Diagram ID:** `DGM-001`  
**Purpose:** Show the system, its people, providers, data exchanges, and trust crossings.  
**Audience:** Executives, Product, Security

### Elements

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

### Connections

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

### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-SYSTEM | Modeled system boundary | SCP-001 | B-001, B-003, B-004, B-005, B-006 | Logical scope only; deployment topology unresolved |

### Annotations and ordering

- Use neutral threat markers; no comparable ordered rating exists.
- Payment and email are distinct external exchanges.

- Place SCP-001 centrally.
- Place people left, providers right, ACT-009 below.
- Do not merge payment and email crossings.

### Legend

| Symbol or label | Meaning |
| --- | --- |
| solid box | modeled actor/system element |
| dashed boundary | trust boundary crossing |
| T-nnn | neutral threat reference; no severity implied |

### Text preview

```text
People and generic requester -> [SCP-001 Picky Party] <-> payment provider
[SCP-001 Picky Party] -> email provider
```

### Omissions

- Exact provider products, deployment/network topology, and native-client exchanges are unresolved.
- Protocol is known only as proposed HTTP JSON at the client boundary; provider protocols are unresolved.

### Validation notes

- All external actors ACT-001–ACT-009 represented.
- All listed threat IDs exist; ranking intentionally omitted.

## Picky Party Containers and Components

**Diagram ID:** `DGM-002`  
**Purpose:** Show logical client, application, persistence, payment, email, provider, and durable-work structure.  
**Audience:** Developers, Architects, Security

### Elements

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

### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| Z-001/Z-002 | Z-003 | bidirectional | Client requests and responses; HTTP JSON proposed; native unresolved | Public through restricted (D-001–D-007) | B-001, B-006 | Threats: T-008, T-009, T-015; Controls: C-002, C-003, C-012 |
| Z-003 | Z-004 | bidirectional | State persistence; Unresolved | Personal, restricted, operational, financial (D-001,D-003–D-007) | B-002 | Threats: T-005; Controls: C-006, C-007, C-009, C-010 |
| Z-003 | Z-005 | bidirectional | Payment commands and validated results; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-005 | Z-007 | bidirectional | Payment provider operations; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-003 | Z-006 | outbound | Access and notice dispatch; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: T-009; Controls: C-001, C-013 |
| Z-006 | Z-007 | outbound | Email provider delivery; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: None; Controls: C-001, C-013 |
| ACT-010 | Z-003/Z-004/Z-005/Z-006 | internal/bidirectional | Scheduled, retry, reconciliation, notification work; Unresolved | Operational and financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-006, T-012, T-043; Controls: C-008 |

### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

### Annotations and ordering

- Dashed groups represent trust boundaries, not deployment networks.
- Technology labels preserve proposed/unresolved status.

- Clients left; application center; persistence below; payment and email gateways right; providers far right.
- Keep payment and email gateways separate.
- Place ACT-010 near application/persistence without implying a deployed service.

### Legend

| Symbol or label | Meaning |
| --- | --- |
| solid box | logical zone or actor |
| dashed group | trust boundary |
| proposed/unresolved | evidence status, not implementation |

### Text preview

```text
Z-001/Z-002 -> Z-003 <-> Z-004
Z-003 <-> Z-005 <-> Z-007
Z-003 -> Z-006 -> Z-007
ACT-010 -> Z-003/Z-004/Z-005/Z-006
```

### Omissions

- No cache, queue, file store, concrete service split, endpoint list, or deployment node is specified.
- Exact technology versions and Node.js/Fastify roles are unresolved.

### Validation notes

- Component names match model zones.
- Only confirmed payment/email logical separation is shown as confirmed; other placement remains proposed or unresolved.

## Picky Party Data Flows

**Diagram ID:** `DGM-003`  
**Purpose:** Trace all nine modeled flows, their data classifications, protocols, and trust crossings.  
**Audience:** Security, Privacy, Developers, Auditors

### Elements

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

### Connections

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

### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

### Annotations and ordering

- Mark every D-003, D-004, D-006, and D-007 carrying flow as sensitive.
- F-001 public disclosure and F-003/F-004/F-009 privacy lifecycle distinctions must remain visible.

- Follow F-001 through F-009 top-to-bottom.
- Keep provider legs beside their gateway.
- Show B-006 response projection separately from B-001 request crossing.

### Legend

| Symbol or label | Meaning |
| --- | --- |
| public | required public data D-002 |
| sensitive | restricted/personal/financial/audience-filtered data |
| dashed crossing | one or more B-nnn trust boundaries |

### Text preview

```text
F-001 public discovery: application -> visitor
F-002 access: application -> email -> client -> application
F-003/F-004 audience data: account roles <-> application <-> persistence
F-005/F-006 finance: clients/application <-> persistence/payment
F-007/F-008 updates/notices: application -> staff/account/email
F-009 lifecycle: application/work dispatcher <-> persistence
```

### Omissions

- Exact message schemas, provider protocols, persistence protocol, field-level pre-confirmation cook update projection, and native paths are unresolved.

### Validation notes

- All F-001–F-009 and D-001–D-007 are represented.
- Sensitivity text is copied from model classifications; no new classification assigned.

## Picky Party Threat-Annotated Architecture

**Diagram ID:** `DGM-004`  
**Purpose:** Overlay every stable threat ID on the architecture without implying a common severity.  
**Audience:** Security reviewers, Developers, Architects

### Elements

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

### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| Z-001/Z-002 | Z-003 | bidirectional | Client requests and responses; HTTP JSON proposed; native unresolved | Public through restricted (D-001–D-007) | B-001, B-006 | Threats: T-008, T-009, T-015; Controls: C-002, C-003, C-012 |
| Z-003 | Z-004 | bidirectional | State persistence; Unresolved | Personal, restricted, operational, financial (D-001,D-003–D-007) | B-002 | Threats: T-005; Controls: C-006, C-007, C-009, C-010 |
| Z-003 | Z-005 | bidirectional | Payment commands and validated results; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-005 | Z-007 | bidirectional | Payment provider operations; Unresolved | Financial (D-006) | B-003, B-004 | Threats: T-002, T-016; Controls: C-001, C-006, C-007 |
| Z-003 | Z-006 | outbound | Access and notice dispatch; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: T-009; Controls: C-001, C-013 |
| Z-006 | Z-007 | outbound | Email provider delivery; Unresolved | Access and filtered notice data (D-001,D-007) | B-005 | Threats: None; Controls: C-001, C-013 |
| ACT-010 | Z-003/Z-004/Z-005/Z-006 | internal/bidirectional | Scheduled, retry, reconciliation, notification work; Unresolved | Operational and financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-006, T-012, T-043; Controls: C-008 |

### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-CLIENT | Client/application trust boundary | Z-001, Z-002, Z-003 | B-001, B-006 | HTTP JSON and server projections proposed; native unresolved |
| BG-PERSIST | Application/persistence trust boundary | Z-003, Z-004 | B-002 | Interfaces and technology unresolved |
| BG-PAY | Isolated payment integration boundary | Z-003, Z-005, Z-007 | B-003, B-004 | Logical isolation confirmed; implementation/protocol unresolved |
| BG-EMAIL | Separate email integration boundary | Z-003, Z-006, Z-007 | B-005 | Logical isolation confirmed; implementation/protocol unresolved |

### Annotations and ordering

- Use one neutral T-nnn marker style for all threats.
- Place markers on A-nnn asset anchors because most asset placement is unresolved; do not infer a storage component.
- T-012/T-013 are availability/failure risks, not attacker assertions.
- T-023–T-029 intentional/required disclosures are privacy tradeoffs, not vulnerability findings.

- Reuse DGM-002 layout.
- Place A-001–A-006 in an unplaced asset rail; A-007 beside Z-005 and A-008 beside Z-006.
- Cluster threat markers by asset; use callouts to keep architecture readable.

### Legend

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

### Text preview

```text
[Unplaced asset rail A-001–A-006 with neutral T-nnn markers]
Z-001/Z-002 -> Z-003 <-> Z-004
Z-003 <-> Z-005[A-007] <-> Z-007
Z-003 -> Z-006[A-008] -> Z-007
```

### Omissions

- Component placement for A-001–A-006 is unresolved, so markers cannot be placed more specifically.
- No unified threat rating exists; no color, size, order, or emphasis implies severity.

### Validation notes

- Every T-001–T-045 appears in the legend and at least one asset or boundary reference.
- Related methods remain distinct; no threat IDs are merged.

## Picky Party Attack Surface

**Diagram ID:** `DGM-005`  
**Purpose:** Show all modeled entry points with authentication, authorization, and derived threat counts.  
**Audience:** Security reviewers, Developers, Auditors

### Elements

| Stable model ID | Label | Kind | Zone | Relevant threats or controls |
| --- | --- | --- | --- | --- |
| EP-001 | Public calendar, event page, and QR URL | entry point | External-facing | Threats: T-012, T-023, T-024, T-026, T-031, T-036; Controls: C-003; Access: Public; no authentication required. Public-field projection C-003.; Threat count: 6 |
| EP-002 | Email verification/sign-in link | entry point | External-facing | Threats: T-001, T-013, T-022, T-035, T-044; Controls: C-011; Access: Possession of verification/sign-in artifact; lifecycle unresolved. Session control C-011.; Threat count: 5 |
| EP-003 | Authenticated views/actions | entry point | External-facing | Threats: T-003, T-004, T-006, T-007, T-009, T-010, T-011, T-012, T-013, T-014, T-018, T-019, T-020, T-021, T-025, T-027, T-028, T-029, T-030, T-031, T-033, T-034, T-035, T-036, T-037, T-040, T-041, T-042, T-043; Controls: C-002, C-003; Access: Authenticated. Ownership, role, suspension, and current assignment C-002; endpoints unspecified.; Threat count: 29 |
| EP-004 | Checkout browser flow | entry point | External-facing | Threats: T-002, T-004, T-005, T-006, T-016, T-017, T-032, T-038, T-039; Controls: C-002, C-006; Access: Authentication requirement not stated in the model. Order/hold and payment checks C-002/C-006.; Threat count: 9 |
| EP-005 | Payment callbacks/reconciliation | entry point | External-facing | Threats: T-002, T-003, T-004, T-005, T-006, T-007, T-012, T-013, T-014, T-016, T-017, T-018, T-020, T-032, T-033, T-038, T-039, T-040, T-043; Controls: C-001, C-006, C-007; Access: Provider-origin authentication protocol unresolved. Evidence/state authorization C-006/C-007.; Threat count: 19 |
| EP-006 | Email delivery gateway | entry point | Integration/internal | Threats: T-001, T-009, T-013, T-019, T-020, T-022, T-035, T-044; Controls: C-001, C-013; Access: Gateway/provider authentication unresolved. Isolation and filtered notices C-001/C-013.; Threat count: 8 |
| EP-007 | Scheduled/retry work | entry point | Integration/internal | Threats: T-003, T-004, T-006, T-007, T-009, T-011, T-012, T-013, T-014, T-017, T-018, T-019, T-020, T-029, T-030, T-033, T-034, T-038, T-040, T-043, T-044; Controls: C-007, C-008; Access: Operational identity unresolved. Eligibility, deduplication, and durable execution C-007/C-008.; Threat count: 21 |

### Connections

| Source ID | Destination ID | Direction | Label / protocol | Data sensitivity | Boundary crossings | Relevant threats or controls |
| --- | --- | --- | --- | --- | --- | --- |
| ACT-001 | EP-001 | inbound | Public discovery; HTTP JSON proposed | Required public (D-002) | B-001, B-006 | Threats: T-012, T-023, T-024, T-026, T-031, T-036; Controls: C-003 |
| ACT-008/Z-001/Z-002 | EP-002 | email then inbound browser use | Verification/sign-in link; Email protocol and link lifecycle unresolved | Access data (D-001) | B-005, B-001 | Threats: T-001, T-013, T-022, T-035, T-044; Controls: C-011 |
| ACT-002/ACT-003/ACT-004/ACT-005/ACT-006 | EP-003 | bidirectional | Authenticated views and actions; HTTP JSON proposed | Restricted and financial (D-001,D-003–D-007) | B-001, B-006 | Threats: T-003, T-004, T-006, T-007, T-009, T-010, T-011, T-012, T-013, T-014, T-018, T-019, T-020, T-021, T-025, T-027, T-028, T-029, T-030, T-031, T-033, T-034, T-035, T-036, T-037, T-040, T-041, T-042, T-043; Controls: C-002, C-003 |
| ACT-003 | EP-004 | bidirectional | Checkout browser flow; Protocol unresolved | Booking and financial (D-005,D-006) | B-001, B-003 | Threats: T-002, T-004, T-005, T-006, T-016, T-017, T-032, T-038, T-039; Controls: C-002, C-006 |
| ACT-007 | EP-005 | inbound/bidirectional | Callbacks and reconciliation; Protocol/authenticity unresolved | Financial (D-006) | B-004 | Threats: T-002, T-003, T-004, T-005, T-006, T-007, T-012, T-013, T-014, T-016, T-017, T-018, T-020, T-032, T-033, T-038, T-039, T-040, T-043; Controls: C-001, C-006, C-007 |
| SCP-001 | EP-006/ACT-008 | outbound | Email delivery; Provider unresolved | Access and filtered notice (D-001,D-007) | B-005 | Threats: T-001, T-009, T-013, T-019, T-020, T-022, T-035, T-044; Controls: C-001, C-013 |
| ACT-010 | EP-007/SCP-001 | internal | Scheduled and retry work; Unresolved | Operational/financial metadata (D-006,D-007) | B-002, B-003, B-005 | Threats: T-003, T-004, T-006, T-007, T-009, T-011, T-012, T-013, T-014, T-017, T-018, T-019, T-020, T-029, T-030, T-033, T-034, T-038, T-040, T-043, T-044; Controls: C-007, C-008 |

### Boundary groups

| Group ID | Label | Members | Model boundaries | Status |
| --- | --- | --- | --- | --- |
| BG-ENTRY | System entry boundary | EP-001, EP-002, EP-003, EP-004, EP-005, EP-006, EP-007 | B-001, B-003, B-004, B-005, B-006 | Entry points are logical; endpoint/protocol detail is incomplete |

### Annotations and ordering

- Threat count equals distinct threats whose affected_ids contain the entry point or one of its flow_ids.
- Use equal neutral styling for every threat; counts do not imply severity.

- Order EP-001 through EP-007.
- Group public/user, provider, and internal-work entries without ranking them.

### Legend

| Symbol or label | Meaning |
| --- | --- |
| EP-nnn | stable entry point ID |
| count | derived number of linked threats; not a score |
| T-nnn | neutral linked threat |

### Text preview

```text
EP-001 Public calendar, event page, and QR URL: 6 linked threats
EP-002 Email verification/sign-in link: 5 linked threats
EP-003 Authenticated views/actions: 29 linked threats
EP-004 Checkout browser flow: 9 linked threats
EP-005 Payment callbacks/reconciliation: 19 linked threats
EP-006 Email delivery gateway: 8 linked threats
EP-007 Scheduled/retry work: 21 linked threats
```

### Omissions

- Concrete API routes, upload/admin-panel endpoints, endpoint schemas, rate limits, provider authentication, operational identities, and native entry points are not specified.

### Validation notes

- All EP-001–EP-007 represented.
- Counts are reproducible from affected entry point/flow IDs and do not create a risk ranking.
