# CLAUDE.md — Solution Sourcing Kit

## What This Repository Is

This is the **Solution Sourcing Kit** — an AIEOS kit that governs the Build/Buy/Adopt decision for an initiative. It is Layer 3 of the AIEOS system. It receives a frozen Discovery PRD (DPRD) from the Product Intelligence Kit and produces a Sourcing Decision Record that routes the initiative to the Engineering Execution Kit with clear sourcing intent and downstream implications.

## Repository Structure

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
```

## Artifact Types

This kit produces three governed artifact types:

1. **Sourcing Options Evaluation Record (SOER)** — Entry gate artifact (human-authored). Identifies candidate sourcing options (Build, Buy candidates, Adopt candidates) mapped against DPRD requirements. Validates that viable alternatives have been considered before committing resources to detailed evaluation.
2. **Vendor/Solution Evaluation Record (VER)** — Structured comparison of shortlisted candidates on cost, risk, functional fit, integration complexity, and long-term viability. Generated from SOER inputs.
3. **Sourcing Decision Record (SDR)** — Terminal artifact declaring the sourcing decision: Build, Buy, or Adopt. The human provides the decision; AI generates the formal record documenting rationale, implications, and downstream routing.

Each artifact type has exactly four governing files: spec, template, prompt, validator.

## Key Rules

- **Specs are the source of truth** — prompts and validators reference specs, never inline rules
- **Validators judge, they do not help** — no suggestions, no redesign
- **Freeze before promote** — DPRD must be frozen before SOER; SOER must be frozen before VER generation; VER must be frozen before SDR generation
- **Separate generation and validation** — different AI sessions to prevent self-validation bias
- **No scope expansion** — downstream artifacts must not expand scope beyond the DPRD
- **No inferred information** — mark missing information explicitly, do not fill gaps
- **SSK is optional** — if Build is obviously correct (no market alternatives, unique domain, competitive advantage), skip SSK and document the justification in the EEK Kit Entry Record (KER)
- **Governance model sync** — `docs/governance-model.md` is a synchronized copy of `aieos-governance-foundation/governance-model.md` (canonical authority). Do not edit kit copy directly; update `aieos-governance-foundation` first, then sync all kit copies to match exactly. See governance-model.md §15 for versioning and change protocol.
- **Engagement Record** — SSK maintains the Layer 3 section of the project's ER. Add artifact IDs as they freeze. See `docs/playbook.md §Maintaining the Engagement Record` and `aieos-governance-foundation/docs/engagement-record-spec.md`.

## Artifact Flow

```
Step 0: Pre-Flight — Confirm DPRD is frozen, ER exists
Step 1: Sourcing Options Evaluation Record (SOER) — human-authored
        → validate → freeze
Step 2: Vendor/Solution Evaluation Record (VER) — generated from SOER
        → validate → freeze
Step 3: Sourcing Decision Record (SDR) — generated (human provides decision)
        → validate → freeze → handoff to Layer 4 (EEK)
```

## Boundary Contracts

- **Upstream (Layer 2):** Receives a frozen DPRD from the Product Intelligence Kit. The DPRD defines what the organization needs; SSK determines how to source it. See `docs/entry-from-pik.md` for the boundary briefing.
- **Downstream (Layer 4):** Produces a frozen SDR that the Engineering Execution Kit receives alongside the frozen DPRD. The SDR §Sourcing Decision section is the downstream boundary contract. It routes the initiative:
  - **Build** — Full EEK flow (greenfield or brownfield engineering)
  - **Buy** — Integration-scoped EEK flow (vendor integration, configuration, adapter development)
  - **Adopt** — Integration-scoped EEK flow (OSS integration, customization, wrapper development)

## File Naming

| Type | Pattern |
|------|---------|
| Spec | `{type}-spec.md` |
| Template | `{type}-template.md` |
| Prompt | `{type}-prompt.md` |
| Validator | `{type}-validator.md` |

## Commit Message Style

Follow conventional commits: `docs: <description>`

## When Working on This Kit

- Read the playbook (`docs/playbook.md`) for the full process definition
- Read the governance model (`docs/governance-model.md`) for structural rules
- Check `docs/how-to-use-with-ai.md` for session setup instructions
- Use `docs/session-setup.md` for per-artifact setup checklists and pre-flight gate checks
- Reference `examples/` for worked examples

## Building or Auditing AIEOS Kits

- `aieos-governance-foundation/docs/kit-structure-standard.md` — compliance checklist for building and auditing kits
- `aieos-governance-foundation/docs/philosophy.md` — design rationale for governance model decisions
- `aieos-governance-foundation/docs/layer-model.md` — layer model and kit registry
