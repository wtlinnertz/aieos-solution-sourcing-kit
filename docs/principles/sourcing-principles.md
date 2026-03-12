# Sourcing Principles

Version: v1.0

This document defines the organization's sourcing evaluation standards and philosophy. It is input material for artifact generation within the Solution Sourcing Kit — not a governed artifact. Adapt this file to reflect your organization's actual sourcing policies.

---

## 1. Evaluate Before Committing

- Every initiative with a non-trivial sourcing investment must consider Build, Buy, and Adopt options before committing resources.
- "We always build" is not a sourcing strategy. Default-to-Build without evaluation risks overinvestment in commodity capabilities that are better served by existing solutions.
- The evaluation depth should be proportional to the investment: small initiatives may need only a lightweight assessment; large initiatives require full SSK flow.
- When Build is genuinely the only viable option (no market alternatives, unique domain, competitive advantage), the fast-path is valid — but the justification must be documented.

## 2. Total Cost of Ownership Over Acquisition Cost

- Sourcing decisions must be based on total cost of ownership (TCO), not acquisition cost alone.
- TCO for Build includes: development cost, ongoing maintenance, infrastructure, staffing for long-term support, opportunity cost of engineering capacity.
- TCO for Buy includes: license fees (initial and recurring), integration development, vendor management overhead, contract renewal risk, data migration costs, exit costs.
- TCO for Adopt includes: integration development, internal maintenance burden, security patching responsibility, community health monitoring, contribution overhead, fork risk if the project diverges.
- A 3-5 year TCO horizon is the minimum for meaningful comparison. Point-in-time cost comparisons are unreliable.

## 3. Integration Complexity Is a First-Class Risk

- Integration complexity must be assessed as a primary evaluation dimension, not an afterthought.
- Buy and Adopt options that appear cheaper on TCO may become more expensive when integration costs are fully accounted for: adapters, data transformation, authentication bridging, monitoring integration, and operational runbook changes.
- Integration risk compounds: each external dependency adds surface area for failure, version incompatibility, and upgrade coordination.
- The evaluation must document specific integration points, not just assert that "integration is straightforward."

## 4. Vendor Lock-In Assessment Is Mandatory for Buy Options

- Every Buy option must include a vendor lock-in assessment: what happens if the vendor raises prices, discontinues the product, changes terms, or is acquired?
- Lock-in assessment must cover: data portability (can you export your data in a usable format?), API dependency (are you building against proprietary APIs?), contract terms (what are the exit conditions?), and alternative availability (what would migration to an alternative look like?).
- Lock-in is not inherently disqualifying — but unacknowledged lock-in is. The SDR must document accepted lock-in with explicit rationale.

## 5. OSS Maintenance Burden Assessment Is Mandatory for Adopt Options

- Every Adopt option must include a maintenance burden assessment: what ongoing effort is required to keep the OSS dependency healthy and secure?
- Maintenance assessment must cover: community health (is the project actively maintained? how many active contributors?), security patching cadence (how quickly are CVEs addressed?), upgrade compatibility (do major versions break APIs?), license compatibility (does the license permit your intended use?), and fork risk (if you customize, can you stay on the mainline?).
- An OSS project with a single maintainer, infrequent updates, or an incompatible license is a risk that must be documented and accepted explicitly.

## 6. Fast-Path Validity

- The fast-path (skipping SSK entirely) is valid when Build is the only viable option.
- Valid fast-path justifications include: no market alternatives exist for the capability, the capability is unique to the organization's domain, the capability is a competitive differentiator that must be proprietary, or organizational policy mandates custom development for this category.
- Invalid fast-path justifications include: "we prefer to build," "we have engineers available," "we don't have time to evaluate," or "we've never used vendor products."
- Fast-path justification must be documented in the EEK Kit Entry Record (KER). An undocumented fast-path is a policy violation.
