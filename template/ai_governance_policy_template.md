# AI Governance Policy
**Template v1.0 | Aligned to NIST AI RMF 1.0 | EU AI Act | ISO/IEC 42001**

---

**Organization:** ___________________________  
**Policy Owner:** ___________________________  
**Effective Date:** ___________________________  
**Review Date:** ___________________________  
**Approved By:** ___________________________

---

## 1. Purpose

This policy establishes the governance framework for the responsible development, procurement, deployment, and monitoring of artificial intelligence systems within [Organization Name]. It ensures AI systems are used in a manner that is lawful, ethical, transparent, and aligned with organizational values and applicable regulatory requirements.

---

## 2. Scope

This policy applies to:

- All employees, contractors, and vendors who develop, procure, deploy, or use AI systems on behalf of the organization
- All AI systems used in organizational operations, including third-party AI tools and services
- All data used to train, validate, or operate AI systems

---

## 3. Definitions

**AI System** — A machine-based system that processes inputs to generate outputs such as predictions, recommendations, decisions, or content, with varying levels of autonomy.

**High-Risk AI System** — An AI system that poses significant risk to health, safety, or fundamental rights as defined under the EU AI Act Annex III or equivalent regulatory classification.

**Automated Decision** — Any decision made wholly or substantially by an AI system without meaningful human review.

**Consequential Decision** — A decision that materially affects an individual's access to employment, credit, housing, education, healthcare, or essential services.

**Bias Audit** — A systematic evaluation of AI system outputs across demographic groups to identify discriminatory patterns.

**Human Oversight** — The ability of a human to monitor, understand, intervene in, and override AI system outputs.

---

## 4. Acceptable Use

### 4.1 Permitted Uses

AI systems may be used for:

- Operational efficiency and process automation
- Data analysis and pattern recognition
- Decision support where humans retain final authority
- Customer service augmentation
- Research and development activities
- Content generation with appropriate human review

### 4.2 Prohibited Uses

AI systems may not be used for:

- [ ] Social scoring of individuals based on behavior or personal characteristics
- [ ] Real-time biometric surveillance in publicly accessible spaces without legal authorization
- [ ] Manipulation of individuals through subliminal techniques
- [ ] Exploitation of vulnerabilities of specific groups
- [ ] Automated employment decisions without human review and appeal mechanism
- [ ] Any purpose prohibited under applicable law including EU AI Act Article 5

---

## 5. AI Risk Classification

All AI systems must be classified prior to deployment:

| Risk Level | Definition | Requirements |
|------------|------------|--------------|
| **Critical** | Prohibited under applicable law | Immediate decommission |
| **High** | Material impact on individuals or regulated domain | Full risk assessment, bias audit, human oversight, regulatory compliance |
| **Medium** | Moderate operational or reputational risk | Risk assessment, monitoring plan, human review mechanism |
| **Low** | Minimal risk, no individual impact | Standard security review, usage documentation |

**Classification Authority:** AI Risk Officer or designated assessor

---

## 6. Human Oversight Requirements

### 6.1 Mandatory Human Oversight

Human oversight is required for all:

- Consequential decisions affecting individuals
- High-risk AI system outputs
- Outputs with legal or regulatory implications
- Automated actions with irreversible consequences

### 6.2 Oversight Standards

Human reviewers must:

- Have sufficient understanding of the AI system to evaluate its outputs
- Have authority to override or escalate AI decisions
- Document their review and decision rationale
- Not be subject to quotas or incentives that discourage override

### 6.3 Override and Appeal

- All individuals affected by AI-assisted consequential decisions have the right to request human review
- Override requests must be logged and responded to within [X] business days
- Override decisions must be documented with rationale

---

## 7. Bias and Fairness Requirements

### 7.1 Pre-Deployment Bias Assessment

All medium and high-risk AI systems must undergo bias assessment prior to deployment measuring:

- Accuracy by demographic group
- True Positive Rate (TPR) by demographic group
- False Positive Rate (FPR) by demographic group
- Disparity analysis against acceptable thresholds

**Acceptable Disparity Threshold:** [Define organizational threshold — e.g., no group TPR more than 10% below highest performing group]

### 7.2 Ongoing Monitoring

- Bias metrics must be monitored at minimum [quarterly / monthly] intervals
- Significant disparity triggers mandatory review and remediation
- Results must be documented and retained for audit purposes

### 7.3 NYC Local Law 144 Compliance

For AI systems used in employment decisions affecting New York City residents:

- Annual independent bias audit required
- Audit results published on organizational website
- Candidates and employees notified prior to AI system use
- Audit methodology documented and available upon request

---

## 8. Transparency and Explainability

### 8.1 Disclosure Requirements

Organizations must disclose:

- When AI systems are used in decisions affecting individuals
- The categories of data used by AI systems
- The logic of automated decisions upon individual request
- Contact information for AI-related inquiries and appeals

### 8.2 Explainability Standards

AI systems used in consequential decisions must support:

- Local explanations — why a specific decision was made for a specific individual
- Global explanations — how the system generally operates
- Documentation sufficient for regulatory audit

### 8.3 EU AI Act Transparency

For AI systems subject to EU AI Act requirements:

- Technical documentation maintained per Article 11
- Instructions for use provided per Article 13
- Logging capabilities implemented per Article 12

