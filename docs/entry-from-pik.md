# Entry from Product Intelligence Kit (PIK)

**You are here because:** PIK discovery is complete and the Discovery PRD (DPRD) is frozen. The initiative needs a sourcing decision before proceeding to engineering.

**What you must bring:**

| Artifact | Status Required | Where to Find It |
|----------|----------------|-----------------|
| Discovery PRD (DPRD-{PROJECT}-{NNN}) | Frozen | PIK delivery location or `docs/sdlc/` in the consuming project |

**First artifact to produce in this kit:** Sourcing Options Evaluation Record (SOER) — human-authored, no prompt

**Where to start:** `docs/playbook.md` → "Step 0 — Pre-Flight"

**What changes at this boundary:**

- You shift from problem definition to sourcing evaluation. The "what" is settled (DPRD); now you determine "how to source it."
- The discovery team and the sourcing evaluation team may be different people. The SOER is the sourcing evaluator's entry acknowledgment.
- The focus broadens from product requirements to market landscape: what exists commercially, what exists as open source, and whether custom development is the right approach.
- The DPRD is an input, not a starting point for redesign. SSK evaluates sourcing options against DPRD requirements — it does not change the requirements.

**Common mistakes at this transition:**

| Mistake | How to Avoid |
|---------|--------------|
| Skipping SSK because "we always build" | If Build is genuinely the only option (no market alternatives, unique domain, competitive advantage), document the justification in the EEK KER and use the fast-path. Do not skip SSK without explicit justification. |
| Treating the SOER as a vendor comparison | The SOER identifies options; the VER compares them. The SOER maps candidates to DPRD requirements at a high level. Detailed comparison is Step 2. |
| Starting VER before SOER is frozen | The VER depends on the SOER shortlist. Do not begin VER generation until the SOER is validated and frozen. |
| Expanding scope beyond the DPRD | SSK evaluates how to source what the DPRD defines. If the sourcing evaluation reveals that additional capabilities are needed, that is a signal to return to PIK — not to expand scope within SSK. |

**If you arrived here without a complete upstream artifact:**

Stop. Return to PIK, complete the discovery flow, freeze the DPRD, and then enter SSK. SSK cannot evaluate sourcing options without a frozen requirements baseline. Evaluating options against a draft DPRD produces unreliable results because the requirements may change.

**If you are considering skipping this kit:**

SSK is optional. If Build is obviously correct, you may skip SSK and proceed directly to EEK. The fast-path requires:
1. A justification documented in the EEK Kit Entry Record (KER)
2. The justification must explain why sourcing evaluation is unnecessary (e.g., no market alternatives exist, the capability is a competitive differentiator, organizational policy mandates custom development)

See `docs/playbook.md` → "Step 0 — Pre-Flight" for the fast-path protocol.

---

*For the full entry flow, see `docs/playbook.md`.*
