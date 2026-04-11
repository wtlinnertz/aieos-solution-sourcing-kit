# Sourcing Options Evaluation Record — Specification

Version: v1.0

The Sourcing Options Evaluation Record (SOER) is the entry gate for the Solution Sourcing Kit. It must be completed before the Vendor/Solution Evaluation Record can be generated. It confirms the upstream DPRD is frozen, names the sourcing evaluation owner, identifies initial sourcing options, and defines the evaluation criteria against which options will be assessed.

This is a **boundary contract**, not a governed artifact. The record is human-authored. It is validated against this spec before VER generation begins.

---

## What This Artifact Is Not

- **Not a vendor evaluation.** The SOER identifies options and criteria — it does not evaluate, score, or compare them. Detailed evaluation belongs in the VER.
- **Not a sourcing decision.** The SOER defines the evaluation scope; it does not select an approach. The decision belongs in the SDR.
- **Not a substitute for the DPRD.** The SOER confirms the DPRD is frozen and captures key references; it does not summarize or replace the DPRD's definition of what to build.

---

## Purpose

The SOER serves two roles:

1. **Intake gate** — Confirms that the upstream DPRD is frozen, the sourcing evaluation owner has accepted accountability, and at least one alternative to custom build has been identified; prevents sourcing evaluation from beginning without a verified handoff and defined scope
2. **Scope record** — Captures the initial set of sourcing options and the evaluation criteria that will govern the VER, so the evaluation has an authoritative starting point

---

## Upstream Dependencies

- Frozen Discovery PRD (DPRD) from the Product Intelligence Kit — must be in Frozen status
- Organizational sourcing principles or policies (if applicable)

---

## Required Sections

1. Document Control
2. Upstream Reference
3. Sourcing Evaluation Owner
4. Sourcing Options
5. Evaluation Criteria
6. Constraints and Assumptions
7. Completeness Checklist
8. Freeze Declaration

---

## Content Rules

### Document Control
**Rules**
- SOER ID must be present (format: SOER-{PROJECT}-{NNN})
- Date must be present
- A brief initiative summary must be present (1-2 sentences identifying the initiative and the scope of the sourcing evaluation)
- Spec Version must be present

**Failure Examples**
- Missing SOER ID
- Initiative summary absent or "TBD"

### Upstream Reference
**Rules**
- The DPRD being referenced must be identified by ID
- The DPRD status must be confirmed as Frozen (not Draft or Validated)
- The key functional requirements from the DPRD that drive sourcing evaluation must be listed (minimum 3 requirements or "all requirements" with justification if the DPRD scope is small)
- Any non-functional requirements from the DPRD that constrain sourcing (performance, compliance, data residency, integration) must be listed

**Failure Examples**
- DPRD ID missing or "unknown"
- DPRD status listed as "Validated" rather than "Frozen"
- No functional requirements listed
- Non-functional requirements not addressed

### Sourcing Evaluation Owner
**Rules**
- A named individual (not a team or role title) must be identified as sourcing evaluation owner
- Contact information must be present (channel, email, or equivalent)
- The owner's scope must be stated (what initiative or sourcing decision they own)

**Failure Examples**
- "Procurement team" — not a named individual
- Contact information absent
- Scope absent or "all sourcing"

### Sourcing Options
**Rules**
- At minimum, two sourcing options must be listed: Build (custom development) and at least one Buy (commercial off-the-shelf product from a named vendor or product category) or Adopt (open-source project by name or project category)
- Each option must include: option name, sourcing type (Build / Buy / Adopt), a brief description (1-3 sentences describing the option), and an initial viability assessment (why this option is worth evaluating — not a full evaluation, just enough to justify inclusion)
- If only Build and one alternative are listed, a justification must be provided for why no additional alternatives were identified
- Options must not include a recommendation or ranking — the SOER identifies, the VER evaluates, the SDR decides
- If an option was considered but excluded from evaluation, it must be listed in a "Dismissed Options" subsection with the reason for exclusion

**Failure Examples**
- Only Build listed with no alternatives
- Options listed without sourcing type classification
- Options include a recommendation ("we recommend Option B")
- Description absent or a single word
- Viable alternatives exist in the market but none were identified

### Evaluation Criteria
**Rules**
- At minimum the following criteria categories must be addressed: cost (acquisition + ongoing), time-to-value, risk profile, functional fit, maintenance burden, and vendor/project lock-in
- Each criterion must have: a name, a definition (what it measures), and a weight or priority indication (critical / important / nice-to-have)
- At least two criteria must be marked as critical
- Criteria must be traceable to DPRD requirements or organizational constraints — each criterion must reference the requirement or constraint that motivates it
- Organization-specific criteria may be added beyond the minimum set

**Failure Examples**
- Fewer than the six minimum criteria categories addressed
- Criteria listed without definitions
- No criteria marked as critical
- Criteria not traceable to DPRD or organizational constraints
- Criteria are vague ("quality" without a definition of what quality means in this context)

### Constraints and Assumptions
**Rules**
- Budget constraints must be stated (even if "no fixed budget" — the constraint is the absence of a constraint)
- Timeline constraints must be stated (when must the solution be operational)
- Technical constraints must be stated (platform requirements, integration points, compliance mandates)
- Assumptions about the evaluation must be listed (e.g., "vendor will provide trial access," "OSS project has active maintainers")
- If no constraints exist for a category, this must be explicitly stated

**Failure Examples**
- Constraints section empty
- Budget not addressed
- Timeline not addressed
- Assumptions absent

---

## Format Requirements

- SOER ID must follow the standard format
- Sourcing evaluation owner must be a person's name, not a team name or role title
- Contact information must be usable — a specific channel, email, or equivalent
- Options must be structured consistently (same fields for each)
- Criteria must be structured consistently (same fields for each)

---

## Completeness Rules

- All six substantive sections must be present and non-empty
- DPRD must be in Frozen status
- Named sourcing evaluation owner with contact information
- At least two sourcing options listed (Build + at least one alternative)
- At least six evaluation criteria categories addressed with definitions and weights
- Constraints and assumptions documented

---

## Relationship Rules

- The SOER gates VER generation — no VER may be generated until the SOER is frozen and validated
- The SOER does not replace the VER — the VER follows after the entry gate passes
- The sourcing options identified in the SOER are the starting point for VER evaluation; the VER must evaluate all SOER options (unless an option is formally withdrawn with justification) but must not add new options without SOER amendment
- The evaluation criteria defined in the SOER are binding for the VER — the VER must score against these criteria

---

## Hard Gates

1. **dprd_frozen** — DPRD ID referenced; DPRD status confirmed as Frozen; key functional requirements listed; non-functional requirements that constrain sourcing addressed
2. **owner_identified** — Named individual (not team) as sourcing evaluation owner with contact information and scope stated
3. **options_enumerated** — At least two sourcing options listed (Build + at least one Buy or Adopt alternative); each option has name, sourcing type, description, and initial viability assessment; no recommendation or ranking present
4. **criteria_defined** — At least six evaluation criteria categories addressed (cost, time-to-value, risk, functional fit, maintenance burden, lock-in); each criterion has name, definition, and weight; at least two criteria marked critical; criteria traceable to DPRD or organizational constraints
5. **no_premature_decision** — No recommendation, ranking, preferred option, or decision language present anywhere in the document; the SOER identifies and scopes, it does not evaluate or decide
