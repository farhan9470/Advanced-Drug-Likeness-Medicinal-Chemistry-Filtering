# Advanced Drug-Likeness & Medicinal Chemistry Filtering Pipeline Using Python & RDKit

## Project Overview

Drug discovery involves evaluating thousands of chemical compounds before selecting candidates for experimental testing. Early-stage computational filtering helps eliminate compounds with undesirable physicochemical properties or problematic chemical substructures, significantly reducing time and cost.

In this project, an end-to-end **cheminformatics screening pipeline** was developed using **Python** and **RDKit** to assess the drug-likeness and structural quality of compounds retrieved from the **ChEMBL database**.

Unlike a basic Lipinski analysis, this project integrates multiple medicinal chemistry filters—including **Lipinski**, **Veber**, **Ghose**, **Egan**, **PAINS**, and **Brenk**—into a unified workflow. A custom **Quality Score** was also developed to rank compounds based on their overall suitability for further drug discovery studies.

---

# Objectives

The primary objectives of this project were to:

- Retrieve molecular structures from the ChEMBL database
- Calculate molecular descriptors using RDKit
- Evaluate compounds using multiple drug-likeness rules
- Screen compounds for problematic chemical substructures
- Rank compounds using an integrated Quality Score
- Visualize screening results using scientific plots
- Demonstrate a practical medicinal chemistry workflow used during early drug discovery

---

# Workflow

```
ChEMBL API
      │
      ▼
Retrieve Molecular Structures
      │
      ▼
SMILES Validation
      │
      ▼
RDKit Descriptor Calculation
      │
      ▼
Drug-Likeness Filtering
(Lipinski • Veber • Ghose • Egan)
      │
      ▼
Medicinal Chemistry Screening
(PAINS • Brenk)
      │
      ▼
Quality Score Calculation
      │
      ▼
Quality Classification
      │
      ▼
Statistical Analysis
      │
      ▼
Visualization
      │
      ▼
Compound Ranking
```

---

# Dataset

| Description | Value |
|------------|------:|
| Retrieved from ChEMBL | 1000 compounds |
| Successfully processed | 969 compounds |

---

# Molecular Descriptors Calculated

The following physicochemical descriptors were calculated using **RDKit**:

- Molecular Weight (MW)
- LogP
- Hydrogen Bond Donors (HBD)
- Hydrogen Bond Acceptors (HBA)
- Topological Polar Surface Area (TPSA)
- Rotatable Bonds
- Ring Count
- Atom Count

---

# Drug-Likeness Filters Applied

## Lipinski Rule of Five

Evaluates oral drug-likeness using:

- Molecular Weight ≤ 500 Da
- LogP ≤ 5
- HBD ≤ 5
- HBA ≤ 10

---

## Veber Rule

Evaluates molecular flexibility and polarity:

- TPSA ≤ 140 Å²
- Rotatable Bonds ≤ 10

---

## Ghose Filter

Evaluates:

- Molecular Weight
- LogP
- Atom Count

to identify compounds occupying classical drug-like chemical space.

---

## Egan Rule

Evaluates oral absorption using:

- TPSA ≤ 131 Å²
- LogP ≤ 5.88

---

# Medicinal Chemistry Filters

## PAINS Screening

PAINS (Pan-Assay Interference Compounds) identify molecular substructures known to produce false-positive biological assay results.

Removing PAINS compounds helps improve the reliability of downstream biological screening.

---

## Brenk Structural Alerts

The Brenk filter detects structural fragments associated with:

- Toxicity
- Chemical instability
- Poor pharmacokinetic properties
- Synthetic difficulties

These alerts help prioritize chemically attractive compounds.

---

# Drug-Likeness Results

| Filter | Pass | Fail |
|---------|-----:|-----:|
| Lipinski | 769 | 200 |
| Veber | 818 | 151 |
| Ghose | 489 | 480 |
| Egan | 796 | 173 |

---

# PAINS Screening

| Category | Count |
|----------|------:|
| Clean | 924 |
| PAINS | 45 |

---

# Brenk Screening

| Category | Count |
|----------|------:|
| Clean | 523 |
| Alert | 446 |

---

# Compound Quality Classification

A custom Quality Score was calculated by combining six independent screening criteria:

- Lipinski
- Veber
- Ghose
- Egan
- PAINS
- Brenk

Each passed criterion contributed one point.

Quality Classes:

| Score | Classification |
|-------:|---------------|
| 6 | Excellent |
| 5 | Good |
| 3–4 | Moderate |
| 0–2 | Poor |

---

# Quality Distribution

| Quality Class | Count |
|--------------|------:|
| Good | 362 |
| Excellent | 269 |
| Moderate | 186 |
| Poor | 152 |

---

# Key Scientific Findings

### Drug-Like Chemical Space

Most compounds satisfied multiple drug-likeness criteria, indicating that the ChEMBL dataset largely occupies chemically relevant drug-like space.

---

### Physicochemical Quality

Approximately 79% of compounds satisfied Lipinski's Rule of Five, suggesting favorable physicochemical properties for oral drug candidates.

---

### Structural Alerts

Only a small proportion of compounds contained PAINS alerts, while Brenk screening identified a larger number of compounds containing potentially undesirable structural fragments.

This demonstrates why multiple medicinal chemistry filters should be used rather than relying solely on Lipinski's Rule.

---

### Overall Compound Quality

Most compounds achieved Quality Scores of 5 or 6, indicating that the majority satisfied several independent drug-likeness and medicinal chemistry criteria simultaneously.

---

# Visualizations

The project includes:

- Drug-Likeness Filter Comparison
- Drug-Likeness Pass Percentage
- Descriptor Correlation Heatmap
- PAINS Screening Results
- Quality Score Distribution

---

# Technologies Used

- Python
- Pandas
- NumPy
- RDKit
- Matplotlib
- Seaborn
- ChEMBL API

---

# Skills Demonstrated

- API Data Retrieval
- Data Cleaning
- Molecular Descriptor Calculation
- Drug-Likeness Evaluation
- Medicinal Chemistry Filtering
- PAINS Screening
- Brenk Structural Alert Analysis
- Scientific Data Visualization
- Statistical Analysis
- Compound Prioritization
- Python Programming
- RDKit

---

# Repository Structure

```
Advanced-Drug-Likeness-Medicinal-Chemistry-Filtering/

│
├── notebook/
├── data/
├── results/
├── README.md
├── requirements.txt
└── LICENSE
```

---

# Future Improvements

Potential future extensions include:

- Chemical Space Visualization (PCA / UMAP)
- Molecular Fingerprint Analysis
- Similarity Searching
- Molecular Clustering
- Bioactivity Analysis
- Structure–Activity Relationship (SAR) Exploration
- Machine Learning-Based Compound Prioritization

---

# Conclusion

This project demonstrates a complete cheminformatics workflow for early-stage compound screening by integrating physicochemical descriptor calculation, multiple drug-likeness rules, medicinal chemistry structural alert filters, statistical analysis, and compound quality scoring. The workflow illustrates how computational methods can prioritize chemically attractive molecules before experimental validation and reflects practices commonly used during the early phases of drug discovery.
