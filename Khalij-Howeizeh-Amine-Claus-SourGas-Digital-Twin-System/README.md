# Khalij-Howeizeh-Amine-Claus-SourGas-Digital-Twin-System (Khalij-HACS)

## Intelligent system for predicting amine degradation/foaming from a four-source sour gas composition and real-time chain optimization of the Claus sulfur recovery unit — a dedicated product of Persian Gulf Howeizeh Gas Refining Company

> This document is a **dedicated** product for Persian Gulf Howeizeh Gas Refining Company — a sweetening refinery for associated sour gas from four oil fields (Yadavaran, Yaran, Azadegan, Darkhovin) with a final capacity of 500 million cubic feet/day. This product does not overlap with the dedicated Bidboland product (cryogenic NGL extraction), because the chemistry of Howeizeh (amine sweetening + Claus sulfur recovery on severely sour gas) is completely different.

---

## 0. Understanding Persian Gulf Howeizeh Gas Refining Company and the technical gap

**Sources:** [Persian Wikipedia — Persian Gulf Howeizeh Gas Refinery](https://fa.wikipedia.org/wiki/%D9%BE%D8%A7%D9%84%D8%A7%DB%8C%D8%B4%DA%AF%D8%A7%D9%87_%DA%AF%D8%A7%D8%B2_%DB%8C%D8%A7%D8%AF%D8%A2%D9%88%D8%B1%D8%A7%D9%86_%D8%AE%D9%84%DB%8C%D8%AC%E2%80%8C%D9%81%D8%A7%D8%B1%D8%B3)

### Products and Process Nature

| Feature | Value |
|---|---|
| Location | Jafir area, Howeizeh, Khuzestan |
| Feed | Associated sour gas from the Yadavaran, Yaran, Azadegan, Darkhovin fields (West Karoun fields — known for very sour/corrosive gas) |
| Final capacity (phase 2) | 500 million cubic feet/day |
| Phase 1 capacity | 250 million cubic feet/day |
| Product destination | 250 million cubic feet/day to the national gas network, 90 million cubic feet/day fuel for the West Karoun combined-cycle power plant |

**Technical process:** Sour gas from four different fields (with different and variable H₂S/CO₂ ratios) enters the **amine sweetening unit** (usually MDEA) that absorbs H₂S/CO₂; the H₂S-rich acid gas then goes to the **Claus sulfur recovery unit (SRU)**. Two key risks: (a) degradation/foaming of the amine solvent caused by variable feed contaminants, and (b) a decline in SRU efficiency if the H₂S concentration of the incoming acid gas fluctuates suddenly (which itself results from feed change/amine performance).

### Technical gap relative to the holding's other products

| Product | Why it is not enough for Howeizeh |
|---|---|
| Bidboland dedicated product | Completely different chemistry (cryogenic/NGL versus amine sweetening/Claus); Bidboland deals with hydrate and ethane recovery, not amine degradation or sulfur yield |
| No holding product | Has addressed the **amine → acid gas → Claus** chain in which a fluctuation in one unit directly affects the efficiency of the next unit |

**Conclusion:** Howeizeh needs a dedicated chain digital twin of amine-Claus that sees the variable four-source feed composition.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | *Effect of sour gas composition on amine-based gas sweetening: A hybrid simulation-machine learning model* (ScienceDirect, 2026) | Offline simulation-ML model for the effect of gas composition on sweetening; does not address real-time connection to a real DCS or to the downstream Claus unit | Real-time connection to real DCS data + direct link to downstream Claus yield |
| 2 | **US 7,951,347 B2** – *Sour-gas sweetening solutions and methods* | Chemical/solvent formulation solution for reducing foaming; a material approach, not software prediction | Complementary: a real-time foaming risk prediction software layer on the existing solvent |
| 3 | *Machine Learning-Enabled Prediction and Optimization of Sulfur Recovery Units* (Industry 4.0) | Independent Claus unit optimization assuming a given acid gas feed; not connected to the dynamic change of this feed caused by the upstream amine unit | **Direct link of upstream amine performance to downstream Claus optimization (main innovation)** |
| 4 | *Simulation and multi-objective optimization of Claus process* (ScienceDirect) | Offline optimization/simulation; not a real-time industrial system connected to real multi-source data | Conversion to a real-time industrial system with real four-source feed composition input |

### Core Patentable Claim

> **"A chain digital twin system of amine-Claus that, for the first time, infers the incoming sour gas composition from four different fields in real time, predicts the amine solvent degradation/foaming risk from this composition, and — by recognizing that a fluctuation in amine unit performance directly changes the concentration and flow of H₂S entering the Claus unit — predictively readjusts the Claus furnace air/feed ratio in real time to maintain sulfur recovery efficiency against this fluctuation."**

---

## 2. SRS Document – Dedicated product of Persian Gulf Howeizeh Gas Refining

### 2-1. Introduction
**Purpose:** Increase the stability and life of the amine solvent, and maintain Claus sulfur recovery efficiency against four-source feed composition fluctuation.

**Field challenges:**
- The variable sour gas composition from four different fields (with different H₂S/CO₂/contaminant ratios) causes unpredicted fluctuation in amine performance.
- A drop in amine absorption efficiency or foaming directly changes the H₂S concentration/flow entering Claus and reduces sulfur recovery efficiency (environmental risk and emission standard compliance).
- There is no tool that sees these two units as a chain.

**Scope:** Howeizeh complex; connection to the DCS of the amine sweetening and Claus units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous incoming gas composition data (H₂S, CO₂, contaminants) | High |
| R-GEN-02 | Reception of amine unit data (solvent concentration, tower temperature, pressure drop — a foaming indicator) | High |
| R-GEN-03 | Reception of Claus unit data (air/feed ratio, furnace temperature, sulfur recovery efficiency) | High |
| R-GEN-04 | Amine-Claus chain dashboard | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-SOURCE-01 | Real-time inference of the relative share of each of the four feed fields | Multi-field feed source inference |
| FR-AMINE-01 | Prediction of amine solvent degradation/foaming risk from feed composition and operating conditions | Dedicated degradation/foaming prediction |
| FR-CLAUS-01 | Predictive optimization of the Claus furnace air/feed ratio based on the predicted incoming H₂S fluctuation from the amine unit | **Amine-Claus chain link (main innovation)** |
| FR-ALERT-01 | Alert on the risk of sulfur yield loss/environmental non-compliance | Environmental compliance recommender |
| FR-LOOP-01 | Recording actual laboratory results and yield for retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Delay in readjusting the Claus air/feed ratio | Less than 3 minutes |
| NFR-PER-02 | Sulfur recovery yield prediction accuracy | Less than 5% error |
| NFR-AVAIL-01 | System availability | 99.9% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Amine/Claus       ││ Source Infer + ││ Claus Air/Feed   │
│Ingestion (DCS)   ││ Amine Degrade  ││ Predictive       │
│                  ││ Model          ││ Optimizer        │
└──────┬───────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬─────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/amine-claus-ingestion/` | Connection to the DCS of the amine and Claus units |
| `services/amine-degradation-model/` | Degradation/foaming prediction |
| `services/claus-chain-optimizer/` | Chain predictive optimizer |
| `shared/` | Reuse of products 1-4 and the Bidboland product |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(minutes=i) for i in range(NUM_RECORDS)]

fields = ["Yadavaran", "Yaran", "Azadegan", "Darkhovin"]
field_shift = np.random.choice(range(4), size=NUM_RECORDS // 250 + 1)
current_field_idx = np.repeat(field_shift, 250)[:NUM_RECORDS]

base_h2s = np.array([3.2, 2.5, 4.0, 2.0])[current_field_idx]  # H2S mole percent
base_co2 = np.array([1.8, 2.2, 1.5, 2.5])[current_field_idx]

feed_h2s_percent = base_h2s + np.random.normal(0, 0.15, NUM_RECORDS)
feed_co2_percent = base_co2 + np.random.normal(0, 0.1, NUM_RECORDS)

# amine unit
amine_loading_mol_ratio = 0.45 + 0.02 * feed_h2s_percent + np.random.normal(0, 0.02, NUM_RECORDS)
foaming_index = 0.5 + 0.3 * (feed_h2s_percent - 3) + np.random.normal(0, 0.2, NUM_RECORDS)
foaming_index = np.clip(foaming_index, 0, 5)

# acid gas to Claus
acid_gas_h2s_percent = 88 - 2 * foaming_index + np.random.normal(0, 1.5, NUM_RECORDS)
acid_gas_flow_nm3h = 4200 + 150 * (feed_h2s_percent - 3) + np.random.normal(0, 80, NUM_RECORDS)

# Claus unit
air_feed_ratio = 2.05 + 0.01 * (acid_gas_h2s_percent - 88) + np.random.normal(0, 0.02, NUM_RECORDS)
sulfur_recovery_efficiency_percent = 98.5 - 0.5 * np.abs(air_feed_ratio - 2.05) * 10 - 0.3 * foaming_index + np.random.normal(0, 0.3, NUM_RECORDS)
sulfur_recovery_efficiency_percent = np.clip(sulfur_recovery_efficiency_percent, 90, 99.5)

# labels
foaming_critical_alert = (foaming_index > 3).astype(int)
sru_efficiency_risk = (sulfur_recovery_efficiency_percent < 96).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'current_field': [fields[i] for i in current_field_idx],
    'feed_h2s_percent': np.round(feed_h2s_percent, 3),
    'feed_co2_percent': np.round(feed_co2_percent, 3),
    'amine_loading_mol_ratio': np.round(amine_loading_mol_ratio, 3),
    'foaming_index': np.round(foaming_index, 3),
    'acid_gas_h2s_percent': np.round(acid_gas_h2s_percent, 2),
    'acid_gas_flow_nm3h': np.round(acid_gas_flow_nm3h, 1),
    'air_feed_ratio': np.round(air_feed_ratio, 3),
    'sulfur_recovery_efficiency_percent': np.round(sulfur_recovery_efficiency_percent, 2),
    'foaming_critical_alert': foaming_critical_alert,
    'sru_efficiency_risk': sru_efficiency_risk,
})

df.to_csv("howeizeh_amine_claus_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-HACS | Approximate financial/environmental impact |
| :--- | :--- | :--- | :--- |
| Amine solvent life/stability | Reactive after foaming occurs | Preventive prediction from feed composition | Reduced replacement solvent consumption and unplanned shutdowns |
| Claus sulfur recovery yield | Fixed air/feed ratio, reactive to H₂S fluctuation | Real-time predictive readjustment | Maintaining environmental compliance and reducing SO₂ emissions at the scale of 500 million cubic feet/day |

**Payback:** Given the strict environmental requirements for sulfur emissions and the large scale (500 million cubic feet/day), the stability of Claus yield has significant regulatory and financial value.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Four-field feed source inference model |
| 3 | Amine degradation/foaming prediction model |
| 4 | Claus chain predictive optimizer |
| 5 | Dashboard + operational pilot |

---

## 6. Summary of Patentable Innovations

1. **Real-time inference of the feed share of four different oil fields** and its effect on amine performance.
2. **Direct chain linkage of upstream amine performance to predictive optimization of the downstream Claus furnace**.
3. **Preventive prediction of amine foaming/degradation risk** from the actual feed composition.

---

## 7. References

- [Persian Wikipedia — Yadavaran Persian Gulf Gas Refinery (Howeizeh)](https://fa.wikipedia.org/wiki/%D9%BE%D8%A7%D9%84%D8%A7%DB%8C%D8%B4%DA%AF%D8%A7%D9%87_%DA%AF%D8%A7%D8%B2_%DB%8C%D8%A7%D8%AF%D8%A2%D9%88%D8%B1%D8%A7%D9%86_%D8%AE%D9%84%DB%8C%D8%AC%E2%80%8C%D9%81%D8%A7%D8%B1%D8%B3)
- [Effect of sour gas composition on amine-based gas sweetening: A hybrid simulation-machine learning model — ScienceDirect](https://www.sciencedirect.com/science/article/pii/S259000562600281X)
- [US7951347B2 — Sour-gas sweetening solutions and methods](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/7951347)
- [Machine Learning-Enabled Prediction and Optimization of Sulfur Recovery Units](https://doi.org/10.3390/materproc2024017006)
- [Simulation and multi-objective optimization of Claus process of sulfur recovery unit — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S2213343723017086)
