# Khalij-Arvand-ChlorAlkali-PVC-Digital-Twin-System (Khalij-ACPT)

## Intelligent System for Health Monitoring of Chlor-Alkali Electrolysis Cells, Prediction of PVC Polymerization Reactor Fouling, and Real-Time Energy Optimization of the EDC-VCM-PVC Chain — Proprietary Product of Arvand Petrochemical Company

> This document describes a **proprietary and customized** product for Arvand Petrochemical Company which, unlike the holding's generic products 1 to 4 (which were later allocated to one company), is designed from the start based on this company's real and unique process (chlor-alkali chain → EDC/VCM → PVC) and uses the shared infrastructure of the holding's previous products in an evolutionary manner.

---

## 0. Understanding Arvand Petrochemical Company (based on a study of the official website) and the Technical Gap

**Source:** [Official website of Arvand Petrochemical](https://arvandpvc.ir/) — section "Arvand Petrochemical at a Glance"

### Products and Process Units (according to the company website)

| Process unit | Product | Nominal annual capacity |
|---|---|---|
| Brine electrolysis (Membrane Cell) | Chlorine gas | 186,700 tons |
| Brine electrolysis | Caustic soda (100% purity) | 634,000 tons |
| EDC/VCM | Ethylene dichloride | 329,300 tons |
| Suspension polymerization | S-PVC | 300,000 tons |
| Emulsion polymerization | E-PVC (exclusive producer in Iran) | 40,000 tons |

Arvand is the **largest PVC chain producer in the Middle East** and has the highest caustic production capacity in the country; according to the company's official statement, it uses modern membrane cell technology without the use of mercury, which indicates the company's high sensitivity to the efficiency and health of the electrolysis cells.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not sufficient for Arvand |
|---|---|
| Product 1 (reactor process optimization) | Designed for generic process reactors (temperature/pressure/flow), not membrane electrolysis cells, which have entirely different physics (cell voltage, current density, caustic current efficiency) |
| Product 3 (energy and carbon) | Sees energy consumption at the macro level of the unit; it does not address gradual membrane degradation as the **root cause of increased specific energy consumption** (kWh/ton chlorine) — and 90% of the total electricity consumed by the Arvand complex goes to this electrolysis section |
| Product 4 (rotating asset/furnace/catalyst monitoring) | Designed for compressors, cracking furnaces and gas polymerization catalyst; the membrane electrolysis cell and PVC autoclave reactor (polymer scale fouling, not catalyst degradation) are entirely different phenomena that require dedicated modeling |

**Conclusion:** Arvand needs a dedicated product that sees the three interrelated phenomena of its chain — (a) electrolysis cell membrane degradation, (b) fouling of the PVC polymerization autoclave, (c) specific energy cost/consumption that is directly caused by (a) — in a single model.

---

## 1. Patent Background and Competitive Analysis (Prior-Art Search)

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | ML papers for predicting cell voltage and caustic current efficiency in a chlor-alkali cell (Extreme Learning Machine) | Only single-cell level/single output variable; not connected to PVC fouling or energy cost | Integrating cell health with the entire downstream chain and the real energy cost |
| 2 | Toyota Central R&D — membrane state estimation through separator water quality measurement (2025) | Designed for water electrolysis cells (PEM/Alkaline Water), not large-scale industrial chlor-alkali cells | Adapting and extending the method to an industrial chlor-alkali membrane cell with real DCS data |
| 3 | **US 7,645,841 B2** – *Method and system to reduce polymerization reactor fouling* | Detects generic polymerization reactor fouling through periodogram analysis; does not consider the specific chemical product (PVC) and the connection to the upstream cell | Dedicated PVC autoclave fouling model with simultaneous input from the VCM quality produced by the electrolysis cell |
| 4 | **US 8,396,600 B2** – *Prediction and control solution for polymerization reactor operation* | Generic predictive control of a polymerization reactor; lacks a link to the energy cost of the upstream chain | Direct output to simultaneous optimization of production scheduling and time-varying electricity tariff |
| 5 | Optimization studies of chlor-alkali electricity cost with time-varying tariff (Mixed-Integer NLP, savings ~4%) | Optimization based solely on the electricity tariff, without considering the instantaneous health status of the cell (which changes actual consumption relative to the design value) | Simultaneous optimization of tariff + real cell health (not the nominal design value) |

### Core Patentable Claim

> **"A Chain-Level Digital Twin system that, for the first time, connects the gradual degradation of the chlor-alkali electrolysis cell membrane (via the cell voltage and current efficiency trend) as a direct input variable to the downstream PVC polymerization reactor fouling prediction model (via the quality of the VCM produced), and simultaneously, in a single optimization loop, adjusts the production schedule based on a combination of three signals (cell health + reactor fouling risk + time-varying electricity tariff)."**

This upstream-downstream link (electrolysis cell ↔ polymerization reactor) was not seen in an integrated form in any source found.

---

## 2. SRS Document – Proprietary Product of Arvand Petrochemical

### 2-1. Introduction
**Purpose:** Continuous health monitoring of membrane electrolysis cells, prediction of the optimal washing time of the PVC autoclave, and simultaneous optimization of production schedule and energy consumption across the entire chlor-alkali-PVC chain.

**Field challenges this product solves:**
- Gradual increase in cell voltage and reduction of caustic current efficiency due to membrane degradation, which directly raises the kWh/ton chlorine cost (90% of the complex's electricity consumption goes to electrolysis).
- Scale fouling inside PVC polymerization autoclaves that causes loss of heat transfer, longer cycle time and loss of quality (K-value).
- Lack of connection between the decision "when do we produce" and the real status of the cells and the hourly electricity tariff.

**Scope:** Arvand Petrochemical site (Zone 3 of the Bandar Imam Petrochemical Special Economic Zone); connection to the DCS of the electrolysis, EDC/VCM and PVC units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Receive real-time voltage/current data of each electrolysis cell (down to the single-cell level where measurement exists) | High |
| R-GEN-02 | Receive PVC autoclave process data (jacket temperature, pressure, agitator speed, agitator motor power) | High |
| R-GEN-03 | "Chlor-alkali-PVC chain health" dashboard showing the status of cells and reactors simultaneously | High |
| R-GEN-04 | Connection to the energy management/electricity tariff system of the distribution company | Medium |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-CELL-01 | Predict the membrane degradation trend (cell voltage, current efficiency) with a confidence interval and an estimate of the recommended membrane replacement date | Trend-based membrane degradation model rather than a fixed threshold |
| FR-CELL-02 | Estimate real instantaneous specific energy consumption (kWh/ton chlorine) versus the design value and separate the deviation caused by cell degradation | Root cause detection of increased energy consumption |
| FR-PVC-01 | Predict the optimal PVC autoclave washing time from the trend of jacket heat transfer coefficient decline and agitator power increase | Predictive (not calendar-based) washing scheduling |
| FR-PVC-02 | Predict PVC K-value/grade quality based on the incoming VCM quality (which itself depends on the upstream cell's health) | **Linking the downstream quality model to upstream cell health (main innovation)** |
| FR-OPT-01 | Optimize the hourly production schedule with simultaneous input (cell health + fouling risk + electricity tariff) | **Three-signal chain optimization (main innovation)** |
| FR-ALERT-01 | Tiered alerting with action recommendation (e.g., "5 days until autoclave 2 needs washing") | Real-time action advisor |
| FR-LOOP-01 | Record real feedback on membrane replacement/autoclave washing time for model retraining | Closed-loop learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Cell/reactor data processing latency | Less than 10 seconds |
| NFR-PER-02 | Autoclave washing time prediction accuracy (MAPE) | Less than 20% |
| NFR-AVAIL-01 | System availability | 99.9% |
| NFR-SEC-01 | AES-256 encryption + RBAC for electrolysis operator/PVC operator/energy manager roles | Mandatory |

### 2-5. Technical Architecture (reusing the pattern of products 1-4)

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA — shared holding pattern)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│Cell/Reactor     ││ Digital-Twin   ││ Chain Production │
│Ingestion        ││ Prediction     ││ Optimization     │
│(Cell V/I, PVC   ││ (Membrane decay││ (hourly schedule │
│ autoclave DCS)  ││ + Fouling LSTM)││ vs tariff + risk)│
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB/  │
        │ (shared)   │    │ InfluxDB      │
        └────────────┘    └───────────────┘
                                  │
                           ┌────────────┐
                           │   MLflow   │
                           └────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/cell-reactor-ingestion/` | Connection to the electrolysis and PVC unit DCS, reusing the shared OPC-UA client |
| `services/digital-twin-prediction/` | Membrane degradation model (LSTM), autoclave fouling model, K-value quality model |
| `services/chain-optimization/` | Hourly production schedule optimizer (MILP) with health + tariff input |
| `shared/` | Full reuse of products 1-4 |

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

# 1. Membrane electrolysis cell
cell_voltage_v = 3.05 + 0.00004 * np.arange(NUM_RECORDS) + 0.02 * np.sin(t * 0.3) + np.random.normal(0, 0.01, NUM_RECORDS)
current_efficiency_percent = 96.5 - 0.0003 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.3, NUM_RECORDS)
current_efficiency_percent = np.clip(current_efficiency_percent, 88, 97)
specific_energy_kwh_per_ton = 2350 + 15 * (cell_voltage_v - 3.05) * 100 + np.random.normal(0, 20, NUM_RECORDS)

# 2. PVC polymerization autoclave
jacket_heat_transfer_coeff = 850 - 0.03 * np.arange(NUM_RECORDS) + np.random.normal(0, 15, NUM_RECORDS)
jacket_heat_transfer_coeff = np.clip(jacket_heat_transfer_coeff, 400, 900)
agitator_motor_power_kw = 120 + 0.002 * np.arange(NUM_RECORDS) + np.random.normal(0, 3, NUM_RECORDS)
batch_cycle_time_min = 240 + 0.004 * np.arange(NUM_RECORDS) + np.random.normal(0, 5, NUM_RECORDS)

# 3. Product quality
vcm_purity_percent = 99.9 - 0.02 * (100 - current_efficiency_percent) / 8 + np.random.normal(0, 0.02, NUM_RECORDS)
pvc_k_value = 68 - 0.5 * (99.95 - vcm_purity_percent) + np.random.normal(0, 0.3, NUM_RECORDS)

# 4. Labels
needs_wash_7d = (jacket_heat_transfer_coeff < 550).astype(int)
membrane_replace_flag_90d = (current_efficiency_percent < 90).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'cell_voltage_v': np.round(cell_voltage_v, 4),
    'current_efficiency_percent': np.round(current_efficiency_percent, 2),
    'specific_energy_kwh_per_ton': np.round(specific_energy_kwh_per_ton, 1),
    'jacket_heat_transfer_coeff': np.round(jacket_heat_transfer_coeff, 1),
    'agitator_motor_power_kw': np.round(agitator_motor_power_kw, 2),
    'batch_cycle_time_min': np.round(batch_cycle_time_min, 1),
    'vcm_purity_percent': np.round(vcm_purity_percent, 3),
    'pvc_k_value': np.round(pvc_k_value, 2),
    'needs_wash_7d': needs_wash_7d,
    'membrane_replace_flag_90d': membrane_replace_flag_90d,
})

df.to_csv("arvand_chain_health_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-ACPT | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Specific energy consumption of electrolysis | Membrane degradation is usually detected after a noticeable quality drop or a sharp rise in consumption | Early detection of the degradation trend + optimal replacement planning | Given the 90% share of electricity in electrolysis cost, every 1% improvement in efficiency equals significant savings in the complex's annual electricity cost (634 thousand tons caustic/year) |
| PVC autoclave shutdown for washing | Time-based or after a noticeable quality drop | Predictive, based on the real heat transfer trend | Increased effective production rate (Uptime) of the 300-thousand-ton S-PVC lines |
| PVC waste/grade loss | Caused by VCM quality fluctuations whose root cause (the cell) is detected late | Root cause detection before affecting the final grade | Reduced waste and rework (Off-grade) |

**Payback:** Given the dominant share of electrolysis energy cost in Arvand's cost structure, even a 1-2% improvement in cell current efficiency can offset the implementation cost within the first months of the pilot.

---

## 5. Proposed Evolution Roadmap (Phase 1-7)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator + shared Kafka/TimescaleDB connection |
| 2 | Membrane degradation and specific energy consumption prediction model |
| 3 | PVC autoclave fouling model and washing scheduling |
| 4 | VCM quality→PVC K-value link model |
| 5 | Hourly production schedule optimizer (health + electricity tariff) |
| 6 | Chlor-alkali-PVC chain management dashboard + real-time alerting |
| 7 | Operational pilot on one cell line and one real autoclave at the Arvand site |

---

## 6. Summary of Patentable Innovations

1. **Direct link between electrolysis cell membrane degradation and the downstream polymerization reactor fouling/quality model** in a single chain digital twin.
2. **Three-signal hourly production schedule optimization** (cell health + fouling risk + time-varying electricity tariff).
3. **Root cause separation of increased specific energy consumption** (cell degradation versus other operational factors).

---

## 7. References

- [Official website of Arvand Petrochemical — At a Glance](https://arvandpvc.ir/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%A7%D8%B1%D9%88%D9%86%D8%AF-%D8%AF%D8%B1-%DB%8C%DA%A9-%D9%86%DA%AF%D8%A7%D9%87)
- [Petrochemicals complex profile: Arvand Petrochemical Company — offshore-technology.com](https://www.offshore-technology.com/marketdata/arvand-petrochemical-company-bandar-imam-complex-iran/)
- [Determination of cell voltage and current efficiency in a chlor-alkali membrane cell based on machine learning approach](https://doi.org/10.1080/10916466.2022.2153867)
- [Machine Learning Models for Predicting Electrode and Membrane Degradation in Alkaline Water Electrolysis](https://www.researchgate.net/publication/398896117_Machine_Learning_Models_for_Predicting_Electrode_and_Membrane_Degradation_in_Alkaline_Water_Electrolysis_for_Hydrogen_Production)
- [US7645841B2 — Method and system to reduce polymerization reactor fouling](https://patents.google.com/patent/US7645841B2/en)
- [US8396600B2 — Prediction and control solution for polymerization reactor operation](https://patents.google.com/patent/US8396600B2/en)
- [Energy Efficiency and Cost-Saving Opportunities for the Chlor-Alkali Industry (EPA ENERGY STAR)](https://www.energystar.gov/sites/default/files/2025-01/EPA_ES_Chlor-Alkali_Guide_20250114.pdf)
- [Flexible and economical operation of chlor-alkali process with subsequent PVC production — AIChE Journal](https://aiche.onlinelibrary.wiley.com/doi/full/10.1002/aic.17480)
