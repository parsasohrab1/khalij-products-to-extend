# Khalij-Hengam-Ammonia-Urea-Corrosion-Biuret-Digital-Twin-System (Khalij-HAUC)

## Intelligent system for predicting the stress-corrosion cracking (SCC) risk of the urea reactor, biuret virtual sensor, and dual-objective temperature/residence-time optimization to simultaneously minimize corrosion risk and biuret — a dedicated product of Hengam Petrochemical Company

> This document is a **dedicated** product for Hengam Petrochemical Company (phase 2, Assaluyeh) — the first ammonia-urea complex in this project's list. The ammonia-urea process chain (ammonia synthesis with an iron catalyst + urea synthesis in a severely corrosive carbamate environment) is completely different from the holding's other olefin/aromatics petrochemical companies.

---

## 0. Understanding Hengam Petrochemical Company and the technical gap

**Sources:** [PGPIC — Hengam Petrochemical](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D9%87%D9%86%DA%AF%D8%A7%D9%85)

### Products and Process Nature

| Feature | Value |
|---|---|
| Ammonia | 726,000 tons/year (Haldor Topsoe license) |
| Urea | 1,155,000 tons/year (Saipem/Snamprogetti license — CO₂ stripping process) |
| Location | Pars Energy Special Economic Zone, phase 2, Assaluyeh — 25.47 hectares |
| Investment | 800 million euros |

**Critical process physics:** The urea synthesis reactor operates at high temperature (~180-210 degrees Celsius) and very high pressure (~140-250 bar) with an **ammonium carbamate** environment, which is one of the most corrosive industrial environments for austenitic stainless steel and has been known since the 1970s as a source of stress corrosion cracking (SCC) accidents. At the same time, higher temperature is required to reduce the **biuret** content (an impurity toxic to some plants, which must stay below ~1%) — meaning **reducing biuret and increasing corrosion risk usually go in the same direction**, a real physical trade-off.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Hengam |
|---|---|
| All products 1-4 and previous dedicated products | None covers the ammonia-urea chain, the corrosive carbamate environment, or biuret quality; this is the holding's first product in the chemical fertilizer field |

**Conclusion:** Hengam needs a dedicated digital twin that quantitatively models the physical trade-off between corrosion risk and biuret quality.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | *Stress Corrosion Cracking in Ammonia Urea Synthesis — Corrosion of Austenitic Stainless Steel* (classic industry reference, 1971) | Historical metallurgical analysis; lacks a real-time learning-based prediction model | Converting classical metallurgical knowledge into a real-time ML model with real DCS data |
| 2 | *Machine Learning for modeling intergranular SCC of stainless steels in light water reactors* (Nature — npj Materials Degradation) | Nuclear industry domain (pressurized water); corrosion chemistry completely different from ammonium carbamate | The first adaptation of ML SCC prediction methods to the ammonium carbamate environment of the fertilizer industry |
| 3 | ML studies on predicting ammonia synthesis catalyst activity (ScienceDirect, JPC) | For design/discovery of a new catalyst (research); not operational monitoring of a real plant | Real-time operational monitoring of the existing catalyst with real industrial data |
| 4 | Biuret analysis/urea quality literature | Mainly focuses on biuret analytical chemistry, not real-time plant-level prediction | Real-time biuret virtual sensor + direct connection to the corrosion risk model |

### Core Patentable Claim

> **"A Dual-Objective Digital Twin system that, for the first time, combines real-time prediction of the stress corrosion cracking (SCC) risk of the urea reactor in an ammonium carbamate environment with a real-time virtual sensor of biuret content and — considering the inherent physical trade-off between the two (higher temperature: less biuret but more corrosion risk) — proposes the optimal temperature/pressure/residence-time operating point to minimize both risks simultaneously."**

---

## 2. SRS Document – Dedicated product of Hengam Petrochemical

### 2-1. Introduction
**Purpose:** Increase urea reactor safety by predicting SCC risk, and guarantee product quality (biuret below the threshold) by intelligently managing the temperature/quality/corrosion trade-off.

**Field challenges:**
- Urea reactor SCC risk is usually managed with periodic inspection (not continuous monitoring).
- Reducing biuret requires higher temperature which increases corrosion risk — the operational decision is usually made conservatively and suboptimally.
- The activity of the iron ammonia synthesis catalyst declines over time and affects the N₂:H₂ ratio entering urea.

