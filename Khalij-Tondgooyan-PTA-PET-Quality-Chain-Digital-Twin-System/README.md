# Khalij-Tondgooyan-PTA-PET-Quality-Chain-Digital-Twin-System (Khalij-TPQC)

## Intelligent system linking PTA oxidation quality (4-CBA impurity and b* color) to intrinsic viscosity (IV) and optimization of solid-state polymerization (SSP) of bottle-grade polyester — a dedicated product of Shahid Tondgooyan Petrochemical Company

> This document is the **second dedicated product** for Shahid Tondgooyan Petrochemical Company (the only bottle-grade PET producer in Iran). The holding's general product 3 (energy/carbon) was previously assigned to this company and focuses on energy consumption and Scope 1/2/3 carbon. The present product complements it and focuses on the **quality chain** (not energy) from the PTA oxidation reactor to the final bottle-grade PET product — a gap not covered by any of products 1 to 4.

---

## 0. Understanding Shahid Tondgooyan Petrochemical Company and the technical gap

**Sources:** [Persian Wikipedia — Shahid Tondgooyan Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D8%AA%D9%86%D8%AF%DA%AF%D9%88%DB%8C%D8%A7%D9%86), [Shaguya analysis — Signal](https://isignal.ir/%D8%A8%D8%B1%D8%B1%D8%B3%DB%8C-%D9%88-%D8%AA%D8%AD%D9%84%DB%8C%D9%84-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%B4%D9%87%DB%8C%D8%AF-%D8%AA%D9%86%D8%AF%DA%AF%D9%88%DB%8C%D8%A7%D9%86/)

### Products and operational status

| Feature | Value |
|---|---|
| Nominal PTA (purified terephthalic acid) capacity | 700,000 tons/year |
| Nominal PET capacity | 888,000 tons/year |
| Position | The only **bottle-grade** PET producer in Iran |
| Current utilization rate | Rose from 61% (1398 SH) to 83% of nominal capacity — an upward trend with potential for further growth |
| Main feed (paraxylene) | Mainly supplied from Nouri Petrochemical |

### Technical process (scientific basis for product design)

The PTA→PET chain has two critical quality stages:
1. **Oxidation of PX to PTA** in a titanium reactor (due to the corrosive acetic acid/bromide environment) with a cobalt-manganese-bromine (Co:Mn:Br) catalyst; vital output: the concentration of the **4-CBA** impurity and the **b-value** color, which determine the final PTA quality.
2. **PET polymerization and solid-state polymerization (SSP)** to reach the **intrinsic viscosity (IV)** suitable for bottle grade; IV is directly a function of the incoming PTA quality (4-CBA/color) and the SSP conditions (temperature, nitrogen flow, residence time).

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Tondgooyan |
|---|---|
| Product 3 (previously assigned to Tondgooyan) | Focuses purely on energy/carbon; it does not address the causal relationship "PTA quality ← final PET quality" and cannot diagnose the root cause of loss of IV or color in the final product |
| Products 1, 2, 4 | None covers polyester IV, 4-CBA impurity or the SSP process; these parameters are unique to the bottle-grade polyester chain |

**Conclusion:** Tondgooyan needs a dedicated PTA→PET quality chain that acts as a second, complementary product alongside the existing energy product (product 3).

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 4,755,048** – *Optical analysis of impurity absorptions* (optical measurement of PTA b-value at 445 nm wavelength) | Offline/point measurement tool; does not address prediction or connection to the downstream PET process | Converting the point measurement to a predictive virtual sensor connected to the oxidation reactor DCS |
| 2 | **EP 2,754,649 A1** – *Method for determining impurity concentration in terephthalic acid* | 4-CBA measurement method; lacks a learning-based prediction model or a link to downstream quality | An ML model for 4-CBA prediction from process parameters (Co:Mn:Br ratio, temperature, O2) + a direct link to the final IV |
| 3 | **US 7,557,180** – *Solid phase continuous polymerisation of PET reactor and process* | SSP equipment/process design; lacks a real-time learning-based IV prediction layer | A real-time SSP IV virtual sensor with simultaneous upstream PTA quality input |
| 4 | Academic studies on automated PET viscometry (Polymer Char) | Automated laboratory measurement, not prediction before batch production | IV prediction **before** the end of the batch for real-time correction of SSP parameters |

### Core Patentable Claim

> **"A quality-chain digital twin system that, for the first time, connects learning-based prediction of the 4-CBA impurity and b* color of the PTA oxidation reactor as a direct input to the downstream solid-state polymerization (SSP) intrinsic viscosity (IV) prediction model, and — before the batch ends — automatically proposes correction of SSP parameters (temperature/nitrogen flow/residence time) to reach the bottle-grade target IV."**

A direct and real-time link of the PTA oxidation reactor quality to the downstream SSP process was not seen in an integrated form in the patent literature found.

---

## 2. SRS Document – Dedicated product of Shahid Tondgooyan Petrochemical

### 2-1. Introduction
**Purpose:** Guarantee the stable quality of bottle-grade PET through early prediction of PTA quality and real-time correction of the SSP process before the end of each batch.

**Field challenges:**
- Fluctuation of PTA quality (4-CBA, b* color), which is usually identified with laboratory delay and carried over to downstream PET batches.
- IV control in SSP is usually done with fixed settings, without actually accounting for the incoming PTA quality of each batch.
- As the utilization rate rises (from 61% to 83% of capacity), the pressure to maintain uniform quality at a higher production rate has increased.

**Scope:** Shahid Tondgooyan complex; connection to the DCS of the PTA oxidation unit and the SSP/PET polymerization unit.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous oxidation reactor data (temperature, pressure, Co:Mn:Br ratio, O2 concentration) | High |
| R-GEN-02 | Reception of SSP unit data (temperature, nitrogen flow, residence time, laboratory IV of the previous batch) | High |
| R-GEN-03 | Batch-to-batch quality tracking dashboard from PTA to final PET | High |
| R-GEN-04 | Connection to the laboratory system (LIMS) for 4-CBA/b-value/IV results | Medium |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-PTA-01 | Real-time virtual sensor of 4-CBA impurity and b* color from oxidation reactor parameters | PTA quality virtual sensor without waiting for the laboratory |
| FR-CHAIN-01 | Final PET IV prediction model from the combination of incoming PTA quality and SSP conditions | **Direct upstream-downstream quality link (main innovation)** |
| FR-CHAIN-02 | Recommendation of real-time correction of SSP parameters (temperature/nitrogen flow/time) to reach the target IV before the batch ends | **Cross-process predictive control (main innovation)** |
| FR-CAT-01 | Monitoring of the Co:Mn:Br catalyst ratio and alert on deviation from the optimal range | Catalyst system health monitoring |
| FR-ALERT-01 | Off-spec risk alert before batch completion with financial impact estimation | Preventive action recommender |
| FR-LOOP-01 | Recording real LIMS results for continuous retraining of the virtual sensor | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | 4-CBA/color virtual sensor delay | Less than 30 seconds |
| NFR-PER-02 | Final IV prediction accuracy (MAPE) | Less than 5% |
| NFR-AVAIL-01 | System availability | 99.9% |
| NFR-SEC-01 | AES-256 encryption + RBAC for PTA/SSP/quality-control operators | Mandatory |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │ (RBAC + 2FA)
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│PTA/SSP          ││ PTA Quality    ││ IV Prediction +  │
│Ingestion (DCS + ││ Soft-Sensor    ││ SSP Control      │
│ LIMS)           ││ (4-CBA/color)  ││ Recommendation   │
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
| `services/pta-ssp-ingestion/` | Connection to PTA oxidation and SSP DCS + LIMS |
| `services/quality-chain-model/` | 4-CBA/color virtual sensor + IV prediction model |
| `services/ssp-control-recommender/` | Real-time SSP parameter correction recommender |
| `shared/` | Reuse of products 1-4 (especially this company's energy product 3) |

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

# 1. PTA oxidation reactor
co_mn_br_ratio = 20 + 3 * np.sin(t * 0.1) + np.random.normal(0, 0.5, NUM_RECORDS)
oxidation_temp_c = 195 + 3 * np.sin(t * 0.12) + np.random.normal(0, 0.8, NUM_RECORDS)
o2_concentration_percent = 4.2 + 0.3 * np.sin(t * 0.15) + np.random.normal(0, 0.1, NUM_RECORDS)

# 2. PTA quality (virtual sensor)
cba_4_ppm = 250 - 4 * (co_mn_br_ratio - 20) + 2 * (oxidation_temp_c - 195) + np.random.normal(0, 8, NUM_RECORDS)
cba_4_ppm = np.clip(cba_4_ppm, 100, 400)
pta_color_b = 1.2 + 0.02 * (cba_4_ppm - 250) / 10 + np.random.normal(0, 0.1, NUM_RECORDS)

# 3. SSP unit
ssp_temp_c = 215 + 2 * np.sin(t * 0.08) + np.random.normal(0, 0.5, NUM_RECORDS)
n2_flow_rate_nm3h = 1200 + 50 * np.sin(t * 0.09) + np.random.normal(0, 15, NUM_RECORDS)
ssp_residence_time_h = 18 + np.random.normal(0, 0.5, NUM_RECORDS)

# 4. Final PET quality
final_iv_dlg = 0.80 - 0.0008 * (cba_4_ppm - 250) + 0.002 * (ssp_temp_c - 215) + 0.0005 * (ssp_residence_time_h - 18) + np.random.normal(0, 0.005, NUM_RECORDS)

# 5. Label
off_spec_risk = ((final_iv_dlg < 0.78) | (final_iv_dlg > 0.84) | (pta_color_b > 1.8)).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'co_mn_br_ratio': np.round(co_mn_br_ratio, 2),
    'oxidation_temp_c': np.round(oxidation_temp_c, 2),
    'o2_concentration_percent': np.round(o2_concentration_percent, 3),
    'cba_4_ppm': np.round(cba_4_ppm, 1),
    'pta_color_b': np.round(pta_color_b, 3),
    'ssp_temp_c': np.round(ssp_temp_c, 2),
    'n2_flow_rate_nm3h': np.round(n2_flow_rate_nm3h, 1),
    'ssp_residence_time_h': np.round(ssp_residence_time_h, 2),
    'final_iv_dlg': np.round(final_iv_dlg, 4),
    'off_spec_risk': off_spec_risk,
})

