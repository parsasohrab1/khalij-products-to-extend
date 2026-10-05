# Khalij-Bidboland-MultiSource-Feed-Adaptive-NGL-Optimization-System (Khalij-BMFA)

## Intelligent system for real-time inference of the three-source feed composition (Pazanan/Gachsaran/Bibi Hakimeh), adaptive turboexpander/demethanizer optimization, and hydrate risk prediction — a dedicated product of Persian Gulf Bidboland Gas Refining Company

> This document is a **dedicated** product for Persian Gulf Bidboland Gas Refining Company — the largest gas gathering and processing facility in the history of Iran's oil industry. Unlike petrochemical units with relatively constant feedstock, Bidboland receives feed from **three different oil fields with variable associated-gas composition** — a challenge no other holding product has addressed.

---

## 0. Understanding Persian Gulf Bidboland Gas Refining Company and the technical gap

**Sources:** [Persian Wikipedia — Bidboland Gas Refinery](https://fa.wikipedia.org/wiki/%D9%BE%D8%A7%D9%84%D8%A7%DB%8C%D8%B4%DA%AF%D8%A7%D9%87_%DA%AF%D8%A7%D8%B2_%D8%A8%DB%8C%D8%AF%D8%A8%D9%84%D9%86%D8%AF), [Official site pgbidboland.ir](https://www.pgbidboland.ir/fa/introduction)

### Products and Capacity

| Product | Annual capacity |
|---|---|
| Methane | 10.4 million tons |
| Ethane | 1.5 million tons (destination: Mahshahr Petrochemical Special Zone — cracker feed for companies such as Arvand/Bandar Imam/Karoun) |
| Propane | 1 million tons |
| Butane | 0.5 million tons |
| Gas condensate | 0.6 million tons |
| Acid gas | 0.9 million tons |

**Unique feature:** The refinery's feed is supplied from the associated gas of **three different oil fields** (Pazanan, Gachsaran, Bibi Hakimeh) through NGL units 900, 1000, 1200 and 1300. The associated-gas composition of each field (the ratio of methane/ethane/propane/water/CO₂/H₂S) is inherently different and varies over time (reservoir pressure decline, change in the produced-water ratio).

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Bidboland |
|---|---|
| All petrochemical holding products | Designed for units with **relatively constant feed** (naphtha/pure natural gas); they do not address the challenge of **continuously changing feed composition from three different sources** and its effect on ethane/propane recovery and hydrate risk |
| No holding product | Covers the **cryogenic turboexpander** process (cryogenic expansion, very low temperature, hydrate formation risk) |

**Conclusion:** Bidboland needs a system that infers the variable three-source feed composition in real time and adaptively readjusts the turboexpander/demethanizer operating point (not fixed based on design).

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | *Operation optimization of a cryogenic NGL recovery unit using deep learning based surrogate modeling* (ScienceDirect) | Optimization for **a single feed of known composition**; does not address continuous change of source/composition of feed from multiple fields | **Real-time adaptive** optimization that recomputes with every change of the three-source feed composition |
| 2 | **US 6,755,965 B2** – *Ethane extraction process for a hydrocarbon gas stream* | Fixed engineered process for ethane extraction; process approach, not adaptive software | Adaptive software layer on top of the existing process infrastructure |
| 3 | **US 6,907,752 B2** – *Cryogenic liquid natural gas recovery process* | Engineered process for one type of feed; does not address three-source composition and dynamic change | Generalization to a multi-source scenario with real-time inference of each source's share |
| 4 | ML studies on hydrate formation prediction (Random Forest, XGBoost) | General models for predicting the hydrate formation temperature from gas composition; do not address a real-time connection with operational optimization of the turboexpander | Direct connection of hydrate prediction to the real-time turboexpander adjustment decision |

### Core Patentable Claim

> **"A Multi-Source Feed-Adaptive Optimization system that, for the first time, infers in real time the relative share of three associated-gas feed sources (Pazanan/Gachsaran/Bibi Hakimeh) from the instantaneous composition pattern of the incoming gas, continuously readjusts the turboexpander/demethanizer operating point to maximize ethane/propane recovery, and simultaneously predicts and prevents the hydrate formation risk caused by a sudden change in feed composition."**

---

## 2. SRS Document – Dedicated product of Persian Gulf Bidboland Gas Refining

### 2-1. Introduction
**Purpose:** Maximize ethane/propane recovery (strategic feedstock of the Mahshahr petrochemicals) through continuous adaptive optimization matched to changes in the three-source feed composition, and prevent hydrate risk.

**Field challenges:**
- The fixed turboexpander/demethanizer operating point designed for an average feed composition is not optimal with the actual change in each field's share.
- A sudden change in the water/CO₂ ratio in the feed (especially from fields with pressure decline) increases the risk of hydrate formation and blockage in cold sections.
- The ethane produced is the direct feed of the Mahshahr petrochemical crackers; fluctuation of ethane recovery directly affects the holding's petrochemical supply chain.

**Scope:** Bidboland complex; connection to the DCS of NGL units 900/1000/1200/1300.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous incoming gas composition data of each NGL unit | High |
| R-GEN-02 | Reception of temperature/pressure data of the cryogenic sections (turboexpander, demethanizer) | High |
| R-GEN-03 | Dashboard "Feed source share + ethane/propane recovery + hydrate risk" | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-SOURCE-01 | Real-time inference of the relative share of each of the three feed sources from the incoming gas composition pattern | **Real-time feed source inference (main innovation)** |
| FR-OPT-01 | Adaptive readjustment of the turboexpander/demethanizer operating point to maximize ethane/propane recovery | **Multi-source adaptive optimization (main innovation)** |
| FR-HYDRATE-01 | Prediction of hydrate formation risk from feed composition and operating conditions | Hydrate prediction linked to the operational decision |
| FR-ALERT-01 | Preventive hydrate risk alert with action recommendation (inhibitor injection/temperature adjustment) | Preventive action recommender |
| FR-LOOP-01 | Recording actual product recovery results and hydrate events for retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Operating point readjustment delay after a feed composition change | Less than 2 minutes |
| NFR-PER-02 | Accuracy of hydrate risk prediction | Less than 10% error |
| NFR-AVAIL-01 | System availability | 99.9% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│NGL 900/1000/    ││ Source Inference││ Adaptive        │
│1200/1300        ││ + Hydrate Risk  ││ Turboexpander   │
│Ingestion         ││ Model           ││ Optimizer       │
└──────┬───────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬─────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/ngl-units-ingestion/` | DCS connection of the four NGL units |
| `services/source-inference-hydrate-model/` | Feed source inference + hydrate prediction |
| `services/adaptive-turboexpander-optimizer/` | Adaptive optimizer |
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

# relative share of the three feed sources (time-varying as random steps)
source_shift = np.random.choice([0, 1, 2], size=NUM_RECORDS // 300 + 1)  # 0=Pazanan 1=Gachsaran 2=Bibi Hakimeh
current_source = np.repeat(source_shift, 300)[:NUM_RECORDS]

base_methane = np.array([78, 82, 75])[current_source]
base_ethane = np.array([8, 6, 10])[current_source]
base_water_ppm = np.array([40, 25, 60])[current_source]

feed_methane_percent = base_methane + np.random.normal(0, 1, NUM_RECORDS)
feed_ethane_percent = base_ethane + np.random.normal(0, 0.5, NUM_RECORDS)
feed_water_ppm = base_water_ppm + np.random.normal(0, 3, NUM_RECORDS)

# turboexpander temperature/pressure
turboexpander_outlet_temp_c = -95 + 0.1 * (feed_ethane_percent - 8) + np.random.normal(0, 1, NUM_RECORDS)
demethanizer_pressure_bar = 28 + np.random.normal(0, 0.5, NUM_RECORDS)

# ethane recovery (dependent on matching the operating point to feed composition)
ethane_recovery_percent = 92 - 3 * np.abs(feed_ethane_percent - 8) / 8 + np.random.normal(0, 1, NUM_RECORDS)
ethane_recovery_percent = np.clip(ethane_recovery_percent, 75, 97)

# hydrate risk (increases with high water and very low temperature)
hydrate_risk_index = 0.02 * feed_water_ppm - 0.05 * (turboexpander_outlet_temp_c + 95) + np.random.normal(0, 0.5, NUM_RECORDS)
hydrate_risk_index = np.clip(hydrate_risk_index, 0, 10)

hydrate_critical_alert = (hydrate_risk_index > 6).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'current_source': current_source,
    'feed_methane_percent': np.round(feed_methane_percent, 2),
    'feed_ethane_percent': np.round(feed_ethane_percent, 2),
    'feed_water_ppm': np.round(feed_water_ppm, 1),
    'turboexpander_outlet_temp_c': np.round(turboexpander_outlet_temp_c, 2),
    'demethanizer_pressure_bar': np.round(demethanizer_pressure_bar, 2),
    'ethane_recovery_percent': np.round(ethane_recovery_percent, 2),
    'hydrate_risk_index': np.round(hydrate_risk_index, 3),
    'hydrate_critical_alert': hydrate_critical_alert,
})

df.to_csv("bidboland_multisource_ngl_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-BMFA | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Ethane recovery | Fixed design operating point, suboptimal with feed source change | Real-time adaptive readjustment | Increased ethane recovery on the 1.5 million ton capacity — direct feed of the Mahshahr crackers |
| Hydrate risk | Reactive after a blockage occurs | Preventive prediction | Preventing emergency shutdown of the cryogenic section |

**Payback:** Given Bidboland's role as the largest ethane supplier of the Mahshahr petrochemical chain, even a 1-2% improvement in ethane recovery has a large chain effect on the entire holding.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Real-time feed source share inference model |
| 3 | Hydrate risk prediction model |
| 4 | Adaptive turboexpander/demethanizer optimizer |
| 5 | Dashboard + operational pilot on one of the NGL units |

---

## 6. Summary of Patentable Innovations

1. **Real-time inference of the relative feed share from three different oil field sources** from the incoming gas composition pattern.
2. **Continuous adaptive optimization of the turboexpander/demethanizer operating point** matched to feed change (not a fixed design point).
3. **Hydrate risk prediction and prevention linked directly to the real-time operational decision**.

---

## 7. References

- [Persian Wikipedia — Bidboland Gas Refinery](https://fa.wikipedia.org/wiki/%D9%BE%D8%A7%D9%84%D8%A7%DB%8C%D8%B4%DA%AF%D8%A7%D9%87_%DA%AF%D8%A7%D8%B2_%D8%A8%DB%8C%D8%AF%D8%A8%D9%84%D9%86%D8%AF)
- [Official site of Persian Gulf Bidboland Gas Refining](https://www.pgbidboland.ir/fa/introduction)
- [Operation optimization of a cryogenic NGL recovery unit using deep learning based surrogate modeling — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0098135420300636)
- [US6755965B2 — Ethane extraction process for a hydrocarbon gas stream](https://patents.google.com/patent/US6755965)
- [US6907752B2 — Cryogenic liquid natural gas recovery process](https://patents.google.com/patent/US6907752B2/en)
- [Application of Machine Learning in Gas-Hydrate Formation and Trendline Prediction](https://www.researchgate.net/publication/355368091_Application_of_Machine_Learning_in_Gas-Hydrate_Formation_and_Trendline_Prediction)
