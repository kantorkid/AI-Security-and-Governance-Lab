# Standard Operating Procedure: Bias Audit and Risk Assessment

**Document Control**
- **SOP ID**: SOP-BA-001
- **Version**: 1.0
- **Effective Date**: 2024
- **System**: AI Bias Risk Assessment System (Facial Recognition Gender Classification)
- **System Owner**: Jake Kantor — ODU M.S. Cybersecurity & AI Security
- **EU AI Act Classification**: High Risk (Annex III, Category 1(a) - Biometric categorization)
- **Scope**: United States only
- **Use Case**: Research - Bias and Security Risk Assessment
- **Review Cycle**: Quarterly or upon material system change

---

## 1. PURPOSE

This SOP establishes procedures for conducting bias audits of the facial recognition gender classification system to:
- Identify, measure, and mitigate algorithmic bias across demographic groups
- Assess disparate impact and ensure fairness in model predictions
- Maintain compliance with NIST AI RMF, EU AI Act Article 10 (Data Governance), Article 15 (Accuracy), NYC Local Law 144
- Document known vulnerabilities: training data imbalance (42.5% White overrepresentation), adversarial vulnerability (FGSM attack degradation 65.5%→14.5%), and TPR gender disparity

---

## 2. SCOPE

**In Scope:**
- Pre-deployment bias assessment
- Periodic bias audits (quarterly minimum)
- Performance metric disaggregation by demographic subgroups
- Dataset quality and representativeness evaluation
- Adversarial robustness testing
- Documentation and reporting requirements

**Out of Scope:**
- General system monitoring (see SOP-MON-001)
- Vendor assessment (see SOP-VEN-001)
- Incident response procedures (see SOP-IR-001)

---

## 3. REGULATORY COMPLIANCE MAPPING

| Requirement | Regulation | Specific Citation | Implementation |
|------------|------------|-------------------|----------------|
| Bias Testing & Mitigation | EU AI Act | Article 10(2)(f), Article 10(3) | Sections 6.2-6.5 |
| Data Governance | EU AI Act | Article 10(2), Article 10(3), Article 10(5) | Section 6.1 |
| Accuracy Requirements | EU AI Act | Article 15(1), Annex IV Section 2 | Section 6.3 |
| Human Oversight | EU AI Act | Article 14(1), Article 14(4)(c) | Section 4.3 |
| Technical Documentation | EU AI Act | Article 11, Annex IV | Section 7 |
| Record Keeping | EU AI Act | Article 12(1) | Section 7 |
| Fairness Measurement | NIST AI RMF | MEASURE 2.6, 2.7, 2.8, 2.13 | Section 6.3-6.4 |
| Demographic Parity | NYC LL144 | §5-300, §20-871(b)(1) | Section 6.4 |
| Bias Audit Requirement | NYC LL144 | §20-871(a), §20-871(b) | Section 6 |
| Disparate Impact Analysis | NYC LL144 | §20-871(b)(2) | Section 6.4 |

---

## 4. ROLES AND RESPONSIBILITIES

### 4.1 System Owner (Jake Kantor)
- Final authority on bias assessment findings and remediation plans
- Approves deployment/continuation decisions based on audit results
- Escalation point for unacceptable bias levels
- Ensures resource availability for bias mitigation

### 4.2 AI Ethics Lead
- Designs bias audit methodology and fairness metrics
- Conducts bias assessments per Section 6
- Prepares bias audit reports with remediation recommendations
- Reviews demographic data collection protocols
- **Escalation Trigger**: Any fairness metric exceeding threshold (Section 6.6)

### 4.3 Data Scientist
- Executes technical bias measurements
- Performs statistical significance testing
- Conducts adversarial robustness testing
- Implements bias mitigation techniques
- Documents all test procedures and results

### 4.4 Human Oversight Monitor
- Reviews flagged predictions with demographic disparities
- Validates automated fairness measurements
- Provides qualitative bias assessment
- **Authority**: May suspend testing for ethical concerns

### 4.5 Compliance Officer
- Validates regulatory mapping accuracy
- Reviews audit documentation completeness
- Ensures records retention (EU AI Act Article 12: 10 years for high-risk systems)
- Coordinates with legal counsel on regulatory interpretation

---

## 5. DEFINITIONS

- **Bias Audit**: Independent evaluation measuring system performance across demographic groups (NYC LL144 §20-870)
- **Disparate Impact**: Selection rate for protected group < 80% of highest-performing group (4/5ths rule)
- **True Positive Rate (TPR)**: Proportion of actual positives correctly identified
- **False Positive Rate (FPR)**: Proportion of actual negatives incorrectly identified as positive
- **Demographic Parity**: Equal positive prediction rates across groups (|P(Ŷ=1|A=a) - P(Ŷ=1|A=b)| ≤ τ)
- **Equalized Odds**: Equal TPR and FPR across groups
- **Adversarial Robustness**: System performance under adversarial perturbations (FGSM, PGD)
- **Protected Attributes**: Gender, race, ethnicity, age (where detectable/annotated)

