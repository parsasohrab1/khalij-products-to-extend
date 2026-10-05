# Khalij-Critical-Asset-Prognostics-and-Maintenance-Optimization-System (Khalij-CAPM)

## Intelligent system for health monitoring, remaining useful life prediction and maintenance optimization of critical assets (rotating equipment, cracking furnaces and catalyst) — the fourth product of the Persian Gulf Holding

> This document presents the fourth product following the three previously introduced products of the holding and uses their infrastructure, technical patterns and shared data in an **evolutionary** way (not a parallel and duplicate product).

---

## 0. The position of this product in the holding's product roadmap — why this product, why now

Each of the holding's three previous products covers one layer of the "digital brain" of a petrochemical complex, but one critical and costly layer remains empty: **the physical health of assets (Asset Health)**.

| # | Product | Layer covered | What it does not cover (gap) |
|---|--------|------------------------|----------------------------|
| 1 | Khalij-Production-Process-Prediction-and-Optimization-System | Real-time optimization of reactor **process parameters** (temperature, pressure, flow) for quality/energy/cost | Assumes equipment (compressor, pump, turbine, furnace) is always healthy and available; does not deal with the physical health and life of equipment |
| 2 | khalij-Digital-Transformation-and-Value-Chain-Integration-System | Integration of the **supply/production/distribution/sales chain** at holding level (Data Mesh) | Does not deal with the equipment and production line level; its level is macro (Board/Command Center) |
| 3 | khalij-Intelligent-Energy-Carbon-and-Sustainability-Management-System | Energy consumption, Scope 1/2/3 carbon and real-time energy optimization (RTO) | Does not diagnose energy efficiency loss caused by **physical equipment deterioration** (furnace fouling, corrosion, rotor unbalance) as a root cause |
| **4 (this document)** | **Khalij-Critical-Asset-Prognostics-and-Maintenance-Optimization-System** | **Failure/remaining-life prediction of rotating equipment, decoking scheduling of cracking furnaces, catalyst activity-loss prediction, and optimization of maintenance schedule/spare-parts inventory** | — |

**Why this gap is the most important next priority:**
1. The biggest source of unplanned shutdown in a petrochemical is the failure of critical rotating equipment (cracked-gas compressor, propylene refrigeration compressor) and fouling/coking of cracking furnaces — not the process parameter deviation that product 1 covers.
2. Technically, this product **is built directly on the infrastructure of products 1 and 3** (the same XGBoost/LSTM virtual sensor pattern, the same Kafka/TimescaleDB/InfluxDB, the same MLflow) and only extends the data and model scope from "reactor process variables" to "vibration/thermal/furnace pressure-drop/catalyst signals"; thus it is exactly the **evolutionary** path requested, not a redefinition from scratch.
3. Unlike the previous three products that target "optimization" and "integration", this product focuses directly on **preventing catastrophic financial loss** (multi-day shutdown of an olefin unit), which is the simplest and fastest product for persuading a petrochemical's management to invest (ROI that is calculable and tangible in the first few weeks of the pilot).

---

## 1. Patent history and competitive analysis (Prior-Art Search) — the basis of innovation

A search of patent records and the technical literature (results and sources in section 8) shows:

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 11,650,184 B2** – *System and method for monitoring rotating equipment* | Only fault detection/RUL of rotating equipment based on mechanical signals (vibration/temperature); not connected to the chemical process | This system correlates equipment signals with **DCS process variables** (temperature/pressure/composition) to separate the root cause (process or mechanical) |
| 2 | **US 2018/0282633 A1** – *Rotating equipment in a petrochemical plant or refinery* (Invariant/PCA-based) | General unit-level anomaly detection; does not go down to a specific equipment and maintenance schedule | Separation at the Tag/Asset level + direct output to the maintenance scheduler and part inventory |
| 3 | **US 10,913,905 B2** – *Catalyst cycle length prediction using eigen analysis* | Only the reactor catalyst domain; completely separate from rotating equipment and furnace | A single model (Digital Twin) that sees catalyst + furnace + rotating equipment simultaneously |
| 4 | **US 12,044,642 B2** – *Estimating outer surface temperature of radiant coil of cracking furnace* | A point method for measuring/estimating coil skin temperature; a separate hardware/computational tool, without machine learning or a maintenance optimization loop | Decoking scheduling as a learning-based prediction (LSTM on the temperature-drop/pressure-drop trend) + direct link to the shutdown/maintenance schedule |
| 5 | Shana news (2023) – an Iranian knowledge-based company achieves rotating machine condition monitoring technology | Purely condition monitoring hardware/software; lacks spare-parts inventory optimization and repair workforce planning | Combining monitoring with **maintenance decision optimization** (when, with which part, by which team) |
| 6 | Academic/industrial papers (PNNL, AIChE, ScienceDirect) on ML for catalyst deterioration and cracking-furnace cycle scheduling | Single-domain research models, without an industrial product architecture, without a real DCS/CMMS connection | Turning these research findings into an **integrated industrial product** with operational APIs and connection to the maintenance CMMS/ERP |

