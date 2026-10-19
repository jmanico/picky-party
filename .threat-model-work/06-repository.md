# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "S06-SCOPE-001",
    "repository": "/Users/jmanico/Dropbox/github/picky-party",
    "scan_date": "2026-10-19",
    "included": {
      "files": ["AGENTS.md", "ARCHITECTURE.md", "DESIGN.md", "README.md", "REQUIREMENTS.md", "REQUIREMENT_TEMPLATE.md", "SECURITY.md", "logo.svg"],
      "count": 8,
      "directories": ["repository root"]
    },
    "excluded": [
      {"path": ".git/", "reason": "Git metadata excluded by caller instruction."},
      {"path": ".threat-model-work/", "reason": "Generated threat-model pipeline artifacts excluded by caller instruction."}
    ],
    "inventory_result": "Seven Markdown documents and one static SVG are present. No application source, dependency manifest, lockfile, database schema/migration, test, runtime configuration, secret/environment file, CI workflow, container manifest, infrastructure-as-code, or deployment artifact is present.",
    "implementation_status": "No application implementation exists.",
    "analysis_limit": "Repository reconnaissance can report specification intent and missing implementation evidence, but cannot test runtime behavior, control presence/effectiveness, vulnerabilities, or production topology."
  },
  "evidence": [
    {
      "id": "S06-E-001",
      "path": "AGENTS.md",
      "line_range": "1-16",
      "kind": "repository instructions",
      "claims_supported": ["The four primary specifications are required project instructions.", "Leaf implementation issues use REQUIREMENT_TEMPLATE.md.", "Package, build, test, lint, format, CI, release, and version-control workflow decisions are TO BE DECIDED."]
    },
    {
      "id": "S06-E-002",
      "path": "README.md",
      "line_range": "1",
      "kind": "minimal repository readme",
      "claims_supported": ["The README contains only the repository title."]
    },
    {
      "id": "S06-E-003",
      "path": "REQUIREMENT_TEMPLATE.md",
      "line_range": "1-124",
      "kind": "implementation-issue requirement template",
      "claims_supported": ["The repository contains a template for traceability, security context, failure behavior, testing, dependencies, and implementation notes.", "The template is guidance/placeholders rather than an implemented control."]
    },
    {
      "id": "S06-E-004",
      "path": "REQUIREMENTS.md",
      "line_range": "1-288",
      "kind": "product requirements",
      "claims_supported": ["The intended actors, workflows, business records, payment/email integrations, verified-email access, privacy obligations, and quality targets are specified.", "Requirements are product decisions rather than measured results.", "Provider selection and jurisdictions remain unresolved."]
    },
    {
      "id": "S06-E-005",
      "path": "ARCHITECTURE.md",
      "line_range": "1-282",
      "kind": "architecture design",
      "claims_supported": ["The document explicitly describes a system with no implementation at line 7.", "Node.js, Fastify, ReactJS, and React Native are documented choices without versions at line 15 and lines 264-267.", "Logical modules, HTTP commands/reads, persistence, callbacks, sessions, and trust boundaries are proposed or specified design, not repository implementation.", "Payment/email outbound separation is a confirmed logical design boundary; other module boundaries remain proposed.", "Deployment is UNKNOWN and no topology is specified at line 153."]
    },
    {
      "id": "S06-E-006",
      "path": "SECURITY.md",
      "line_range": "1-180",
      "kind": "security decisions and candidate-rule inventory",
      "claims_supported": ["No application implementation exists and framework/runtime versions are unresolved.", "Every SC-001 through SC-009 rule is BLOCKED.", "No candidate secure-coding pack is selected or active.", "Persistence, deployment, providers, session lifecycle, validation, update transport, and rendering remain open."]
    },
    {
      "id": "S06-E-007",
      "path": "DESIGN.md",
      "line_range": "1-181",
      "kind": "visual and interaction design",
      "claims_supported": ["The document explicitly says no application implementation exists at line 96.", "It defines proposed presentation patterns and treats REQUIREMENTS.md as behavior authority.", "It identifies logo.svg as the primary mark and defines its presentation constraints."]
    },
    {
      "id": "S06-E-008",
      "path": "logo.svg",
      "line_range": "1-6",
      "kind": "static SVG asset",
      "claims_supported": ["The repository contains a 64-by-64 Picky Party SVG with title, description, one rectangle, and one path.", "The SVG contains no repository-evidenced script, external resource, link, form, or runtime entry point."]
    },
    {
      "id": "S06-E-009",
      "path": "repository inventory",
      "line_range": "not applicable",
      "kind": "automated checkout enumeration",
      "claims_supported": ["rg --files -uu excluding .git/** and .threat-model-work/** returned exactly the eight included files.", "A targeted filename scan found no manifest, lockfile, source, configuration, database, CI, deployment, container, or infrastructure file.", "The checkout has no included subdirectory."],
      "evidence_limit": "This is a scan result rather than a repository file and has no file line."
    },
    {
      "id": "S06-E-010",
      "path": "secure-coding lookup output",
      "line_range": "not applicable",
      "kind": "tool execution record",
      "claims_supported": ["find_pack.py was run for nodejs, fastify, react, and react native.", "resolve_prompt.py was run for current candidate identities js/nodejs/26, js/fastify/5.12, js/react/19, and js/react-native/0.87.", "No candidate is eligible as a project rule source because the repository establishes no corresponding version or implementation."],
      "evidence_limit": "Lookup results describe available packs, not the repository's implemented stack."
    }
  ],
  "system": {
    "assets": [
      {"id": "S06-AST-001", "name": "Project instruction and specification corpus", "status": "present", "paths": ["AGENTS.md", "REQUIREMENTS.md", "ARCHITECTURE.md", "SECURITY.md", "DESIGN.md"], "evidence_ids": ["S06-E-001", "S06-E-004", "S06-E-005", "S06-E-006", "S06-E-007"]},
      {"id": "S06-AST-002", "name": "Implementation requirement template", "status": "present", "paths": ["REQUIREMENT_TEMPLATE.md"], "evidence_ids": ["S06-E-003"]},
      {"id": "S06-AST-003", "name": "Repository README", "status": "present but title-only", "paths": ["README.md"], "evidence_ids": ["S06-E-002"]},
      {"id": "S06-AST-004", "name": "Picky Party logo", "status": "present static SVG", "paths": ["logo.svg"], "evidence_ids": ["S06-E-007", "S06-E-008"]},
      {
        "id": "S06-AST-005",
        "name": "Documented intended technology choices",
        "status": "specification only; no implementation or versions",
        "technologies": [
          {"name": "Node.js", "version": "UNKNOWN", "role": "role label conflicts with Fastify input"},
          {"name": "Fastify", "version": "UNKNOWN", "role": "role label conflicts with Node.js input"},
          {"name": "ReactJS", "version": "UNKNOWN", "role": "web client choice"},
          {"name": "React Native", "version": "UNKNOWN", "role": "client choice with unresolved native scope"},
          {"name": "PostgreSQL", "version": "UNKNOWN", "role": "PROPOSED and unconfirmed persistence"}
        ],
        "evidence_ids": ["S06-E-005", "S06-E-006"]
      }
    ],
    "actors": [
      {"id": "S06-ACT-001", "name": "Visitor, Organizer, Attendee, cook/shopper, and Admin", "status": "specified product actors only; no actor-handling implementation", "evidence_ids": ["S06-E-004", "S06-E-005"]},
      {"id": "S06-ACT-002", "name": "Payment and email services", "status": "specified external systems only; provider selection and integration absent", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-006"]}
    ],
    "data": [
      {"id": "S06-DAT-001", "name": "Repository documentation content", "status": "present", "evidence_ids": ["S06-E-001", "S06-E-002", "S06-E-003", "S06-E-004", "S06-E-005", "S06-E-006", "S06-E-007"]},
      {"id": "S06-DAT-002", "name": "Static logo vector data", "status": "present", "evidence_ids": ["S06-E-008"]},
      {"id": "S06-DAT-003", "name": "Accounts, event addresses, food needs, orders/bookings, financial records, updates, and audit records", "status": "specified product data only; no schema, store, or sample data", "evidence_ids": ["S06-E-004", "S06-E-005"]}
    ],
    "zones": [
      {"id": "S06-ZON-001", "name": "Repository checkout", "status": "observed; documentation and logo only after exclusions", "evidence_ids": ["S06-E-009"]},
      {"id": "S06-ZON-002", "name": "Untrusted client / trusted application / persistence / external providers", "status": "documentation-only logical zones; no runtime topology", "evidence_ids": ["S06-E-005"]}
    ],
    "boundaries": [
      {"id": "S06-BND-001", "name": "Client-to-application", "status": "documented logical boundary; no implementation evidence", "evidence_ids": ["S06-E-005"]},
      {"id": "S06-BND-002", "name": "Application-to-persistence", "status": "proposed logical boundary; no implementation evidence", "evidence_ids": ["S06-E-005"]},
      {"id": "S06-BND-003", "name": "Application-to-payment and callback", "status": "specified logical design; no provider/implementation evidence", "evidence_ids": ["S06-E-005", "S06-E-006"]},
      {"id": "S06-BND-004", "name": "Application-to-email", "status": "specified logical design; no provider/implementation evidence", "evidence_ids": ["S06-E-005", "S06-E-006"]}
    ],
    "flows": [
      {"id": "S06-FLW-001", "name": "HTTP commands and reads", "status": "proposed; no routes, handlers, schemas, or server files", "boundary_ids": ["S06-BND-001"], "evidence_ids": ["S06-E-005", "S06-E-009"]},
      {"id": "S06-FLW-002", "name": "Persistence reads/writes and durable work", "status": "proposed; no store, schema, migration, worker, or scheduler files", "boundary_ids": ["S06-BND-002"], "evidence_ids": ["S06-E-005", "S06-E-009"]},
      {"id": "S06-FLW-003", "name": "Payment outbound and callback", "status": "specified; no provider adapter or receiver", "boundary_ids": ["S06-BND-003"], "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009"]},
      {"id": "S06-FLW-004", "name": "Email outbound", "status": "specified; no provider adapter", "boundary_ids": ["S06-BND-004"], "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009"]}
    ],
    "entry_points": [
      {"id": "S06-EP-001", "name": "Proposed HTTP JSON commands and reads", "status": "documentation only; no enumeratable endpoint", "flow_ids": ["S06-FLW-001"], "authentication": "specified verified-email/session behavior; implementation absent", "authorization": "specified role/ownership/assignment behavior; implementation absent", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-009"]},
      {"id": "S06-EP-002", "name": "Proposed payment callback adapter", "status": "documentation only; no receiver", "flow_ids": ["S06-FLW-003"], "authentication": "provider authenticity contract unresolved", "authorization": "workflow validation specified; implementation absent", "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009"]}
    ]
  },
  "methods": [
    {
      "id": "S06-M-001",
      "name": "Automated repository analysis",
      "procedure": ["Enumerated all files with rg --files -uu excluding .git/** and .threat-model-work/**.", "Inspected every included readable file.", "Classified file types and scanned for source, manifests, locks, schemas, tests, configuration, CI, deployment, containers, and infrastructure.", "Executed the eight required phases in order.", "Ran secure-coding pack discovery and candidate composition resolution for documented technology names."],
      "limitations": "There is no application implementation or repository-established technology version."
    },
    {
      "id": "S06-M-002",
      "name": "Secure-coding rule resolution",
      "discovery": [
        {"term": "nodejs", "result": "versioned candidates found; repository version UNKNOWN"},
        {"term": "fastify", "result": "js/fastify/5.12 candidate found; repository version UNKNOWN"},
        {"term": "react", "result": "versioned React and alternate candidates found; repository version UNKNOWN"},
        {"term": "react native", "result": "versioned candidates found; repository version UNKNOWN"}
      ],
      "resolved_candidate_metadata": ["js/nodejs/26", "js/fastify/5.12", "js/react/19", "js/react-native/0.87"],
      "active_rule_dependencies": [],
      "disposition": "No pack is active or eligible because no implementation or version establishes a matching in-scope stack. Candidate rules were not used for findings.",
      "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-010"]
    }
  ],
  "threats": [],
  "controls": [],
  "requirements": [
    {"id": "S06-REQ-001", "name": "Specification linkage and issue-body governance", "status": "repository instruction", "evidence_ids": ["S06-E-001", "S06-E-003"]},
    {"id": "S06-REQ-002", "name": "Documented product security, privacy, reliability, and accessibility behavior", "status": "requirements only; not implemented/tested", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-007"]},
    {"id": "S06-REQ-003", "name": "Blocked secure-coding rules and open security decisions", "status": "all rules BLOCKED; no active implementation rule", "evidence_ids": ["S06-E-006"]}
  ],
  "risks": [],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [],
  "coverage": [
    {"id": "S06-COV-001", "phase": "1 — Technology Stack Identification", "disposition": "documentation-only / implementation not applicable", "result": "Node.js, Fastify, ReactJS, and React Native are intended choices without versions; PostgreSQL is proposed. No manifests, locks, imports, source, schema, or runtime config exist. Pack discovery/resolution ran, but no pack is eligible.", "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009", "S06-E-010"]},
    {"id": "S06-COV-002", "phase": "2 — Entry Point Enumeration", "disposition": "not applicable to implementation", "result": "No REST route, GraphQL schema, gRPC definition, WebSocket, webhook receiver, queue consumer, CLI, cron, worker, scheduler, upload/download endpoint, or import/export implementation exists. Proposed HTTP and callback paths are documentation-only.", "evidence_ids": ["S06-E-005", "S06-E-009"]},
    {"id": "S06-COV-003", "phase": "3 — Data Store Analysis", "disposition": "not applicable to implementation; evidence gap", "result": "No store configuration, schema, model, migration, encryption setting, deletion job, or retention implementation exists. Product data/retention is specified; relational/PostgreSQL persistence is proposed.", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-006", "S06-E-009"]},
    {"id": "S06-COV-004", "phase": "4 — Authentication and Authorization Architecture", "disposition": "not applicable to implementation; evidence gap", "result": "Identity and authorization behavior is specified, but no middleware, handler, policy, decorator, session store, token code, or endpoint enforcement exists. No endpoint can be classified as protected/unprotected in code.", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-006", "S06-E-009"]},
    {"id": "S06-COV-005", "phase": "5 — Security Controls Inventory", "disposition": "not applicable to implementation; evidence gap", "result": "No code/config demonstrates validation, parameterized queries, sanitization, encoding, headers, CORS, CSP, rate limiting, logging, monitoring, secrets, locking, scanning, or update policy. All SC rules are BLOCKED. Absence is not a vulnerability finding.", "evidence_ids": ["S06-E-006", "S06-E-009"]},
    {"id": "S06-COV-006", "phase": "6 — Deployment and Infrastructure Analysis", "disposition": "not applicable to implementation; evidence gap", "result": "No container, orchestrator, IaC, network, environment, production, or debug config exists. Deployment environment/topology is UNKNOWN.", "evidence_ids": ["S06-E-001", "S06-E-005", "S06-E-006", "S06-E-009"]},
    {"id": "S06-COV-007", "phase": "7 — AI/ML Component Analysis", "disposition": "not applicable", "result": "No model serving, embeddings, vector database, RAG, LLM, prompt, training data, model artifact, inference endpoint, AI dependency, agent, or AI tool exists. Automatic dietary certification is out of scope.", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-006", "S06-E-007", "S06-E-009"]},
    {"id": "S06-COV-008", "phase": "8 — Trust Boundary Identification", "disposition": "documentation-only / implementation evidence gap", "result": "Architecture documents client/application, persistence, payment, callback, and email logical boundaries. No runtime component, endpoint, adapter, store, deployment, or control implementation establishes an operational crossing.", "evidence_ids": ["S06-E-004", "S06-E-005", "S06-E-006", "S06-E-009"]}
  ],
  "conflicts": [
    {"id": "S06-CON-001", "description": "Node.js is supplied under server framework and Fastify under runtime, while architecture proposes the technically reversed roles; acceptance remains TO BE DECIDED.", "evidence_ids": ["S06-E-005", "S06-E-006"], "disposition": "unresolved; no implementation/version selected"},
    {"id": "S06-CON-002", "description": "Available candidate compositions contain different Node.js baselines, while the repository establishes no project version.", "evidence_ids": ["S06-E-006", "S06-E-010"], "disposition": "unresolved; candidate packs inactive"}
  ],
  "gaps": [
    {"id": "S06-GAP-001", "description": "No application implementation, source layout, generated application output, dependency manifest, lockfile, or test exists; implementation security cannot be assessed.", "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-007", "S06-E-009"]},
    {"id": "S06-GAP-002", "description": "Languages, runtimes, frameworks, libraries, providers, and versions are not established by implementation evidence; no secure-coding pack is eligible as an active finding dependency.", "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009", "S06-E-010"]},
    {"id": "S06-GAP-003", "description": "No implemented entry point, auth enforcement point, persistence layer, data protection mechanism, security configuration, deployment topology, operational control, or runtime boundary can be inspected.", "evidence_ids": ["S06-E-005", "S06-E-006", "S06-E-009"]},
    {"id": "S06-GAP-004", "description": "Package, install, development, build, test, lint, format, CI, release, and version-control conventions remain TO BE DECIDED.", "evidence_ids": ["S06-E-001"]},
    {"id": "S06-GAP-005", "description": "README.md provides no setup, architecture, security, testing, or operational inventory beyond the title.", "evidence_ids": ["S06-E-002"]}
  ]
}
```

## Reconnaissance Report

### Checkout inventory and exclusions

The analyzed checkout contains exactly eight included files at the root: AGENTS.md, ARCHITECTURE.md, DESIGN.md, README.md, REQUIREMENTS.md, REQUIREMENT_TEMPLATE.md, SECURITY.md, and logo.svg. The first seven are documentation; logo.svg is a static 64-by-64 vector containing a title, description, rectangle, and path. Git metadata and .threat-model-work/ were excluded as directed. No other included directory or file was found.

The scan found no application source, manifest, lockfile, schema, migration, test, runtime configuration, environment/secret file, CI workflow, container artifact, infrastructure-as-code, or deployment manifest. ARCHITECTURE.md line 7 and DESIGN.md line 96 independently state that no application implementation exists. This is an implementation evidence gap, not proof of a vulnerability.

### Phase 1 — Technology stack

Documentation names Node.js, Fastify, ReactJS, and React Native without versions. Their Node.js/Fastify role labels conflict, native scope is unresolved, and PostgreSQL is only a proposal. No repository artifact establishes an implemented technology or version.

The required lookup ran for all four names, and current candidate composition metadata was resolved. None is active or eligible because selecting its version would invent facts. SECURITY.md likewise marks all SC rules BLOCKED. No technology-specific rule was used for a finding.

### Phase 2 — Entry points

No implemented HTTP route, GraphQL schema, gRPC service, WebSocket, webhook receiver, queue consumer, CLI, cron, worker, scheduled task, upload/download endpoint, or import/export interface exists. Architecture proposes HTTP JSON commands/reads and a payment callback adapter, but there are no route or receiver files. Authentication and authorization remain specification intent.

### Phase 3 — Data stores

No database, cache, object storage, filesystem store, or message queue is configured. No schema, model, migration, connection string, encryption-at-rest setting, deletion job, or retention implementation exists. Requirements specify sensitive data and retention duties; architecture proposes relational records and PostgreSQL without confirming them.

### Phase 4 — Authentication and authorization

Requirements specify verified email, email-link sign-in, logout, roles, Admin grants, event ownership, current assignments, suspension, and own-record access. Architecture proposes server-side sessions and server enforcement. No middleware, policy, decorator, handler, session store, or authorization code exists. No endpoint can be classified from code as protected, unprotected, correctly enforced, or incorrectly enforced.

### Phase 5 — Security controls

No implementation/config demonstrates validation, parameterized data access, sanitization, output encoding, headers, CORS, CSP, rate limiting, logging, monitoring, secrets management, dependency locking, vulnerability scanning, or update automation. SECURITY.md contains only BLOCKED rule groups and open decisions. The requirement template has future placeholders, which are not controls. No implemented or verified control is recorded.

### Phase 6 — Deployment and infrastructure

No Dockerfile, Compose file, Kubernetes manifest, Terraform, CloudFormation, Pulumi, Ansible, network definition, load balancer, firewall, VPC, service mesh, environment profile, or debug/production setting exists. Architecture records deployment as UNKNOWN and omits topology.

### Phase 7 — AI/ML

No model serving, embeddings, vector database, RAG, LLM, prompt, AI agent/tool, training data, model artifact, inference endpoint, or AI dependency exists. Automatic dietary certification is outside first-release scope. AI/ML implementation analysis is not applicable.

### Phase 8 — Trust boundaries

Architecture documents client/application, persistence, payment outbound/callback, and email logical boundaries. Payment/email separation is a confirmed design instruction; other boundaries/mechanisms are proposed or unresolved. No runtime component, adapter, store, deployment, or control demonstrates an operational crossing.

### Findings, assumptions, and gaps

No repository-supported threat finding is emitted. There is no active versioned rule dependency and no code/config against which to establish a weakness. Missing implementation evidence appears only in gaps.

Material gaps are the absence of application/dependency/test evidence; unresolved versions/providers; no inspectable endpoints, stores, auth enforcement, controls, deployment, or runtime boundary; undecided development/CI/release commands; and a title-only README. No new runtime topology or control is assumed.
