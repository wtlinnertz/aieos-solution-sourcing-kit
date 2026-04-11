# Sourcing Decision Record — Specification

Version: v1.0

The Sourcing Decision Record (SDR) is the terminal artifact of the Solution Sourcing Kit. It documents the sourcing decision (Build, Buy, or Adopt), provides rationale grounded in VER evaluation data, and defines the downstream routing that determines how the initiative enters the Engineering Execution Kit.

The SDR is a human-authored decision artifact. It is validated against this spec before the initiative proceeds to EEK.

---

## What This Artifact Is Not

- **Not an evaluation.** The SDR records the decision and its rationale — it does not evaluate or score options. Evaluation belongs in the VER.
- **Not a procurement contract.** The SDR documents the sourcing decision; commercial terms, vendor contracts, and licensing agreements are downstream activities.
- **Not a technical design.** The SDR states what sourcing approach was selected; how the solution is implemented or integrated belongs in EEK artifacts (SAD, TDD).
- **Not a PRD or requirements document.** The SDR does not define what to build — the DPRD does. The SDR determines how the solution is sourced.

---

## Purpose

The SDR serves three roles:

1. **Decision record** — Captures the specific sourcing decision (Build / Buy / Adopt), who made it, and when, providing an auditable trail
2. **Rationale preservation** — Documents why the decision was made by referencing VER evaluation data, ensuring the reasoning is preserved and traceable
3. **Routing directive** — Defines how the initiative enters EEK based on the sourcing decision, including scope adjustments for Buy and Adopt paths

---

## Upstream Dependencies

- Frozen Vendor/Solution Evaluation Record (VER) — provides the evaluation data the decision must reference
- Frozen Sourcing Options Evaluation Record (SOER) — provides the options and criteria context
- Frozen Discovery PRD (DPRD) — provides the requirements the sourcing decision must satisfy

---

## Required Sections

1. Document Control
2. Decision Statement
3. Decision Rationale
4. Tradeoffs Accepted
5. Risk Mitigations
6. Downstream Routing
7. Stakeholder Sign-off
8. Completeness Checklist
9. Freeze Declaration

---

## Content Rules

### Document Control
**Rules**
- SDR ID must be present (format: SDR-{PROJECT}-{NNN})
- Date must be present
- VER reference must be present (the frozen VER ID this SDR is based on)
- SOER reference must be present
- DPRD reference must be present
- Decision authority must be present — the named individual who made the decision (not a team or committee; decisions have individual accountability)
- Spec Version must be present
- Status must be one of: Draft | Validated | Frozen

**Failure Examples**
- SDR ID absent
- VER reference absent
- Decision authority listed as a team name ("Architecture Board") rather than a named individual
- DPRD reference absent

### Decision Statement
**Rules**
- A single, clear, specific sourcing decision must be stated
- The decision must be one of:
  - **Build** — custom development to satisfy DPRD requirements
  - **Buy {vendor/product}** — acquire a commercial product (vendor and product must be named)
  - **Adopt {project}** — adopt an open-source project (project must be named)
- The statement must be unambiguous — a reader must be able to determine exactly what was decided
- The statement must not be conditional ("If vendor negotiations succeed, we will Buy" is not a decision)
- If the decision is Buy or Adopt, the specific vendor/product or OSS project must be identified by name

**Failure Examples**
- Decision statement absent
- Statement is vague ("We will use an external solution")
- Statement is conditional
- Buy decision without named vendor/product
- Adopt decision without named project
- Multiple decisions combined ("We will Buy X and Build Y" — each requires its own SDR if they are separate sourcing decisions; or clarify that the initiative has a single combined approach)

### Decision Rationale
**Rules**
- The rationale must explain why the selected option was chosen over the alternatives
- The rationale must reference specific VER evaluation data — criterion scores, cost model findings, risk assessment findings, capability fit results, or integration complexity estimates
- Every VER criterion where the selected option did not score highest must be addressed — the rationale must explain why the overall decision is justified despite those criterion-level disadvantages
- The rationale must not introduce evaluation data not present in the VER
- The rationale must not rely solely on authority ("the CTO decided") without substantive reasoning grounded in VER data

**Failure Examples**
- Rationale absent
- Rationale does not reference VER data
- Rationale introduces new evaluation information not in the VER
- Selected option scored lower on cost but rationale does not address the cost disadvantage
- Rationale is "industry best practice" without specific reasoning from VER evidence

### Tradeoffs Accepted
**Rules**
- At least one explicit tradeoff must be stated
- Each tradeoff must identify what was given up or accepted as a consequence of the sourcing decision
- Tradeoffs must be specific, not generic ("some limitations" is not a tradeoff; "Buy option does not support bulk import — manual workaround required for initial data migration, estimated 2-week effort" is)
- Tradeoffs must reference VER findings where the selected option had weaknesses or the rejected options had strengths
- If the decision is Buy or Adopt, vendor/project lock-in tradeoffs must be explicitly addressed

**Failure Examples**
- Tradeoffs section absent
- Only benefits listed (every sourcing decision has tradeoffs)
- Tradeoffs are vague ("some additional complexity")
- Buy/Adopt decision without lock-in tradeoff addressed
- Tradeoffs do not reference VER data

