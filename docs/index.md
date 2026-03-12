# Solution Sourcing Kit — Documentation Index

This kit governs the Build/Buy/Adopt sourcing decision for an initiative. It is Layer 3 of the AIEOS system.

---

## Start Here

| Document | Purpose |
|----------|---------|
| `playbook.md` | End-to-end process definition — read this first |
| `how-to-use-with-ai.md` | AI session setup and tool guidance |
| `session-setup.md` | Per-artifact session setup checklists |
| `how-to-adapt.md` | Organizational adoption guidance |
| `governance-model.md` | AIEOS structural rules (reference) |

---

## Artifact Governing Files

### Step 1 — Sourcing Options Evaluation Record (SOER)

| File | Location | Purpose |
|------|----------|---------|
| Spec | `specs/soer-spec.md` | Content rules and hard gates |
| Template | `artifacts/soer-template.md` | Entry record structure |
| Prompt | *(human-authored — no generation prompt)* | — |
| Validator | `validators/soer-validator.md` | Pass/fail evaluation |

### Step 2 — Vendor/Solution Evaluation Record (VER)

| File | Location | Purpose |
|------|----------|---------|
| Spec | `specs/ver-spec.md` | Content rules and hard gates |
| Template | `artifacts/ver-template.md` | VER structure |
| Prompt | `prompts/ver-prompt.md` | Generation instructions |
| Validator | `validators/ver-validator.md` | Pass/fail evaluation |

### Step 3 — Sourcing Decision Record (SDR)

| File | Location | Purpose |
|------|----------|---------|
| Spec | `specs/sdr-spec.md` | Content rules and hard gates |
| Template | `artifacts/sdr-template.md` | SDR structure |
| Prompt | `prompts/sdr-prompt.md` | Generation instructions |
| Validator | `validators/sdr-validator.md` | Pass/fail evaluation |

---

## Principles

| File | Purpose |
|------|---------|
| `principles/sourcing-principles.md` | Organizational sourcing policy — evaluate before committing, TCO over acquisition cost, integration complexity as first-class risk |

---

## Examples

`examples/` — Worked examples (initially empty; to be populated with a complete sourcing evaluation flow)

---

## Guides

| Document | Purpose |
|----------|---------|
| `entry-from-pik.md` | Boundary briefing when arriving from the Product Intelligence Kit |
| `session-setup.md` | Per-artifact session setup checklists and pre-flight checks |

---

## Tests

Structural tests are run via `aieos-governance-foundation/tests/check-structure.sh`.
