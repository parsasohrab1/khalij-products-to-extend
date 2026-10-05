# Khalij-BuAliSina-Aromatics-Catalyst-Adsorbent-Digital-Twin-System (Khalij-BACAT)

## Intelligent system for predicting platinum reforming catalyst (CCR) activity, paraxylene separation molecular-sieve adsorbent (Parex/Isomar) deterioration, and simultaneous yield/purity optimization of aromatic products — a dedicated product of Bu Ali Sina Petrochemical Company

> This document is a **dedicated** product for Bu Ali Sina Petrochemical Company (BSPC), Iran's third aromatics complex with 7 licensed process units from AXENS, KRUPP UHDE and SINOPEC. This product uses the holding's common technical pattern but extends the data and model scope to the unique physics of **platinum reforming catalyst + paraxylene separation molecular-sieve adsorbent**, which is not covered by any of products 1 to 4.

---

## 0. Understanding Bu Ali Sina Petrochemical Company (based on a study of the official site) and the technical gap

**Sources:** [BSPC official site](https://bspc.ir/), [BSPC Products (EN)](https://bspc.ir/en/products/), [PGPIC — Bu Ali Sina](https://pgpic.ir/en/Subsidiaries/Production-Companies/Bou-Ali-Sina-Petrochemical-Company)

### Products and process units

| Feature | Value |
|---|---|
| Location | Imam Khomeini Port Special Economic Zone, 36 hectares |
| Total capacity | About 1.1 to 1.74 million tons/year |
| Paraxylene (PX) | 400,000 tons/year |
| Orthoxylene (OX) | 30,000 tons/year |
| Benzene | 180,000 tons/year (feed for styrene monomer and LAB) |
| Naphtha/LPG/raffinate | Up to 499,000 tons/year of by-products |
| Technology licensors | AXENS, KRUPP UHDE (Germany), SINOPEC (China) — 7 process units |
| Third aromatics project of Iran | Operating since 2004 |

The technical core of this complex is the **continuous catalytic reforming (CCR) unit** with platinum catalyst (for converting naphtha to aromatics) and the **paraxylene adsorptive separation unit (Parex/Isomar)** with zeolite adsorbent — two physical/chemical phenomena completely different from the polymerization reactors or cracking furnaces covered in the other holding products.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Bu Ali Sina |
|---|---|
| Product 1 (reactor process optimization) | Designed for a cracking/polymerization reactor; it does not cover the physics of catalytic reforming (gradual coking on platinum in the continuous catalyst-movement cycle between reactors) |
| Product 4 (asset monitoring + catalyst deterioration) | Catalyst deterioration in product 4 is modeled for the **PE/PP polymerization catalyst** (gradual deterioration over weeks) and assigned to Karoun; the CCR catalyst behaves completely differently (continuous, rotating regeneration every few hours, not periodic replacement) — and the **Parex molecular-sieve adsorbent is not covered in any product at all** |
| Product 3 (energy/carbon) | Does not identify the decrease in PX separation efficiency due to adsorbent deterioration as the cause of the solvent recovery process becoming energy-intensive |

**Conclusion:** Bu Ali Sina needs a dedicated digital twin that sees the continuous platinum CCR catalyst regeneration cycle and the long-term deterioration trend of the Parex zeolite adsorbent simultaneously with the yield/purity of the final products (PX/OX/benzene).

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 11,975,316** – *Methods and reforming systems for re-dispersing platinum on reforming catalyst* | Chemical/hardware method of re-dispersing platinum on the catalyst after regeneration; lacks a learning-based prediction layer for optimal regeneration timing | ML prediction of the catalyst activity trend to optimize regeneration cycle timing, not just improving the regeneration process itself |
| 2 | Predictive Modeling of CCR Reforming (Wiley/ACS – Energy & Fuels) | Offline simulation/kinetic modeling for process design and optimization; not a real-time industrial system connected to a real DCS | Converting the kinetic model into a real-time prediction service connected to real CCR data + operational recommendation |
| 3 | **US 8,778,823** – *Feed additives for CCR reforming* | Chemical additive to reduce coking; a material approach, not software/predictive | Complementary: instead of changing the feed material, predict and optimize regeneration timing based on real performance data |
| 4 | Paraxylene adsorptive separation patents (US5495061, US5849981, US6706938, etc.) | All focus on adsorbent and solvent (Desorbent) materials/formulation; none presents a machine-learning model for predicting adsorbent performance degradation over time | **A learning-based model for predicting PX purity/recovery loss caused by gradual deterioration of the adsorbent bed (a completely empty gap in the patent literature found)** |

### Core Patentable Claim

> **"An integrated digital twin system for aromatics units that, for the first time, combines (a) prediction of the activity/coking trend of the platinum catalyst in the continuous CCR regeneration cycle and (b) prediction of the gradual deterioration of the adsorption capacity of the zeolite adsorbent bed of the Parex/Isomar unit in a single model, and estimates and optimizes in real time the joint effect of both on the final yield and purity of paraxylene/benzene."**

Part (b) — learning-based prediction of Parex adsorbent deterioration — had no precedent in any source found and on its own is a strong Independent Claim.

---

## 2. SRS Document – Dedicated product of Bu Ali Sina Petrochemical

### 2-1. Introduction
**Purpose:** Continuous health monitoring of the CCR catalyst and Parex adsorbent, prediction of the optimal regeneration/replacement time, and optimization of the yield and purity of final aromatic products.

**Field challenges:**
- Coking of the platinum catalyst during continuous circulation between CCR reactors which, if regeneration timing is unsuitable, reduces the aromatics yield (PX/OX/benzene).
- Gradual deterioration of the adsorption capacity of the Parex zeolite adsorbent bed, which causes a drop in PX purity (below polymer-grade specification) or an increase in solvent (Desorbent) recovery energy consumption.
- No tool that sees the combined effect of these two phenomena on the final output (PX 400 thousand tons/year) simultaneously.

**Scope:** Bu Ali Sina complex, Mahshahr; connection to the DCS of the CCR, Parex/Isomar and fractionation units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous temperature/pressure/inlet-outlet composition data of CCR reactors in the regeneration cycle | High |
| R-GEN-02 | Reception of pressure drop, solvent flow and output purity data of the Parex unit | High |
| R-GEN-03 | "Catalyst + adsorbent" health dashboard with an integrated view of the effect on PX/OX/benzene yield | High |
| R-GEN-04 | Connection to the laboratory quality system (online/offline PX purity) | Medium |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-CCR-01 | Prediction of the activity/coking trend of the platinum catalyst in each CCR reactor with a confidence interval | Regeneration cycle prediction by trend learning rather than a fixed sequence |
| FR-PAREX-01 | Prediction of the deterioration of the adsorption capacity of the Parex adsorbent bed from the trend of PX purity/recovery loss | **Learning-based model of zeolite adsorbent deterioration (main innovation)** |
| FR-YIELD-01 | Real-time estimation of PX/OX/benzene yield and purity with simultaneous input of catalyst and adsorbent state | **Integrated model of the joint effect of catalyst+adsorbent on the final product (main innovation)** |
| FR-OPT-01 | Optimization of catalyst regeneration timing and adsorbent recovery/replacement cycle to maximize annual yield | Joint scheduling of two interdependent maintenance events |
| FR-ALERT-01 | Tiered alert with prediction of the financial impact of quality degradation on the polymer-grade sales contract | Action recommender with commercial impact |
| FR-LOOP-01 | Recording the actual result of each regeneration/adsorbent replacement for model retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | CCR/Parex data processing delay | Less than 10 seconds |
| NFR-PER-02 | PX purity prediction accuracy (MAPE) | Less than 10% |
| NFR-AVAIL-01 | System availability | 99.9% |
| NFR-SEC-01 | AES-256 encryption + RBAC for CCR/Parex/quality-control operations | Mandatory |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│CCR/Parex        ││ Catalyst/      ││ Yield-Purity     │
│Ingestion (DCS,  ││ Adsorbent Twin ││ Optimization     │
│lab QC feed)     ││ (LSTM decay)   ││ (schedule sync)  │
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
| `services/ccr-parex-ingestion/` | DCS connection of the CCR and Parex/Isomar units + laboratory QC system |
| `services/catalyst-adsorbent-twin/` | Catalyst coking model + adsorbent deterioration model |
| `services/yield-purity-optimization/` | Joint regeneration/replacement scheduling for maximum yield |
| `shared/` | Reuse of products 1-4 |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(minutes=i) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# 1. CCR catalyst - activity loss between regeneration cycles (sawtooth)
cycle_position = (np.arange(NUM_RECORDS) % 500) / 500  # one regeneration cycle every 500 records
catalyst_activity_percent = 98 - 6 * cycle_position + np.random.normal(0, 0.5, NUM_RECORDS)
reactor_delta_t_c = 15 + 3 * cycle_position + np.random.normal(0, 0.4, NUM_RECORDS)

# 2. Parex adsorbent - long-term deterioration (slow downward trend over the whole period)
adsorbent_capacity_percent = 100 - 0.0008 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.3, NUM_RECORDS)
adsorbent_capacity_percent = np.clip(adsorbent_capacity_percent, 82, 100)
desorbent_ratio = 1.05 + 0.0003 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.02, NUM_RECORDS)