---

## 6. PROCEDURE

### 6.1 Dataset Quality Assessment

**Frequency**: Pre-deployment and when training data changes

**Steps**:

1. **Demographic Distribution Analysis**
   - Calculate representation percentages for each demographic group
   - Document known imbalance: White subjects = 42.5% (overrepresented)
   - Compare to U.S. Census Bureau population statistics
   - **Evidence Required**: 
     - Distribution tables with counts and percentages
     - Statistical comparison to target population
     - Visualization (bar charts, pie charts)
   - **Threshold**: No single group >35% unless population-justified
   - **Escalation**: Imbalance >15 percentage points → AI Ethics Lead → System Owner

2. **Label Quality Evaluation**
   - Assess ground truth label accuracy via manual review (n≥500 random samples)
   - Calculate inter-annotator agreement (Cohen's Kappa ≥0.8 required)
   - Document labeling methodology and annotator qualifications
   - **Evidence Required**: 
     - Annotation guidelines document
     - Kappa score calculation
     - Error analysis report
   - **Compliance**: EU AI Act Article 10(3) - training data quality requirements

3. **Data Sufficiency Check**
   - Verify minimum sample sizes per demographic group (n≥1000 per intersectional category)
   - Calculate statistical power for subgroup analysis (power ≥0.8, α=0.05)
   - **Evidence Required**: Power analysis calculations
   - **Escalation**: Insufficient samples → Defer testing until data acquisition

4. **Documentation**
   - Complete Data Quality Assessment Report (Template DQAR-001)
   - Submit to System Owner within 5 business days
   - Store in compliance repository (10-year retention)
   - **Compliance**: EU AI Act Article 11, Annex IV Section 2(d)

---

### 6.2 Bias Measurement Protocol

**Frequency**: Pre-deployment, quarterly, post-modification

**Steps**:

1. **Test Set Preparation**
   - Create demographically stratified test set (minimum 5,000 samples)
   - Ensure balanced representation (±5% of uniform distribution)
   - Separate from training/validation data
   - **Evidence Required**: Test set demographic distribution report

2. **Overall Performance Baseline**
   - Calculate aggregate metrics on full test set:
     - Accuracy (known baseline: 65.5%)
     - Precision, Recall, F1-Score
     - AUC-ROC
   - **Evidence Required**: Confusion matrix, metric calculations
   - **Threshold**: Accuracy ≥60% for proceeding with disaggregated analysis

3. **Disaggregated Performance Analysis**
   
   For each demographic group (Gender: Male/Female; Race: White/Black/Asian/Hispanic/Other):
   
   - Calculate group-specific metrics:
     - True Positive Rate (TPR / Recall / Sensitivity)
     - False Positive Rate (FPR)
     - False Negative Rate (FNR)
     - Precision
     - F1-Score
     - Accuracy
   
   - **Evidence Required**:
     - Per-group confusion matrices
     - Metric comparison table
     - Statistical significance tests (chi-square, p<0.05)
   
   - **Known Issue**: Document existing TPR disparity between male/female subjects

4. **Intersectional Analysis**
   - Repeat Step 3 for intersectional categories (e.g., White Male, Black Female)
   - Identify most disadvantaged subgroup
   - **Evidence Required**: Heatmap visualization of performance across intersections

5. **Documentation**
   - Complete Performance Disaggregation Report (Template PDR-001)
   - Include all evidence artifacts
   - **Compliance**: NIST AI RMF MEASURE 2.6, 2.7, 2.8

---

### 6.3 Fairness Metric Evaluation

**Steps**:

1. **Demographic Parity Assessment**
   
   Calculate positive prediction rate for each group:
   ```
   PPR_group = (TP + FP) / N_group
   ```
   
   Measure maximum disparity:
   ```
   Δ_DP = max|PPR_i - PPR_j| for all group pairs i,j
   ```
   
   - **Threshold**: Δ_DP ≤ 0.10 (10 percentage points)
   - **Evidence Required**: PPR table, disparity calculations
   - **Compliance**: NYC LL144 §20-871(b)(1)

2. **Equalized Odds Assessment**
   
   For each demographic attribute:
   ```
   Δ_TPR = max|TPR_i - TPR_j| for all group pairs
   Δ_FPR = max|FPR_i - FPR_j| for all group pairs
   ```
   
   - **Threshold**: Δ_TPR ≤ 0.10 AND Δ_FPR ≤ 0.10
   - **Evidence Required**: TPR/FPR comparison tables, disparity calculations
   - **Escalation**: Violation → Mandatory remediation plan within 10 business days

3. **Disparate Impact Ratio (4/5ths Rule)**
   
   For each protected group vs. highest-performing group:
   ```
   DI_ratio = PPR_protected / PPR_highest
   ```
   
   - **Threshold**: DI_ratio ≥ 0.80
   - **Evidence Required**: Ratio calculations for all groups
   - **Compliance**: NYC LL144 §20-871(b)(2)

4. **Equal Opportunity Difference**
   
   ```
   Δ_EOpp = max|TPR_i - TPR_j|
   ```
   
   - **Threshold**: Δ_EOpp ≤ 0.10
   - **Evidence Required**: EOpp calculation worksheet
   - **Note**: Particularly relevant for known TPR gender disparity

5. **Statistical Significance Testing**
   - Perform chi-square tests on confusion matrix differences (α=0.05)
   - Apply Bonferroni correction for multiple comparisons
   - **Evidence Required**: Test statistics, p-values, corrected α levels

6. **Documentation**
   - Complete Fairness Metrics Report (Template FMR-001)
   - Flag all threshold violations
   - **Compliance**: NIST AI RMF MEASURE 2.13, EU AI Act Article 15(1)

---

### 6.4 Adversarial Robustness Testing

**Frequency**: Pre-deployment, semi-annually, post-model update

**Purpose**: Assess vulnerability to adversarial attacks affecting bias properties

**Steps**:

1. **FGSM Attack Testing**
   
   Execute Fast Gradient Sign Method attacks:
   - Perturbation budgets: ε = [0.01, 0.05, 0.1, 0.3]
   - Apply to stratified test set (n≥1000 per group)
   
   - **Known Vulnerability**: Baseline accuracy 65.5% → 14.5% under FGSM
   
   - **Evidence Required**:
     - Accuracy degradation curves per epsilon value
     - Per-group robustness metrics
     - Adversarial example visualizations

2. **Demographic-Disaggregated Robustness**
   
   For each demographic group, calculate:
   - Accuracy under attack per ε value
   - Robustness disparity: max|Acc_adv,i - Acc_adv,j|
   
   - **Threshold**: Robustness disparity ≤ 0.15 across groups
   - **Evidence Required**: Robustness comparison table
   - **Escalation**: Disparity >0.15 → Immediate AI Ethics Lead review

3. **Projected Gradient Descent (PGD) Testing**
   
   Execute PGD attacks (stronger):
   - ε = 0.05, α = 0.01, iterations = 40
   - Measure accuracy degradation per demographic group
   
   - **Evidence Required**: PGD attack results table

4. **Bias Amplification Under Attack**
   
   Compare fairness metrics (Section 6.3) under:
   - Clean conditions
   - FGSM attack (ε=0.1)
   
   Document whether attacks disproportionately degrade performance for specific groups
   
   - **Evidence Required**: Comparative fairness metrics table
   - **Compliance**: NIST AI RMF MEASURE 2.8 (adversarial robustness)

5. **Mitigation Assessment**
   
   If adversarial training/defenses deployed:
   - Retest with adversarial examples
   - Verify defense doesn't introduce new bias
   
   - **Evidence Required**: Pre/post mitigation comparison

6. **Documentation**
   - Complete Adversarial Robustness Report (Template ARR-001)
   - Include all attack parameters and results
   - **Retention**: 10 years per EU AI Act Article 12(1)

---

### 6.5 Bias Mitigation Planning

**Trigger**: Any threshold violation in Sections 6.3 or 6.4

**Steps**:

1. **Root Cause Analysis** (Due: 5 business days from finding)
   
   Investigate:
   - Training data imbalance contribution (known: 42.5% White overrepresentation)
   - Feature engineering issues
   - Model architecture limitations
   - Evaluation metric appropriateness
   
   - **Evidence Required**: Root Cause Analysis Report (Template RCA-001)
   - **Owner**: AI Ethics Lead + Data Scientist

2. **Mitigation Strategy Selection**
   
   Evaluate applicability:
   
   **Pre-processing**:
   - Resampling (oversampling minority, undersampling majority)
   - Reweighting training samples
   - Synthetic data generation (with validation)
   
   **In-processing**:
   - Fairness constraints in objective function
   - Adversarial debiasing
   - Regularization techniques
   
   **Post-processing**:
   - Threshold optimization per group
   - Calibration adjustments
   
   - **Evidence Required**: Mitigation options analysis, selection justification
   - **Approval**: System Owner must approve strategy

3. **Implementation & Validation**
   
   - Apply mitigation technique(s)
   - Re-run full bias audit (Sections 6.1-6.4)
   - Verify improvement without unacceptable accuracy loss
   
   - **Threshold**: Overall accuracy must not decrease >5 percentage points
   - **Evidence Required**: 
     - Implementation documentation
     - Before/after comparison tables
     - Validation test results

4. **Residual Risk Assessment**
   
   Document:
