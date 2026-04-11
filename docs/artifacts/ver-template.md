# Vendor/Solution Evaluation Record

---

## 1. Document Control

| Field | Value |
|-------|-------|
| Artifact ID | VER-{INITIATIVE}-{NNN} |
| Initiative | {name} |
| Date | {YYYY-MM-DD} |
| Author | {name/role} |
| Status | Draft / Validated / Freeze Pending / Frozen |
| SOER Reference | {SOER-{INITIATIVE}-{NNN}} |
| Governance Model Version | {from governance-model.md §15} |
| Prompt Version | {from prompt file version header, or N/A for human-authored} |
| Spec Version | {from spec file Version header} |
| Principles Version | {from principles file(s) version, or N/A} |

---

## 2. Evaluation Scope

| Field | Value |
|-------|-------|
| SOER Reference | {SOER-{INITIATIVE}-{NNN}} |
| Shortlisted Options | {list of Option IDs from SOER §6} |

### Criteria Weights

| Criterion | Weight |
|-----------|--------|
| {criterion from SOER §5} | {weight} |

---

## 3. Option Evaluations

{Repeat this section for each shortlisted option.}

### 3.N {Option ID}: {Option Name}

#### 3.N.1 Option Overview

| Field | Value |
|-------|-------|
| Option ID | {OPT-NNN} |
| Name | {name} |
| Type | Build / Buy / Adopt |
| Vendor / Project | {vendor name or open-source project} |

#### 3.N.2 Capability Fit Assessment

{How well does this option meet the DPRD requirements? Reference specific DPRD capabilities.}

#### 3.N.3 Cost Model

| Cost Category | Estimate | Basis |
|---------------|----------|-------|
| Acquisition | {amount or range} | {how estimated} |
| Implementation | {amount or range} | {how estimated} |
| Ongoing (annual) | {amount or range} | {how estimated} |
| **Total Cost of Ownership ({N} years)** | **{amount or range}** | — |

#### 3.N.4 Time to Value

| Milestone | Estimated Timeline | Dependencies |
|-----------|-------------------|--------------|
| {milestone} | {duration or date} | {what it depends on} |

#### 3.N.5 Integration Assessment

{What integration work is needed? What systems, APIs, or workflows are affected?}

| Integration Point | Complexity | Notes |
|-------------------|-----------|-------|
| {system or interface} | Low / Medium / High | {details} |

#### 3.N.6 Risk Assessment

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| {risk description} | Low / Medium / High | Low / Medium / High | {mitigation approach} |

#### 3.N.7 Maintenance Model

| Field | Value |
|-------|-------|
| Maintained By | {vendor / internal team / community} |
| Update Cadence | {frequency} |
| Support Model | {SLA, community, contracted, internal} |
| End-of-Life Risk | {assessment} |

#### 3.N.8 Score

| Criterion | Weight | Rating | Weighted Score |
|-----------|--------|--------|---------------|
| {criterion} | {weight} | {1-5 or similar scale} | {calculated} |
| **Total** | — | — | **{total}** |

---

## 4. Comparative Summary

| Criterion | Weight | {Option 1 Name} | {Option 2 Name} | {Option N Name} |
|-----------|--------|-----------------|-----------------|-----------------|
| {criterion} | {weight} | {weighted score} | {weighted score} | {weighted score} |
| **Total** | — | **{total}** | **{total}** | **{total}** |

---

## 5. Key Findings

### Major Differentiators

- {finding}

### Deal-Breakers

- {finding, or "None identified."}

### Standout Strengths

- {finding}
