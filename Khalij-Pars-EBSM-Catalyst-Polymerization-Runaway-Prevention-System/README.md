# Khalij-Pars-EBSM-Catalyst-Polymerization-Runaway-Prevention-System (Khalij-PECR)

## Intelligent system for predicting the deterioration of the iron-potassium ethylbenzene dehydrogenation catalyst and preventive warning of inhibitor depletion/runaway polymerization of styrene monomer — a dedicated product of Pars Petrochemical Company

> This document is a **dedicated** product for Pars Petrochemical Company (Pars Special Economic Energy Zone, Assaluyeh), which consists of three units: ethane extraction, ethylbenzene (EB) and styrene monomer (SM) — a unique process chain among the holding's companies.

---

## 0. Understanding Pars Petrochemical Company and the technical gap

**Sources:** [PGPIC — Pars Petrochemical](https://pgpic.ir/en/Subsidiaries/Production-Companies/Pars-Petrochemical-Co), [wikiplast.ir — Pars Petrochemical](https://wikiplast.ir/petros/68/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D9%BE%D8%A7%D8%B1%D8%B3)

### Products and process units

| Unit | Description |
|---|---|
| Ethane extraction | Initial feed from natural gas/condensate |
| Ethylbenzene (EB) | Benzene alkylation with ethylene |
| Styrene monomer (SM) | Catalytic dehydrogenation of EB with an iron-potassium catalyst (Fe-K₂O, active phase KFeO₂) |

### Critical technical process (basis of product design)

The EB→SM chain has two serious and strongly interrelated technical risks:
1. **Deterioration of the Fe-K₂O dehydrogenation catalyst**: potassium migration, reduction of Fe³⁺ to Fe²⁺ and coking; catalyst activity falls to 50% in the first month and to 40% by month thirty.
2. **Runaway polymerization of styrene monomer**: styrene is highly prone to spontaneous exothermic polymerization; the TBC inhibitor (4-tert-butylcatechol, ~15 ppm) requires dissolved oxygen to be effective and is rapidly depleted with increased temperature or contact with water/a separate phase — an event that has led to real disasters (including explosions) in the global industry.

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Pars |
|---|---|
| Product 4 (catalyst deterioration) | Designed for the PE/PP polymerization catalyst; the Fe-K₂O dehydrogenation catalyst (potassium migration/coking mechanism) has completely different physics |
| No holding product | Addresses the risk of **runaway monomer polymerization in the distillation column/storage tank** (a phenomenon unique to vinyl monomers such as styrene) |

**Conclusion:** Pars needs a digital twin that directly links upstream catalyst deterioration to downstream safety risk (inhibitor depletion/runaway polymerization) — because the loss of catalyst activity changes the thermal load and temperature of the downstream distillation column.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 4,758,543 / US 6,184,174** – ethylbenzene to styrene dehydrogenation catalysts | Chemical catalyst formulation; lacks a learning-based prediction layer for regeneration scheduling | An ML deterioration-prediction model from real DCS data (not a new formulation) |
| 2 | **US 7,128,826** – *Polymerization inhibitor for styrene dehydrogenation units* | Chemical alternative-inhibitor solution; a material approach, not real-time inhibitor-depletion prediction | A real-time prediction model of the TBC level and polymerization risk from actual temperature/oxygen/residence time |
| 3 | *Probing into Styrene Polymerization Runaway Hazards* (ACS Omega) — lumped kinetic modeling | Laboratory/offline simulation model; not connected to real DCS data or the upstream catalyst state | Real-time connection to the real DCS + direct link to the upstream catalyst state |
| 4 | *Modeling Catalyst Deactivation In Dehydrogenation of Ethylbenzene to Styrene* (AIChE) | Offline catalyst deterioration modeling; lacks a link to downstream safety risk | **Direct link of catalyst deterioration to downstream runaway polymerization risk (a completely empty gap)** |

### Core Patentable Claim

> **"A risk-chain digital twin system that, for the first time, connects the learning-based prediction of Fe-K₂O dehydrogenation catalyst deterioration (potassium migration and coking) as a direct input to the real-time prediction model of TBC inhibitor depletion and the runaway polymerization risk of styrene in the downstream distillation column/storage tank — arguing that the loss of catalyst activity changes the thermal load and operating temperature of the downstream distillation unit and directly increases the inhibitor depletion rate."**

---

## 2. SRS Document – Dedicated product of Pars Petrochemical

### 2-1. Introduction
**Purpose:** Increase the EB-to-SM conversion yield through catalyst deterioration prediction, and increase process safety through preventive prediction of styrene runaway polymerization risk.

**Field challenges:**
- Rapid loss of catalyst activity (50% in the first month) which requires precise regeneration/replacement scheduling.
- Risk of styrene runaway polymerization if the TBC inhibitor is depleted (high temperature, contact with water, lack of dissolved oxygen) — a real and documented danger in the global industry.
- Lack of an integrated view of the effect of catalyst loss on downstream distillation conditions.

**Scope:** Pars Petrochemical complex, Assaluyeh; connection to the DCS of the EB, dehydrogenation and SM distillation units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous dehydrogenation reactor data (temperature, pressure, EB conversion) | High |
| R-GEN-02 | Reception of SM distillation column/storage tank data (temperature, TBC concentration, dissolved oxygen) | Critical (HSE) |
| R-GEN-03 | Integrated catalyst-safety dashboard with a separate critical alert | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-CAT-01 | Prediction of the Fe-K₂O catalyst deterioration trend (potassium migration/coking) with a confidence interval | Dedicated dehydrogenation catalyst deterioration prediction |
| FR-SAFE-01 | Real-time prediction of residual TBC concentration and runaway polymerization risk | Inhibitor virtual sensor with preventive alert |
| FR-CHAIN-01 | Model linking the effect of catalyst activity loss on the thermal load/distillation temperature and hence the TBC depletion rate | **Direct upstream catalyst-downstream safety link (main innovation)** |
| FR-ALERT-01 | Tiered HSE alert (critical for polymerization risk) separate from the catalyst yield alert | Dual recommender |
| FR-LOOP-01 | Recording actual TBC sampling results and catalyst regeneration for retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-SAFE-01 | Delay of the runaway polymerization risk alert | Less than 10 seconds |
| NFR-PER-01 | TBC concentration prediction accuracy (MAPE) | Less than 15% |
| NFR-AVAIL-01 | Availability of the safety module | 99.99% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│EB/Dehydrogenation││ Catalyst Decay ││ TBC Depletion +  │
│/Distillation     ││ Model          ││ Runaway Risk     │
│Ingestion         ││                ││ Chain Model      │
└──────┬───────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬─────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/eb-sm-ingestion/` | Connection to the DCS of dehydrogenation and SM distillation |
| `services/catalyst-decay-model/` | Fe-K₂O deterioration prediction model |
| `services/tbc-runaway-risk-model/` | Chain model linking catalyst and safety |
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

# 1. Dehydrogenation catalyst
catalyst_activity_percent = 100 - 0.004 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.6, NUM_RECORDS)
catalyst_activity_percent = np.clip(catalyst_activity_percent, 38, 100)
eb_conversion_percent = 65 * (catalyst_activity_percent / 100) + np.random.normal(0, 0.5, NUM_RECORDS)

# 2. Effect on the thermal load and temperature of the downstream distillation column
distillation_temp_c = 60 + 0.15 * (100 - catalyst_activity_percent) + 2 * np.sin(t * 0.1) + np.random.normal(0, 0.5, NUM_RECORDS)
dissolved_o2_ppm = 12 - 0.05 * (distillation_temp_c - 60) + np.random.normal(0, 0.5, NUM_RECORDS)
dissolved_o2_ppm = np.clip(dissolved_o2_ppm, 2, 15)

# 3. TBC inhibitor concentration (faster depletion at higher temperature/less oxygen)
tbc_depletion_rate = 0.02 + 0.001 * (distillation_temp_c - 60) - 0.0005 * dissolved_o2_ppm
tbc_ppm = 15 - np.cumsum(np.clip(tbc_depletion_rate, 0, None)) / 200 + np.random.normal(0, 0.3, NUM_RECORDS)
tbc_ppm = np.clip(tbc_ppm, 2, 16)

# 4. Labels
catalyst_regen_needed_30d = (catalyst_activity_percent < 55).astype(int)
runaway_risk_critical = ((tbc_ppm < 8) | (dissolved_o2_ppm < 5)).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'catalyst_activity_percent': np.round(catalyst_activity_percent, 2),
    'eb_conversion_percent': np.round(eb_conversion_percent, 2),
    'distillation_temp_c': np.round(distillation_temp_c, 2),
    'dissolved_o2_ppm': np.round(dissolved_o2_ppm, 2),
    'tbc_ppm': np.round(tbc_ppm, 2),
    'catalyst_regen_needed_30d': catalyst_regen_needed_30d,
    'runaway_risk_critical': runaway_risk_critical,
})

df.to_csv("pars_ebsm_catalyst_safety_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-PECR | Approximate financial/safety impact |
| :--- | :--- | :--- | :--- |
| EB→SM conversion yield | Rapid loss without optimal regeneration scheduling | Early prediction and optimal regeneration scheduling | Increased effective styrene monomer yield |
| Runaway polymerization risk | Periodic TBC sampling | Real-time preventive alert | Preventing a catastrophic accident (explosion/fire) — a documented risk in the global industry |

**Payback:** Given the real history of global styrene runaway polymerization accidents, the value of prevention is incomparable to the implementation cost; moreover, improved catalyst yield has direct economic value.

---

## 5. Proposed Evolution Roadmap (Phase 1-5)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Fe-K₂O catalyst deterioration prediction model |
| 3 | TBC concentration and runaway polymerization risk virtual sensor (HSE priority) |
| 4 | Chain model linking catalyst and safety |
| 5 | Dashboard + operational pilot under HSE supervision |

---

## 6. Summary of Patentable Innovations

1. **Direct linking of upstream dehydrogenation catalyst deterioration to downstream runaway polymerization risk** in a single chain model.
2. **Real-time virtual sensor of TBC inhibitor concentration** with a preventive alert before falling below the safe threshold.
3. **Optimal catalyst regeneration scheduling** taking into account its effect on downstream safety risk.

---

## 7. References

- [PGPIC — Pars Petrochemical Co.](https://pgpic.ir/en/Subsidiaries/Production-Companies/Pars-Petrochemical-Co)
- [Wikiplast — Pars Petrochemical](https://wikiplast.ir/petros/68/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D9%BE%D8%A7%D8%B1%D8%B3)
- [US7128826 — Polymerization inhibitor for styrene dehydrogenation units](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/7128826)
- [US4758543 — Dehydrogenation catalyst](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/4758543)
- [Probing into Styrene Polymerization Runaway Hazards — ACS Omega](https://pubs.acs.org/doi/10.1021/acsomega.9b00004)
- [Modeling Catalyst Deactivation In Dehydrogenation of Ethylbenzene to Styrene — AIChE](https://proceedings.aiche.org/conferences/aiche-spring-meeting-and-global-congress-on-process-safety/2011/proceeding/paper/28e-modeling-catalyst-deactivation-dehydrogenation-ethylbenzene-styrene-0)
- [Metrohm — TBC in Styrene tank application note](https://www.metrohm.com/content/dam/metrohm/shared/documents/application-notes/an-p/AN-PAN-1027.pdf)