### Core Patentable Claim

> **"A Multi-Layer Asset Digital Twin system that, for the first time, combines three domains: (a) vibration/thermal monitoring of rotating equipment, (b) virtual sensor of thermal deterioration of cracking furnaces and catalyst activity loss based on DCS process variables, and (c) dynamic simultaneous optimization of the maintenance schedule and spare-parts inventory based on the remaining-useful-life prediction uncertainty interval (RUL Confidence Interval) in a closed loop of recommendation→operator approval→action→real feedback."**

This triple combination (rotating equipment + furnace/catalyst + maintenance decision optimization, with shared input from the virtual sensors of product 1) was not seen in an integrated form in any of the patents or papers found and is the basis of the patent claim (Independent Claim) of this product.

---

## 2. SRS Document – Product 4: Critical asset health monitoring and maintenance optimization (patentable)

### 2-1. Introduction
**Purpose:** Develop a system based on machine learning and optimization that, by continuously monitoring critical rotating equipment, cracking furnaces and reactor catalysts, prevents unplanned production shutdowns and reduces maintenance and spare-parts inventory costs.

**Field challenges this product solves:**
- The traffic of cracked-gas and propylene/ethylene refrigeration compressors, where the failure of any one means a complete shutdown of the olefin unit (several million dollars of daily loss).
- Gradual coking of the pyrolysis furnace coils, which if detected late causes coil rupture or a sharp reduction in ethylene yield.
- Gradual loss of catalyst activity in polymerization reactors (PE/PP), which increases catalyst consumption, reduces production rate and causes grade quality fluctuation.
- Traditional maintenance planning (time-based) that either replaces a healthy part much earlier than necessary (extra cost) or too late (risk of catastrophic failure).

**Scope:** This system is implemented at the level of units with critical rotating equipment and process furnaces of the holding (priority: olefin units) and connects to the existing maintenance CMMS/ERP; its sensor input is fed from the same Data Ingestion infrastructure of product 1.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Simultaneous reception of vibration/thermal/pressure data of rotating equipment (rate ≥ 1 record/second) and furnace/reactor process variables from the same data bus of product 1 | High |
| R-GEN-02 | Retention of the health history of each Asset (equipment ID, serial, installation date, repair history) for at least 10 years | High |
| R-GEN-03 | Unit "Maintenance command center" dashboard showing a heat map of the health of all critical assets of the unit | High |
| R-GEN-04 | Two-way connection with the existing CMMS/ERP (SAP-PM or equivalent) for automatic Work Order issuance | Medium |

### 2-3. Functional Requirements (with emphasis on patentability)

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-ROT-01 | Fault detection of rotating equipment (unbalance, bearing wear, pump cavitation) from the vibration spectrum (FFT) + temperature with deep learning models | Simultaneous multi-fault detection with probabilistic confidence |
| FR-ROT-02 | Remaining useful life (RUL) prediction of every critical rotating equipment with a confidence interval, not just a single deterministic number | **RUL uncertainty interval as a direct input to maintenance optimization (main innovation)** |
| FR-FUR-01 | Virtual sensor of thermal efficiency loss and prediction of the optimal decoking time of the cracking furnace based on the coil skin temperature and pressure-drop trend | Predictive decoking scheduling (learning-based, not a fixed threshold) |
| FR-CAT-01 | Prediction of polymerization/cracking reactor catalyst activity loss and estimation of the optimal replacement/regeneration point | Catalyst deterioration virtual sensor integrated with equipment and furnace in one model |
| FR-OPT-01 | Simultaneous optimization of the shutdown/repair schedule, repair team allocation and critical spare-parts inventory level with a meta-heuristic algorithm (e.g., NSGA-II) with RUL intervals of multiple equipment as simultaneous input | **Integrated multi-asset maintenance optimization (main innovation)** |
| FR-ALERT-01 | Issuing tiered alerts (Watch/Warning/Critical) to the operator and maintenance manager + specific action recommendation | Real-time repair action recommender |
| FR-LOOP-01 | Recording real feedback (did a failure occur? how long did the repair take?) for continuous model retraining (Closed-Loop Learning) | Continuous learning loop based on real field outcome |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Detection delay of acute rotating equipment fault | Less than 5 seconds |
| NFR-PER-02 | RUL prediction accuracy (MAPE) in the pilot phase | Less than 15% |
| NFR-AVAIL-01 | Availability of the monitoring system | 99.9% |
| NFR-SEC-01 | Sensor data encryption (AES-256) + RBAC separation of operator/maintenance supervisor/HSE manager roles | Mandatory |
| NFR-INTEG-01 | Compatibility with industrial condition monitoring standards (ISO 13374, ISO 17359) | Mandatory |

