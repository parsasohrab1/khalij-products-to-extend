# Khalij-Gachsaran-CrackerRampUp-PipelineAllocation-System (Khalij-GCPA)

## Intelligent system for self-learning optimization of the cracking severity of a domestically built furnace during capacity ramp-up and real-time allocation of national-pipeline ethylene among five downstream consumers — a dedicated product of Gachsaran Petrochemical Company

> This document is a **dedicated** product for Gachsaran Petrochemical Company — **Iran's most indigenous olefin complex** (designed and built domestically, without the usual foreign license) which currently operates at about 40% of nominal capacity and transports its ethylene via the **national pipeline** to five independent downstream destinations. These two features (technology indigenization + multi-consumer pipeline distribution) are not seen in any other holding company.

---

## 0. Understanding Gachsaran Petrochemical Company and the technical gap

**Sources:** [Global Energy Monitor — Gachsaran Petrochemical Complex](https://www.gem.wiki/Gachsaran_Petrochemical_Complex), [Shana — Gachsaran petrochemical project progress](https://www.shana.ir/news/457430/), [PGPIC — Gachsaran Polymer Industries](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D8%B5%D9%86%D8%A7%DB%8C%D8%B9-%D9%BE%D9%84%DB%8C%D9%85%D8%B1-%DA%AF%DA%86%D8%B3%D8%A7%D8%B1%D8%A7%D9%86)

### Products and unique features

| Feature | Value |
|---|---|
| Ethylene | 1,000,000 tons/year (nominal capacity) |
| C3+ (propane and heavier) | 84,000 tons/year |
| Current status | Operating at ~40% of nominal capacity (increasing, requiring facilities) |
| Technology feature | **Iran's most indigenous olefin complex** — domestic design/construction, not relying solely on international vendors' advanced process control (APC) packages such as Lummus/Technip |
| Product distribution | Ethylene via the **western Iran national ethylene pipeline** to 5 destinations: Mamasani, Kazerun, Boroujen petrochemicals, Dehdasht Polymer, Gachsaran Polymer |

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Gachsaran |
|---|---|
| Product 1 (reactor process optimization) | Designed for units with an international vendor's advanced control package; Gachsaran's domestically built cracker lacks a proven vendor performance model and requires a **self-learning (Self-Learning)** approach without relying on a pre-existing design curve |
| Bandar Imam dedicated product (multi-company allocation) | Designed for coordination of **co-located** subsidiaries; Gachsaran sends ethylene to 5 **independent, remote companies through a national pipeline** — a pipe network hydraulics problem, not coordination within one site |
| No holding product | Has addressed the **gradual capacity ramp-up (Ramp-Up)** phase of a newly commissioned plant whose capacity changes over time |

**Conclusion:** Gachsaran needs a system that (a) self-learningly optimizes the cracking severity of the domestically built furnace without relying on a foreign vendor model and (b) manages the pipeline ethylene allocation among 5 consumers in real time in proportion to the plant's actual, changing capacity.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | *Machine Learning-Based Profit Optimization for a Furnace in Naphtha Cracking Center with Uncertainties in Feed Composition* (SSRN) | Furnace profitability optimization under feed uncertainty; assumes a baseline vendor model; does not address ramp-up phase or pipeline distribution | A fully self-learning model with no need for a vendor baseline model, specific to the capacity ramp-up phase |
| 2 | *Toward Intelligent and Green Ethylene Manufacturing: AI-Based Multi-Objective Dynamic Optimization* (ScienceDirect) | General steam cracking optimization framework; does not address pipeline multi-consumer product distribution | Direct connection of furnace optimization output to pipeline allocation |
| 3 | **US 10,268,212 B2** – *Method and devices for balancing a group of consumers in a fluid transport system* | General method of balancing consumers in a fluid transport system (general water/gas industry); does not address petrochemical ethylene or dependency on variable upstream cracker capacity | Adaptation to an ethylene pipeline network with variable upstream cracker capacity input in ramp-up |
| 4 | **CN103524284A** – *Forecasting and optimizing method for ethylene cracking material configuration* | Optimization of cracking feed configuration; single-unit level, without considering multi-destination downstream distribution | Complete chain connection from furnace to final allocation among 5 destinations |

### Core Patentable Claim

> **"An integrated self-learning optimization-distribution system that, for the first time, (a) optimizes the cracking furnace severity/yield of a domestically built plant without a baseline vendor performance model through reinforcement learning directly from real operational ramp-up data, and (b) connects the furnace's predicted instantaneous capacity output as a dynamic input to the hydraulic allocation engine of the national pipeline among five independent downstream consumers, to prevent sudden feed cut/shortage to any of the consumers during the gradual capacity increase period."**

---

## 2. SRS Document – Dedicated product of Gachsaran Petrochemical

### 2-1. Introduction
**Purpose:** Sustainably increase the yield of the domestically built cracking furnace during the ramp-up phase, and fair, uninterrupted allocation of pipeline ethylene among 5 consumers in proportion to the plant's actual variable capacity.

**Field challenges:**
- No proven vendor performance model for the domestically built furnace; optimization must learn directly from real operational data.
- Production capacity is gradually increasing (from 40% toward nominal capacity), which changes the pipeline allocation every month/week.
- Risk of a sudden feed shortage for one of the 5 consumers if the cracker capacity fluctuates in the short term.

**Scope:** Gachsaran complex; connection to the cracking furnace DCS and the national ethylene pipeline SCADA system.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous cracking furnace data (temperature, severity, ethylene yield) | High |
| R-GEN-02 | Reception of pipeline pressure/flow data at five delivery points | High |
| R-GEN-03 | Integrated dashboard "Furnace capacity + pipeline allocation" | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-FURNACE-01 | Self-learning optimization of furnace severity/yield without a vendor baseline model, learning directly from ramp-up data | **Self-learning optimization of a domestically built cracker (main innovation)** |
| FR-PIPE-01 | Real-time allocation of pipeline ethylene among 5 consumers in proportion to instantaneous furnace capacity | **Ramp-up-aware pipeline allocation (main innovation)** |
| FR-PIPE-02 | Preventive alert of feed shortage risk of each consumer before it occurs | Preventive distribution recommender |
| FR-FORECAST-01 | Prediction of the furnace capacity increase trend during the ramp-up phase for medium-term allocation planning | Ramp-up trajectory prediction |
| FR-LOOP-01 | Recording actual yield and actual delivery for continuous retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Delay in readjusting pipeline allocation | Less than 5 minutes |
| NFR-PER-02 | Furnace capacity prediction accuracy (MAPE) | Less than 12% |
| NFR-AVAIL-01 | System availability | 99.9% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Furnace/Pipeline ││ Self-Learning  ││ Pipeline         │
│Ingestion (DCS + ││ Furnace Model  ││ Allocation       │
│ SCADA)          ││ (RL-based)     ││ Optimizer        │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/furnace-pipeline-ingestion/` | Connection to the furnace DCS and pipeline SCADA |
| `services/self-learning-furnace-model/` | Reinforcement learning model without a vendor baseline model |
| `services/pipeline-allocation-optimizer/` | Real-time capacity-aware allocator |
| `shared/` | Reuse of products 1-4 |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(hours=i/20) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# gradual furnace capacity increase trend (ramp-up from ~40% toward higher capacity)
ramp_progress = 40 + 0.0018 * np.arange(NUM_RECORDS) + 3 * np.sin(t * 0.05) + np.random.normal(0, 1.5, NUM_RECORDS)
furnace_capacity_percent = np.clip(ramp_progress, 30, 85)
ethylene_production_tph = 114 * (furnace_capacity_percent / 100) + np.random.normal(0, 2, NUM_RECORDS)

# allocation to the five consumers (base share + dependence on instantaneous capacity)
consumers = ["Mamasani", "Kazeroun", "Boroujen", "Dehdasht_Polymer", "Gachsaran_Polymer"]
base_share = np.array([0.15, 0.25, 0.15, 0.25, 0.20])
allocations = np.outer(ethylene_production_tph, base_share)

demand_tph = np.tile(np.array([16, 27, 16, 27, 22]), (NUM_RECORDS, 1)) + np.random.normal(0, 1, (NUM_RECORDS, 5))
shortfall = np.clip(demand_tph - allocations, 0, None)
shortfall_risk = (shortfall.sum(axis=1) > 5).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'furnace_capacity_percent': np.round(furnace_capacity_percent, 2),
    'ethylene_production_tph': np.round(ethylene_production_tph, 2),
})
for i, c in enumerate(consumers):
    df[f'allocation_{c}_tph'] = np.round(allocations[:, i], 2)
    df[f'demand_{c}_tph'] = np.round(demand_tph[:, i], 2)
df['pipeline_shortfall_risk'] = shortfall_risk

df.to_csv("gachsaran_furnace_pipeline_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-GCPA | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Furnace yield in the ramp-up phase | Manual adjustment without a proven optimal model | Continuous self-learning optimization | Faster achievement of nominal capacity and increased effective yield during ramp-up |
| Pipeline allocation among 5 consumers | Fixed/manual, shortage risk under capacity fluctuation | Dynamic and preventive allocation | Preventing unplanned shutdown of downstream units (Mamasani/Kazerun/Boroujen/Dehdasht/Gachsaran) due to feed shortage |

**Payback:** Given the direct dependence of five downstream companies on this pipeline and the current sensitive ramp-up phase, this system helps both accelerate Gachsaran's return on investment and the stability of downstream production.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Self-learning furnace optimization model (first priority due to the current ramp-up phase) |
| 3 | Capacity increase trajectory prediction |
| 4 | Real-time pipeline allocator among 5 consumers |
| 5 | Integrated dashboard + operational pilot |

---

## 6. Summary of Patentable Innovations

1. **Self-learning optimization of a domestically built cracking furnace without relying on a foreign vendor performance model**.
2. **Real-time allocation of the national ethylene pipeline among five independent consumers, aware of the upstream plant's capacity ramp-up trajectory**.
3. **Preventive alert of downstream feed shortage** before it occurs, caused by upstream capacity fluctuation.

---

## 7. References

- [Global Energy Monitor — Gachsaran Petrochemical Complex](https://www.gem.wiki/Gachsaran_Petrochemical_Complex)
- [Shana — Gachsaran petrochemical project reached 91.5 percent progress](https://www.shana.ir/news/457430/)
- [PGPIC — Gachsaran Polymer Industries Company](https://pgpic.ir/%D8%B4%D8%B1%DA%A9%D8%AA-%D9%87%D8%A7%DB%8C-%D8%AA%D8%A7%D8%A8%D8%B9%D9%87/%D8%B7%D8%B1%D8%AD-%D9%87%D8%A7%DB%8C-%D8%AF%D8%B1-%D8%AD%D8%A7%D9%84-%D8%A7%D8%AC%D8%B1%D8%A7/%D8%B4%D8%B1%DA%A9%D8%AA-%D8%B5%D9%86%D8%A7%DB%8C%D8%B9-%D9%BE%D9%84%DB%8C%D9%85%D8%B1-%DA%AF%DA%86%D8%B3%D8%A7%D8%B1%D8%A7%D9%86)
- [Toward Intelligent and Green Ethylene Manufacturing — ScienceDirect](https://www.sciencedirect.com/science/article/pii/S2095809925004382)
- [US10268212B2 — Method and devices for balancing a group of consumers in a fluid transport system](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/10268212)
- [CN103524284A — Forecasting and optimizing method for ethylene cracking material configuration](https://patents.google.com/patent/CN103524284A/en)
