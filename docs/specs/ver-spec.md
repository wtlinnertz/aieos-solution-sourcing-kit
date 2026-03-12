# Vendor/Solution Evaluation Record — Specification

Version: v1.0

The Vendor/Solution Evaluation Record (VER) is the detailed evaluation artifact of the Solution Sourcing Kit. It assesses each shortlisted sourcing option from the SOER against the defined evaluation criteria, providing structured evidence-based analysis that the SDR uses to make the sourcing decision.

The VER is an AI-generated artifact. It is validated against this spec before the SDR can be authored.

---

## What This Artifact Is Not

- **Not a decision document.** The VER evaluates options against criteria — it does not select an approach or make a recommendation. The decision belongs in the SDR.
- **Not a procurement contract.** The VER documents evaluation findings; commercial terms, SLAs, and contract negotiations are outside its scope.
- **Not a technical design.** The VER assesses integration complexity and capability fit at a sourcing level; detailed technical design belongs in EEK artifacts (SAD, TDD).
- **Not a market survey.** The VER evaluates the specific options identified in the SOER; it does not survey the broader market or identify new candidates.

---

## Purpose

The VER serves three roles:

1. **Structured evaluation** — Provides a consistent, criteria-based assessment of each sourcing option so that options can be compared on equal footing
2. **Evidence record** — Documents the evidence behind each assessment, ensuring the sourcing decision is grounded in verifiable data rather than opinion or assumption
3. **Decision input** — Serves as the primary input to the SDR, providing the evaluation data the decision maker needs

---

## Upstream Dependencies

- Frozen Sourcing Options Evaluation Record (SOER) — provides the options to evaluate and the criteria to evaluate against
- Frozen Discovery PRD (DPRD) — provides the functional and non-functional requirements for capability fit assessment
- Vendor documentation, product specifications, OSS project documentation, or equivalent evidence sources for each option

---

## Required Sections

1. Document Control
2. Evaluation Scope
3. Option Evaluations (one subsection per option)
4. Comparative Summary
5. Evaluation Limitations
6. Completeness Checklist

---

## Content Rules

### Document Control
**Rules**
- VER ID must be present (format: VER-{PROJECT}-{NNN})
- Date must be present
- SOER reference must be present (the frozen SOER ID this VER evaluates against)
- DPRD reference must be present
- Spec Version must be present
- Status must be one of: Draft | Validated | Frozen

**Failure Examples**
- VER ID absent
- SOER reference absent
- DPRD reference absent

### Evaluation Scope
**Rules**
- The options being evaluated must be listed (must match the SOER options, minus any formally withdrawn)
- The evaluation criteria must be listed (must match the SOER criteria)
- Any withdrawn options must be listed with the justification for withdrawal and a reference to the SOER amendment
- The evidence sources used for each option must be stated (vendor documentation, product trials, OSS repository analysis, reference customers, analyst reports, etc.)
- The evaluation date range must be stated

**Failure Examples**
- Options list does not match SOER
- Criteria list does not match SOER
- Evidence sources not stated
- Options withdrawn without justification

### Option Evaluations
**Rules**
- Each sourcing option from the SOER must have its own evaluation subsection
- At minimum, the Build option and at least one alternative must be evaluated
- Each option evaluation must contain the following structured assessments:
  - **Capability Fit**: How well the option addresses the DPRD functional requirements; each key functional requirement from the SOER upstream reference must be assessed as: fully met, partially met (with gap description), or not met
  - **Cost Model**: Acquisition cost (or development cost for Build), ongoing operational cost, and total cost of ownership over a stated time horizon (minimum 1 year, maximum 5 years); currency and basis of estimate must be stated
  - **Risk Assessment**: Risks specific to this option including technology risk, vendor/project viability risk, dependency risk, and compliance risk; each risk must have likelihood and impact
  - **Integration Complexity**: What integration work is required to connect this option with existing systems; APIs, data migration, authentication, and workflow integration must be addressed; estimated effort must be stated
  - **Maintenance Model**: Who maintains the solution (internal team, vendor, OSS community); what the ongoing maintenance burden is; what the support model is (SLA, community, internal); upgrade and patching cadence
