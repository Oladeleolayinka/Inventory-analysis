# Inventory-analysis
# Nigerian FMCG Inventory Intelligence, Store Ledger & Replenishment System

## Project Overview
In Nigeria's high-interest-rate environment, unmonitored stock imbalances—both slow-moving overstock and Class A stockouts—directly erode working capital and daily revenue. Using **Google Sheets** and **Maven Analytics data visualization principles**, I built an end-to-end inventory tracking and replenishment system for a **50-SKU Nigerian FMCG portfolio** (`₦4.03B` annual COGS, `₦413.4M` annual revenue) across three hubs (**Ikeja Hub, Agbara Plant, and Sagamu Depot**).

![Analysis preview]

<img width="1920" height="1200" alt="Daily sales Tracker" src="https://github.com/user-attachments/assets/5de17857-102b-4ff6-86e7-110b376d5c67" />
<img width="1920" height="1200" alt="Monthly Stock Report" src="https://github.com/user-attachments/assets/646c33f5-df7b-4143-8caa-ae8223391a26" />

<img width="1920" height="1090" alt="Stock Status report" src="https://github.com/user-attachments/assets/51e82500-8887-4f62-8a9d-abb0dd9bad21" />
<img width="1920" height="1012" alt="Exipry Assessment report" src="https://github.com/user-attachments/assets/31a1623e-b3cf-44c2-a167-50a5d336c4a2" />
 <img width="1920" height="1200" alt="Inventory Master Data" src="https://github.com/user-attachments/assets/e597b78a-1dbd-4b26-8673-8c6fa0fbb02c" />
<img width="1920" height="1094" alt="purchase ledger worksheet" src="https://github.com/user-attachments/assets/05728203-a528-488e-bdf0-075350160287" />


---

## System Architecture
1. **Daily Transaction Ledgers (`PURCHASES` & `SALES`):** 365-day inbound supplier delivery logs and daily customer order logs tracking unit movements across all 50 SKUs.
2. **12-Month Periodic Inventory Ledger (`JANUARY` – `DECEMBER`):** Aggregates daily movements (`Opening Stock + Stock In - Stock Out = Closing Stock`) to compute a true 12-month periodic average inventory valuation rather than relying on a single-day snapshot.
3. **Analytical & Diagnostic Engine:**
   * **Pareto ABC Classification:** Segments high-velocity Class A staples (80% of COGS) from Class B and C items.
   * **GMROI × Months on Hand (MoH) Matrix:** Evaluates profitability yield against forward stock coverage (`2.5x` GMROI and `9.0x` turnover targets), applying GMROI decomposition ($\text{Turnover} \times \text{Cost Markup}$) to design turnaround actions for slow movers.
4. **Automated Replenishment & Risk Plan:**
   * **Shelf-Life-Capped EOQ:** Calculates Economic Order Quantity (`₦25,000` order cost, `30%` holding cost) capped at **80% of post-transit net shelf life** to prevent FEFO expiry write-offs.
   * **Probabilistic Safety Stock:** Models demand-proportional safety buffers ($Z \times \bar{D} \times \sqrt{L}$) at a **96% service level** (`Z = 1.75` via `NORM.S.INV`).
   * **Daily Revenue-at-Risk Monitor:** Flags items below their Reorder Point (`Out of Stock!(Reorder)`) and quantifies daily revenue exposure.

---

## Key Findings & Business Recommendations
* **₦34.02M Trapped in Excess Capital (12 SKUs):** Slow-moving items averaging **3.62x turnover** tie up **₦34.02M** in excess stock above target coverage, led by **SKU-041 (Dove Beauty Cream Bar: ₦7.11M excess, 3.09x turnover)** and **SKU-050 (St. Ives Apricot Scrub: ₦6.04M excess, 2.04x turnover)**. *Action:* Freeze reorders on all 12 excess SKUs and execute B2B promotional bundling with fast-moving Class A items to release trapped cash.
* **₦8.87M/Day Revenue at Risk on Fast Movers:** High-velocity Class A staples (including **SKU-003 Indomie**, **SKU-007 Devon Kings Oil**, and **SKU-004 Milo**) sit below their probabilistic Reorder Points, representing **₦8.87M in daily revenue exposure** requiring immediate PO release.
* **FEFO Perishable Protection:** Capping EOQ against net post-transit shelf life reduced order quantities on short-shelf-life dairy and beverages such as **Hollandia Yoghurt (`246 → 173` cartons)** and **Viju Milk (`352 → 205` cartons)**, preventing downstream distributor rejections.
