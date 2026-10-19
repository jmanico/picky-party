# THREAT_MODEL_FRAGMENT

## Model

```json
{
  "scope": {
    "id": "S05-SCOPE-001",
    "system": "Picky Party first-release specification",
    "analysis_scope": "AI and machine-learning lifecycle and threat coverage for the supplied system evidence",
    "disposition": "not applicable to the documented system",
    "rationale": "The supplied specifications define conventional deterministic web, identity, event, order, payment, notification, and ingredient-calculation workflows. They identify no AI/ML model, model-serving component, AI agent, LLM, retrieval system, training or adaptation process, AI dataset, model artifact, inference interface, AI monitoring, or feedback loop. Automatic dietary certification is expressly outside first-release scope.",
    "limits": [
      "No implementation exists, so the absence of AI/ML in an implemented system cannot be independently verified.",
      "This disposition applies only to the supplied first-release specification and must be reassessed if an AI/ML component is added."
    ]
  },
  "evidence": [
    {
      "id": "S05-E-001",
      "artifact": "REQUIREMENTS.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Required Requirement Inputs", "Product Rules and Terms", "FR-1.1–FR-11.7", "NFR-1.1–NFR-3.6"],
      "observations": [
        "The required entities and workflows contain no AI/ML component or behavior.",
        "Ingredient planning is defined by exact conversions, a fixed 10% multiplier, and upward rounding.",
        "Dietary labels are requests rather than automatic certifications, and automatic dietary certification is outside first-release scope."
      ],
      "limits": "Requirements are stated product decisions rather than implementation evidence."
    },
    {
      "id": "S05-E-002",
      "artifact": "ARCHITECTURE.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["§3–§8", "§12", "Required Architecture Inputs", "AQ-1–AQ-8"],
      "observations": [
        "The component, trust-boundary, runtime, data-flow, and dependency models identify no AI/ML component, lifecycle, dependency, interface, model artifact, retrieval path, agent, or feedback loop.",
        "Ingredient totals are described as deterministic exact arithmetic.",
        "The document states that the system has no implementation."
      ],
      "limits": "Most technical mechanisms are proposed and deployment is unresolved; architecture labels do not prove implementation."
    },
    {
      "id": "S05-E-003",
      "artifact": "SECURITY.md",
      "revision": "not supplied",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Secure-Coding Inputs", "Selected Manicode Prompts", "SC-001–SC-009", "OD-001–OD-012"],
      "observations": [
        "No selected or candidate technology is identified as an AI/ML model, model-serving system, LLM, agent, retrieval component, or ML lifecycle tool.",
        "No application implementation exists and all secure-coding rules are BLOCKED."
      ],
      "limits": "Candidate technology notes do not establish project facts or active controls."
    },
    {
      "id": "S05-E-004",
      "artifact": "DESIGN.md",
      "revision": "alpha",
      "provenance": "project specification supplied as SYSTEM_UNDER_REVIEW",
      "locators": ["Overview", "Components", "Do's and Don'ts"],
      "observations": [
        "The interaction patterns expose no AI-generated content, inference, recommendation, assistant, retrieval, agent, or feedback behavior.",
        "The design forbids treating dietary labels or the logo as proof of medical suitability and forbids adding behavior not defined by REQUIREMENTS.md.",
        "The document states that no application implementation exists."
      ],
      "limits": "Visual arrangements and tokens are assumptions, not observed implementation."
    }
  ],
  "system": {
    "assets": [],
    "actors": [],
    "data": [],
    "zones": [],
    "boundaries": [],
    "flows": [],
    "entry_points": []
  },
  "methods": [
    {
      "id": "S05-M-001",
      "name": "MITRE ATLAS",
      "release": "ATLAS content v2026.09, data format v6",
      "verification_source": "https://github.com/mitre-atlas/atlas-data/releases/tag/v2026.09",
      "verification_status": "verified",
      "release_inventory": "1 matrix, 16 tactics, 120 techniques, 88 sub-techniques",
      "application": "All current tactics, techniques, and sub-techniques were checked for applicability. No AI/ML lifecycle element exists in the documented system, so every item is not applicable and no ATLAS identifier is attached to a finding."
    },
    {
      "id": "S05-M-002",
      "name": "OWASP Machine Learning Security Top 10",
      "edition": "2023 draft release v0.2",
      "verification_source": "https://github.com/OWASP/www-project-machine-learning-security-top-10",
      "verification_status": "verified as the published draft list referenced by the current project repository",
      "release_inventory": "10 draft ML categories",
      "application": "All ten draft categories were checked. No ML model, data pipeline, training, artifact, deployment, inference, monitoring, or feedback element exists in the documented system, so every category is not applicable and no ML identifier is attached to a finding."
    },
    {
      "id": "S05-M-003",
      "name": "OWASP GenAI LLM Top 10",
      "edition": "2026",
      "verification_source": "https://genai.owasp.org/resource/owasp-genai-llm-top-10-2026/",
      "verification_status": "verified as the current edition",
      "release_inventory": "10 LLM application categories",
      "application": "Not applicable under the stage rule limiting this checklist to evidenced LLM, retrieval, agent, or tool behavior. The supplied system contains none; all ten categories therefore have a not-applicable disposition and no LLM identifier is attached to a finding."
    }
  ],
  "threats": [],
  "controls": [],
  "requirements": [
    {
      "id": "S05-REQ-001",
      "source": "REQUIREMENTS.md, Product Rules and Terms",
      "statement": "Group bookings, extra portions, offline payments, waitlists, discounts, and automatic dietary certification are outside first-release scope.",
      "evidence_ids": ["S05-E-001"]
    },
    {
      "id": "S05-REQ-002",
      "source": "REQUIREMENTS.md FR-3.23 and DESIGN.md Do's and Don'ts",
      "statement": "Dietary labels are presented as requests rather than medical or dietary certifications; neither labels nor the logo prove medical suitability.",
      "evidence_ids": ["S05-E-001", "S05-E-004"]
    },
    {
      "id": "S05-REQ-003",
      "source": "REQUIREMENTS.md FR-10.2–FR-10.11 and ARCHITECTURE.md §8",
      "statement": "Ingredient totals use deterministic specified inputs, exact unit conversion, a fixed 10% multiplier, and upward rounding.",
      "evidence_ids": ["S05-E-001", "S05-E-002"]
    }
  ],
  "risks": [],
  "attack_trees": [],
  "attack_paths": [],
  "visualizations": [],
  "coverage": [
    {
      "id": "S05-COV-001",
      "subject": "AI/ML lifecycle",
      "method_ids": ["S05-M-001", "S05-M-002", "S05-M-003"],
      "items": [
        {"phase": "data sourcing and preparation", "disposition": "not present", "rationale": "No AI/ML dataset, label, feature, corpus, embedding source, or preparation process is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "training or adaptation", "disposition": "not present", "rationale": "No model training, fine-tuning, adaptation, prompt construction, or optimization process is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "evaluation", "disposition": "not present", "rationale": "No AI/ML evaluation, benchmark, red-team evaluation, or model-safety test is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "artifact storage", "disposition": "not present", "rationale": "No model, weight, checkpoint, prompt, embedding index, tokenizer, or other AI artifact is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "deployment", "disposition": "not present", "rationale": "No AI/ML service, runtime, model server, accelerator, or AI provider deployment is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "inference", "disposition": "not present", "rationale": "No inference input/output, recommendation, classification, generation, retrieval, agent, or AI tool-call interface is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "monitoring", "disposition": "not present", "rationale": "No AI/ML behavior, drift, output, safety, or model-performance monitoring is specified.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]},
        {"phase": "feedback", "disposition": "not present", "rationale": "No human or automated feedback loop updates an AI/ML dataset, prompt, model, policy, or artifact.", "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]}
      ]
    },
    {
      "id": "S05-COV-002",
      "subject": "MITRE ATLAS",
      "method_ids": ["S05-M-001"],
      "items_checked": "All 16 tactics, 120 techniques, and 88 sub-techniques in ATLAS content v2026.09",
      "disposition": "not applicable",
      "rationale": "There is no supported AI/ML lifecycle element, system component, artifact, interface, tool, retrieval path, or autonomous behavior to which an ATLAS item could attach.",
      "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"],
      "threat_ids": []
    },
    {
      "id": "S05-COV-003",
      "subject": "OWASP Machine Learning Security Top 10",
      "method_ids": ["S05-M-002"],
      "items_checked": "All 10 categories in the 2023 draft release v0.2",
      "disposition": "not applicable",
      "rationale": "The documented system contains no ML lifecycle, model, artifact, pipeline, deployment, inference, or output.",
      "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"],
      "threat_ids": []
    },
    {
      "id": "S05-COV-004",
      "subject": "OWASP GenAI LLM Top 10",
      "method_ids": ["S05-M-003"],
      "items_checked": "All 10 categories in the 2026 edition",
      "disposition": "not applicable",
      "rationale": "The documented system contains no LLM, generative AI, retrieval, agent, tool-use, or model-output behavior.",
      "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"],
      "threat_ids": []
    }
  ],
  "conflicts": [],
  "gaps": [
    {
      "id": "S05-GAP-001",
      "description": "No implementation exists, so the specification-level absence of AI/ML cannot be independently confirmed against source code, dependencies, deployment configuration, provider contracts, runtime inventory, or telemetry.",
      "evidence_ids": ["S05-E-002", "S05-E-003", "S05-E-004"]
    },
    {
      "id": "S05-GAP-002",
      "description": "The specifications exclude automatic dietary certification but do not state a project-wide permanent prohibition on every possible future AI/ML component. Any later AI/ML, LLM, retrieval, agent, or AI tool addition requires a new lifecycle and taxonomy assessment.",
      "evidence_ids": ["S05-E-001", "S05-E-002"]
    },
    {
      "id": "S05-GAP-003",
      "description": "No approved risk method, likelihood, impact, severity, owner, or deadline is supplied. No risk result is created because no evidence-supported AI/ML threat exists.",
      "evidence_ids": ["S05-E-001", "S05-E-002", "S05-E-003", "S05-E-004"]
    }
  ]
}
```

