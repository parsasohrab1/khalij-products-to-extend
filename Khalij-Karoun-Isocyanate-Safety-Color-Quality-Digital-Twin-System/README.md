# Khalij-Karoun-Isocyanate-Safety-Color-Quality-Digital-Twin-System (Khalij-KISQ)

## Intelligent system for preventive warning of thermal runaway reactions in nitration/hydrogenation reactors and a virtual sensor of color and NCO percentage of TDI/MDI products — a dedicated product of Karoun Petrochemical Company

> This document is a **dedicated** product for Karoun Petrochemical Company — the first and only producer of isocyanates (TDI, MDI, PMI) in the Middle East. With a process chain completely different from the holding's other companies (aromatic nitration → hydrogenation → phosgenation), this company needs a dedicated product.

---

## 0. Understanding Karoun Petrochemical Company and the technical gap

**Sources:** [Persian Wikipedia — Karoun Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%DA%A9%D8%A7%D8%B1%D9%88%D9%86), [Official site krnpc.ir](https://krnpc.ir/)

### Products and Process Nature

| Feature | Value |
|---|---|
| Products | TDI (toluene diisocyanate), MDI (methylene diphenyl diisocyanate), PMDI grades |
| Position | First isocyanate producer in the Middle East |
| Established/inaugurated | 2002 (1381 SH) / March 2009 (Esfand 1387 SH) |
| Location | Bandar Imam Khomeini — site 2 of the Petrochemical Special Economic Zone |

**Technical process chain (basis of product design):** TDI/MDI production involves two different critical stages:
1. **Aromatic nitration** (toluene→dinitrotoluene for TDI; or aniline-formaldehyde condensation for MDA) and then **hydrogenation** to amine — strongly exothermic reactions with a real risk of **thermal runaway (Thermal Runaway)** and explosion of nitro-aromatic compounds (one of the most dangerous classes of reactions in the chemical industry).
2. **Phosgenation** of the amine (TDA/MDA) to isocyanate — as in Khuzestan, phosgene is used but the downstream product and chemistry are completely different (color and NCO percentage of the final product, not polymer molecular weight).

### Technical gap relative to holding products 1 to 4 and the Khuzestan product

| Product | Why it is not enough for Karoun |
|---|---|
| Holding products 1-4 | None covers aromatic nitration/hydrogenation reaction or the isocyanate product |
| Khuzestan dedicated product (Khalij-KPSI) | Focuses on **phosgene mass balance** (leakage) and **polymer** quality (PC molecular weight); Karoun's main risk is **thermal runaway of the nitration reaction** (completely different safety physics: exothermic explosion versus gas leak) and its target quality is the **color/NCO% of the isocyanate monomer**, not polymer molecular weight |

**Conclusion:** Karoun needs a dedicated "nitration thermal runaway" safety layer that is not covered in any other holding product (including the Khuzestan product), together with a color/NCO quality virtual sensor specific to isocyanate.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | AIChE study — *A Machine Learning Tool for Thermal Runaway Prediction of Chemical Reactors* (Random Forest) | General model for batch/fixed-bed reactors; not connected to the specific TDI/MDI nitration-hydrogenation-phosgenation chain | Adaptation and direct connection to the real TDI/MDI production process chain with industrial DCS data |
| 2 | **Soft-sensor development for product quality estimation... in industrial MDI production** (ScienceDirect, research) | Only a quality virtual sensor (time delay/feature selection); lacks a thermal runaway safety layer and a formal patent | Combining a thermal runaway safety layer + quality virtual sensor in a single patented industrial product |
| 3 | **US 10,189,945** – *Method for producing light-coloured TDI-polyisocyanates* | Chemical/process solution for improving color (formulation change); a material approach, not real-time software prediction | Real-time prediction and predictive control of product color from existing process parameters, without changing the formulation |
| 4 | **US 8,748,655** – *Process for preparing light-coloured isocyanates of the diphenylmethane series* | Similar to above, a fixed process/chemical solution | Complementary: a software layer for prediction and early color warning for each production batch |

### Core Patentable Claim

> **"A chain digital twin system for isocyanate that, for the first time, combines preventive thermal runaway warning in aromatic nitration/hydrogenation reactors (based on the trend of the heat generation-removal rate difference) with a real-time virtual sensor of color (Hazen/APHA) and NCO percentage of the final phosgenation product, in an integrated risk-quality model with a closed feedback loop."**

---

## 2. SRS Document – Dedicated product of Karoun Petrochemical

### 2-1. Introduction
**Purpose:** Increase the process safety of nitration/hydrogenation reactions through preventive thermal runaway warning, and guarantee the color/NCO quality of TDI/MDI products through a real-time virtual sensor.

**Field challenges:**
- Aromatic nitration reactions are strongly exothermic, and insufficient control can lead to thermal runaway (Thermal Runaway) and a catastrophic accident.
- The color of the TDI/MDI product (Hazen/APHA index) and NCO percentage are usually measured with laboratory delay, whereas color quality directly affects the product's sale value (especially for rigid foam and coating applications).

**Scope:** Karoun complex, Bandar Imam site 2; connection to the DCS of the nitration, hydrogenation and phosgenation units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous temperature/pressure/heat-removal-rate data of nitration and hydrogenation reactors | Critical (HSE) |
| R-GEN-02 | Reception of process data of the phosgenation unit (phosgene/amine ratio, temperature, residence time) | High |
| R-GEN-03 | Separate safety-quality dashboard similar to the structure of the Khuzestan product but with this company's dedicated models | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-SAFE-01 | Preventive thermal runaway warning from the trend of heat generation/removal rate difference in nitration/hydrogenation reactors | **Isocyanate-chain-specific thermal runaway prediction (main innovation)** |
| FR-QUAL-01 | Real-time virtual sensor of color (Hazen/APHA) and NCO percentage of the phosgenation product | Color/NCO quality virtual sensor without waiting for the laboratory |
| FR-CHAIN-01 | Combined risk-quality model that estimates the effect of first-stage safety deviation on final product quality | **Integrated risk-quality model (main innovation)** |
| FR-ALERT-01 | Tiered HSE alert with critical priority separate from the quality alert | Dual recommender |
| FR-LOOP-01 | Recording real laboratory results and safety events for model retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-SAFE-01 | Thermal runaway alert delay | Less than 2 seconds (critical) |
| NFR-PER-01 | Product color prediction accuracy (MAPE) | Less than 10% |
| NFR-AVAIL-01 | Availability of the safety module | 99.99% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Nitration/       ││ Runaway Early- ││ Color/NCO Soft-  │
│Hydrogenation/   ││ Warning Model  ││ Sensor +         │
│Phosgenation     ││ (Random Forest)││ Risk-Quality Link│
│Ingestion        ││                ││                  │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/nitration-safety-ingestion/` | Connection to the nitration/hydrogenation DCS with critical message priority |
| `services/runaway-early-warning/` | Random Forest/LSTM thermal runaway warning model |
| `services/color-nco-soft-sensor/` | Color and NCO virtual sensor |
| `shared/` | Reuse of products 1-4 and the safety pattern of the Khuzestan product |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(seconds=i*2) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# 1. Nitration reactor - heat generation rate versus heat removal
heat_generation_rate_kw = 850 + 40 * np.sin(t * 0.2) + np.random.normal(0, 10, NUM_RECORDS)
heat_removal_rate_kw = 860 + 35 * np.sin(t * 0.2 - 0.1) + np.random.normal(0, 12, NUM_RECORDS)
heat_balance_deviation_kw = heat_generation_rate_kw - heat_removal_rate_kw
# injection of several simulated events of increased thermal runaway risk
risk_idx = np.random.choice(NUM_RECORDS, size=12, replace=False)
heat_balance_deviation_kw[risk_idx] += np.random.uniform(30, 70, size=12)
reactor_temp_c = 55 + 0.05 * heat_balance_deviation_kw + np.random.normal(0, 1, NUM_RECORDS)

# 2. Phosgenation unit
phosgene_amine_molar_ratio = 3.2 + 0.1 * np.sin(t * 0.1) + np.random.normal(0, 0.03, NUM_RECORDS)
phosgenation_temp_c = 130 + 4 * np.sin(t * 0.08) + np.random.normal(0, 0.8, NUM_RECORDS)

# 3. Final product quality
product_color_hazen = 25 + 3 * (phosgene_amine_molar_ratio - 3.2) * 10 + 0.5 * (phosgenation_temp_c - 130) + np.random.normal(0, 2, NUM_RECORDS)
product_color_hazen = np.clip(product_color_hazen, 10, 80)
nco_content_percent = 33.5 - 0.02 * (product_color_hazen - 25) + np.random.normal(0, 0.15, NUM_RECORDS)

# 4. Labels
thermal_runaway_risk = (heat_balance_deviation_kw > 25).astype(int)
off_spec_color_risk = (product_color_hazen > 40).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'heat_generation_rate_kw': np.round(heat_generation_rate_kw, 2),
    'heat_removal_rate_kw': np.round(heat_removal_rate_kw, 2),
    'heat_balance_deviation_kw': np.round(heat_balance_deviation_kw, 2),
    'reactor_temp_c': np.round(reactor_temp_c, 2),
    'phosgene_amine_molar_ratio': np.round(phosgene_amine_molar_ratio, 3),
    'phosgenation_temp_c': np.round(phosgenation_temp_c, 2),
    'product_color_hazen': np.round(product_color_hazen, 1),
    'nco_content_percent': np.round(nco_content_percent, 3),
    'thermal_runaway_risk': thermal_runaway_risk,
    'off_spec_color_risk': off_spec_color_risk,
})

df.to_csv("karoun_isocyanate_safety_quality_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-KISQ | Approximate financial/safety impact |
| :--- | :--- | :--- | :--- |
| Nitration/hydrogenation reaction safety | Manual monitoring of operating parameters | Preventive warning from the thermal difference trend | Reduced risk of a thermal runaway/explosion accident — critical for the region's only isocyanate producer |
| TDI/MDI color quality | Laboratory measurement with delay | Real-time prediction and immediate phosgenation correction | Reduced waste/discounted sale of off-spec dark-colored products |

**Payback:** Given the catastrophic risk of thermal runaway and Karoun's exclusive position in the region's isocyanate production, this product is a simultaneous safety and economic priority.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Preventive nitration/hydrogenation thermal runaway warning model (first HSE priority) |
| 3 | Color/NCO virtual sensor for the phosgenation product |
| 4 | Integrated risk-quality model |
| 5 | Dashboard + operational pilot under HSE team supervision |

---

## 6. Summary of Patentable Innovations

1. **Preventive thermal runaway warning specific to the isocyanate nitration-hydrogenation chain**.
2. **Real-time virtual sensor of Hazen/APHA color and NCO% of the phosgenation product**.
3. **An integrated risk-quality model** linking the effect of first-stage safety deviation to final product quality.

---

## 7. References

- [Persian Wikipedia — Karoun Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%DA%A9%D8%A7%D8%B1%D9%88%D9%86)
- [Official site of Karoun Petrochemical](https://krnpc.ir/)
- [AIChE — A Machine Learning Tool for Thermal Runaway Prediction of Chemical Reactors](https://proceedings.aiche.org/conferences/aiche-annual-meeting/2020/proceeding/paper/314b-machine-learning-tool-thermal-runaway-prediction-chemical-reactors)
- [Soft-sensor development for product quality estimation in industrial MDI production — ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2666821125000481)
- [US10189945 — Method for producing light-coloured TDI-polyisocyanates](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/10189945)
- [US8748655 — Process for preparing light-coloured isocyanates of the diphenylmethane series](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/8748655)
- [Runaway Reaction Hazards in Processing Organic Nitro Compounds — ACS](https://pubs.acs.org/doi/abs/10.1021/op970035s)