### 2-5. Technical architecture (direct reuse of the pattern of products 1 and 3)

```
                         ┌──────────────────┐
                         │   API Gateway     │  (RBAC + 2FA — same pattern as product 1)
                         └─────────┬─────────┘
        ┌───────────────┬─────────┼───────────────┬───────────────┐
┌───────▼───────┐┌───────▼────────┐ ┌──────────────▼───┐┌──────────▼──────────┐
│Asset Ingestion ││ Digital-Twin   │ │ Maintenance       ││ Alerting /           │
│(Vibration/     ││ Prediction     │ │ Optimization      ││ CMMS-ERP Connector   │
│Thermal/DCS tags││(RUL/Furnace/   │ │(NSGA-II spare-part││ (SAP-PM Work Order)  │
│OPC-UA/Modbus)  ││ Catalyst LSTM) │ │+ crew scheduling) ││                      │
└──────┬─────────┘└───────┬────────┘ └─────────┬─────────┘└──────────┬───────────┘
       │                  │                     │                     │
       └──────────┬───────┴──────────┬──────────┘                     │
                   ▼                  ▼                                ▼
            ┌────────────┐    ┌───────────────┐                ┌────────────┐
            │   Kafka    │    │  TimescaleDB/ │                │ PostgreSQL │
            │ (same broker│    │  InfluxDB     │                │ (Work      │
            │  of product 1)│  │ (time signal) │                │  Orders)   │
            └────────────┘    └───────────────┘                └────────────┘
                                       │
                                ┌────────────┐
                                │   MLflow   │ (same model registry of product 1/3)
                                └────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/asset-ingestion/` | Connection to vibration/thermal sensors (IEPE/Accelerometer, Thermocouple) + reuse of product 1's OPC-UA client |
| `services/digital-twin-prediction/` | RUL models (LSTM/Survival Analysis), furnace virtual sensor, catalyst virtual sensor |
| `services/maintenance-optimization/` | Multi-objective NSGA-II (failure risk, downtime cost, spare-part inventory cost) |
| `services/cmms-connector/` | SAP-PM/ERP adapter for automatic Work Order issuance |
| `shared/` | Full reuse of product 1's Pydantic models, Kafka utils and settings |

---

## 3. Synthetic Data Generator Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

# ==============================================
# Data generation parameters
# ==============================================
NUM_RECORDS = 10000          # ~2.7 hours of data at 1 record/second
START_TIME = datetime(2026, 9, 12, 8, 0, 0)

timestamps = [START_TIME + timedelta(seconds=i) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# ------------------------------------------------
# 1. Critical rotating equipment: Cracked Gas Compressor
# ------------------------------------------------
# overall vibration amplitude (RMS, mm/s) - gradual upward trend = bearing deterioration
vibration_rms = 2.5 + 0.0006 * np.arange(NUM_RECORDS) + 0.3 * np.sin(t * 0.4) + np.random.normal(0, 0.15, NUM_RECORDS)
vibration_rms = np.clip(vibration_rms, 1.0, 12.0)

# Bearing Temperature - correlated with vibration
bearing_temp_c = 65 + 4 * (vibration_rms - 2.5) + np.random.normal(0, 1.2, NUM_RECORDS)
bearing_temp_c = np.clip(bearing_temp_c, 55, 110)

# compressor speed (RPM)
compressor_rpm = 9500 + 200 * np.sin(t * 0.2) + np.random.normal(0, 30, NUM_RECORDS)

# ------------------------------------------------
# 2. Cracking furnace (Pyrolysis Furnace) - decoking
# ------------------------------------------------
# Coil Outlet Skin Temperature - gradual increase with coke accumulation
coil_skin_temp_c = 850 + 0.008 * np.arange(NUM_RECORDS) + 5 * np.sin(t * 0.1) + np.random.normal(0, 2, NUM_RECORDS)
coil_skin_temp_c = np.clip(coil_skin_temp_c, 830, 1050)

# Coil Pressure Drop (bar) - gradual increase with coking
coil_pressure_drop_bar = 1.2 + 0.0003 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.05, NUM_RECORDS)
coil_pressure_drop_bar = np.clip(coil_pressure_drop_bar, 1.0, 3.5)

