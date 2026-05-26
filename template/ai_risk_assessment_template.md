# AI System Risk Assessment Template
**Aligned to NIST AI RMF 1.0 | EU AI Act | NYC Local Law 144**

---

**Prepared by:** ___________________________  
**Organization:** ___________________________  
**Assessment Date:** ___________________________  
**Review Date:** ___________________________  
**Version:** 1.0

---

## Section 1 — System Description

| Field | Details |
|-------|---------|
| System Name | |
| System Owner | |
| Business Unit | |
| Deployment Date | |
| System Version | |
| Primary Use Case | |
| Intended Users | |
| Geographic Scope | |

**System Description:**
Provide a plain-language description of what the AI system does, how it makes decisions, and what data it uses.

_______________________________________________

**Data Sources:**
List all data sources used for training, validation, and inference.

| Data Source | Type | Sensitivity | Retention Period |
|-------------|------|-------------|-----------------|
| | | | |
| | | | |

---

## Section 2 — Regulatory Classification

### EU AI Act Risk Classification
*(Check all that apply)*

- [ ] **Unacceptable Risk** — System is prohibited under Article 5
- [ ] **High Risk** — System falls under Annex III categories
- [ ] **Limited Risk** — Transparency obligations apply
- [ ] **Minimal Risk** — No specific obligations

**High Risk Category (if applicable):**
- [ ] Biometric identification
- [ ] Critical infrastructure
- [ ] Education and vocational training
- [ ] Employment and worker management
- [ ] Access to essential services
- [ ] Law enforcement
- [ ] Migration and border control
- [ ] Administration of justice

### NYC Local Law 144 Applicability
- [ ] System is used in employment decisions affecting NYC residents
- [ ] Bias audit required annually
- [ ] Public notice required prior to use
- [ ] Not applicable

### Additional Regulatory Considerations
- [ ] GDPR / CCPA — personal data processing
- [ ] Colorado AI Act — consequential decisions
- [ ] HIPAA — healthcare data
- [ ] FCRA — credit decisions
- [ ] Sector-specific regulations: ___________________________

---

## Section 3 — NIST AI RMF Assessment

### GOVERN — Organizational Context

| Control Area | Status | Evidence | Gap |
|-------------|--------|----------|-----|
| AI governance policy exists | ☐ Yes ☐ No ☐ Partial | | |
| Roles and responsibilities defined | ☐ Yes ☐ No ☐ Partial | | |
| Risk tolerance documented | ☐ Yes ☐ No ☐ Partial | | |
| Human oversight mechanisms in place | ☐ Yes ☐ No ☐ Partial | | |
| Incident response plan exists | ☐ Yes ☐ No ☐ Partial | | |
| Vendor AI governance requirements defined | ☐ Yes ☐ No ☐ Partial | | |

**GOVERN Notes:**
_______________________________________________

---

### MAP — Risk Identification

#### 3.1 Intended Use Risks

| Risk | Likelihood (1-5) | Impact (1-5) | Risk Score | Mitigation |
|------|-----------------|--------------|------------|------------|
| Misclassification causing harm | | | | |
| Scope creep beyond intended use | | | | |
| User over-reliance on outputs | | | | |
| Output used in prohibited context | | | | |

#### 3.2 Data Risks

| Risk | Likelihood (1-5) | Impact (1-5) | Risk Score | Mitigation |
|------|-----------------|--------------|------------|------------|
| Training data bias | | | | |
| Data poisoning | | | | |
| Privacy violation | | | | |
| Data drift / distribution shift | | | | |
| Unauthorized data use | | | | |

#### 3.3 Model Risks

| Risk | Likelihood (1-5) | Impact (1-5) | Risk Score | Mitigation |
|------|-----------------|--------------|------------|------------|
| Adversarial attack vulnerability | | | | |
| Model extraction / inversion | | | | |
| Membership inference | | | | |
| Prompt injection (LLMs) | | | | |
| Model drift over time | | | | |

**Risk Score Calculation:** Likelihood × Impact  
**Risk Rating:** 1-5 Low | 6-12 Medium | 13-19 High | 20-25 Critical

---

### MEASURE — Risk Assessment

#### 4.1 Fairness and Bias Assessment

**Protected Groups Assessed:**
- [ ] Race / Ethnicity
- [ ] Gender
- [ ] Age
- [ ] Disability
- [ ] National Origin
- [ ] Other: ___________________________

**Fairness Metrics:**

| Group | Sample Size | Accuracy | TPR | FPR | Precision | Disparity Flag |
|-------|-------------|----------|-----|-----|-----------|----------------|
| | | | | | | |
| | | | | | | |
| | | | | | | |

**Acceptable Disparity Threshold:** ___________________________

**Bias Finding:** ☐ Acceptable ☐ Requires Mitigation ☐ System Should Not Deploy

---

#### 4.2 Robustness Assessment

| Test | Method | Baseline Performance | Post-Test Performance | Pass / Fail |
|------|--------|---------------------|----------------------|-------------|
| Noise perturbation | Gaussian noise | | | |
| Adversarial attack | FGSM / PGD | | | |
| Distribution shift | Out-of-distribution data | | | |
| Input validation | Boundary testing | | | |

**Robustness Finding:** ☐ Acceptable ☐ Requires Mitigation ☐ System Should Not Deploy

---

#### 4.3 Explainability Assessment

