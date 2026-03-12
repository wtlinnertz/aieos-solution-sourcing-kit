# How to Use This Kit with AI

This guide explains how to set up AI sessions for each step in the Solution Sourcing Kit workflow. Follow the session setup instructions precisely — incorrect session setup is the most common cause of poor artifact quality.

---

## Core Discipline

**One artifact per session.** Do not generate multiple artifacts in the same session.

**Separate generation and validation.** Always validate in a new session. Never ask the AI that generated an artifact to validate it — this produces self-validation bias.

**Include full frozen documents.** Do not summarize upstream artifacts. Provide the complete document.

---

## SOER — Human-Authored (No AI Generation Session)

The SOER is human-authored. Do not use AI to generate it. The value of the SOER depends on the evaluator's market knowledge and organizational context — information that cannot be reliably generated.

AI can assist with research (identifying potential vendors, summarizing product capabilities from documentation), but the SOER itself is completed by the sourcing evaluator.

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

The VER structures and compares the candidates identified in the SOER. AI is well-suited to this task because it involves systematic comparison against consistent criteria.

**Session setup:**
```
Documents to provide:
1. Frozen SOER (full document)
2. Frozen DPRD (full document)
3. Vendor/solution documentation, pricing, and technical specs for each shortlisted candidate
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
- Scoring criteria are applied consistently (same dimensions, same scale)
- Total cost of ownership includes ongoing costs, not just acquisition
- Integration complexity is assessed with specific technical detail
- Vendor lock-in and exit costs are documented for Buy options
- Maintenance burden and community health are documented for Adopt options

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

The SDR records a human decision with AI-generated formal documentation. The human provides the decision and rationale; the AI structures it according to the template and grounds it in VER evidence.

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
- The decision matches what the human provided
- The rationale references specific VER scores and findings
- Rejected alternatives are listed with brief explanation
- Downstream implications specify the EEK scope (full vs integration-scoped)
- For Buy: vendor name, contract implications, and integration requirements are documented
- For Adopt: project name, license implications, and maintenance commitments are documented
- For Build: scope confirmation and resource implications are documented

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
Ensure vendor/solution documentation was provided in full for all candidates. Partial documentation for some candidates produces uneven evaluation quality.

**SDR rationale not grounded in evidence**
Ensure the frozen VER was provided in full to the SDR generation session. The SDR prompt requires specific VER references. If the rationale reads as generic, the VER was likely summarized or omitted.

**Integration complexity underestimated**
Provide detailed technical documentation for the selected vendor/solution. The AI can only assess integration complexity from the information provided. If technical docs are thin, supplement with architecture diagrams, API documentation, and known integration patterns.

**SOER has too few or too many options**
The SOER should identify genuinely viable options, not exhaustively list every product in the market. 2-5 candidates per category (Build/Buy/Adopt) is typical. If the SOER has only one option, consider whether SSK is necessary (fast-path may apply). If it has many options, the shortlisting step should narrow to 2-4 candidates for VER evaluation.