# 3. Quality and yield of the final product
px_purity_percent = 99.7 - 0.03 * (100 - adsorbent_capacity_percent) - 0.01 * (100 - catalyst_activity_percent) + np.random.normal(0, 0.05, NUM_RECORDS)
px_purity_percent = np.clip(px_purity_percent, 97.5, 99.9)
aromatics_yield_percent = 62 - 0.08 * (100 - catalyst_activity_percent) + np.random.normal(0, 0.4, NUM_RECORDS)

# 4. Labels
needs_regen_24h = (catalyst_activity_percent < 93).astype(int)
adsorbent_replace_flag = (adsorbent_capacity_percent < 88).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'catalyst_activity_percent': np.round(catalyst_activity_percent, 2),
    'reactor_delta_t_c': np.round(reactor_delta_t_c, 2),
    'adsorbent_capacity_percent': np.round(adsorbent_capacity_percent, 3),
    'desorbent_ratio': np.round(desorbent_ratio, 3),
    'px_purity_percent': np.round(px_purity_percent, 3),
    'aromatics_yield_percent': np.round(aromatics_yield_percent, 2),
    'needs_regen_24h': needs_regen_24h,
    'adsorbent_replace_flag': adsorbent_replace_flag,
})

df.to_csv("bspc_aromatics_catalyst_adsorbent_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-BACAT | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| CCR catalyst regeneration timing | Fixed cycle based on operator experience | Predictive based on the real activity trend | Increased aromatics yield and reduced energy consumed by premature/late regeneration |
| Parex adsorbent deterioration | Usually not identified until a noticeable drop in PX purity or a sharp rise in solvent consumption | Early prediction with optimal replacement planning | Preventing sale of PX below polymer-grade specification (risk of returns/customer penalty) on 400 thousand tons/year of PX |
| Overall aromatics yield | Yield fluctuation due to lack of coordination of the timing of two maintenance events | Coordinated optimization | A multi-percent increase in annual effective yield |

**Payback:** Given the high value of polymer-grade PX (direct PTA feed), preventing even a few days of substandard production or one unplanned Parex shutdown offsets the implementation cost during the pilot phase.

---

## 5. Proposed Evolution Roadmap (Phase 1-6)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator + shared Kafka/TimescaleDB connection |
| 2 | CCR catalyst coking prediction model |
| 3 | Parex adsorbent deterioration prediction model |
| 4 | Integrated PX-OX-benzene yield/purity model |
| 5 | Joint regeneration/replacement scheduling optimizer |
| 6 | Management dashboard + operational pilot on one real CCR reactor and Parex bed |

---

## 6. Summary of Patentable Innovations

1. **A learning-based model for predicting deterioration of the Parex zeolite adsorbent** (a completely empty gap in the patent record found).
2. **Combining CCR catalyst and Parex adsorbent prediction in one integrated model of the effect on final yield/purity**.
3. **Coordinated scheduling of two interdependent maintenance events** (catalyst regeneration and adsorbent replacement) to maximize annual yield.

---

## 7. References

- [Official site of Bu Ali Sina Petrochemical](https://bspc.ir/)
- [BSPC — Products (EN)](https://bspc.ir/en/products/)
- [PGPIC — Bou Ali Sina Petrochemical Company](https://pgpic.ir/en/Subsidiaries/Production-Companies/Bou-Ali-Sina-Petrochemical-Company)
- [US11975316 — Methods and reforming systems for re-dispersing platinum on reforming catalyst](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11975316)
- [US8778823 — Feed additives for CCR reforming](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/8778823)
- [Predictive Modeling of Continuous Catalyst Regeneration (CCR) Reforming Process — Wiley](https://onlinelibrary.wiley.com/doi/10.1002/9783527813391.ch5)
- [US5495061A — Adsorptive separation of para-xylene with high boiling desorbents](https://patents.google.com/patent/US5495061)
- [US6706938B2 — Adsorptive separation process for recovery of para-xylene](https://patents.google.com/patent/US6706938B2/ko)
