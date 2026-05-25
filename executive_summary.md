# Executive Summary
## AI Bias Risk Assessment: Facial Recognition System
### Applied NIST AI Risk Management Framework Analysis

---

**Prepared by:** Jake Kantor  
**Affiliation:** M.S. Cybersecurity, AI Security Concentration — Old Dominion University  
**Patent:** Provisional Patent Holder, Adversarial ML Protection System (USPTO, 2026)  
**Date:** May 2026  
**Framework:** NIST AI RMF 1.0  
**Classification:** Research — Public Distribution

---

## Purpose

This executive summary presents findings from a comprehensive AI bias and security risk assessment conducted on a gender classification model trained on the UTKFace facial recognition dataset. The assessment applies the NIST AI Risk Management Framework (AI RMF 1.0) and produces governance recommendations relevant to organizations deploying facial recognition AI in regulated contexts.

The methodology demonstrates a practical implementation of technical AI governance — the kind of assessment required under the EU AI Act for high-risk AI systems and mandated under NYC Local Law 144 for automated employment decision tools.

---

## Assessment Scope

**System assessed:** Convolutional Neural Network (CNN) for binary gender classification from facial images  
**Dataset:** UTKFace — 23,708 facial images labeled with age, gender, and race  
**Assessment subset:** 1,000 images  
**Framework applied:** NIST AI RMF (GOVERN, MAP, MEASURE, MANAGE)  
**Risk domains evaluated:** Robustness, adversarial vulnerability, demographic fairness, explainability, privacy

---

## Critical Findings

### Finding 1 — Significant Gender Classification Bias
The baseline model achieves 70% overall accuracy but demonstrates severe performance disparity by gender. Female subjects are correctly classified at a 94.6% recall rate while male subjects are misclassified at a 51.4% rate. This disparity indicates the model has learned demographic shortcuts rather than generalizable classification features, creating unacceptable bias risk in any regulated deployment context.

**Risk Level: High**  
**Regulatory Implication:** Directly violates EU AI Act Article 10 data governance requirements and NYC Local Law 144 bias audit thresholds for employment AI systems.

---

### Finding 2 — Extreme Adversarial Vulnerability
A targeted Fast Gradient Sign Method (FGSM) attack with perturbation magnitude epsilon=0.1 — producing pixel changes invisible to the human eye — reduced model accuracy from 70% to 14.5%. This 55.5 percentage point degradation represents a critical security failure for any deployment where adversarial manipulation is possible, including law enforcement, access control, and hiring systems.

**Risk Level: Critical**  
**Regulatory Implication:** Directly conflicts with EU AI Act Article 15 accuracy and robustness requirements for high-risk AI systems.

---

### Finding 3 — Demographic Performance Disparities by Race
Fairness analysis across five racial categories (White, Black, Asian, Indian, Other) revealed significant TPR and FPR disparities. Underrepresented racial groups — particularly Indian and Other categories comprising 16.8% and 7.1% of the dataset respectively — demonstrated lower classification performance, a predictable consequence of training data imbalance.

**Risk Level: High**  
**Regulatory Implication:** Constitutes actionable bias under NYC Local Law 144 and triggers documentation requirements under EU AI Act Article 13.

---

### Finding 4 — Privacy Mechanism Tradeoffs Require Governance Decision
Differential Privacy implementation reduced model accuracy from 70% to approximately 47% across tested epsilon values (0.1–5.0), representing a 23 percentage point utility cost for privacy guarantees. Federated Learning achieved 77% accuracy while simulating distributed training without centralized data access — demonstrating a more favorable privacy-utility balance for this use case.

**Risk Level: Medium**  
**Governance Implication:** Privacy mechanism selection cannot be defaulted — it requires explicit risk-based decision making documented in the AI system's risk management plan.

---

## Mitigation Results

### Adversarial Training
Training the model on a mixed dataset of clean and FGSM-generated adversarial examples produced 100% accuracy on adversarial test images. Clean accuracy decreased to 57.5%, confirming the robustness-utility tradeoff that governance frameworks must explicitly address.

### Bias Mitigation — Re-weighting
Assigning higher sample weights to underrepresented racial groups during training reduced TPR disparity across demographic groups. This approach improves fairness without requiring post-deployment intervention.

### Bias Mitigation — Threshold Calibration
Lowering the classification threshold from 0.5 to 0.3 for the lowest-TPR demographic group improved recall for underrepresented populations. This post-processing approach is deployable without model retraining.

---

## Governance Recommendations

**Recommendation 1 — Pre-Deployment Bias Audit Required**  
No deployment should proceed without documented bias audit results showing acceptable TPR and FPR parity across demographic groups. Current baseline performance fails this threshold.

**Recommendation 2 — Mandatory Adversarial Testing Protocol**  
Standard accuracy metrics are insufficient for security-critical deployments. A formal adversarial testing protocol covering at minimum FGSM, PGD, and Carlini-Wagner attacks must be established and conducted pre-deployment and after any model update.

**Recommendation 3 — Training Data Rebalancing**  
The 42.5% White subject overrepresentation in UTKFace structurally disadvantages minority group performance. Organizations must either rebalance training data to achieve demographic parity or formally document and disclose performance disparities across all deployment contexts.

**Recommendation 4 — Privacy Mechanism Selection via Risk Assessment**  
Federated Learning demonstrated superior privacy-utility balance for this task compared to Differential Privacy. Organizations should select privacy mechanisms based on formal risk assessment of their specific deployment context rather than defaulting to any single approach.

**Recommendation 5 — Continuous Explainability Monitoring**  
LIME analysis revealed the model relies on facial edge and structural features. Continuous explainability monitoring should be implemented in production to detect feature drift that may indicate emerging bias or model degradation.

**Recommendation 6 — Regulatory Compliance Documentation**  
Any organization deploying facial recognition AI in high-risk contexts must maintain documentation covering the requirements identified in this assessment: risk management records (EU AI Act Article 9), training data governance (Article 10), transparency mechanisms (Article 13), and robustness validation (Article 15).

---

## Regulatory Alignment Summary

| Regulation | Requirement | Assessment Coverage |
|------------|-------------|---------------------|
| EU AI Act Article 9 | Risk management system | NIST AI RMF full framework application |
| EU AI Act Article 10 | Training data governance | Dataset bias analysis and documentation |
| EU AI Act Article 13 | Transparency | LIME explainability implementation |
| EU AI Act Article 15 | Accuracy and robustness | Adversarial testing and noise perturbation |
| NYC Local Law 144 | Bias audit | TPR/FPR by demographic group before/after mitigation |
| NIST AI RMF | Full framework | GOVERN, MAP, MEASURE, MANAGE applied |

---

## Conclusion

This assessment demonstrates that facial recognition AI systems require active governance intervention — not passive deployment — to meet emerging regulatory requirements. The baseline model's adversarial vulnerability, demographic bias, and privacy tradeoffs represent governance risks that cannot be addressed through standard performance monitoring alone.

The NIST AI RMF provides an effective operational structure for conducting this type of assessment. Organizations deploying facial recognition in regulated contexts should treat this methodology as a minimum baseline for pre-deployment risk management, with ongoing monitoring and periodic re-assessment built into their AI governance programs.

As EU AI Act high-risk AI system requirements enter full enforcement on August 2, 2026, organizations that have not conducted and documented this type of assessment face material regulatory exposure.

---

*Full methodology, code, and detailed results available at: [GitHub Repository Link]*  
*Contact: jake.t.kantor@gmail.com | linkedin.com/in/jakekantor*
