# public-policy-impact-evaluation-rct
Experimental causal inference protocol evaluating non-pharmacological health interventions for atopic dermatitis using stratified RCT, ITT/OLS, 2SLS instrumental variables (CACE/LATE), and scenario-based power analysis.
# Public Policy Impact Evaluation: Home Allergen Reduction Kits in Chronic Dermatitis

[![Status](https://img.shields.io/badge/Status-Completed-success)]()
[![Domain](https://img.shields.io/badge/Domain-Public%20Policy%20%7C%20Health%20Economics-darkblue)]()
[![Methodology](https://img.shields.io/badge/Methodology-Causal%20Inference%20%7C%20RCT%20%7C%202SLS-orange)]()

An experimental public policy impact evaluation protocol designed to assess whether providing standardized, non-pharmacological Allergen-Reduction Kits causally reduces flare frequency and clinical burden among adults diagnosed with Atopic Dermatitis (AD).

The framework establishes an experimental design combining stratified randomization, an Intent-to-Treat (ITT) econometric baseline, Instrumental Variables (2SLS) for non-compliance correction (CACE/LATE), and scenario-based statistical power modeling.

**Documentation:**
- **Full Research Proposal:** [Download Research Paper PDF](docs/Research_Proposal_Impact_Evaluation.pdf)
- **Project Presentation:** [Download Slides PDF](docs/Project_Presentation_Slides.pdf)

---

## Executive Summary and Policy Motivation

- **The Policy Problem:** Atopic dermatitis affects up to 8% of Italian adults, generating severe clinical and economic burdens via outpatient healthcare costs, topical steroid reliance, sleep disruption, and labor productivity loss. While indoor allergens (dust mites, airborne particulate) trigger chronic flare cycles, adoption of environmental preventive technologies remains hindered by information asymmetries and upfront financial constraints.
- **The Intervention:** Distribution of a standardized, low-cost preventive kit (260 EUR unit cost) containing certified anti-mite mattress/pillow encasings, bedroom HEPA air purifiers, hypoallergenic cleansers, and environmental protocol leaflets.
- **Experimental Strategy:** A 1:1 individually randomized controlled trial (RCT) with household-level clustering and pre-randomization stratification (baseline disease severity and environmental humidity/ventilation).
- **Addressing Attenuation Bias:** Incorporates an extensive pre-screening phase (N ≈ 1,000) excluding households already utilizing allergen-control tools, eliminating treatment contrast dilution.

---

## Theory of Change and Results Chain

```text
Inputs (157,680 EUR Budget, Staff, Standardized Kits)
        |
        v
Activities (Pre-screening Survey, Stratified 1:1 Randomization, Kit Delivery)
        |
        v
Outputs (Adoption of Encasings, Continuous HEPA Operation, Cleanser Routine)
        |
        v
Intermediate Outcomes (Lower Indoor Allergen Load, Fewer Monthly Flare Days)
        |
        v
Final Socio-Economic Impacts (Reduced Healthcare Utilization, Lower Absenteeism)
Econometric Strategy and Causal Identification
1. Intent-to-Treat (ITT) Effect
The primary policy-relevant estimand captures the average causal impact of being offered the intervention, irrespective of individual compliance:
Y_i = alpha + beta * T_i + gamma' * X_i + epsilon_i
Where:

Y_i: Clinical outcome (monthly flare count, EASI severity score).

T_i: Random treatment assignment (1 if kit offered, 0 if control).

X_i: Pre-registered baseline stratification covariates (severity, humidity/ventilation).

beta: Average Intent-to-Treat causal effect estimated via Ordinary Least Squares (OLS) with robust standard errors.
2. Imperfect Compliance: Complier Average Causal Effect (CACE / LATE)
To account for non-compliance where assigned individuals fail to maintain continuous protocol usage, treatment assignment (Z_i) serves as an exogenous instrument for actual physical kit adoption (D_i).
First Stage:   D_i = pi_0 + pi_1 * Z_i + v_i
Second Stage:  Y_i = alpha + beta * D_hat_i + epsilon_i
Under the monotonicity assumption, the 2SLS coefficient beta identifies the Local Average Treatment Effect (LATE), isolating the causal treatment effect strictly among compliers.

Statistical Power Analysis
The primary trial endpoint evaluates monthly flare counts modeled as count distributions. Power calculations specify a minimum clinically meaningful effect of -1 flare per month across three baseline variance scenarios (alpha = 0.05, Power = 0.80):
Scenario,Baseline Mean (mu),Standard Deviation (sigma),Required n (per Arm),Total Sample (N),Relative Impact
Scenario A (Low Variance),2.0 flares/mo,1.5,36,72,50% relative reduction
Scenario B (Moderate),3.0 flares/mo,2.0,63,126,33% relative reduction
Scenario C (Conservative),4.0 flares/mo,3.0,141,282,25% relative reduction

To safeguard statistical power under elevated empirical dispersion, the protocol adopts the conservative target of N = 282 participants (141 per treatment arm).

Operational Roadmap and Budgeting
Dec 2026                 Jan 2027                 Jun 2027                 Jan 2028
   |                        |                        |                        |
   v                        v                        v                        v
Baseline Screening      Randomization &           Midline Follow-Up       Endline Clinical
(N ≈ 1,000 Survey)      Kit Distribution          (6-Month Review)         Evaluation (12-Mo)

Budget Category,Allocated Cost (EUR),Scope and Operational Description
Kit Procurement,"73,320",Standardized kits for treatment cohort (282 x 260 EUR)
Recruitment & Screening,"18,000",Enumerator staffing for survey administration
Clinical Assessments,"14,000",Certified dermatological evaluators (blinded)
Logistics & Warehousing,"16,000","Storage, dispatch, and physical delivery"
Coordination & Tracking,"20,000","Participant tracking, reminders, and flare diaries"
Data Architecture & Analytics,"16,360","Database management, econometric evaluation"
Total Program Budget,"157,680",Comprehensive 12-month experimental trial
Key Visualizations
1. Theory of Change
Causal transmission mechanisms linking non-pharmacological environmental inputs to clinical outcomes:

2. Results Chain
Structural logic mapping inputs, activities, outputs, and socioeconomic endpoints:

3. Implementation Roadmap
12-month experimental milestone progression:

Repository Structure
├── docs/
│   ├── Research_Proposal_Impact_Evaluation.pdf
│   └── Project_Presentation_Slides.pdf
├── images/
│   ├── 01_theory_of_change.png
│   ├── 02_results_chain.png
│   └── 03_implementation_timeline.png
└── README.md
Author
Enio Hoxha - M.Sc. in Data Analytics for Economics and Management, Free University of Bozen-Bolzano
