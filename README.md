# Sales Performance & Logistics Optimization (End-to-End Analytics Case)

A data-driven analytics project focused on evaluating the operational efficiency, product portfolio velocity, and supply chain dynamics of a global e-commerce and retail enterprise. 

This project unifies messy transaction records, geographical frameworks, and product catalogs into a single analytical data warehouse to extract high-impact business insights.

## 📊 Core Business Problems Solved

### 1. Relational Data Architecture
* **Problem:** Operational footprints were fragmented across independent, multi-format source data (`events`, `countries`, `products`).
* **Solution:** Designed and executed a clean entity-relationship mapping strategy by treating `Country Code` and `Product ID` as Foreign Keys to perform optimized relational memory merges (`pd.merge`), resulting in a single flat-file analytical schema.

### 2. Data Cleaning & Integrity Auditing
* **Handling Structural Gaps:** Diagnosed 82 missing entries in destination routing. Rather than discarding viable transaction records and lowering top-line revenue reporting, rows were systematically imputed with an explicit `"UNKNOWN"` categorical string. Irrecoverable volume records (missing `Units Sold`) were dropped to eliminate data noise.
* **Geographical Imputation:** Identified non-standard regional attributes (Antarctica) and explicitly normalized them into standard UN macrographic frameworks (`"ANTARCTIC"` / `"UNKNOWN"` sub-regions) to prevent failure loops during categorical aggregations.
* **Text Normalization:** Implemented an automated string pipeline using `.str.upper().str.strip()` to eliminate hidden duplicate classifications caused by trailing whitespaces or mixed-case formatting.

### 3. Financial Performance & Product P&L Analysis
* **Volume vs. Value Mapping:** Uncovered a clear positive skew in corporate pricing models. While high-volume everyday commodities (Office Supplies, Clothes, Beverages) exceed **570,000 units sold**, they operate under high wholesale margins.
* **Star Categories:** Isolated **Cosmetics** as the absolute financial powerhouse. Despite capturing a significantly lower revenue share than bulk categories (e.g., Household), it delivers the highest absolute net profit (**$88M**), revealing the highest profit-to-revenue ratio across the portfolio.

### 4. Geographical & Macro-Regional Strategy
* **The Ukraine Phenomenon:** Successfully flagged a critical market arbitrage opportunity. While Ukraine ranks 9th in raw physical shipment volume (~164k units), it ranks **2nd globally in Net Profit (~$15M)**. This explicitly proves a high-margin, low-logistics-overhead consumer base.
* **Macro-Regional Risk Mitigation:** Identified heavy systemic dependence on a single core market—**Europe accounts for 94.7% of global net profit**. Generated data evidence indicating an immediate need for an operational audit in the **Asian market (currently generating only 5.3%)** to transform it into the primary zone for future scaling.

## 🛠️ Tech Stack & Methods
* **Language:** Python 3.x
* **Libraries:** Pandas, Seaborn, Matplotlib, NumPy
* **Techniques:** Descriptive Statistical Screening, Outlier Isolation, Categorical Standardization, Vectorized Feature Engineering, Relational Mapping, Multi-Layered Visualizations.