- Each assessment must be evidence-based — claims must reference specific evidence (documentation page, pricing sheet, repository metrics, reference customer feedback, trial results); assertions without evidence sources are not valid
- Each option must be scored against every SOER evaluation criterion using a consistent rating scale (1-5 or equivalent); the scale must be defined and applied uniformly across all options

**Failure Examples**
- SOER option missing from evaluation without formal withdrawal
- Capability fit assessment does not address DPRD requirements
- Cost model missing time horizon or basis of estimate
- Risk assessment without likelihood and impact
- Integration complexity described as "minimal" without evidence or effort estimate
- Maintenance model absent
- Claims made without evidence references
- Rating scale inconsistent across options
- Build option not evaluated

### Comparative Summary
**Rules**
- A side-by-side comparison table must be present showing all options scored against all criteria
- The comparison must use the ratings from the individual option evaluations — no new ratings introduced in the summary
- Strengths and weaknesses of each option must be summarized (2-3 bullet points each)
- The comparative summary must not include a recommendation, ranking by preference, or decision language — it presents the data; the SDR decides

**Failure Examples**
- Comparison table absent
- Comparison introduces ratings not present in individual evaluations
- Summary includes a recommendation ("Option B is the best choice")
- Options ranked by preference
- Strengths or weaknesses absent

### Evaluation Limitations
**Rules**
- Any gaps in the evaluation must be documented: information that was unavailable, assumptions that were made, areas where evidence was insufficient
- Each limitation must identify which option(s) and which criterion/criteria it affects
- The impact of each limitation on the reliability of the evaluation must be stated
- If no limitations exist, this must be explicitly stated with justification (this is rare and should be scrutinized)

**Failure Examples**
- Limitations section absent
- Limitations listed without identifying affected options or criteria
- Impact of limitations not stated
- "No limitations" without justification

---

## Format Requirements

- VER ID must follow the standard format
- Each option evaluation must use the same structure (capability fit, cost model, risk assessment, integration complexity, maintenance model)
- Rating scale must be defined once and applied consistently
- Comparison table must include all options and all criteria
- Evidence references must be specific enough to be verifiable

---

## Completeness Rules

- All five substantive sections must be present and non-empty
- Every SOER option evaluated (or formally withdrawn with justification)
- Every SOER criterion scored for every option
- All five structured assessment areas present for each option (capability fit, cost model, risk assessment, integration complexity, maintenance model)
- Evidence cited for all claims
- Comparative summary present without recommendation

---

## Relationship Rules

- The VER gates SDR authoring — no SDR may be authored until the VER is frozen and validated
- The VER does not replace the SDR — the SDR follows after the VER is frozen
- The VER evaluates only options identified in the SOER; new options require SOER amendment and VER revision
- The VER applies only criteria defined in the SOER; new criteria require SOER amendment
- The VER evaluation data is the evidence base the SDR must reference — the SDR must not introduce evaluation data not present in the VER

---

## Hard Gates

1. **all_options_evaluated** — Every sourcing option from the SOER has a complete evaluation subsection (or is formally withdrawn with justification and SOER amendment reference); at minimum Build + one alternative evaluated; all five structured assessments present for each option
2. **criteria_coverage** — Every SOER evaluation criterion is scored for every option using a consistently defined and uniformly applied rating scale; comparative summary table includes all options and all criteria; no new ratings introduced in the summary
3. **evidence_based** — Every claim in every option evaluation references specific evidence (documentation, pricing data, repository metrics, trial results, reference feedback); no assertions without evidence sources; evidence references are specific enough to be verifiable
4. **integration_assessment** — Each option's integration complexity is assessed with specific integration points identified (APIs, data migration, authentication, workflows); estimated effort is stated; integration complexity is grounded in evidence, not assertion
5. **risk_assessment** — Each option has a risk assessment covering technology risk, vendor/project viability, dependency risk, and compliance risk; each risk has likelihood and impact; risks are specific to the option, not generic
6. **no_recommendation** — No recommendation, preferred option, ranking by preference, or decision language is present anywhere in the VER; the VER evaluates and presents data; the SDR decides