# ------------------------------------------------
# 3. Polymerization reactor catalyst (PE/PP)
# ------------------------------------------------
# relative catalyst activity (%) - gradual decrease
catalyst_activity_percent = 100 - 0.0015 * np.arange(NUM_RECORDS) - 2 * np.sin(t * 0.05) + np.random.normal(0, 0.8, NUM_RECORDS)
catalyst_activity_percent = np.clip(catalyst_activity_percent, 40, 100)

# actual production rate (tons per hour) - depends on catalyst activity
production_rate_tph = 45 * (catalyst_activity_percent / 100) + np.random.normal(0, 1, NUM_RECORDS)
production_rate_tph = np.clip(production_rate_tph, 15, 48)

# ------------------------------------------------
# 4. Target variables (model training labels)
# ------------------------------------------------
# binary label of imminent compressor failure within the next 72 hours (for RUL/classification model training)
failure_risk_72h = (vibration_rms > 7.5).astype(int)

# days remaining until the recommended furnace decoking (based on a 2.8 bar pressure-drop threshold)
days_to_recommended_decoke = np.clip((2.8 - coil_pressure_drop_bar) / 0.0003 / 86400, 0, 45)

df = pd.DataFrame({
    'timestamp': timestamps,
    # compressor
    'compressor_vibration_rms_mms': np.round(vibration_rms, 3),
    'compressor_bearing_temp_c': np.round(bearing_temp_c, 2),
    'compressor_rpm': np.round(compressor_rpm, 0).astype(int),
    'compressor_failure_risk_72h': failure_risk_72h,
    # cracking furnace
    'furnace_coil_skin_temp_c': np.round(coil_skin_temp_c, 2),
    'furnace_coil_pressure_drop_bar': np.round(coil_pressure_drop_bar, 3),
    'days_to_recommended_decoke': np.round(days_to_recommended_decoke, 1),
    # catalyst
    'catalyst_activity_percent': np.round(catalyst_activity_percent, 2),
    'production_rate_tph': np.round(production_rate_tph, 2),
})

