# Data

This folder contains all datasets and calculated values used throughout the phishing risk analysis.

It provides a complete, structured representation of how raw phishing simulation data was transformed into organizational risk exposure, financial impact, and executive decision insights.

---

## Structure

The datasets in this folder are organized to reflect the progression of the analysis across all phases.

---

## Files

### 1. phase1_phishing_metrics.csv

This dataset contains the foundational behavioral metrics derived from the phishing simulations.

It includes:

- Emails sent, opened, and clicked  
- Credentials submitted and sensitive data entered  
- Calculated rates:
  - Open rate  
  - Click-through rate  
  - Credential submission rate  
  - Data entry rate  
  - Conversion rates (Open → Click, Click → Credential)  

This file represents the **human behavior layer** of the analysis.

---

### 2. phase2_risk_projection.csv

This dataset contains the organizational risk scaling based on the results from Phase 1.

It includes:

- Credential compromise rate  
- Total employees considered  
- Estimated compromised users  
- Breach probability  
- Expected number of breaches  
- Financial exposure (Annualized Loss Expectancy)

This file represents the **risk quantification layer**, where behavior is translated into business risk.

---

### 3. phase2_control_analysis.csv

This dataset evaluates the effectiveness of security controls.

It includes:

- Control type (MFA, Training)  
- Cost of implementation  
- Effectiveness assumptions  
- Adjusted compromise rates  
- New expected breaches  
- New financial exposure (ALE)  
- Risk reduction  
- Return on Investment (ROI)  

This file represents the **decision-making layer**, where controls are evaluated based on financial impact.

---

### 4. phase3_risk_matrix.csv

This dataset summarizes the final risk assessment across all phishing campaigns.

It includes:

- Risk classification (e.g., Critical, High)  
- Financial exposure per campaign  
- Priority levels  
- Recommended mitigation actions  

This file represents the **risk prioritization layer** used for executive decision-making.

---

### 5. phishing_risk_dashboard.xlsx

This file provides an integrated view of the entire analysis.

It contains:

- All datasets from Phase 1 to Phase 3  
- Pre-structured tables for analysis  
- Embedded charts for:
  - Financial exposure  
  - ROI comparison  

The dashboard is designed to support:

- Interactive exploration of results  
- Executive-level presentation  
- Validation of calculations across all phases  

---

## Data Flow (Important)

The datasets follow a logical flow:

Phase 1 (Behavioral Metrics)  
→ Phase 2 (Risk Projection)  
→ Phase 2 (Control Evaluation)  
→ Phase 3 (Risk Assessment)

Each dataset builds on the previous one, ensuring full traceability of results.

---

## Purpose

These datasets ensure that the entire analysis is:

- Transparent  
- Reproducible  
- Verifiable  

All results presented in the documentation and visuals are directly derived from these files.

---

## Usage Guidance

- Use **phase1_phishing_metrics.csv** to understand user behavior  
- Use **phase2_risk_projection.csv** to see how risk scales across the organization  
- Use **phase2_control_analysis.csv** to evaluate security investments  
- Use **phase3_risk_matrix.csv** for final decision-making  
- Use **phishing_risk_dashboard.xlsx** for a complete, interactive overview  

---

## Note

All values in these datasets are aligned with the assumptions and calculations presented in the documentation.

They are intended for analytical demonstration and decision-support modeling within the context of this project.
