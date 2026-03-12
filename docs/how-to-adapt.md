# How to Adapt This Kit

This kit provides the structure, rules, and prompts for sourcing decision governance. Adapting it to your organization means filling in the content that is specific to your context — without modifying the governance structure.

---

## What to Adapt

### Organizational Principles

**Directory:** `docs/principles/`

This directory contains `sourcing-principles.md` with baseline sourcing principles. Review and extend it with your organization's actual sourcing policies. Additional files you might create:

- **vendor-management-policy.md** — Approved vendor lists, vendor assessment criteria, contract requirements, compliance prerequisites.
- **open-source-policy.md** — OSS license compatibility requirements, contribution policies, maintenance commitment thresholds, security review requirements.
- **procurement-process.md** — Budget approval workflows, procurement timelines, legal review requirements.

Replace the defaults with your organization's actual policies. Keep the structure (numbered sections, clear policy statements) but change the content to match your standards.

### Evaluation Criteria

The VER template includes standard evaluation dimensions: cost, risk, functional fit, integration complexity, and long-term viability. If your organization uses additional dimensions (e.g., regulatory compliance score, data sovereignty assessment, accessibility maturity), add them to the VER template and update the VER spec to include them in the evaluation gates.

### Scoring Weights

The VER spec requires consistent scoring across candidates but does not prescribe specific weights. If your organization has standard weighting (e.g., security risk weighted 2x, cost weighted 1.5x), document those weights in your principles files and reference them during VER generation.

### Fast-Path Criteria

The playbook defines when SSK can be skipped (fast-path). If your organization requires sourcing evaluation for all initiatives above a certain budget threshold, document that policy in your principles files. The fast-path criteria should match your organization's procurement and governance requirements.

### Decision Authority

The SDR records a human decision. If your organization requires specific approval authorities for sourcing decisions (e.g., CTO approval for Buy decisions above a threshold, architecture review board approval for Adopt decisions), document those authority requirements in your principles files.

---

## What Not to Adapt

### Specs

The specs define what makes an artifact valid. Do not soften hard gates to make artifacts easier to produce. If a hard gate is failing consistently, that usually means the artifact is incomplete — not that the gate is wrong.

If you genuinely need to add a hard gate (your organization requires something the spec does not check), add it. Do not remove existing hard gates.

### Validator Logic

Validators evaluate against specs. If a validator is producing unexpected results, check whether the spec accurately captures your requirements — and adjust the spec if needed, not the validator.

### Governance Model

`docs/governance-model.md` is a synchronized copy of the canonical governance model. Do not edit it. If you believe the governance model should change, update `aieos-governance-foundation/governance-model.md` and sync all kit copies.

---

## Adding Evaluation Dimensions

If your organization needs additional evaluation dimensions beyond the defaults, follow this process:

1. Add the dimension to the VER spec as a required evaluation field
2. Add the dimension to the VER template as a section
3. Update the VER prompt to include the dimension in generation instructions
4. Update the VER validator to check the dimension is present and populated

Register the change in the VER spec's version history.

---

## Tool Bindings

This kit is tool-agnostic. Templates use generic placeholders for procurement systems, vendor management platforms, and approval workflows.

When adopting this kit, create a bindings document:

```
docs/bindings/
  procurement-system-mapping.md    # Maps approval workflows to your procurement system
  vendor-platform-mapping.md       # Maps vendor data to your vendor management platform
  contract-system-mapping.md       # Maps contract references to your legal/contract system
```

Bindings are not governed artifacts — they have no spec, validator, or prompt. Update them when your tooling changes without touching the governed files.

---

## First-Time Setup Checklist

- [ ] Read `docs/playbook.md` fully before beginning
- [ ] Obtain a frozen DPRD from the Product Intelligence Kit
- [ ] Review and customize `docs/principles/sourcing-principles.md` for your organization
- [ ] Conduct market research on commercial and open-source alternatives
- [ ] Complete and freeze the SOER
- [ ] Generate and freeze the VER
- [ ] Make the sourcing decision
- [ ] Generate and freeze the SDR
- [ ] Hand off frozen DPRD + frozen SDR to the Engineering Execution Kit
