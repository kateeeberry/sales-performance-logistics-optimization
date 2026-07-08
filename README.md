# Sales Performance & Logistics Optimization (End-to-End Analytics Case)

A data-driven analytics project focused on evaluating operational efficiency, product portfolio velocity, macro-regional supply chain bottlenecks, and daily consumer seasonality of a global retail and e-commerce enterprise.

This project unifies fragmented transaction records, geographical structures, and product catalogs into an analytical data pipeline to extract high-impact business insights and operational diagnoses.

## 📊 Core Business Problems Solved

### 1. Relational Data Architecture
* **Problem:** Operational footprints were fragmented across independent source datasets (`events`, `countries`, `products`).
* **Solution:** Designed an entity-relationship mapping strategy by treating `Country Code` and `Product ID` as Foreign Keys to perform memory-optimized relational merges (`pd.merge`), building a clean master flat-file database.

### 2. Data Cleaning & Integrity Management
* **Handling Structural Gaps:** Diagnosed 82 missing entries in destination routing. Rather than discarding viable transaction records and lowering top-line revenue reporting, rows were imputed with an explicit `"UNKNOWN"` categorical label. Missing physical volume records (`Units Sold`) were dropped to prevent aggregation noise.
* **Geographical Normalization:** Identified missing regional data for non-standard zones (Antarctica) and mapped them into explicit UN macrographic frameworks (`"ANTARCTIC"` / `"UNKNOWN"` sub-regions) to prevent failure loops during categorical partitioning.
* **Text Normalization:** Implemented a string cleanup sequence (`.str.upper().str.strip()`) to remove whitespace padding and prevent duplicate categorical keys caused by mixed-case inputs.

### 3. Financial Performance & Margin Analysis
* **Volume vs. Value Drivers:** Uncovered a positive skew in corporate pricing. While high-volume commodities (Office Supplies, Clothes, Beverages) exceed **570,000 units sold**, they operate under high wholesale margins.
* **The Margin Superstar:** Isolated **Cosmetics** as the core profit engine. Despite generating lower revenue than bulk volume categories (like Household), it delivers the highest absolute net profit (**$88M**), yielding the optimal profit-to-revenue efficiency.

### 4. Supply Chain & Logistics Efficiency Audit
* **Localized Logistics Gaps:** Identified **Hungary** as the absolute global logistics underperformer, with fulfillment lead times reaching a critical average of **32 days to ship**.
* **Systemic Diagnostic Discovery:** Aggregated lead times across macro-regions, revealing an average shipping duration of **26.1 days in Asia** and **24.8 days in Europe**. The marginal variance of just **1.3 days** proves that fulfillment lag is completely independent of geographic distance or transit routes. The root cause is internal: warehouse operational step friction and corporate red tape.
* **Financial Insulation & Caveats:** Correlation analysis via scatter-plots confirmed **zero statistical correlation** between shipping delays and profit per transaction ($Days\_to\_Ship$ vs $Profit$). While unit margins are completely insulated from fulfillment delays, these lag times present severe retention (LTV) and capital turnover risks.

### 5. Day-of-Week Seasonality & Micro-Market Dynamics
* **Macro-Regional Dominance:** Continuous time-series validation demonstrates absolute European dominance, generating between **150 to 183 orders daily**, peaking sharply on Saturdays.
* **Category Consumer Fluctuations:** Isolated the top 3 highly seasonal categories utilizing intra-week max-min delta tracking:
  * *Fruits:* Displays a strong upward weekend trend, climbing from a Friday low to a Sunday peak (23 orders).
  * *Household:* Experiences a mid-week surge, peaking sharply on Wednesdays (21 orders).
  * *Cosmetics:* Maintains a flat baseline early in the week before experiencing a massive pre-weekend spike on **Fridays (27 orders)**.
* **Geographical Demand Patterns:** Line-plot layering exposed distinct, highly actionable purchasing schedules across focus markets:
  * *Ukraine:* Drives early-week momentum with a dominant peak on **Mondays**.
  * *Slovakia:* Exhibits an abrupt mid-week spike, peaking on **Wednesdays**.
  * *Denmark:* Operates on a late-week cycle, concentrating volume on **Sundays**.

## 🛠️ Tech Stack & Methods
* **Language:** Python 3.x
* **Libraries:** Pandas, Seaborn, Matplotlib, NumPy
* **Techniques:** Descriptive Statistical Screening, Relational Entity Joins, Vectorized Feature Engineering, Time-Series Categorical Casts (`pd.Categorical`), Statistical Imputation, Outlier & Correlation Profiling, Advanced Data Visualization (Donut Charts, Shared-Axis Dual Plotting, Line Layers).
