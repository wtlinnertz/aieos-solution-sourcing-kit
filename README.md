# aieos-solution-sourcing-kit

**Layer 3 of the AIEOS system — Solution Sourcing**

This kit governs the Build/Buy/Adopt decision for an initiative after the Product Intelligence Kit (Layer 2) defines what is needed via a frozen Discovery PRD. It produces a Sourcing Decision Record that routes the initiative to the Engineering Execution Kit with clear sourcing intent.

## What this kit does

The Product Intelligence Kit (Layer 2) defines what the organization needs. But "what we need" doesn't automatically mean "what we build." This kit fills that gap:

- **Sourcing options identification** — What options exist? Build from scratch, buy a commercial product, adopt an open-source solution, or some hybrid?
- **Vendor/solution evaluation** — How do candidates compare on cost, risk, fit, integration complexity, and long-term viability?
- **Sourcing decision** — Which option best serves the organization, and what are the implications for downstream engineering?

## Artifact types

This kit produces three governed artifact types:

| Step | Artifact | Purpose |
|------|----------|---------|
| 1 | Sourcing Options Evaluation Record (SOER) | Entry gate: identifies candidate sourcing options against DPRD requirements |
| 2 | Vendor/Solution Evaluation Record (VER) | Structured comparison of candidates on cost, risk, fit, and integration |
| 3 | Sourcing Decision Record (SDR) | Terminal artifact declaring the sourcing decision: Build, Buy, or Adopt |

Each governed artifact type has exactly four governing files: spec, template, prompt, validator.

## When to use this kit

Use SSK when any of the following are true:

- Commercial products or open-source solutions exist in the problem space
- The organization has not previously committed to a sourcing approach for this capability
- The initiative involves significant investment where sourcing alternatives should be evaluated
- Regulatory or compliance requirements mandate formal sourcing evaluation

## When to Skip This Kit

SSK is optional. Skip it when:

- Build is the only viable option (no market alternatives, unique domain, competitive advantage)
- The organization has an existing sourcing decision that covers this initiative
- The initiative is an enhancement to an existing system where the sourcing approach is already established

When skipping SSK, the justification must be documented in the EEK Kit Entry Record (KER). The fast-path bypasses SSK entirely and proceeds from frozen DPRD directly to EEK.

## Quick start

1. Read `docs/playbook.md` — the complete process definition
2. Read `docs/how-to-use-with-ai.md` — session setup and AI tool guidance
3. See `examples/` — worked examples (initially empty; to be populated)

## Repository structure

```
docs/
  principles/          # Organizational sourcing policy (input material)
  specs/               # Content rules and hard gates per artifact type
  artifacts/           # Templates
  prompts/             # AI generation prompts
  validators/          # Quality gate definitions
  playbook.md          # End-to-end process definition
  index.md             # Documentation entry point
  how-to-adapt.md      # Organizational adoption guidance
  how-to-use-with-ai.md # AI tool usage guide
  session-setup.md     # Per-artifact session setup checklists
  governance-model.md  # AIEOS structural rules (reference)
  entry-from-pik.md    # Boundary briefing from Product Intelligence Kit
examples/              # Worked examples
tests/                 # Structural integrity checks
CLAUDE.md              # AI operating instructions
```

## AIEOS layer

| Layer | Kit | Status |
|-------|-----|--------|
| 2. Product Intelligence | `aieos-product-intelligence-kit` | Built |
| **3. Solution Sourcing** | **`aieos-solution-sourcing-kit`** | **Built** |
| 4. Engineering Execution | `aieos-engineering-execution` | Built |
| 5. Release & Exposure | `aieos-release-exposure-kit` | Built |
| 6. Reliability & Resilience | `aieos-reliability-resilience-kit` | Built |
| 7. Insight & Evolution | `aieos-insight-evolution-kit` | Built |

See `aieos-governance-foundation/docs/layer-model.md` for the full layer model.