**Scope:** Hengam complex, Assaluyeh; connection to the DCS of the ammonia and urea synthesis units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous temperature/pressure/composition data of the urea reactor | Critical (HSE) |
| R-GEN-02 | Reception of ammonia catalyst activity data and N₂:H₂ ratio | High |
| R-GEN-03 | Dual-objective "corrosion-quality" dashboard with the proposed operating point | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-SCC-01 | Real-time prediction of urea reactor SCC risk from the trend of temperature/pressure/carbamate concentration | Real-time SCC prediction specific to the fertilizer industry |
| FR-BIURET-01 | Real-time virtual sensor of biuret content from temperature/residence time/NH₃:CO₂ ratio parameters | Biuret quality virtual sensor |
| FR-TRADEOFF-01 | Proposing the optimal temperature/pressure/residence-time operating point to minimize SCC and biuret simultaneously | **Physical trade-off dual-objective optimization (main innovation)** |
| FR-CAT-01 | Prediction of the activity loss of the ammonia synthesis iron catalyst | Ammonia-specific catalyst monitoring |
| FR-ALERT-01 | Tiered HSE alert for critical SCC risk | Critical action recommender |
| FR-LOOP-01 | Recording real inspection results and biuret laboratory results for retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-SAFE-01 | Delay of the critical SCC risk alert | Less than 10 seconds |
| NFR-PER-01 | Biuret virtual sensor accuracy (MAPE) | Less than 10% |
| NFR-AVAIL-01 | Availability of the safety module | 99.99% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Ammonia/Urea     ││ SCC Risk Model ││ Biuret Sensor +  │
│Ingestion (DCS)  ││ + Catalyst     ││ Dual-Objective   │
│                 ││ Activity Model ││ Optimizer        │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/ammonia-urea-ingestion/` | Connection to the DCS of the ammonia and urea units |
| `services/scc-biuret-twin/` | SCC risk model + biuret virtual sensor |
| `services/dual-objective-optimizer/` | Proposing the optimal operating point |
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

# 1. Urea reactor
reactor_temp_c = 190 + 6 * np.sin(t * 0.08) + np.random.normal(0, 1, NUM_RECORDS)
reactor_pressure_bar = 150 + 5 * np.sin(t * 0.08 + 0.2) + np.random.normal(0, 1.5, NUM_RECORDS)
carbamate_concentration_percent = 38 + 2 * np.sin(t * 0.06) + np.random.normal(0, 0.5, NUM_RECORDS)

# 2. SCC risk (function of temperature, pressure and carbamate concentration)
scc_risk_index = 0.02 * (reactor_temp_c - 190) + 0.015 * (reactor_pressure_bar - 150) + 0.01 * (carbamate_concentration_percent - 38) + np.random.normal(0, 0.05, NUM_RECORDS)
scc_risk_index = np.clip(scc_risk_index, 0, 5)

# 3. Biuret quality (decreases with increasing temperature)
biuret_content_percent = 1.3 - 0.015 * (reactor_temp_c - 190) + np.random.normal(0, 0.05, NUM_RECORDS)
biuret_content_percent = np.clip(biuret_content_percent, 0.3, 2.0)

# 4. Ammonia catalyst
ammonia_catalyst_activity_percent = 100 - 0.0005 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.3, NUM_RECORDS)
n2_h2_ratio = 0.33 + 0.02 * np.sin(t * 0.1) + np.random.normal(0, 0.005, NUM_RECORDS)

# 5. Labels
scc_critical_alert = (scc_risk_index > 3.5).astype(int)
biuret_off_spec = (biuret_content_percent > 1.0).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'reactor_temp_c': np.round(reactor_temp_c, 2),
    'reactor_pressure_bar': np.round(reactor_pressure_bar, 2),
    'carbamate_concentration_percent': np.round(carbamate_concentration_percent, 2),
    'scc_risk_index': np.round(scc_risk_index, 3),
    'biuret_content_percent': np.round(biuret_content_percent, 3),
    'ammonia_catalyst_activity_percent': np.round(ammonia_catalyst_activity_percent, 2),
    'n2_h2_ratio': np.round(n2_h2_ratio, 4),
    'scc_critical_alert': scc_critical_alert,
    'biuret_off_spec': biuret_off_spec,
})

df.to_csv("hengam_ammonia_urea_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-HAUC | Approximate financial/safety impact |
| :--- | :--- | :--- | :--- |
| Urea reactor SCC risk | Periodic inspection | Continuous monitoring and preventive alert | Preventing a catastrophic accident in a high-pressure reactor |
| Biuret quality | Conservative temperature setting (sacrificing safety or quality) | Optimal dual-objective operating point | Simultaneous reduction of corrosion risk and biuret waste on the 1.155 million tons/year urea capacity |

**Payback:** Given the known history of SCC accidents in the global urea industry and the high value of production capacity, this product is a simultaneous safety and quality priority.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | SCC risk prediction model (first HSE priority) |
| 3 | Biuret virtual sensor |
| 4 | Dual-objective operating point optimizer |
| 5 | Dashboard + operational pilot under HSE supervision |

---

## 6. Summary of Patentable Innovations

1. **The first adaptation of learning-based SCC prediction to the ammonium carbamate environment of the chemical fertilizer industry**.
2. **Real-time virtual sensor of biuret content** without waiting for the laboratory.
3. **Physical dual-objective optimization** that quantifies the inherent trade-off between corrosion risk and biuret quality.

---

## 7. References

- [PGPIC — Hengam Petrochemical Company](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D9%87%D9%86%DA%AF%D8%A7%D9%85)
- [Stress Corrosion Cracking in Ammonia Urea Synthesis — ureaknowhow.com](https://ureaknowhow.com/wp-content/uploads/2017/12/1971-Horst-SCC-in-Ammonia-Urea-Synthesis-Synthesos-corrosion-of-austenitic-stainless-steel.pdf)
- [Machine learning for modeling intergranular SCC of stainless steels — Nature npj Materials Degradation](https://www.nature.com/articles/s41529-025-00717-0)
- [Machine Learning-Assisted Prediction of Stress Corrosion Crack Growth Rate in Stainless Steel](https://doi.org/10.3390/cryst14100846)
- [Machine learning for predicting catalytic ammonia decomposition — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S2352152X24012738)
