# Khalij-Nouri-Reformer-APC-ExportSlate-Optimization-System (Khalij-NRES)

## Intelligent learning-based advanced control of the CCR reforming reactor (unit 300/350) and constrained optimization of the export-domestic product slate with a guaranteed feed supply share for Tondgooyan Petrochemical — a dedicated product of Nouri Petrochemical Company

> This document is a **dedicated** product for Nouri Petrochemical Company (Borzouyeh) — the country's fourth aromatics producer and one of the world's largest paraxylene complexes (750 thousand tons/year PX). This product does not overlap with the dedicated Bu Ali Sina product (which focuses on the catalyst/adsorbent of a medium-sized complex), because Nouri's global scale (13 process units) and **its strategic role in supplying PX feed to Shahid Tondgooyan Company** create completely different requirements.

---

## 0. Understanding Nouri Petrochemical Company and the technical gap

**Sources:** [Persian Wikipedia — Nouri Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D9%86%D9%88%D8%B1%DB%8C), [nopc.co — Production units](https://www.nopc.co/fa/commerceandsale/products/productionprocess/productionsunits), [Shana — Nouri's product basket](https://www.shana.ir/news/301946/)

### Products and scale

| Feature | Value |
|---|---|
| Total capacity | 4.5 million tons/year (the country's fourth aromatics producer) |
| Paraxylene (PX) | 750,000 tons/year (one of the world's largest PX complexes) |
| Other products | Benzene, orthoxylene (OX), heavy cut, raffinate, hydrotreated naphtha (HTN), LPG |
| Number of process units | 13 units + storage and transfer unit |
| Key unit | Unit 300 (CCR catalytic reforming) + unit 350 (unit 300 catalyst regeneration) |
| Exports | A significant portion of the products (benzene, OX, PX, raffinate, HTN) is exported |
| Strategic role | The main PX feed of Shahid Tondgooyan is mainly supplied from Nouri |

### Technical gap relative to the holding's other products (including the dedicated Bu Ali Sina product)

| Product | Why it is not enough for Nouri |
|---|---|
| Bu Ali Sina dedicated product (Khalij-BACAT) | Focuses on the CCR catalyst health and Parex adsorbent of a **medium-scale** single-product complex; does not address **multi-product export/domestic slate** or **the strategic feed supply commitment to another company** |
| Bandar Imam dedicated product (Khalij-BIMO) | Designed for coordination **among subsidiaries of a single complex**; the Nouri-Tondgooyan relationship is between **two completely independent holding companies** with a feed supply contract, not subsidiaries of one parent |
| Products 1, 3, 4 | None covers global-scale learning-based CCR advanced control or export-domestic slate optimization |

**Conclusion:** Nouri needs a system that (a) optimizes the CCR reactor with learning-based advanced control and (b) optimizes the product slate between the export market (maximizing foreign-currency revenue) and **the strategic PX supply commitment to Tondgooyan** (domestic supply chain security) in a constrained way.

---

## 1. Patent Background and Competitive Analysis

| No. | Existing patent/technology | Main limitation | Difference of this product |
|---|---|---|---|
| 1 | **US 11,318,438 B2** – *Advanced process control in a continuous catalytic regeneration reformer* | Classic APC (model predictive control based on traditional linear/nonlinear models); lacks an adaptive machine-learning layer and a connection to product slate optimization | Upgrade to learning-based APC (adaptive with real data) + direct connection to product slate optimization |
| 2 | **US 6,312,586 B1** – *Multireactor parallel flow hydrocracking process* | Hardware process for catalyst circulation among parallel reactors; a process approach, not software | Complementary: a software prediction and optimization layer on the existing process infrastructure |
| 3 | *Yield and energy optimization of CCR reforming based on Particle Swarm Optimization* (ScienceDirect) | Unit-level yield/energy optimization; does not address inter-company feed supply commitments or the export market | Constrained optimization with the hard constraint "minimum Tondgooyan PX supply" + the objective of maximizing export revenue |
| 4 | General petrochemical industry S&OP/feed allocation modeling (similar to the Bandar Imam product reference) | For feed allocation within a single complex; does not address the contractual strategic supply relationship between two independent companies with national supply security priority | A dedicated model with domestic supply security as the first priority, then maximizing export revenue |

### Core Patentable Claim

> **"An integrated control and optimization system that combines learning-based advanced control of the CCR reactor/regenerator (unit 300/350) with a constrained product slate optimization engine; for the first time, this engine solves the hard constraint 'minimum paraxylene feed supply to the downstream Tondgooyan company' together with the objective of maximizing export revenue of aromatic products (benzene, OX, raffinate, HTN) based on the instantaneous global market price, in a single multi-objective optimization model."**

---

## 2. SRS Document – Dedicated product of Nouri Petrochemical

### 2-1. Introduction
**Purpose:** Increase the yield and performance stability of the CCR reactor, and simultaneously optimize the product slate between the export market and the strategic domestic PX supply commitment.

**Field challenges:**
- The existing advanced control (classic APC) in unit 300/350 is not adaptively updated to the actual and variable feed/catalyst conditions.
- The decision "how much PX to Tondgooyan and how much to exports" is usually made without systematic optimization against the simultaneous fluctuation of export price and the priority of domestic supply security.
- Diversification of the product basket (per Shana's official announcement) requires a more sophisticated decision-support tool than in the past.

**Scope:** Nouri complex, Borzouyeh; connection to the DCS of unit 300/350 and the other processing units; connection to the sales/export system.

### 2-2. General Requirements

| ID | Requirement | Priority |
| :--- | :--- | :--- |
| R-GEN-01 | Reception of instantaneous data of the CCR reactor/regenerator (unit 300/350) | High |
| R-GEN-02 | Reception of instantaneous export prices of PX/OX/benzene/HTN from the global market | High |
| R-GEN-03 | Reception of the PX supply commitment schedule to Tondgooyan (contract) | High |
| R-GEN-04 | Integrated dashboard "Reactor control + product slate" | High |

### 2-3. Functional Requirements

| ID | Requirement | Patent capability |
| :--- | :--- | :--- |
| FR-APC-01 | Learning-based predictive control of the CCR reactor (temperature/pressure/H2 ratio) with continuous adaptation to real data | Upgrading classic APC to adaptive learning-based control |
| FR-APC-02 | Prediction of the optimal catalyst regeneration timing of unit 350 | Predictive regeneration scheduling at a large industrial scale |
| FR-SLATE-01 | Constrained product slate optimization with the hard constraint of minimum Tondgooyan PX supply and the objective of maximizing export revenue | **Constrained supply-security / export-revenue optimization (main innovation)** |
| FR-ALERT-01 | Alert for domestic PX supply shortfall risk before it occurs | National supply chain preventive recommender |
| FR-LOOP-01 | Recording actual PX delivery and export sales results for model retraining | Closed learning |

### 2-4. Non-Functional Requirements

| ID | Requirement | Target value |
| :--- | :--- | :--- |
| NFR-PER-01 | Product slate recalculation delay after a price change | Less than 5 minutes |
| NFR-PER-02 | PX yield prediction accuracy (MAPE) | Less than 8% |
| NFR-AVAIL-01 | System availability | 99.9% |

### 2-5. Technical Architecture

```
┌──────────────────┐
│   API Gateway     │
└─────────┬─────────┘
┌─────────┼───────────────┬───────────────┐
┌───▼────────────┐┌───────▼────────┐┌──────▼──────────┐
│CCR Unit 300/350 ││ Learning-Based ││ Constrained      │
│+ Market/Contract││ APC Model      ││ Export-Domestic  │
│Ingestion        ││                ││ Slate Optimizer  │
└──────┬──────────┘└───────┬────────┘└─────────┬────────┘
       └──────────┬────────┴───────────────────┘
                   ▼
        ┌────────────┐    ┌───────────────┐
        │   Kafka    │    │ TimescaleDB   │
        └────────────┘    └───────────────┘
```

| Suggested path | Description |
| :--- | :--- |
| `services/ccr-market-ingestion/` | Connection to the DCS of unit 300/350 + export price feed + Tondgooyan contract |
| `services/learning-apc/` | Learning-based predictive control |
| `services/export-domestic-slate-optimizer/` | Constrained multi-objective optimizer |
| `shared/` | Reuse of products 1-4 and the Bu Ali Sina/Tondgooyan dedicated products |

---

## 3. Synthetic Data Generation Code

```python
import numpy as np
import pandas as pd
from datetime import datetime, timedelta

NUM_RECORDS = 10000
START_TIME = datetime(2026, 9, 14, 8, 0, 0)
timestamps = [START_TIME + timedelta(hours=i/30) for i in range(NUM_RECORDS)]
t = np.linspace(0, 20 * np.pi, NUM_RECORDS)

# 1. CCR reactor
reactor_temp_c = 510 + 5 * np.sin(t * 0.1) + np.random.normal(0, 1, NUM_RECORDS)
catalyst_activity_percent = 95 - 0.0006 * np.arange(NUM_RECORDS) + np.random.normal(0, 0.4, NUM_RECORDS)
catalyst_activity_percent = np.clip(catalyst_activity_percent, 78, 97)

# 2. PX yield and other products
px_production_rate_tph = 92 * (catalyst_activity_percent / 95) + np.random.normal(0, 1.5, NUM_RECORDS)
benzene_production_rate_tph = 22 + np.random.normal(0, 1, NUM_RECORDS)

# 3. Export price and domestic commitment
export_price_px_usd_ton = 950 + 70 * np.sin(t * 0.03) + np.random.normal(0, 15, NUM_RECORDS)
tondgooyan_commitment_tph = 65 + 3 * np.sin(t * 0.02) + np.random.normal(0, 1, NUM_RECORDS)

# 4. Optimal allocation between export and domestic commitment
export_allocation_tph = np.clip(px_production_rate_tph - tondgooyan_commitment_tph, 0, None)
supply_shortfall_risk = (px_production_rate_tph < tondgooyan_commitment_tph).astype(int)

df = pd.DataFrame({
    'timestamp': timestamps,
    'reactor_temp_c': np.round(reactor_temp_c, 2),
    'catalyst_activity_percent': np.round(catalyst_activity_percent, 2),
    'px_production_rate_tph': np.round(px_production_rate_tph, 2),
    'benzene_production_rate_tph': np.round(benzene_production_rate_tph, 2),
    'export_price_px_usd_ton': np.round(export_price_px_usd_ton, 1),
    'tondgooyan_commitment_tph': np.round(tondgooyan_commitment_tph, 2),
    'export_allocation_tph': np.round(export_allocation_tph, 2),
    'supply_shortfall_risk': supply_shortfall_risk,
})

df.to_csv("nouri_reformer_slate_data_10k.csv", index=False)
print(f"✅ Saved. Records: {len(df):,} - Variables: {len(df.columns)}")
print(df.describe())
```

---

## 4. Economic Justification

| Indicator | Current state | With Khalij-NRES | Approximate financial impact |
| :--- | :--- | :--- | :--- |
| CCR reactor control | Static classic APC | Adaptive learning-based control | Increased PX yield on the 750 thousand ton capacity |
| Export-domestic slate | Decision-making without systematic optimization | Constrained optimization with supply-security priority | Increased export foreign-currency revenue without jeopardizing Tondgooyan supply |
| Tondgooyan PX shortfall risk | Late discovery | Preventive alert | Maintaining the stability of the national PTA/PET supply chain |

**Payback:** Given Nouri's global scale (750 thousand tons PX/year) and its strategic importance in the national supply chain, even a minor improvement in yield and product slate has very high economic and strategic value.

---

## 5. Proposed Evolution Roadmap (Phase 1-6)

| Phase | Capability |
| :--- | :--- |
| 1 | Base infrastructure + data simulator |
| 2 | Learning-based predictive control of unit 300/350 |
| 3 | PX/OX/benzene yield prediction |
| 4 | Constrained export-domestic slate optimizer |
| 5 | Integrated dashboard + supply shortfall risk alert |
| 6 | Operational pilot with direct coordination of the commercial team and Tondgooyan |

---

## 6. Summary of Patentable Innovations

1. **Upgrading the classic APC of the CCR unit to adaptive learning-based predictive control**.
2. **Constrained product slate optimization with the hard constraint of inter-company feed supply security** (Nouri→Tondgooyan) simultaneously with maximizing export revenue.
3. **Preventive supply-shortfall risk alert** for the national PX/PTA supply chain.

---

## 7. References

- [Persian Wikipedia — Nouri Petrochemical](https://fa.wikipedia.org/wiki/%D9%BE%D8%AA%D8%B1%D9%88%D8%B4%DB%8C%D9%85%DB%8C_%D9%86%D9%88%D8%B1%DB%8C)
- [nopc.co — Production units of Nouri Petrochemical](https://www.nopc.co/fa/commerceandsale/products/productionprocess/productionsunits)
- [Shana — Nouri Petrochemical product basket is diversified](https://www.shana.ir/news/301946/)
- [US11318438B2 — Advanced process control in a continuous catalytic regeneration reformer](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11318438)
- [US6312586B1 — Multireactor parallel flow hydrocracking process](https://patents.google.com/patent/US6312586B1/en)
- [Yield and energy optimization of the CCR reforming process based on particle swarm optimization — ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0360544220312056)