| Requirement | Method Used | Stakeholder Level | Status |
|-------------|-------------|------------------|--------|
| Local explanations | LIME / SHAP | End users | |
| Global explanations | Feature importance | Technical teams | |
| Audit trail | Decision logging | Regulators | |
| Appeal mechanism | Human review process | Affected individuals | |

**Explainability Finding:** ☐ Acceptable ☐ Requires Mitigation ☐ System Should Not Deploy

---

#### 4.4 Privacy Assessment

| Privacy Control | Status | Evidence |
|----------------|--------|----------|
| Data minimization applied | ☐ Yes ☐ No ☐ Partial | |
| Consent mechanisms in place | ☐ Yes ☐ No ☐ Partial | |
| Right to erasure supported | ☐ Yes ☐ No ☐ Partial | |
| Differential privacy considered | ☐ Yes ☐ No ☐ Partial | |
| Privacy impact assessment completed | ☐ Yes ☐ No ☐ Partial | |

---

### MANAGE — Risk Response

#### 5.1 Risk Treatment Plan

| Risk | Rating | Treatment | Owner | Target Date | Status |
|------|--------|-----------|-------|-------------|--------|
| | | ☐ Accept ☐ Mitigate ☐ Transfer ☐ Avoid | | | |
| | | ☐ Accept ☐ Mitigate ☐ Transfer ☐ Avoid | | | |
| | | ☐ Accept ☐ Mitigate ☐ Transfer ☐ Avoid | | | |

#### 5.2 Monitoring Plan

| Metric | Monitoring Frequency | Alert Threshold | Responsible Party |
|--------|---------------------|-----------------|------------------|
| Model accuracy | | | |
| Fairness metrics by group | | | |
| Adversarial incident reports | | | |
| Data drift indicators | | | |
| User complaint rate | | | |

#### 5.3 Incident Response

**Escalation Path:**
1. ___________________________
2. ___________________________
3. ___________________________

**Incident Categories:**
- [ ] Discriminatory output detected
- [ ] Adversarial attack confirmed
- [ ] Data breach involving training data
- [ ] Regulatory inquiry received
- [ ] Significant accuracy degradation

---

## Section 4 — Regulatory Compliance Checklist

### EU AI Act (High Risk Systems)

| Article | Requirement | Status | Evidence |
|---------|-------------|--------|----------|
| Article 9 | Risk management system documented | ☐ Met ☐ Partial ☐ Not Met | |
| Article 10 | Training data governance documented | ☐ Met ☐ Partial ☐ Not Met | |
| Article 11 | Technical documentation maintained | ☐ Met ☐ Partial ☐ Not Met | |
| Article 12 | Logging and audit trail in place | ☐ Met ☐ Partial ☐ Not Met | |
| Article 13 | Transparency documentation available | ☐ Met ☐ Partial ☐ Not Met | |
| Article 14 | Human oversight mechanisms defined | ☐ Met ☐ Partial ☐ Not Met | |
| Article 15 | Accuracy and robustness validated | ☐ Met ☐ Partial ☐ Not Met | |

### NYC Local Law 144

| Requirement | Status | Evidence |
|-------------|--------|----------|
| Annual bias audit completed | ☐ Met ☐ Partial ☐ Not Met | |
| Audit conducted by independent auditor | ☐ Met ☐ Partial ☐ Not Met | |
| Summary of audit results published | ☐ Met ☐ Partial ☐ Not Met | |
| Candidate/employee notice provided | ☐ Met ☐ Partial ☐ Not Met | |

---

## Section 5 — Overall Risk Rating

| Domain | Rating | Justification |
|--------|--------|---------------|
| Bias and Fairness | ☐ Low ☐ Medium ☐ High ☐ Critical | |
| Robustness and Security | ☐ Low ☐ Medium ☐ High ☐ Critical | |
| Privacy | ☐ Low ☐ Medium ☐ High ☐ Critical | |
| Regulatory Compliance | ☐ Low ☐ Medium ☐ High ☐ Critical | |
| Governance | ☐ Low ☐ Medium ☐ High ☐ Critical | |

**Overall System Risk Rating:** ☐ Low ☐ Medium ☐ High ☐ Critical

**Deployment Recommendation:**
- [ ] Approved for deployment
- [ ] Approved with conditions — mitigations required before deployment
- [ ] Not approved — material risks require remediation

**Conditions (if applicable):**
_______________________________________________

---

## Section 6 — Sign-Off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| AI Risk Assessor | | | |
| System Owner | | | |
| Legal / Compliance | | | |
| CISO / Security | | | |
| Executive Sponsor | | | |

---

## Appendix — Definitions

**TPR (True Positive Rate):** Proportion of actual positives correctly identified. Also called recall or sensitivity.

**FPR (False Positive Rate):** Proportion of actual negatives incorrectly classified as positive.

**Disparity Flag:** Triggered when TPR or FPR difference between highest and lowest performing demographic group exceeds acceptable threshold.

**FGSM:** Fast Gradient Sign Method — a common adversarial attack technique that adds imperceptible perturbations to inputs to cause model misclassification.

**NIST AI RMF:** National Institute of Standards and Technology AI Risk Management Framework — a voluntary framework for managing AI risks across four functions: GOVERN, MAP, MEASURE, MANAGE.

---

*Template Version 1.0 | Prepared by Jake Kantor | AI GRC Practitioner | Provisional Patent Holder, Adversarial ML Protection System*  
*Contact: jake.t.kantor@gmail.com | linkedin.com/in/jakekantor*
