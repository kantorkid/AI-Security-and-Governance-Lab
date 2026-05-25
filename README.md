# AI-Bias-Assessment-NIST-RMF# 

AI Bias Risk Assessment: Facial Recognition Using NIST AI RMF

**Author:** Jake Kantor | [LinkedIn](https://linkedin.com/in/jakekantor) | M.S. Cybersecurity, AI Security — Old Dominion University  
**Framework:** NIST AI Risk Management Framework (AI RMF 1.0)  
**Dataset:** UTKFace (23,708 facial images)  
**Prediction Task:** Gender Classification (Binary)

---

## Executive Summary

This project applies the NIST AI Risk Management Framework to conduct a comprehensive bias and security risk assessment of a facial recognition AI system trained on the UTKFace dataset. The assessment evaluates model robustness, adversarial vulnerability, demographic fairness, explainability, and privacy — producing governance recommendations aligned with the EU AI Act, NYC Local Law 144, and NIST AI RMF controls.

Key findings demonstrate that unmitigated facial recognition models exhibit significant demographic bias, extreme adversarial vulnerability, and substantial privacy-utility tradeoffs that require active governance intervention before responsible deployment.

---

## Dataset

**UTKFace Dataset**
- 23,708 facial images labeled with age, gender, and race
- Gender distribution: 12,391 female (52.3%), 11,314 male (47.7%)
- Race distribution: White (42.5%), Black (19.1%), Indian (16.8%), Asian (14.5%), Other (7.1%)
- Assessment subset: 1,000 images (resource-constrained environment)
- Images preprocessed to 64×64 grayscale tensors

**Dataset Limitation:** Significant racial imbalance with White subjects overrepresented at 42.5%. This imbalance directly contributes to disparate model performance across demographic groups and represents a governance risk for any production deployment.

---

## NIST AI RMF Framework Application

This assessment maps to the four core NIST AI RMF functions:

### GOVERN
- Defined scope, prediction task, and ethical constraints prior to model development
- Identified protected demographic groups (race, gender) requiring fairness monitoring
- Documented dataset limitations and their governance implications
- Applied negative prompt controls in generative components to prevent harmful outputs

### MAP
- Mapped AI system risks across robustness, fairness, privacy, and explainability domains
- Identified high-risk deployment contexts: hiring, surveillance, law enforcement
- Documented dataset bias as a primary upstream risk factor

### MEASURE
- Quantified model performance across demographic groups using TPR, FPR, accuracy, and precision
- Measured adversarial vulnerability through FGSM attack success rates
- Evaluated privacy-utility tradeoffs across multiple epsilon values
- Applied LIME explainability to identify which facial regions drive model decisions

### MANAGE
- Implemented bias mitigation through sample re-weighting and threshold calibration
- Demonstrated adversarial training as a defense mechanism
- Evaluated Differential Privacy and Federated Learning as privacy-enhancing alternatives
- Documented residual risks and recommended next steps

---

## Key Results

### Baseline Model Performance
| Metric | Value |
|--------|-------|
| Overall Accuracy | 70.0% |
| Female Recall (TPR) | 94.6% |
| Male Recall (TPR) | 48.6% |
| Female Precision | 61.5% |
| Male Precision | 91.2% |

**Finding:** The baseline model demonstrates significant gender bias — it identifies females with high recall (94.6%) but misclassifies nearly half of all male subjects (51.4% miss rate). This disparity indicates the model has learned demographic shortcuts rather than generalizable features.

---

### Robustness and Adversarial Vulnerability
| Test Condition | Accuracy |
|----------------|----------|
| Clean images (baseline) | 70.0% |
| Gaussian noise perturbation | 46.5% |
| FGSM adversarial attack (ε=0.1) | 14.5% |
| Adversarially trained model — clean images | 57.5% |
| Adversarially trained model — adversarial images | 100.0% |

**Finding:** The baseline model is highly vulnerable to adversarial attack. A targeted FGSM perturbation with epsilon=0.1 — invisible to the human eye — reduced accuracy from 70% to 14.5%. This represents an extreme security risk in any deployment context where adversarial manipulation is possible.

Adversarial training successfully defended against the specific FGSM attack (100% accuracy on adversarial examples) but introduced a clean accuracy tradeoff (57.5% vs 70.0%), illustrating the fundamental robustness-utility tension governance frameworks must account for.

---

### Fairness Metrics by Demographic Group (Before Mitigation)
Race categories: 0=White, 1=Black, 2=Asian, 3=Indian, 4=Other

**Finding:** Fairness metrics varied significantly across racial groups. Groups with fewer training samples (Other, Indian) demonstrated lower TPR, indicating the model underperforms for underrepresented populations — a direct consequence of training data imbalance.

**Post-Mitigation:** Two mitigation strategies were applied:
- **Re-weighting:** Assigned higher sample weights to minority race groups during training to reduce performance disparities
- **Threshold Calibration:** Lowered the classification threshold for the lowest-TPR group from 0.5 to 0.3, improving recall for underrepresented populations

Both strategies improved fairness metrics with measurable reductions in TPR disparity across groups.

---

### Privacy-Utility Tradeoffs

**Differential Privacy (diffprivlib Logistic Regression)**
| Epsilon | Accuracy |
|---------|----------|
| 0.1 | 48.0% |
| 0.5 | ~47-48% |
| 1.0 | 47.0% |
| 5.0 | 47.0% |

**Federated Learning (3 simulated clients, naive weight averaging)**
| Model | Accuracy |
|-------|----------|
| Baseline CNN | 70.0% |
| DP Logistic Regression (ε=1.0) | 47.0% |
| Federated Learning | 77.0% |

**Finding:** Differential Privacy imposed a significant utility cost — accuracy dropped from 70% to approximately 47% across epsilon values, suggesting strong privacy guarantees come at substantial performance cost for this task. Federated Learning achieved 77% accuracy while simulating a privacy-preserving distributed training approach, demonstrating a more favorable privacy-utility balance for this use case.

---

### Explainability (LIME)
LIME analysis identified that the model primarily relies on facial edges, structural contours (nose, jawline, eye regions), and boundaries between facial features and background to make gender classifications.

**Governance Implication:** While the model focuses on intuitive facial regions, the reliance on edge and structural features rather than holistic facial understanding raises concerns about robustness to image quality variations and potential sensitivity to demographic features associated with facial structure rather than gender specifically.

---

## Regulatory Mapping

### EU AI Act (Enforcement: August 2, 2026)
Facial recognition systems used in high-risk contexts (hiring, law enforcement, education) are classified as high-risk AI systems under Annex III. This assessment addresses key Article requirements:
- **Article 9 (Risk Management):** Documented risk identification and mitigation across all assessment phases
- **Article 10 (Training Data):** Identified dataset imbalance and demographic representation gaps
- **Article 13 (Transparency):** LIME explainability demonstrates model decision transparency
- **Article 15 (Accuracy and Robustness):** Adversarial testing quantifies robustness limitations

### NYC Local Law 144
Requires bias audits for automated employment decision tools. This assessment methodology — measuring TPR and FPR by demographic group before and after mitigation — directly implements the bias audit requirements for employment AI systems operating in New York City.

### NIST AI RMF Alignment
Full framework mapping across GOVERN, MAP, MEASURE, and MANAGE functions as documented above.

---

## Governance Recommendations

1. **Do Not Deploy Without Bias Mitigation** — Baseline model TPR disparities across racial groups are unacceptable for any regulated deployment context. Re-weighting or threshold calibration must be applied and validated before production use.

2. **Implement Adversarial Robustness Testing as Standard Practice** — The 55.5 percentage point accuracy drop under FGSM attack demonstrates that standard accuracy metrics are insufficient for security-critical deployments. Adversarial testing should be required pre-deployment and after any model update.

3. **Address Training Data Imbalance** — The White-dominant dataset (42.5%) structurally disadvantages minority group performance. Organizations deploying facial recognition must either rebalance training data or document and disclose demographic performance disparities.

4. **Evaluate Privacy Mechanism Fit** — Differential Privacy imposes significant accuracy costs for this task. Federated Learning demonstrated better privacy-utility balance. Privacy mechanism selection should be driven by deployment context risk assessment, not default implementation.

5. **Establish Ongoing Monitoring** — LIME explainability should be applied continuously in production to detect feature drift — changes in which facial regions drive decisions may indicate model drift or emerging bias.

6. **Scope Adversarial Testing Beyond FGSM** — This assessment focused on FGSM. Production deployments require testing against PGD, Carlini-Wagner, and transfer attacks to fully characterize adversarial risk.

---

## Technical Stack

| Category | Tools |
|----------|-------|
| ML Framework | TensorFlow, Keras |
| Explainability | LIME |
| Adversarial Testing | FGSM (custom implementation) |
| Privacy | diffprivlib, Federated Learning simulation |
| Generative AI | Stable Diffusion v1.5, GPT-2 |
| Data Processing | PyTorch, NumPy, Pandas, PIL |
| Visualization | Matplotlib |
| Environment | Google Colab (GPU) |

---

## Repository Structure

```
ai-bias-assessment-nist-rmf/
├── README.md
├── notebooks/
│   └── bias_assessment.ipynb
├── reports/
│   └── executive_summary.pdf
├── data/
│   └── README.md (dataset description — raw data not included)
└── requirements.txt
```

---

## Limitations

- Dataset limited to 1,000 images due to compute constraints (full dataset: 23,708)
- Adversarial testing limited to FGSM; comprehensive robustness requires additional attack types
- Federated Learning implementation uses naive weight averaging — production FL requires secure aggregation
- DP implementation uses Logistic Regression on flattened data, not directly comparable to CNN baseline

---

## Citation and Usage

UTKFace dataset is intended for research purposes. This assessment abides by UTKFace usage guidelines. All findings are produced for AI governance research and educational purposes.

---

*This project was completed as part of CYSE 640: Trustworthy and Responsible AI at Old Dominion University (Spring 2026). Methodology and governance recommendations represent original analysis.*
