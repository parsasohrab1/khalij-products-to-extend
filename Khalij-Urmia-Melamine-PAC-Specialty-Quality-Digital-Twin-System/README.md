# Khalij-Urmia-Melamine-PAC-Specialty-Quality-Digital-Twin-System (Khalij-UMPQ)

## Intelligent system for real-time quality control of melamine crystallization (purity/particle size distribution) and virtual sensor of polyaluminum chloride (PAC) basicity ratio — a dedicated product of Urmia Petrochemical Company

> This document is a **dedicated** product for Urmia Petrochemical Company (Sharoum) — the only holding company with a portfolio of completely specialty products (melamine crystal, ammonium sulfate, sulfuric acid, polyaluminum chloride) instead of conventional olefin/aromatics petrochemicals.

---

## 0. Understanding Urmia Petrochemical Company and the technical gap

**Sources:** [isignal.ir — Introduction to Urmia Petrochemical (Sharoum)](https://isignal.ir/%D9%85%D8%B9%D8%B1%D9%81%DB%8C-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%A7%D8%B1%D9%88%D9%85%DB%8C%D9%87-%D8%B4%D8%A7%D8%B1%D9%88%D9%85/), [Shana — Urmia polyaluminum chloride unit](https://www.shana.ir/news/459291/)

### Products and Process Nature

| Product | Feature |
|---|---|
| Melamine crystal | The company's exclusive/flagship product — from the reaction of urea at high temperature and pressure |
| Ammonium sulfate | From the reaction of ammonia with domestically produced sulfuric acid |
| Sulfuric acid | Capacity 50,000 tons/year |
| Solid polyaluminum chloride (PAC) | A new national project, currently operating |
| Location | Km 30 of the Urmia-Mahabad road, West Azerbaijan |

**Fundamental difference from the holding's other companies:** Urmia is not an olefin/aromatics complex but a **specialty multi-product chemical complex** with two completely different crystallization/precipitation processes: (a) melamine crystallization whose quality is determined by the **purity and particle size distribution of the crystals** (use in resin/laminate), and (b) PAC synthesis whose quality is determined by the **basicity ratio (Basicity Ratio = [OH]/[Al])** (use in water treatment).

### Technical Gap Relative to the Holding's Products 1 to 4

| Holding product | Why it is not enough for Urmia |
|---|---|
| All holding petrochemical products | None covers melamine crystallization or polyaluminum chloride synthesis; these products are entirely outside the scope of olefin/aromatics/polymer petrochemicals |

**Conclusion:** Urmia needs a completely dedicated multi-product quality control platform (crystallization + chemical precipitation) that has no precedent in any other holding product.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 6,166,204 A** – *Crystalline melamine* / **WO2002022589A1** – *Process for production of high purity melamine from urea* | Chemical process to achieve high purity; a process approach, not software real-time monitoring/control | A software layer for real-time crystallization monitoring and control on the existing process |
| 2 | *Progress of Machine Learning in Molecular Crystal Design and Crystallization Development* (ScienceDirect) | General ML framework for molecular crystallization; does not address melamine or the fertilizer/resin industry specifically | Dedicated adaptation for industrial melamine crystallization with real DCS data |
| 3 | **KR 101409870 B1** – *Method of Preparation for High basicity polyaluminum chloride coagulant* | Chemical formulation for high-basicity PAC; lacks a real-time basicity ratio virtual sensor | A real-time Basicity Ratio virtual sensor without waiting for the laboratory |
| 4 | *Synthesis of polyaluminum chloride: Optimization of process parameters* (ScienceDirect) | Offline optimization of synthesis parameters (temperature, concentration, time); not a real-time industrial system | Conversion to a real-time industrial system connected to real DCS |
| 5 | No source found | Combination of two completely different fields (organic melamine crystallization + inorganic PAC precipitation) in a single quality platform | **A single multi-process quality control platform (main innovation)** |

### Core Patentable Claim

> **"An integrated intelligent multi-product quality control platform that, for the first time, combines real-time control of melamine crystallization (purity and particle size distribution from the temperature/pressure/residence time parameters of the urea-melamine reactor) with a real-time virtual sensor of the polyaluminum chloride basicity ratio (from the concentration/temperature/synthesis time parameters) in a single software architecture reusing shared utility infrastructure (sulfuric acid/ammonia) — despite the fundamental chemical difference between these two processes (organic crystallization versus inorganic precipitation/polymerization)."**

---

## 2. SRS Document – Dedicated product of Urmia Petrochemical

### 2-1. Introduction
**Purpose:** Guarantee the stable quality of melamine crystal (purity/particle size) and PAC (basicity ratio) through real-time monitoring and control.

**Field challenges:**
- The quality of melamine crystal (purity, particle size distribution, bulk density) is usually measured with laboratory delay.
- The PAC basicity ratio — the most important indicator of its effectiveness in water treatment — requires precise control of the synthesis parameters.
- Two production lines with different physics are run with separate, non-integrated quality control tools.

**Scope:** Urmia complex; connection to the DCS of the melamine, PAC, sulfuric acid and ammonium sulfate units.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous melamine reactor data (temperature, pressure, residence time) | High |
| R-GEN-02 | Reception of PAC synthesis data (AlCl₃ concentration, temperature, reaction time) | High |
| R-GEN-03 | Integrated multi-product quality dashboard | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-MEL-01 | Real-time prediction of the purity and particle size distribution of melamine crystals | Melamine crystallization virtual sensor |
| FR-PAC-01 | Real-time virtual sensor of the PAC basicity ratio ([OH]/[Al]) | Basicity Ratio virtual sensor |
| FR-PLATFORM-01 | A single multi-process quality monitoring architecture with shared infrastructure reuse | **Integrated multi-process platform (main innovation)** |
| FR-ALERT-01 | Quality deviation alert for each line with a parameter correction recommendation | Real-time correction recommender |
| FR-LOOP-01 | Recording actual laboratory results of both lines for retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Melamine purity prediction accuracy (MAPE) | Less than 5% |
| NFR-PER-02 | PAC Basicity virtual sensor accuracy | Less than 10% |
| NFR-AVAIL-01 | System availability | 99% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┐
┌───▼────────────┐┌───────▼────────┐
│Melamine/PAC     ││ Multi-Process   │
│Ingestion (DCS)  ││ Quality Twin    │
│                 ││ (Crystal + PAC) │
└──────┬──────────┘└───────┬────────┘
       └──────────┬────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/melamine-pac-ingestion/` | Connection to the DCS of both lines |
| `services/multi-process-quality-twin/` | Shared crystal/precipitate virtual sensor |
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

# 1. Melamine reactor
melamine_reactor_temp_c = 390 + 8 * np.sin(t * 0.1) + np.random.normal(0, 2, NUM_RECORDS)
melamine_residence_time_min = 25 + np.random.normal(0, 1, NUM_RECORDS)
melamine_purity_percent = 99.2 - 0.02 * np.abs(melamine_reactor_temp_c - 390) + np.random.normal(0, 0.1, NUM_RECORDS)
melamine_particle_size_um = 120 + 3 * (melamine_residence_time_min - 25) + np.random.normal(0, 5, NUM_RECORDS)

# 2. PAC synthesis
alcl3_concentration_m = 0.6 + 0.05 * np.sin(t * 0.08) + np.random.normal(0, 0.02, NUM_RECORDS)
pac_synthesis_temp_c = 70 + 3 * np.sin(t * 0.07) + np.random.normal(0, 1, NUM_RECORDS)
pac_basicity_ratio = 2.2 + 0.15 * (pac_synthesis_temp_c - 70) / 10 - 0.1 * (alcl3_concentration_m - 0.6) + np.random.normal(0, 0.03, NUM_RECORDS)

# 3. Labels
melamine_off_spec = (melamine_purity_percent < 98.8).astype(int)
pac_off_spec = ((pac_basicity_ratio < 2.0) | (pac_basicity_ratio > 2.4)).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'melamine_reactor_temp_c': np.round(melamine_reactor_temp_c, 2),
    'melamine_residence_time_min': np.round(melamine_residence_time_min, 2),
    'melamine_purity_percent': np.round(melamine_purity_percent, 3),
    'melamine_particle_size_um': np.round(melamine_particle_size_um, 1),
    'alcl3_concentration_m': np.round(alcl3_concentration_m, 3),
    'pac_synthesis_temp_c': np.round(pac_synthesis_temp_c, 2),
    'pac_basicity_ratio': np.round(pac_basicity_ratio, 3),
    'melamine_off_spec': melamine_off_spec,
    'pac_off_spec': pac_off_spec,
})

df.to_csv("urmia_melamine_pac_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-UMPQ | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| Melamine quality | Laboratory delay, risk of off-spec production | Real-time prediction and immediate correction | Reduced waste of the company's flagship/exclusive product |
| PAC quality | Laboratory delay of the basicity ratio | Real-time virtual sensor | Guaranteeing the effectiveness of the new product in the water treatment market |

**Payback:** Given the exclusive/strategic nature of melamine crystal and the importance of a successful PAC market entry (a new national project), guaranteeing the quality of these two products has high strategic value for export development.

---

## 5. Proposed evolution roadmap (Phase 1-4)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Melamine quality virtual sensor |
| 3 | PAC Basicity virtual sensor |
| 4 | Integrated dashboard + operational pilot |

---

## 6. Summary of Patentable Innovations

1. **Real-time virtual sensor of melamine crystal purity and particle size distribution**.
2. **Real-time virtual sensor of the PAC basicity ratio**.
3. **A single multi-process quality control platform** covering two completely different chemical fields (organic crystallization and inorganic precipitation) in an integrated architecture.

---

## 7. References

- [isignal.ir — Introduction to Urmia Petrochemical Company (Sharoum)](https://isignal.ir/%D9%85%D8%B9%D8%B1%D9%81%DB%8C-%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C-%D8%A7%D8%B1%D9%88%D9%85%DB%8C%D9%87-%D8%B4%D8%A7%D8%B1%D9%88%D9%85/)
- [Shana — Urmia Petrochemical polyaluminum chloride unit](https://www.shana.ir/news/459291/)
- [US6166204A — Crystalline melamine](https://patents.google.com/patent/US6166204A/de)
- [WO2002022589A1 — Process for the production of high purity melamine from urea](https://patents.google.com/patent/WO2002022589A1)
- [KR101409870B1 — Method of Preparation for High basicity polyaluminum chloride coagulant](https://patents.google.com/patent/KR101409870B1/en)
- [Synthesis of polyaluminum chloride: Optimization of process parameters — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S2214714423012205)
