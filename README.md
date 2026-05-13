# Analyzing Market Dynamics and Revitalizing Brand Strategy for Market Cannibalization of an Injectable Anesthesia Drug

**BIA 810 — Healthcare Data & Advanced Analytics | Stevens Institute of Technology | Spring 2026**
**Team 2 — Rx Five**

---

## Overview

This project investigates a failed cannibalization strategy in the injectable anesthesia pharmaceutical market. A newly launched variant drug (Product 2 / midazolam) was intended to absorb market share from the company's own declining market leader (Product 1 / ketorolac). Instead, a competitor drug (Product 3 / fentanyl) captured the majority of that shifting share, leaving Product 2 shrinking alongside Product 1.

Using Medicare CCLF claims data spanning 2016 to 2018, the team conducts a full commercial analytics workup — market share trends, prescriber productivity, territory performance, patient demographics, diagnosis specialty, and writer acquisition and retention — to diagnose the root cause and deliver prioritized, data-driven recommendations for the sales and marketing team.

---

## Team

| Name | Role |
|---|---|
| Puja Dey | Market Dynamics Analyst |
| Bhuvan Chandra Alladi | Writer Productivity & Territory Specialist |
| Aakarsh Reddy Thumma | Patient & Specialty Insights Analyst |
| Chetan Raghavendra Deshpande | Strategic Recommendations Lead |
| Hsin-Yu Shih | Data Strategy & Future Analytics Lead |

**Professor:** Sanjiv Koshal

---

## Market Basket

| Product | Procedure Code | Generic Name | Role |
|---|---|---|---|
| Product 1 | J1885 | Ketorolac tromethamine | Market Leader (declining) |
| Product 2 | J2250 | Midazolam hydrochloride | Variant Brand (our new drug) |
| Product 3 | J3010 | Fentanyl citrate | Main Competitor |
| Product 4 | J2704 | Propofol | Alternative Competitor |

---

## Dataset

- **Source:** Medicare CCLF Claims Data (5 compressed CSV files, ~1M raw records)
- **Analytics-Ready Dataset:** 28,368 records after filtering for the 4 market basket procedure codes
- **Supplementary Files:**
  - HCP Demographics Data
  - Patient Demographics Data
  - Zip to Territory Mapping Data
  - Diagnosis Code Mapping Data (ICD-10 first character to specialty)

---

## Project Structure

```
BIA810-Healthcare_Anesthesia-Market-Analysis/
│
├── input_datasets/
│   ├── claims_part1.csv.gz ... claims_part5.csv.gz
│   ├── HCP_demographics_data.csv
│   ├── Patient_demographics_data.csv
│   ├── Zip_to_Territory_Mapping.csv
│   └── Diagnosis_Code_Mapping.csv
│
├── BIA810_final.ipynb          # Main Jupyter notebook (all data prep + analysis)
└── README.md
```

---

## Key Business Questions & Findings

### KBQ 1 — Market Dynamics & Competitive Landscape

**Share of Claims, Patients, and HCP Writers (2016–2018)**
- Product 1 lost 14.9 points of claim share; Product 3 gained 14.5 points — capturing almost all of it
- Product 2 shrunk 4.6 points instead of growing — failed cannibalization
- Product 2's writer share fell from 23.9% to 15.5%; absolute writer count dropped from 285 to 226

**Writer Productivity**
- Product 3 claims per writer nearly doubled from 1.77 to 3.45 (+95%)
- Product 2 claims per writer declined from 1.51 to 1.34 (-11%)

**Top 5 Declining Territories for Product 2 (2017 to 2018)**
- St. Louis, MO: -73% | Phoenix, AZ: -70% | LA-San Diego, CA: -58%
- New York, NY: -58% | Minneapolis, MN: -53%
- Product 3 grew in all 5 of these territories simultaneously

---

### KBQ 2 — Key Market Drivers

**Diagnosis Specialty**
- Circulatory System diagnoses account for 48% of all claims — 4x the next specialty
- Top 2 specialties (Circulatory + Factors Influencing Health) account for 60% of claims

**HCP Writer Specialty**
- Anesthesiology leads with 228 unique writers, nearly 3x Cardiology (86)
- Product 3 is gaining share uniformly across all 5 specialties simultaneously — rules out a targeting failure

**Patient Age**
- 61-70 age group is the largest segment: 779 unique patients, 21.2% of all claims
- Patients aged 61+ account for 52.7% of unique patients and 54.4% of all claims

**New Writer Acquisition**
- Product 2 new writers collapsed 69% from 111 to 34 between 2017 and 2018
- Total market writer base grew from 1,193 to 1,458 — this is competitive displacement, not saturation
- Product 4 attracted 140 new writers in 2018, the highest of any brand

**Continuing Writers**
- Product 3 continuing writers grew 47% (297 to 436) vs Product 2's 16% (165 to 192)
- By 2018, Product 3 had 2.3x more continuing writers than Product 2

---

### KBQ 3 — Strategic Recommendations

| Priority | Action | Evidence |
|---|---|---|
| CRITICAL | Territory Win-Back — Top 5 Geographies | KBQ 1C territory charts |
| CRITICAL | Co-Pay / Payer Assistance | KBQ 1B patients per writer + KBQ 1A patient share |
| HIGH | Targeted NPP Digital — New Writer Acquisition | KBQ 1A writer share + KBQ 2B new writers |
| MEDIUM | Brand Repositioning — Claims per Writer Growth | KBQ 1B claims per writer |
| MEDIUM | HCP Multi-Specialty Engagement Program | KBQ 2A specialty charts |
| MEDIUM | Patient Segment Focus — 61-70 Age Cohort | KBQ 2A age distribution |

---

### KBQ 4 — Data Gaps & Future Analytics

**Missing from Claims Data**
- Quantity dispensed and dosage per claim — cannot calculate true drug volume
- Secondary diagnoses and full comorbidity profiles — cannot assess clinical protocol differences
- Reimbursement, allowed amounts, and place-of-service codes — cannot assess pricing disadvantage

**External Datasets Needed**
- Xponent / NPA data — full-payer prescription data beyond Medicare
- CRM / Calls data — field rep engagement by territory to isolate coverage gaps
- NPP data — promotional reach and HCP response by channel and geography

---

## Tools & Technologies

- **Python** — Pandas, Matplotlib, Seaborn, Jupyter
- **Data Processing** — Multi-source dataset merging, ICD-10 mapping, ZIP code standardization
- **Visualization** — Stacked bar charts, line graphs, clustered bar charts, pie charts

---

## How to Run

1. Clone the repository
```bash
git clone https://github.com/Jasmine140412/BIA810-Healthcare_Anesthesia-Market-Analysis.git
cd BIA810-Healthcare_Anesthesia-Market-Analysis
```

2. Set up the environment
```bash
uv init
uv add pandas numpy matplotlib seaborn jupyter
```

3. Place the input datasets in the `input_datasets/` folder

4. Launch Jupyter and run the notebook
```bash
jupyter notebook BIA810_final.ipynb
```

5. Run all cells in order — data prep in Section 0, analyses in Sections 1 through 4

---

## Key Insight

Product 3 is winning uniformly across every HCP specialty, patient age group, and geography simultaneously. This rules out a targeting failure and points to a systemic prescriber retention and market access problem. The single highest-ROI immediate action is territory win-back in the 5 key geographies, followed by co-pay assistance to address access friction and a coordinated multi-specialty engagement strategy to stop new writer displacement.