output_file = "critical_asset_health_data_10k.csv"
df.to_csv(output_file, index=False)
print(f"✅ Asset health data was saved to file '{output_file}'.")
print(f"📊 Number of records: {len(df):,} - Number of variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic justification and persuading the petrochemical (Business Case)

What makes this product "sellable and tangible" to a petrochemical's management (not merely an analytical tool):

| Indicator | Typical current state in large petrochemicals | With Khalij-CAPM | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Unplanned shutdown due to critical compressor failure | 1 to 3 events per year, each causing 2 to 5 days of unit shutdown | Detection 72 hours earlier → planned shutdown instead of emergency | Preventing a multi-day shutdown equal to several million dollars of production loss per event |
| Furnace decoking scheduling | Time-based (calendar) or late after a noticeable efficiency drop | Predictive based on the actual pressure-drop/temperature trend | 2 to 4% increase in ethylene yield per furnace cycle + reduced coil damage risk |
| Critical spare-parts inventory | Holding high safety stock ("the more the better") due to uncertainty | Optimal inventory based on the RUL confidence interval of multiple equipment simultaneously | 15 to 30% reduction in working capital locked in the spare-parts warehouse |
| Polymerization catalyst activity loss | Replacement based on a fixed period or noticeable quality loss | Replacement/regeneration planning at the economic optimum | Reduced catalyst consumption + grade quality stability |

**Realistic payback:** By preventing only **one** unplanned compressor shutdown in the first year, the full implementation and pilot cost of this system is usually offset at that first event — this is the simplest argument for budget approval at petrochemical management level.

---

## 5. Allocation of products 1 to 4 to the subsidiaries of the Persian Gulf Holding (PGPIC)

> The full details of the reasoning are in the separate file [`../نقشه-تخصیص-محصولات-به-شرکت-های-هلدینگ.md`](../نقشه-تخصیص-محصولات-به-شرکت-های-هلدینگ.md) (the product-to-company allocation map). Summary:

| Product | Proposed target company | Short reason |
| :--- | :--- | :--- |
| 1 – Production process optimization | **Bandar Imam Petrochemical (BIPC)** | Parent olefin/aromatics/polymer complex with a high diversity of reactors requiring multi-objective optimization |
| 2 – Digital transformation and value chain | **Persian Gulf Holding HQ (PGPIC)** | The product scope is explicitly "all subsidiaries"; the real customer is at the holding/HQ level, not one subsidiary |
| 3 – Energy, carbon and sustainability | **Shahid Tondgooyan Petrochemical (PTA/PET)** | The country's only PTA producer, a highly energy-intensive process with a high Scope 1/2 load; exactly matching the product name ("olefin and PTA units") |
| 4 – Asset health monitoring (this document) | **Maroun Petrochemical** | The holding's largest olefin/polyethylene/polypropylene complex with the largest fleet of critical compressors and cracking furnaces; the highest financial risk from unplanned shutdown |

---

## 6. Proposed evolution roadmap (Phase 1–8) — for later implementation similar to products 1 to 3

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator (this document) + connection to the Kafka/TimescaleDB shared with product 1 |
| 2 | Rotating equipment fault detection/RUL model (LSTM + Survival Analysis) |
| 3 | Cracking furnace virtual sensor (decoking scheduling) |
| 4 | Catalyst deterioration virtual sensor |
| 5 | Multi-objective maintenance optimizer (NSGA-II) + CMMS/SAP-PM connection |
| 6 | "Maintenance command center" dashboard + real-time alert/recommendation |
| 7 | Security, RBAC, Audit trail (full reuse of product 1's security pattern) |
| 8 | Operational pilot on one real compressor train + one cracking furnace at Maroun Petrochemical |

---

## 7. Summary of patentable innovations

1. **Predictive decoking-scheduling virtual sensor** for cracking furnaces based on trend learning (not a fixed engineering threshold).
2. **An integrated remaining-useful-life prediction model with an uncertainty interval** for rotating equipment + furnace + catalyst in a single digital twin.
3. **Simultaneous multi-asset optimization of the maintenance schedule and spare-parts inventory** based on RUL intervals (not calendar scheduling).
4. **A closed learning loop (Closed-Loop)** that records the actual result of every maintenance action for continuous model retraining.

---

## 8. Sources and patent records reviewed (Sources)

- [US11650184 — System and method for monitoring rotating equipment](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11650184)
- [US20180282633A1 — Rotating equipment in a petrochemical plant or refinery (Google Patents)](https://patents.google.com/patent/US20180282633A1/en)
- [US10913905 — Catalyst cycle length prediction using eigen analysis](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/10913905)
- [US12044642 — Method and device for estimating outer surface temperature of radiant coil of cracking furnace](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/12044642)
- [Baker Hughes — Condition Monitoring of Reciprocating Compressors, Oil & Gas](https://www.bakerhughes.com/bently-nevada/orbit-home/orbit-article/condition-monitoring-reciprocating-compressors-oil-and-gas)
- [Remaining Useful Life prediction with uncertainty quantification (arXiv)](https://arxiv.org/pdf/2109.11579)
- [PNNL — Predicting Catalyst Degradation with Machine Learning](https://www.pnnl.gov/news-media/predicting-catalyst-degradation-machine-learning)
- [ScienceDirect — Cyclic scheduling for an ethylene cracking furnace system](https://www.sciencedirect.com/science/article/abs/pii/S0098135417300248)
- [Shana — Iran achieves rotating machine condition monitoring system technology](https://www.shana.ir/news/640166/)
- [Persian Wikipedia — Persian Gulf Petrochemical Industries Company](https://fa.wikipedia.org/wiki/%D8%B4%D8%B1%DA%A9%D8%AA_%D8%B5%D9%86%D8%A7%DB%8C%D8%B9_%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D8%AE%D9%84%DB%8C%D8%AC_%D9%81%D8%A7%D8%B1%D8%B3)
- [Persian Wikipedia — Maroun Petrochemical Company](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D9%85%D8%A7%D8%B1%D9%88%D9%86)
- [PGPIC — About us](https://www.pgpic.ir/)