---

## 9. Data Governance

### 9.1 Training Data Requirements

Training data must:

- Be sourced lawfully with appropriate rights and consents
- Be documented with provenance records
- Be evaluated for demographic representation and imbalance
- Be retained with audit trail for the system lifecycle plus [X] years

### 9.2 Data Minimization

AI systems must use only data necessary for their stated purpose. Requests to expand data use require documented justification and risk assessment.

### 9.3 Individual Rights

The organization must support:

- Right of access to data used in AI decisions
- Right to correct inaccurate data
- Right to erasure where legally required
- Right to object to automated processing

---

## 10. Vendor and Third-Party AI

### 10.1 Procurement Requirements

Before procuring third-party AI systems organizations must:

- Conduct risk classification assessment
- Obtain vendor documentation of training data, model performance, and bias testing
- Contractually require bias audit rights
- Confirm regulatory compliance representations
- Assess vendor incident response capabilities

### 10.2 Vendor Contractual Requirements

AI vendor contracts must include:

- [ ] Data processing agreement compliant with applicable privacy law
- [ ] Right to audit AI system performance and bias metrics
- [ ] Incident notification requirements within [X] hours
- [ ] Model change notification with minimum [X] days advance notice
- [ ] Compliance representations for applicable regulations
- [ ] Liability provisions for discriminatory outputs

### 10.3 Ongoing Vendor Monitoring

- Annual vendor review of AI governance practices
- Immediate review triggered by regulatory action against vendor
- Vendor bias audit results reviewed and documented

---

## 11. Security Requirements

### 11.1 Adversarial Robustness

AI systems used in security-sensitive contexts must be tested for:

- Adversarial input attacks
- Data poisoning vulnerabilities
- Model extraction risks
- Prompt injection (for LLM-based systems)

### 11.2 Access Controls

- AI system access limited to authorized users on least privilege basis
- Model weights and training data classified as sensitive assets
- API access to AI systems logged and monitored

### 11.3 Incident Response

AI security incidents must be escalated per the organizational incident response plan within:

- **Critical** — 1 hour
- **High** — 4 hours
- **Medium** — 24 hours

---

## 12. Roles and Responsibilities

| Role | Responsibilities |
|------|----------------|
| **AI Risk Officer** | Owns AI governance policy, conducts or oversees risk assessments, reports to executive leadership |
| **System Owner** | Responsible for specific AI system compliance, maintains technical documentation, coordinates bias audits |
| **Legal / Compliance** | Regulatory interpretation, contract review, regulatory inquiry response |
| **CISO / Security** | Adversarial security testing, access controls, incident response |
| **HR** | Employment AI compliance, NYC LL144 notices, employee training |
| **Procurement** | Vendor AI governance requirements, contract compliance |
| **All Employees** | Compliant use of AI tools, incident reporting, completion of required training |

---

## 13. Training Requirements

| Audience | Training | Frequency |
|----------|----------|-----------|
| All employees | AI acceptable use policy | Annual |
| AI system owners | Risk assessment methodology | Upon appointment and annually |
| HR and recruiting | Employment AI compliance, NYC LL144 | Annual |
| Technical teams | Secure AI development practices | Annual |
| Executive leadership | AI governance and liability | Annual |

---

## 14. Incident Reporting

### 14.1 Reportable Incidents

Employees must report:

- AI outputs that appear discriminatory or harmful
- Suspected adversarial attacks on AI systems
- Unauthorized use of AI systems
- AI-related data breaches
- Regulatory inquiries related to AI systems

### 14.2 Reporting Channel

Report AI incidents to: ___________________________

### 14.3 Non-Retaliation

Employees who report AI governance concerns in good faith are protected from retaliation.

---

## 15. Policy Compliance and Enforcement

- Violations of this policy may result in disciplinary action up to and including termination
- Vendors found in violation of contractual AI governance requirements may be subject to contract termination
- Material violations will be reported to legal and compliance leadership

---

## 16. Policy Review

This policy will be reviewed:

- Annually at minimum
- Upon significant regulatory change
- Following a material AI-related incident
- Upon deployment of new high-risk AI systems

---

## Appendix A — Regulatory Reference

| Regulation | Jurisdiction | Key Requirements |
|------------|-------------|-----------------|
| EU AI Act | European Union | Risk classification, conformity assessment, transparency, human oversight |
| NYC Local Law 144 | New York City | Annual bias audit, public disclosure, candidate notice |
| Colorado AI Act | Colorado | Consequential decision disclosure, bias assessment |
| GDPR | European Union | Data minimization, consent, individual rights, DPIA |
| CCPA/CPRA | California | Consumer rights, automated decision disclosure |
| NIST AI RMF | United States (voluntary) | GOVERN, MAP, MEASURE, MANAGE framework |
| ISO/IEC 42001 | International | AI management system requirements |

---

## Appendix B — Related Documents

- AI System Risk Assessment Template
- AI Incident Response Procedure
- Vendor AI Governance Questionnaire
- Bias Audit Methodology
- AI Acceptable Use Guidelines

---

*Template Version 1.0 | Prepared by Jake Kantor | AI GRC Practitioner | Provisional Patent Holder, Adversarial ML Protection System*  
*Contact: jake.t.kantor@gmail.com | linkedin.com/in/jakekantor*
