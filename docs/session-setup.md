# Solution Sourcing Kit — Session Setup

This document provides per-artifact session setup checklists for AI-assisted work in the Solution Sourcing Kit.

---

## Pre-Flight Checks (Before Any Session)

Before starting any AI session for SSK work:

- [ ] Confirm the DPRD is frozen (check Document Control section for status)
- [ ] Confirm the Engagement Record exists for this initiative
- [ ] Confirm the previous artifact in the flow is frozen (SOER before VER, VER before SDR)
- [ ] Gather all required input documents in full (do not summarize)

---

## SOER — Human-Authored (No AI Generation Session)

The SOER is human-authored. Do not use AI to generate it. Complete the template yourself using information from the frozen DPRD, market research, and organizational context.

**Validation session setup:**
```
Documents to provide:
1. The completed SOER (full document)
2. docs/specs/soer-spec.md

Prompt:
"Validate this Sourcing Options Evaluation Record against the SOER spec.
Use only the spec as the source of truth for pass/fail criteria.
Do not suggest improvements. Judge only what is explicitly present.
Output JSON using the format defined in the validator."
```

---

## VER — Generation Session

**Session setup:**
```
Documents to provide:
1. Frozen SOER (full document)
2. Frozen DPRD (full document, for requirements baseline)
3. Vendor/solution documentation, pricing, and technical specs
4. docs/principles/sourcing-principles.md
5. docs/specs/ver-spec.md
6. docs/artifacts/ver-template.md

Prompt:
"Generate a Vendor/Solution Evaluation Record using the provided inputs.
Follow the prompt in docs/prompts/ver-prompt.md.
Use the template exactly. Satisfy all hard gates in the spec.
Evaluate all shortlisted candidates from the SOER.
Apply scoring criteria consistently across all candidates.
Do not invent evaluation data — mark any missing information
with [MISSING: reason]. Output pure Markdown."
```

**After generation:** Review the VER. Confirm:
- All shortlisted candidates from the SOER are evaluated
- Scoring criteria are applied consistently
- Total cost of ownership is assessed (not just acquisition cost)
- Integration complexity is assessed for Buy and Adopt options
- Vendor lock-in risk is assessed for Buy options
- Maintenance burden is assessed for Adopt options

**Validation session setup:**
```
Documents to provide:
1. The generated VER (full document)
2. docs/specs/ver-spec.md

Prompt:
"Validate this Vendor/Solution Evaluation Record against the VER spec.
Use only the spec as the source of truth for pass/fail criteria.
Do not suggest improvements. Judge only what is explicitly present.
Output JSON using the format defined in docs/validators/ver-validator.md."
```

---

## SDR — Generation Session

**Session setup:**
```
Documents to provide:
1. Frozen VER (full document)
2. Frozen SOER (full document)
3. Frozen DPRD (full document)
4. Human-provided sourcing decision (Build, Buy, or Adopt — with named selection)
5. Human-provided decision rationale
6. docs/specs/sdr-spec.md
7. docs/artifacts/sdr-template.md

Prompt:
"Generate a Sourcing Decision Record using the provided inputs.
Follow the prompt in docs/prompts/sdr-prompt.md.
Use the template exactly. Satisfy all hard gates in the spec.
The sourcing decision is: [BUILD/BUY/ADOPT — state the human decision].
The rationale is: [state the human rationale].
Ground the rationale in VER evidence.
Document downstream implications for EEK.
Output pure Markdown."
```

**After generation:** Review the SDR. Confirm:
- The decision accurately reflects the human-provided decision
- The rationale references specific VER evidence (not generic statements)
- Downstream implications are documented with specific EEK scope guidance
- Rejected alternatives are acknowledged with brief rationale
- Integration risks are documented for Buy/Adopt decisions

**Validation session setup:**
```
Documents to provide:
1. The generated SDR (full document)
2. docs/specs/sdr-spec.md

Prompt:
"Validate this Sourcing Decision Record against the SDR spec.
Use only the spec as the source of truth for pass/fail criteria.
Do not suggest improvements. Judge only what is explicitly present.
Output JSON using the format defined in docs/validators/sdr-validator.md."
```

---

## Troubleshooting

**Validator returns FAIL on multiple gates**
Check that the generation session included all required inputs. Missing inputs are the most common cause of multi-gate failures.

**VER scoring inconsistent across candidates**
Ensure vendor/solution documentation was provided in full for all candidates. Partial documentation for some candidates produces uneven evaluation.

**SDR rationale not grounded in evidence**
Ensure the frozen VER was provided in full to the SDR generation session. The SDR prompt requires specific VER references in the rationale section.

**Integration complexity underestimated for Buy/Adopt**
Provide detailed technical documentation for the selected vendor/solution. The VER and SDR can only assess integration complexity based on the information provided.