df.to_csv("tondgooyan_pta_pet_quality_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-TPQC | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Detecting PTA quality deviation | With laboratory delay, usually after entering the PET batch | Real-time prediction before affecting SSP | Reduced off-spec batches on the 888 thousand tons/year PET capacity |
| Bottle-grade IV control | Fixed SSP settings, no reaction to batch-to-batch PTA quality fluctuation | Real-time SSP parameter correction based on actual incoming quality | Increased quality uniformity at a higher production rate (83% of capacity and growing) |
| Risk of product return from bottling customers | Due to IV/color fluctuation | Reduced with predictive control | Maintaining the exclusive position of Iran's only bottle-grade PET producer |

**Payback:** Given Tondgooyan's exclusive position in the domestic bottle-grade PET market, even a minor reduction in the off-spec rate on a capacity near 900 thousand tons has considerable economic value.

---

## 5. Proposed Evolution Roadmap (Phase 1-6)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator + Kafka/TimescaleDB connection shared with this company's product 3 |
| 2 | 4-CBA and b* color virtual sensor of the oxidation reactor |
| 3 | Final IV prediction model from combined PTA quality + SSP conditions |
| 4 | Real-time SSP parameter correction recommender |
| 5 | Batch-to-batch quality tracking in an integrated dashboard |
| 6 | Operational pilot on one real SSP line |

---

## 6. Summary of Patentable Innovations

1. **Direct and real-time link of the PTA oxidation reactor quality (4-CBA/b* color) to the downstream SSP IV prediction model**.
2. **A predictive SSP parameter correction recommender before the batch ends** to reach the bottle-grade target IV.
3. **Batch-to-batch chain quality tracking** from the oxidation reactor to the final product in a single model.

---

## 7. References

- [Persian Wikipedia — Shahid Tondgooyan Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D8%AA%D9%86%D8%AF%DA%AF%D9%88%DB%8C%D8%A7%D9%86)
- [Review and analysis of Shahid Tondgooyan Petrochemical Company — Signal](https://isignal.ir/%D8%A8%D8%B1%D8%B1%D8%B3%DB%8C-%D9%88-%D8%AA%D8%AD%D9%84%DB%8C%D9%84-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%B4%D9%87%DB%8C%D8%AF-%D8%AA%D9%86%D8%AF%DA%AF%D9%88%DB%8C%D8%A7%D9%86/)
- [US4755048 — Optical analysis of impurity absorptions (PTA b-value)](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/4755048)
- [EP2754649A1 — Method for determining impurity concentration in terephthalic acid](https://patents.google.com/patent/EP2754649A1/en)
- [US7557180 — Solid phase continuous polymerisation of PET reactor and process](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/7557180)
- [Polymer Char — Automated Intrinsic Viscosity Analysis in PET Production Environments](https://polymerchar.com/library/publications/automated-intrinsic-viscosity-analysis-in-pet-production-environments)