## Summary

### Scope and evidence limits

This stage assessed the supplied first-release Picky Party specifications for AI and machine-learning lifecycle elements. The specifications describe deterministic web, identity, event, order, payment, notification, and ingredient-calculation workflows. They identify no AI/ML model, dataset, training or adaptation process, evaluation, model artifact, deployment, inference interface, retrieval path, agent, AI tool, model monitoring, or feedback loop. Automatic dietary certification is expressly outside first-release scope.

No implementation exists. The result is therefore a specification-level not-applicable disposition, not independent proof that a future or implemented system contains no AI/ML. Any later AI/ML addition requires reassessment.

### AI/ML lifecycle, data flow, and trust boundaries

Data sourcing/preparation, training/adaptation, evaluation, artifact storage, AI deployment, inference, AI monitoring, and AI feedback are each recorded as not present. Because no AI/ML lifecycle component or flow is supported by evidence, this stage models no AI-specific asset, actor, data object, zone, boundary, flow, dependency, or entry point. The ordinary application and provider boundaries in ARCHITECTURE.md do not become AI boundaries merely because they process data.

### Evidenced threats and control status

No AI/ML threat is evidenced, so the threats, controls, risks, attack trees, and attack paths collections are empty. This does not claim that the conventional application is secure. Conventional threats belong to the other pipeline stages. The fixed ingredient calculation, the presentation of dietary labels as requests, and the exclusion of automatic dietary certification establish product behavior; they are not AI security controls.

### ATLAS and OWASP coverage

| Checklist | Edition checked | Disposition | Findings |
| --- | --- | --- | --- |
| MITRE ATLAS | Content v2026.09, data format v6; 16 tactics, 120 techniques, 88 sub-techniques | Every item not applicable because no AI/ML lifecycle element exists | None |
| OWASP Machine Learning Security Top 10 | 2023 draft release v0.2; all 10 categories | Every item not applicable because no ML lifecycle or component exists | None |
| OWASP GenAI LLM Top 10 | 2026; all 10 categories | Every item not applicable because no LLM, retrieval, agent, tool, or generated-output behavior exists | None |

### Risk, conflicts, and gaps

No AI/ML risk result is produced because there is no evidence-supported AI/ML threat and no approved risk method. No AI/ML-relevant conflict appears in the supplied artifacts.

The material gaps are the absence of implementation evidence with which to confirm the specified component inventory, the lack of a permanent project-wide prohibition covering all possible future AI/ML additions, and the absence of a supplied risk method. These gaps do not establish a vulnerability.