### Risk Mitigations
**Rules**
- Each risk identified in the VER for the selected option must have a mitigation plan
- Each mitigation must state: the risk being mitigated (referencing VER risk assessment), the mitigation approach, the owner responsible for the mitigation, and the timeline or trigger
- If the decision is Buy: vendor viability risk mitigation must be present (what happens if the vendor is acquired, pivots, or fails)
- If the decision is Adopt: project sustainability risk mitigation must be present (what happens if the OSS project becomes unmaintained)
- If the decision is Build: key development risks must be mitigated (timeline, skill gaps, complexity)
- Residual risks (risks that remain after mitigation) must be documented

**Failure Examples**
- VER risks for selected option not addressed
- Mitigations without owners
- Buy decision without vendor viability mitigation
- Adopt decision without sustainability mitigation
- Build decision without development risk mitigation
- Residual risks not documented

### Downstream Routing
**Rules**
- The routing must specify the EEK entry path based on the sourcing decision
- The routing table must cover all three possible decision types:
  - **Build → EEK Path A (full scope)**: DPRD + frozen SDR provided to EEK; EEK scope covers full custom development as defined by the DPRD; SDR referenced in the KER as sourcing justification
  - **Buy → EEK Path A (reduced scope: integration + customization)**: DPRD + frozen SDR provided to EEK; EEK scope is reduced to integration with the purchased product, customization, and configuration; the KER must document scope reduction rationale referencing the SDR; DPRD requirements satisfied by the purchased product are marked as "vendor-provided" in the PRD acceptance check
  - **Adopt → EEK Path A (reduced scope: integration + configuration)**: DPRD + frozen SDR provided to EEK; EEK scope is reduced to integration with the adopted project, configuration, and any extension development; the KER must document scope reduction rationale referencing the SDR; DPRD requirements satisfied by the adopted project are marked as "project-provided" in the PRD acceptance check
- The routing must state which DPRD requirements are expected to be satisfied by the vendor/project (for Buy/Adopt) versus which require EEK development work
- The routing must identify any additional EEK inputs needed (vendor documentation, API specifications, OSS project documentation)

**Failure Examples**
- Routing section absent
- Routing does not specify EEK entry path
- Buy/Adopt routing does not define scope reduction
- Requirements not partitioned between vendor/project-provided and EEK development
- Additional EEK inputs not identified

### Stakeholder Sign-off
**Rules**
- At least one stakeholder must sign off on the decision (the decision authority from Document Control is automatically a signatory)
- Each signatory must have: name, role, date of sign-off
- If the initiative has budget implications, a budget-authorized signatory must be present
- If the decision is Buy, procurement or vendor management sign-off must be present (or explicitly noted as not applicable with justification)
- If stakeholders were consulted but did not sign off, their objections or concerns must be documented

**Failure Examples**
- No sign-off present
- Sign-off without dates
- Buy decision without procurement acknowledgment and no justification for its absence
- Dissenting stakeholders not documented

---

## Format Requirements

- SDR ID must follow the standard format
- Decision statement must be a single paragraph or sentence, not a bulleted list
- Routing table must clearly distinguish the three decision types
- Sign-off must include dates
- VER references must cite specific sections or data points, not just the VER ID

---

## Completeness Rules

- All seven substantive sections must be present and non-empty
- Decision clearly stated as Build, Buy {vendor/product}, or Adopt {project}
- Rationale references VER evaluation data
- At least one explicit tradeoff stated
- All VER risks for selected option mitigated
- Downstream routing defined for the selected decision type
- At least one stakeholder sign-off with date

---

## Relationship Rules

- The SDR is the terminal artifact of the Solution Sourcing Kit and the downstream boundary contract for EEK
- A frozen SDR accompanies the frozen DPRD when the initiative enters EEK
- The SDR does not replace the KER — the KER is still required at EEK entry and must reference the frozen SDR
- If the SDR decision is Build, EEK proceeds with full DPRD scope
- If the SDR decision is Buy or Adopt, EEK proceeds with reduced scope (integration + customization/configuration); the scope reduction is documented in the KER and enforced through the PRD acceptance check
- SSK is optional — if an initiative bypasses SSK, the KER must document the justification for why sourcing evaluation was not needed (e.g., "Build is the only viable approach because [specific reason]")

---

## Hard Gates

1. **decision_stated** — A clear, specific, non-conditional sourcing decision is stated as Build, Buy {named vendor/product}, or Adopt {named project}; the statement is unambiguous
2. **rationale_references_ver** — Decision rationale references specific VER evaluation data (criterion scores, cost model, risk assessment, capability fit, integration complexity); every criterion where the selected option did not score highest is addressed; no evaluation data introduced that is not present in the VER
3. **downstream_routing_defined** — EEK entry path is specified for the selected decision type; scope reduction defined for Buy/Adopt; requirements partitioned between vendor/project-provided and EEK development; additional EEK inputs identified
4. **risk_mitigations** — Every VER risk for the selected option has a mitigation plan with approach, owner, and timeline; decision-type-specific risks addressed (vendor viability for Buy, project sustainability for Adopt, development risks for Build); residual risks documented
5. **stakeholder_sign_off** — At least one stakeholder has signed off with name, role, and date; budget-authorized signatory present if budget implications exist; procurement acknowledgment present for Buy decisions (or justified absence); dissenting views documented
