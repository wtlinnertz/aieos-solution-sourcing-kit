# Sourcing Decision Record

---

## 1. Document Control

| Field | Value |
|-------|-------|
| Artifact ID | SDR-{INITIATIVE}-{NNN} |
| Owner | {owner} |
| Initiative | {name} |
| Date | {YYYY-MM-DD} |
| Author | {name/role} |
| Status | DRAFT |
| VER Reference | {VER-{INITIATIVE}-{NNN}} |
| SOER Reference | {SOER-{INITIATIVE}-{NNN}} |
| Governance Model Version | {from governance-model.md §15} |
| Prompt Version | {from prompt file version header, or N/A for human-authored} |
| Spec Version | {from spec file Version header} |
| Principles Version | {from principles file(s) version, or N/A} |

---

## 2. Decision Summary

| Field | Value |
|-------|-------|
| Selected Approach | {Build / Buy / Adopt} |
| Selected Option | {Option ID and name from VER} |
| One-Sentence Rationale | {why this option was selected} |

---

## 3. Decision

| Field | Value |
|-------|-------|
| Decision Type | Build / Buy / Adopt |
| Selected Option | {Option ID from VER §3} |
| Option Name | {name} |
| Vendor / Project | {vendor name or open-source project, or "Internal" for Build} |

### Rationale

{Brief rationale for selecting this option over alternatives. Reference VER §4 comparative data and §5 key findings.}

---

## 4. Detailed Justification

{Detailed justification for the decision. Reference specific VER §4 comparative scores, §5 key findings, and SOER §5 evaluation criteria. Address why the selected option best satisfies the weighted criteria.}

### Advantages of Selected Option

- {advantage, with VER reference}

### Accepted Trade-offs

- {trade-off, with VER reference}

### Why Alternatives Were Not Selected

| Option ID | Name | Primary Reason for Rejection |
|-----------|------|------------------------------|
| {OPT-NNN} | {name} | {reason, referencing VER data} |

---

## 5. Risk Mitigations

{For each significant risk identified in VER §3.N.6 for the selected option, state how it will be addressed.}

| Risk (from VER) | Impact | Mitigation Plan | Owner |
|-----------------|--------|-----------------|-------|
| {risk description} | {impact} | {how it will be mitigated} | {responsible party} |

---

## 6. Downstream Routing

| Decision | Next Step | Scope Impact | EEK Entry Notes |
|----------|-----------|-------------|-----------------|
| Build | EEK Path A | Full scope | DPRD + SDR provided |
| Buy | EEK Path A | Reduced scope (integration + customization) | DPRD + SDR + vendor artifacts provided |
| Adopt | EEK Path A | Reduced scope (integration + configuration) | DPRD + SDR + project docs provided |

### Routing for This Decision

| Field | Value |
|-------|-------|
| Decision Type | {Build / Buy / Adopt} |
| EEK Entry Path | {Path A} |
| Scope Impact | {full / reduced — integration + customization / reduced — integration + configuration} |
| Artifacts to Provide to EEK | {list: DPRD, SDR, and any additional vendor artifacts or project docs} |

---

## 7. Stakeholder Sign-off

| Role | Name | Date | Decision |
|------|------|------|----------|
| {role} | {name} | {YYYY-MM-DD} | Approve / Reject / Abstain |
| {role} | {name} | {YYYY-MM-DD} | Approve / Reject / Abstain |
| {role} | {name} | {YYYY-MM-DD} | Approve / Reject / Abstain |
