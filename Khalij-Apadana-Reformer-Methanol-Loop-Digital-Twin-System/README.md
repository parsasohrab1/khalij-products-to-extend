# Khalij-Apadana-Reformer-Methanol-Loop-Digital-Twin-System (Khalij-ARML)

## Intelligent System for Predicting Reformer Tube Creep Life, Copper Methanol Synthesis Catalyst Degradation, and Real-Time Optimization of the Syngas Module Ratio — Proprietary Product of Persian Gulf Apadana Petrochemical Company

> This document describes a **proprietary** product for Persian Gulf Apadana Petrochemical Company — the holding's largest single-train methanol unit (1.65 million tons/year) in Phase 2 of Asaluyeh. Because of this complex's **single-train** nature, any unplanned shutdown has an immediate and large financial impact; this characteristic calls for a product entirely different from the other multi-unit companies of the holding.

---

## 0. Understanding Persian Gulf Apadana Petrochemical Company and the Technical Gap

**Sources:** [PGPIC — Persian Gulf Apadana](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%A2%D9%BE%D8%A7%D8%AF%D8%A7%D9%86%D8%A7-%D8%AE%D9%84%DB%8C%D8%AC-%D9%81%D8%A7%D8%B1%D8%B3), [offshore-technology.com — Persian Gulf Apadana Petrochemical Assaluyeh Complex](https://www.offshore-technology.com/data-insights/persian-gulf-apadana-petrochemical-assaluyeh-complex-iran-2/)

### Products and Process Nature

| Feature | Value |
|---|---|
| Product | Methanol (single product) |
| Capacity | 1,650,000 tons/year |
| Location | Pars Special Economic Zone, Site 2, Asaluyeh |
| Feed | Natural gas |
| Commercial operation | 1403 (2024/2025) — a relatively new unit |

**Process chain:** Natural gas → steam reforming (SMR/ATR) → syngas (H₂/CO/CO₂) → methanol synthesis reactor (Cu/ZnO/Al₂O₃ copper catalyst) → methanol distillation and purification.

Two critical assets of this chain: (a) **reformer tubes**, which operate at very high temperature and pressure and are exposed to gradual creep and the risk of catastrophic rupture, and (b) the **copper methanol synthesis catalyst**, which over time (1 to 5 years) suffers sintering and loss of activity.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not sufficient for Apadana |
|---|---|
| Product 4 (asset/furnace monitoring) | Its furnace model is designed for a **pyrolysis cracking furnace** (coil skin temperature, decoking pressure drop); the physics of **reformer tube creep** (gradual plastic deformation under very high stress/temperature, not carbon fouling) is entirely different, and it was allocated to Maroun company, not a single-train methanol unit |
| Product 4 (catalyst degradation) | Designed for a gas polymerization catalyst; degradation of the copper methanol synthesis catalyst (thermal sintering, chloride poisoning) has a different mechanism |
| No holding product | Has addressed the special risk of **single-train operation** (no parallel backup unit), where every hour of downtime has a direct and complete impact on the company's entire production |

**Conclusion:** Apadana needs a digital twin that sees the health of reformer tubes (creep) and the methanol synthesis catalyst (sintering) simultaneously with optimization of the syngas module ratio — with a special focus on preventing single-train shutdowns.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US RE50,475 / RE48,734** – *Method and apparatus for determining the health and remaining service life of austenitic steel reformer tubes* | A measurement/inspection method (magnetic induction) at fixed intervals; not a real-time machine-learning prediction system using continuous DCS data | Converting periodic spot inspection into continuous monitoring and real-time ML prediction from real operational data |
| 2 | Creep life estimation of reformer alloy using θ-projection method — Neuro-Fuzzy (ScienceDirect) | Laboratory/offline model based on metal samples; not connected to the unit's real operational data or to the downstream catalyst | Real-time model connected to the real DCS + link to the methanol synthesis catalyst condition |
| 3 | Multi-objective optimization studies of the methanol synthesis loop (Bayesian/NSGA-II, ACS Omega) | Offline optimization/process design; the instantaneous health of the reformer tube or catalyst does not enter as an optimization constraint | Real-time optimization of the syngas module ratio with direct constraints on reformer tube and catalyst health |
| 4 | **US 10,308,576** – *Method for methanol synthesis* | Chemical synthesis process improvement; a process approach, not software/predictive | Complementary: a software layer for prediction and optimization on the existing process |

### Core Patentable Claim

> **"A Single-Train Chain Digital Twin system that, for the first time, combines real-time prediction of reformer tube creep life (from continuous operating temperature/stress trends, not periodic inspection) with a sintering prediction model for the copper methanol synthesis catalyst and real-time optimization of the syngas module ratio (H₂-CO₂)/(CO+CO₂) in a single decision loop with the goal of maximizing the availability of the single-train production line."**

---

## 2. SRS Document – Proprietary Product of Persian Gulf Apadana Petrochemical

### 2-1. Introduction
**Purpose:** Maximize the availability of the single-train production line through early prediction of reformer tube life and catalyst degradation, and real-time optimization of methanol yield.

**Field challenges:**
- Reformer tube rupture caused by cumulative creep, a catastrophic HSE risk and complete shutdown of the single-train production.
- Gradual loss of activity of the copper methanol synthesis catalyst (thermal sintering) which, if detected late, affects yield and specific energy consumption.
- No tool that sees both risks simultaneously with syngas module ratio optimization.

**Scope:** Apadana complex, Asaluyeh Site 2; connection to the DCS of the reforming and methanol synthesis units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Receive real-time skin temperature/estimated stress data for each row of reformer tubes | Critical (HSE) |
| R-GEN-02 | Receive methanol synthesis reactor data (temperature, pressure, syngas composition, catalyst activity loss) | High |
| R-GEN-03 | "Single-train health" dashboard with a unified view from reformer to final product | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-TUBE-01 | Real-time prediction of remaining creep life of each row of reformer tubes with a confidence interval | **Continuous tube creep monitoring (main innovation)** |
| FR-CAT-01 | Predict the sintering trend and activity loss of the methanol synthesis catalyst | Dedicated copper catalyst degradation prediction |
| FR-LOOP-OPT-01 | Real-time optimization of the syngas module ratio with tube and catalyst health constraints | **Chain optimization with dual health constraints (main innovation)** |
| FR-ALERT-01 | Tiered alerting with critical priority for tube rupture risk | Critical action advisor |
| FR-LOOP-02 | Record actual inspection/catalyst replacement results for model retraining | Closed-loop learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-SAFE-01 | Reformer tube critical risk alert latency | Less than 5 seconds |
| NFR-PER-01 | Remaining creep life prediction accuracy (MAPE) | Less than 15% |
| NFR-AVAIL-01 | System availability | 99.99% (due to single-train nature) |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Reformer/Synloop ││ Tube Creep +   ││ Syngas Module    │
│Ingestion (DCS)  ││ Catalyst Sinter││ Ratio Optimizer  │
│                 ││ Twin           ││ (constrained)    │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/reformer-synloop-ingestion/` | Reformer and synthesis loop DCS connection |
| `services/tube-catalyst-twin/` | Tube creep model + catalyst sintering |
| `services/syngas-ratio-optimizer/` | Constrained module ratio optimizer |
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

# 1. Reformer tube - skin temperature and cumulative creep strain
tube_skin_temp_c = 880 + 15 * np.sin(t * 0.1) + 0.003 * np.arange(NUM_RECORDS) + np.random.normal(0, 3, NUM_RECORDS)
creep_strain_percent = 0.0001 * np.arange(NUM_RECORDS) / 100 + np.random.normal(0, 0.002, NUM_RECORDS)
creep_strain_percent = np.clip(creep_strain_percent, 0, 1.2)

# 2. Methanol synthesis catalyst - gradual sintering
catalyst_activity_percent = 100 - 0.0007 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.4, NUM_RECORDS)
catalyst_activity_percent = np.clip(catalyst_activity_percent, 55, 100)

# 3. Syngas module ratio and yield
syngas_module_ratio = 2.05 + 0.05 * np.sin(t * 0.05) + np.random.normal(0, 0.01, NUM_RECORDS)
methanol_yield_tph = 195 - 0.3 * (100 - catalyst_activity_percent) - 5 * np.abs(syngas_module_ratio - 2.05) + np.random.normal(0, 2, NUM_RECORDS)
specific_energy_gj_per_ton = 30.5 + 0.05 * (100 - catalyst_activity_percent) + np.random.normal(0, 0.3, NUM_RECORDS)

# 4. Labels
tube_critical_risk = (creep_strain_percent > 0.8).astype(int)
catalyst_replace_flag_90d = (catalyst_activity_percent < 65).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'tube_skin_temp_c': np.round(tube_skin_temp_c, 2),
    'creep_strain_percent': np.round(creep_strain_percent, 4),
    'catalyst_activity_percent': np.round(catalyst_activity_percent, 2),
    'syngas_module_ratio': np.round(syngas_module_ratio, 3),
    'methanol_yield_tph': np.round(methanol_yield_tph, 2),
    'specific_energy_gj_per_ton': np.round(specific_energy_gj_per_ton, 3),
    'tube_critical_risk': tube_critical_risk,
    'catalyst_replace_flag_90d': catalyst_replace_flag_90d,
})

df.to_csv("apadana_reformer_methanol_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-ARML | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Reformer tube rupture risk | Periodic inspection (annual/biennial) | Continuous monitoring and early prediction | Prevents a complete shutdown of the 1.65-million-ton single-train line — very high daily loss in an emergency shutdown |
| Synthesis catalyst degradation | Replacement on a fixed schedule or noticeable yield loss | Predictive with simultaneous syngas module optimization | Increased effective yield and lower specific energy consumption |

**Payback:** Given the single-train nature and very large capacity (1.65 million tons/year), preventing even a few days of unplanned downtime quickly offsets the implementation cost of this system.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Reformer tube creep life prediction model (HSE first priority) |
| 3 | Methanol synthesis catalyst sintering prediction model |
| 4 | Constrained syngas module ratio optimizer |
| 5 | Single-train health dashboard + operational pilot |

---

## 6. Summary of Patentable Innovations

1. **Continuous monitoring and real-time prediction of reformer tube creep life** from real operational data (not periodic inspection).
2. **Real-time optimization of the syngas module ratio with direct constraints on reformer tube and catalyst health**.
3. **Integrated single-train risk model** that combines upstream (reformer) and downstream (catalyst) health to maximize the availability of the entire line.

---

## 7. References

- [PGPIC — Persian Gulf Apadana Petrochemical Company](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%A2%D9%BE%D8%A7%D8%AF%D8%A7%D9%86%D8%A7-%D8%AE%D9%84%DB%8C%D8%AC-%D9%81%D8%A7%D8%B1%D8%B3)
- [offshore-technology.com — Persian Gulf Apadana Petrochemical Assaluyeh Complex](https://www.offshore-technology.com/data-insights/persian-gulf-apadana-petrochemical-assaluyeh-complex-iran-2/)
- [US RE50475 — Method and apparatus for determining the health and remaining service life of austenitic steel reformer tubes](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/RE50475)
- [Creep life estimation of reformer alloy using θ-projection method — Neuro-Fuzzy — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0308016123000558)
- [Multiobjective Bayesian Optimization Framework for the Synthesis of Methanol from Syngas — ACS Omega](https://pubs.acs.org/doi/10.1021/acsomega.2c04919)
- [US10308576 — Method for methanol synthesis](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/10308576)
