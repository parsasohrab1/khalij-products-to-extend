# Khalij-Khuzestan-Phosgene-Safety-Polymer-Grade-Intelligence-System (Khalij-KPSI)

## Intelligent system for predicting phosgene leakage/mass imbalance, polycarbonate molecular weight virtual sensor, and grade-changeover optimization among 14 epoxy resin grades — a dedicated product of Khuzestan Petrochemical Company

> This document is a **dedicated** product for Khuzestan Petrochemical Company (KZPC) — the only producer of polycarbonate and engineering epoxy resin in the Middle East. Unlike most of the holding's companies that have a "usual petrochemical process", Khuzestan is the only holding company working with **phosgene gas (extremely toxic)** as a process intermediate — requiring a product completely different from the other holding members.

---

## 0. Understanding Khuzestan Petrochemical Company (based on a study of the official site) and the technical gap

**Sources:** [KZPC official site — Introduction](https://kzpc.ir/introduction/), [Plastic Industry Monthly — Khuzestan polycarbonate potential](https://pimw.ir/polycarbonate-potential-of-khuzestan-petrochemical-complex/)

### Products and process units

| Product | Capacity | Description |
|---|---|---|
| Polycarbonate (PC) | ~25,000 tons/year (~2 thousand tons/month) | The first and only engineering polycarbonate producer in the Middle East |
| Solid epoxy resin | 5,000 tons/year | 14 different grades |
| Liquid epoxy resin | 5,000 tons/year | Several grades (such as E01, E06 SPL) |
| Bisphenol A (BPA) | Intermediate product | Direct feed of PC and epoxy resin |
| Sodium hypochlorite (bleach) | 2,000 tons/year | By-product |

**Sensitive intermediate units (per the official site):** carbon monoxide gas production → CO separation → **phosgene (carbonyl chloride) production** → chlorine gas treatment → bleach. The reaction of phosgene with BPA is the core of polycarbonate and some epoxy resin production.

The technology and license are European, and the products' applications are in telecommunications, electronics, construction, aerospace, medical and safety industries — meaning **much stricter quality requirements** than the commodity polymers (PE/PP/PVC) produced by the holding's other companies.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Khuzestan |
|---|---|
| Products 1, 3, 4 | None considered **phosgene** gas (acute toxicity, an internationally controlled substance similar to a chemical weapon) as a process intermediate; a completely dedicated Process Safety layer is required |
| Product 4 (asset/catalyst monitoring) | Designed for gas-phase polymerization catalyst deterioration (PE/PP); polycarbonate quality control based on **molecular weight/melt viscosity** and changeover among 14 epoxy resin grades is a completely different problem (specialty product quality, not equipment health) |
| No holding product | Addresses frequent changeover among several product grades with strict technical specifications (which causes transition-period waste) |

**Conclusion:** Khuzestan needs a product that (a) makes phosgene process safety predictive with machine learning and (b) controls and optimizes the quality/grade of specialty products (PC and 14 epoxy grades) in real time.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 7,442,835** – *Process and apparatus for the production of phosgene* | Equipment for monitoring phosgene leakage into the cooling circuit; merely detecting a leak after it occurs, not preventive prediction from the mass-balance trend | An ML model that warns of CO/Cl₂/phosgene mass imbalance trend **before** an actual leak |
| 2 | **WO2020033316A1** – *Leak detection with artificial intelligence* | General for oil/gas/water pipelines; does not address phosgene-specific chemistry or reaction with BPA in the polycarbonate reactor | Adapted for the phosgene-BPA reactor with combined input from reactor DCS + gas sensors |
| 3 | Molecular weight/melt viscosity soft-sensor studies for polypropylene/PLA (Bayesian Inference, RFE) | For commodity polyolefins; does not address polycarbonate (phosgene-BPA reaction, different sensitivity to temperature/residence time) or epoxy resin | A dedicated virtual sensor of PC molecular weight/epoxy viscosity with input from the phosgene-BPA reactor |
| 4 | General literature on multi-product production sequence optimization (Scheduling) in process industries | Usually aims to minimize changeover time, not simultaneously minimize quality waste of the transition period between precise engineering grades | Sequence optimization of 14 epoxy grades + PC grades aiming to simultaneously minimize transition time and quality waste |

### Core Patentable Claim

> **"An integrated Safety-Quality Digital Twin system that, for the first time, combines preventive prediction of the mass imbalance in the phosgene chain (CO→phosgene→reaction with BPA) — before an actual leak occurs — with real-time virtual sensors of polycarbonate molecular weight and epoxy resin viscosity and a changeover sequence optimizer among several engineering grades, in a single decision loop."**

The preventive (not merely diagnostic) prediction of phosgene leakage based on the mass-balance trend had no precedent in the patent literature found.

---

## 2. SRS Document – Dedicated product of Khuzestan Petrochemical

### 2-1. Introduction
**Purpose:** Increase the process safety of the phosgene unit through preventive mass-imbalance prediction, and increase the quality/yield of polycarbonate and epoxy resin production through virtual sensors and grade changeover sequence optimization.

**Field challenges:**
- Phosgene is a highly toxic and dangerous gas; current detection systems are usually reactive (after a leak is detected by a gas sensor), not preventive from the reactor mass-balance trend.
- The molecular weight of polycarbonate and the viscosity of epoxy resin are usually measured with laboratory delay (not real time), which causes a significant amount of off-spec product.
- Changeover among 14 epoxy resin grades and the different PC grades is usually scheduled based on operator experience, not systematic optimization.

**Scope:** Khuzestan complex; connection to the DCS of the CO/phosgene/BPA/PC/epoxy units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous flow/concentration data of CO, chlorine and phosgene in the production and consumption units | Critical (HSE) |
| R-GEN-02 | Reception of process data of the polycarbonate reactor (temperature, pressure, residence time, BPA/phosgene molar ratio) | High |
| R-GEN-03 | Safety-quality dashboard with separate HSE (critical priority) and quality (operational priority) alerts | High |
| R-GEN-04 | Connection to the company's existing Process Safety Management (PSM) system | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-SAFE-01 | Preventive prediction of the phosgene chain mass imbalance (CO/Cl₂ input versus consumption in the BPA reaction) with an alert before the leak threshold | **Preventive phosgene process safety prediction (main innovation)** |
| FR-QUAL-01 | Real-time virtual sensor of polycarbonate molecular weight/melt flow index from process parameters (without waiting for the laboratory result) | Dedicated polycarbonate quality virtual sensor |
| FR-QUAL-02 | Virtual sensor of resin viscosity and epoxy percentage for each of the 14 grades | Multi-grade virtual sensor |
| FR-SCHED-01 | Grade changeover (epoxy/PC) sequence optimization to simultaneously minimize transition time and amount of off-spec product | **Multi-grade sequence optimization with dual objective of time+waste (main innovation)** |
| FR-ALERT-01 | Tiered HSE alert (critical/warning/monitoring) separate from the quality alert | Dual safety-quality recommender |
| FR-LOOP-01 | Recording actual laboratory results for continuous retraining of the virtual sensor | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-SAFE-01 | Delay of the phosgene mass-imbalance alert | Less than 3 seconds (critical) |
| NFR-PER-01 | PC molecular weight virtual sensor accuracy (MAPE) | Less than 8% |
| NFR-AVAIL-01 | Availability of the safety module | 99.99% (higher than other modules due to the HSE nature) |
| NFR-SEC-01 | AES-256 encryption + RBAC with access restricted to the HSE team for critical alerts | Mandatory |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Phosgene/PC/     ││ Safety Mass-   ││ Quality Soft-    │
│Epoxy Ingestion  ││ Balance Model  ││ Sensor + Grade   │
│(DCS + gas       ││ (predictive    ││ Sequencing       │
│ sensors)        ││ leak precursor)││ Optimizer        │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
                                  │
                           ┌────────────┐
                           │   MLflow   │
                           └────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/phosgene-safety-ingestion/` | Connection to the DCS + gas sensors of the phosgene unit with critical message priority |
| `services/mass-balance-safety-model/` | Preventive mass-imbalance prediction model |
| `services/quality-soft-sensor/` | Virtual sensor of PC molecular weight and epoxy viscosity |
| `services/grade-sequencing-optimizer/` | Grade changeover sequence optimizer |
| `shared/` | Reuse of products 1-4 |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(seconds=i) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# 1. Phosgene chain mass balance (mol/s input versus reaction consumption)
co_feed_rate = 100 + 3 * np.sin(t * 0.2) + np.random.normal(0, 1, NUM_RECORDS)
phosgene_produced_rate = 0.97 * co_feed_rate + np.random.normal(0, 0.8, NUM_RECORDS)
phosgene_consumed_reaction_rate = 0.96 * phosgene_produced_rate + np.random.normal(0, 0.6, NUM_RECORDS)
mass_balance_deviation_percent = 100 * (phosgene_produced_rate - phosgene_consumed_reaction_rate) / phosgene_produced_rate
# injection of several artificial imbalance events for training the alert model
anomaly_idx = np.random.choice(NUM_RECORDS, size=15, replace=False)
mass_balance_deviation_percent[anomaly_idx] += np.random.uniform(3, 8, size=15)

# 2. Polycarbonate reactor
reactor_temp_c = 30 + 2 * np.sin(t * 0.15) + np.random.normal(0, 0.5, NUM_RECORDS)
bpa_phosgene_molar_ratio = 1.02 + 0.01 * np.sin(t * 0.1) + np.random.normal(0, 0.005, NUM_RECORDS)
residence_time_min = 45 + np.random.normal(0, 2, NUM_RECORDS)

# 3. Product quality (virtual sensor)
pc_molecular_weight = 30000 + 1500 * (bpa_phosgene_molar_ratio - 1.02) * 100 - 50 * (reactor_temp_c - 30) + np.random.normal(0, 300, NUM_RECORDS)
epoxy_viscosity_cp = 12000 + 200 * np.sin(t * 0.05) + np.random.normal(0, 150, NUM_RECORDS)

# 4. Labels
phosgene_safety_alert = (np.abs(mass_balance_deviation_percent) > 2.5).astype(int)
off_spec_pc_risk = (np.abs(pc_molecular_weight - 30000) > 2000).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'co_feed_rate_mols': np.round(co_feed_rate, 2),
    'phosgene_produced_rate_mols': np.round(phosgene_produced_rate, 2),
    'phosgene_consumed_reaction_rate_mols': np.round(phosgene_consumed_reaction_rate, 2),
    'mass_balance_deviation_percent': np.round(mass_balance_deviation_percent, 3),
    'reactor_temp_c': np.round(reactor_temp_c, 2),
    'bpa_phosgene_molar_ratio': np.round(bpa_phosgene_molar_ratio, 4),
    'residence_time_min': np.round(residence_time_min, 2),
    'pc_molecular_weight': np.round(pc_molecular_weight, 0).astype(int),
    'epoxy_viscosity_cp': np.round(epoxy_viscosity_cp, 1),
    'phosgene_safety_alert': phosgene_safety_alert,
    'off_spec_pc_risk': off_spec_pc_risk,
})

df.to_csv("kzpc_safety_quality_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-KPSI | Approximate financial/safety impact |
| :--- | :--- | :--- | :--- |
| Phosgene process safety | Leak detection after occurrence with a gas sensor | Preventive alert from the mass-imbalance trend | Reduced risk of a catastrophic HSE accident (highly toxic material) — directly unpriceable value but critical |
| Polycarbonate quality | Laboratory measurement with delay, possibility of producing a significant amount of off-spec product | Real-time virtual sensor + immediate correction | Reduced waste on the 25 thousand tons/year PC capacity with the high value of the engineering product |
| Epoxy grade changeover | Experience-based, significant transition-period waste among 14 grades | Systematic sequence optimization | Reduced transition-period waste and an increased rate of on-time customer order delivery |

**Payback:** Given the high HSE risk nature of phosgene and the high value of specialty engineering products (PC/epoxy), this product has both a safety dimension (irreplaceable) and an economic dimension (reducing waste of expensive product), which makes the investment justification very strong.

---

## 5. Proposed Evolution Roadmap (Phase 1-6)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator + shared Kafka/TimescaleDB connection |
| 2 | Preventive phosgene mass-imbalance prediction model (first priority due to HSE) |
| 3 | Polycarbonate molecular weight virtual sensor |
| 4 | Viscosity/quality virtual sensor of 14 epoxy grades |
| 5 | Grade changeover sequence optimizer |
| 6 | Safety-quality dashboard + operational pilot under direct supervision of the HSE team |

---

## 6. Summary of Patentable Innovations

1. **Preventive (not merely diagnostic) prediction of phosgene leakage/mass imbalance** based on the reaction chain mass-balance trend.
2. **Real-time virtual sensor of polycarbonate molecular weight** with direct input from the phosgene-BPA reactor parameters.
3. **Changeover sequence optimization among 14 epoxy resin grades** with a dual objective of minimizing time and quality waste.

---

## 7. References

- [Official site of Khuzestan Petrochemical — Introduction](https://kzpc.ir/introduction/)
- [Review of the polycarbonate potential of Khuzestan Petrochemical — Plastic Industry Monthly](https://pimw.ir/polycarbonate-potential-of-khuzestan-petrochemical-complex/)
- [US7442835 — Process and apparatus for the production of phosgene](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/7442835)
- [WO2020033316A1 — Leak detection with artificial intelligence](https://patents.google.com/patent/WO2020033316A1/en)
- [A novel Bayesian inference soft sensor for industrial polypropylene melt index prediction](https://onlinelibrary.wiley.com/doi/abs/10.1002/app.45384)
- [Machine learning enhanced grey box soft sensor for melt viscosity prediction](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11830027/)
