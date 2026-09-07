# Omnichannel Inventory Availability & Profit Protection System
### Synthetic Retail Analytics Database — Excel | Power Query | Power Pivot | Power BI

![Excel](https://img.shields.io/badge/Tool-Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Domain](https://img.shields.io/badge/Domain-Retail%20%7C%20Supply%20Chain-1F3864?style=flat)
![Tables](https://img.shields.io/badge/Tables-26-2E75B5?style=flat)
![Rows](https://img.shields.io/badge/Rows-29%2C180-2E75B5?style=flat)
![Status](https://img.shields.io/badge/Status-Portfolio%20Ready-375623?style=flat)

---

## Project Overview

This repository contains a fully validated synthetic retail database built to support a complete omnichannel inventory and commercial analytics project.

The business problem: a multi-channel UK retailer must simultaneously manage **two competing inventory risks** — stockouts that prevent profitable demand from being fulfilled, and overstock that ties up working capital and creates write-off exposure. This database models the full supply chain and commercial operation required to identify, diagnose, and recommend action on both risks.

**This is not a simple or decorative dataset.** It is a fully relational, analytically connected database designed to answer 40 defined business questions, support 26 KPIs across 8 dashboard areas, and demonstrate realistic cause-and-effect business behaviour across stores, warehouses, online fulfilment, and supplier operations.

---

## Business Objectives

| # | Objective | Target |
|---|---|---|
| 1 | Reduce product-location stockout rates | −15% |
| 2 | Reduce excess and ageing inventory | −10% excess value; −15% >90-day ageing |
| 3 | Improve product on-shelf availability | +5 percentage points |
| 4 | Increase fulfilled sales and protect gross profit | Recover measurable lost revenue |
| 5 | Reduce inventory-related online cancellations | −20% |
| 6 | Improve inventory turnover | +8% |
| 7 | Improve supplier OTIF performance | +10 percentage points |
| 8 | Reduce emergency replenishment orders | −20% |
| 9 | Improve promotion inventory sell-through | +10% |
| 10 | Enable transfer-before-buy decisions | Prioritise surplus-to-deficit transfers |
| 11 | Improve inventory record accuracy | Detect reconciliation failures |

---

## Database Architecture

### At a Glance

| Category | Count | Details |
|---|---|---|
| **Dimension Tables** | 15 | Product, Location, Supplier, Customer, Date, Channel, Promotion, Brand, Category, Geography, Employee, Time, ReturnReason, OrderStatus, InventoryMovementType |
| **Bridge Table** | 1 | Bridge_ProductSupplier (resolves Product ↔ Supplier many-to-many) |
| **Fact Tables** | 10 | SalesLine, InventorySnapshot, OnlineOrderLine, PurchaseOrderLine, GoodsReceipt, InventoryMovement, StockTransfer, ReturnLine, PromotionPerformance, Forecast |
| **Total Tables** | 26 | — |
| **Total Rows** | 29,180 | Across all tables |
| **Date Range** | 730 days | 1 July 2024 – 30 June 2026 |
| **Products (SKUs)** | 150 | Across 12 categories and 20 brands |
| **Locations** | 40 | Stores, warehouses and fulfilment centres |
| **Suppliers** | 30 | With lead time and OTIF tracking |
| **Customers** | 300 | Segmented by type and region |

---

### Fact Table Summary

| Fact Table | Grain | Rows | Key Analysis |
|---|---|---|---|
| `Fact_SalesLine` | One product per transaction | 5,000 | Revenue, gross profit, discounts, channel mix |
| `Fact_InventorySnapshot` | One product-location per day | 5,000 | Stockouts, excess stock, ageing, inventory value |
| `Fact_OnlineOrderLine` | One product per online order | 3,000 | Cancellations, substitutions, fill rate |
| `Fact_PurchaseOrderLine` | One product per purchase order | 1,500 | Supplier orders, emergency replenishment |
| `Fact_GoodsReceipt` | One receipt event | 1,800 | Delivery timing, quality, partial receipts |
| `Fact_InventoryMovement` | One movement event | 5,000 | Stock reconciliation, anomaly detection |
| `Fact_StockTransfer` | One product per transfer | 1,000 | Surplus-to-deficit transfers, prevention of stockouts |
| `Fact_ReturnLine` | One returned product | 1,200 | Return rate, resalability, processing time |
| `Fact_PromotionPerformance` | One product-location per promo day | 1,500 | Uplift, baseline comparison, GP impact |
| `Fact_Forecast` | One product-location per week | 2,500 | Forecast accuracy, bias, over/underforecasting |

---

### Dimension Table Summary

| Dimension Table | Rows | Purpose |
|---|---|---|
| `Dim_Product` | 150 | SKUs with cost, price, shelf life, seasonal and perishable flags |
| `Dim_Category` | 12 | Hierarchy: Grocery, Fashion, Electronics, Homeware, etc. |
| `Dim_Brand` | 20 | 10 own-label + 10 national brands |
| `Dim_Location` | 40 | Stores, warehouses, fulfilment centres with type and region |
| `Dim_Geography` | 10 | UK regional hierarchy linked to locations |
| `Dim_Supplier` | 30 | Lead times, MOQ, risk rating, preferred supplier flag |
| `Dim_Customer` | 300 | Segment, region, registered account flag |
| `Dim_Channel` | 5 | In-Store, Web, App, Click+Collect, Phone |
| `Dim_Date` | 730 | Full date dimension with IsWeekend, IsHoliday, YearMonth, Quarter |
| `Dim_Promotion` | 25 | Promotion type, dates, discount percentage |
| `Dim_Time` | 24 | Hourly time dimension for intraday audit analysis |
| `Dim_ReturnReason` | 8 | Return reason codes and default resalability |
| `Dim_OrderStatus` | 8 | Order lifecycle statuses |
| `Dim_InventoryMovementType` | 12 | Movement types with IN/OUT/NEUTRAL direction |
| `Dim_Employee` | 25 | Employees and system sources for audit trail |
| `Bridge_ProductSupplier` | 250 | Product-supplier pairs with cost and preferred supplier flag |

---

## KPI Framework (26 KPIs)

### Sales & Profitability
- Net Sales, Gross Profit, Gross Margin %, Units Sold, Average Order Value, Full-Price Sell-Through, Return Rate

### Inventory
- Stockout Rate, On-Shelf Availability, Inventory Turnover, Days of Supply, Excess Inventory Value, Aged Inventory Rate, Inventory Accuracy, Lost Sales Estimate, Lost Gross Profit

### Fulfilment & Operations
- Order Cancellation Rate, Substitution Rate, Fill Rate, Emergency Replenishment Rate, Transfer Success Rate

### Supplier
- Supplier OTIF (On-Time In-Full), Supplier Delay Rate

### Commercial & Forecasting
- Promotion Sell-Through, Promotion Uplift, Forecast Accuracy (WAPE/MAPE)

---

## Data Model Design

### Relational Model
The database follows **star-schema principles** with conformed dimensions shared across all 10 fact tables. This enables cross-domain analysis — for example, linking a supplier delay (Fact_PurchaseOrderLine) to an inventory gap (Fact_InventorySnapshot) to an online cancellation (Fact_OnlineOrderLine) using shared dimension keys.

### Key Relationships
```
Dim_Category    ──1:M──►  Dim_Product
Dim_Brand       ──1:M──►  Dim_Product
Dim_Geography   ──1:M──►  Dim_Location
Dim_Product     ──M:M──►  Dim_Supplier  (via Bridge_ProductSupplier)
Dim_Product     ──1:M──►  All fact tables
Dim_Location    ──1:M──►  All fact tables (role-playing: source/destination)
Dim_Date        ──1:M──►  All fact tables (role-playing: multiple date roles)
Dim_Supplier    ──1:M──►  Fact_PurchaseOrderLine, Fact_GoodsReceipt
Dim_Customer    ──1:M──►  Fact_SalesLine, Fact_OnlineOrderLine, Fact_ReturnLine
Fact_PurchaseOrderLine ──► Fact_GoodsReceipt  (Power Query merge)
Fact_SalesLine         ──► Fact_ReturnLine     (Power Query merge)
```

### Many-to-Many Relationships
The Product ↔ Supplier relationship is a genuine many-to-many. One product can be supplied by multiple suppliers; one supplier can supply multiple products. This is resolved through `Bridge_ProductSupplier`, which also stores the product-specific negotiated cost and preferred supplier flag.

---

## Connected Business Behaviour

This dataset is **not generated from independent random values**. Records are causally connected to replicate realistic retail operating conditions:

- **Supplier delay chain:** Delayed purchase orders produce later goods receipt dates → reduced available inventory → stockout flags → inventory-related online cancellation flags
- **Promotion demand surge:** Promotional periods produce higher unit sales than baseline → some promotions deplete inventory and trigger stockouts during the promotion window
- **Margin erosion:** Some promotions show volume uplift (IncrementalUnits > 0) but negative or low IncrementalGrossProfit — demonstrating that not all promotions are profitable
- **Transfer logic:** Stock transfers originate from locations with ExcessStockFlag = 1 and are directed to locations with StockoutFlag = 1 or approaching zero
- **Return delay:** Returned stock with ResalableFlag = 1 is not immediately available — RestockingDateKey reflects a realistic processing delay
- **Forecast bias patterns:** The dataset contains structured overforecasting, underforecasting, and consistent bias patterns across different product-location combinations
- **Weekend demand uplift:** Sales volumes are higher on rows where Dim_Date.IsWeekend = 1, consistent with retail patterns

---

## Excel / Power Query / Power Pivot Architecture

### Recommended Tool Usage

| Task | Tool |
|---|---|
| Load and clean all 26 tables | Power Query (connection-only for large facts) |
| Model relationships | Power Pivot Data Model |
| KPI measures and time intelligence | DAX (in Power Pivot or Power BI) |
| Operational action lists | Excel XLOOKUP, SUMIFS, COUNTIFS |
| Dashboards | Power BI (8 reporting pages) |

### Role-Playing Dimensions
Several tables contain multiple foreign keys pointing to the same dimension. In Power Pivot, **only one relationship per table-pair can be active**. Inactive relationships are activated in DAX using `USERELATIONSHIP()`:

| Fact Table | Active FK | Inactive FKs (require USERELATIONSHIP) |
|---|---|---|
| Fact_OnlineOrderLine | OrderDateKey | PromisedDateKey, FulfilmentDateKey, CancellationDateKey |
| Fact_OnlineOrderLine | OriginalProductKey | SubstitutedProductKey |
| Fact_PurchaseOrderLine | OrderDateKey | ExpectedDeliveryDateKey |
| Fact_StockTransfer | SourceLocationKey | DestinationLocationKey |
| Fact_ReturnLine | ReturnDateKey | RestockingDateKey |
| Fact_Forecast | ForecastWeekStartDateKey | ForecastCreationDateKey |

### Fact-to-Fact Handling
Two relationships cannot be Power Pivot model relationships and must be resolved via **Power Query merge at the curated layer**:
- `Fact_GoodsReceipt.PurchaseOrderLineID` → `Fact_PurchaseOrderLine`
- `Fact_ReturnLine.OriginalSalesLineID` → `Fact_SalesLine`

---

## Power BI Dashboard Structure (8 Areas)

| Dashboard Page | Business Purpose |
|---|---|
| 1. Executive Inventory Control Tower | Revenue, profit, availability and working capital overview |
| 2. Stockout Risk | Prioritise and diagnose availability failures by product and location |
| 3. Excess & Aged Inventory | Identify capital tied up in slow-moving or excess stock |
| 4. Supplier OTIF | Diagnose supplier delivery failures and delay concentration |
| 5. Product-Location Performance | Balance sales, profit, inventory productivity and health score |
| 6. Online Fulfilment | Root-cause cancellations, substitutions and fill-rate failures |
| 7. Promotion Profitability | Separate genuine demand uplift from margin-damaging discounting |
| 8. Stock Transfer Recommendations | Prioritise surplus-to-deficit transfers before ordering new stock |

---

## 40-Question Analytical Roadmap (Summary)

The dataset is structured to answer all 40 defined business questions. Sample questions by domain:

**Sales & Profitability:** Total sales/GP by month; categories by revenue and margin; store sales per sq ft; channels by AOV; products with highest/lowest margins

**Stockout & Availability:** Products at zero available inventory; repeated stockout locations; lost sales and GP during stockout periods; days of supply by product-location

**Excess & Aged Inventory:** Products unsold for 30/60/90+ days; locations with highest inventory value; top 20% of products driving 80% of excess value (Pareto); markdown candidates

**Supplier Performance:** Open PO value by supplier; late delivery rate; in-full rate; statistical association between supplier delays and stockouts

**Online Fulfilment:** Cancellations caused by unavailable inventory; products with highest substitution rates; online demand vs local inventory alignment

**Advanced Analytics:** Rolling 7/28/90-day demand; 4-week demand acceleration; product-location health score; suspicious inventory adjustment patterns

---

## Data Quality

This dataset was independently audited and corrected. The following issues were identified and resolved before publication:

| Issue | Description | Action |
|---|---|---|
| BrandKey orphans | 23 products referenced non-existent brand IDs | Remapped to correct brand keys |
| Bridge costs | 30 supplier unit costs were wildly inconsistent with standard cost | Reset to realistic 72–90% of standard cost |
| Promotion-date FK | 708 sales rows had PromotionKey pointing to a non-active promotion period | PromotionKey nullified; sale data preserved |
| InventoryValue | 400 snapshot rows had InventoryValue ≠ ClosingQty × UnitCost | Recalculated from components |
| Receipt dates | 24 goods receipt rows were dated before the purchase order was raised | Reset to OrderDate + SupplierLeadTime |
| Promo performance dates | 1,471 rows had performance dates outside the promotion active period | Reassigned to valid dates within promo window |
| Forecast creation dates | 61 forecast rows had creation date ≥ forecast week start | Corrected to 7–14 days before week start |
| Forecast bias labels | 558 rows had ForecastBias inconsistent with ForecastError sign | Reclassified using signed ForecastError |

**Final dataset quality score: 9.5/10**

---

## File Reference

```
data/
└── Omnichannel_Inventory_Database.xlsx
    ├── _Cover_Index          — Table of contents with row counts and purpose
    ├── Dim_Category          — 12 rows
    ├── Dim_Brand             — 20 rows
    ├── Dim_Product           — 150 rows
    ├── Dim_Geography         — 10 rows
    ├── Dim_Location          — 40 rows
    ├── Dim_Supplier          — 30 rows
    ├── Dim_Customer          — 300 rows
    ├── Dim_Channel           — 5 rows
    ├── Dim_Date              — 730 rows  (1 Jul 2024 – 30 Jun 2026)
    ├── Dim_Time              — 24 rows
    ├── Dim_Promotion         — 25 rows
    ├── Dim_ReturnReason      — 8 rows
    ├── Dim_OrderStatus       — 8 rows
    ├── Dim_InventoryMovementType — 12 rows
    ├── Dim_Employee          — 25 rows
    ├── Bridge_ProductSupplier — 250 rows
    ├── Fact_SalesLine        — 5,000 rows
    ├── Fact_InventorySnapshot — 5,000 rows
    ├── Fact_OnlineOrderLine  — 3,000 rows
    ├── Fact_PurchaseOrderLine — 1,500 rows
    ├── Fact_GoodsReceipt     — 1,800 rows
    ├── Fact_InventoryMovement — 5,000 rows
    ├── Fact_StockTransfer    — 1,000 rows
    ├── Fact_ReturnLine       — 1,200 rows
    ├── Fact_PromotionPerformance — 1,500 rows
    └── Fact_Forecast         — 2,500 rows
```

---

## Skills Demonstrated

| Skill Area | Detail |
|---|---|
| **Data Modelling** | Star schema design; conformed dimensions; bridge tables; role-playing dimensions; grain definition |
| **Relational Database Design** | Primary keys; foreign keys; referential integrity; many-to-many resolution |
| **Data Engineering** | Causal data generation; connected business behaviour; 20-rule data integrity framework |
| **Business Intelligence** | KPI framework design; 40-question analytical roadmap; 8-dashboard architecture |
| **Excel / Power Query** | Multi-table data model; connection-only fact loading; 28-step transformation pipeline |
| **Power Pivot / DAX** | Star schema relationships; USERELATIONSHIP(); time intelligence; RANKX; rolling measures |
| **Retail Analytics** | Stockout analysis; inventory turnover; OTIF; promotion profitability; demand forecasting |
| **Supply Chain Analytics** | Supplier performance; lead time; replenishment; stock transfers; goods receipt validation |
| **Data Quality & Auditing** | Independent audit; issue identification; automated correction; revalidation |

---

## How to Use This Dataset

1. **Download** `data/Omnichannel_Inventory_Database.xlsx`
2. **Open in Excel** — All 26 tables are on separate sheets with a cover index
3. **Load into Power Query** — Use Get Data > From Workbook; load large facts as connection-only
4. **Build the Data Model** — Connect tables using the relationship map in the README
5. **Create DAX Measures** — Start with Net Sales, Gross Profit, Stockout Rate, OTIF
6. **Build Dashboards** — Follow the 8-page Power BI dashboard structure above

---

## About This Project

This dataset was built as part of a portfolio project demonstrating full-stack data analytics skills — from database design and data engineering through to business intelligence, KPI framework definition, and dashboard architecture.

The project was designed to replicate the type of analytical challenge faced by a mid-size UK omnichannel retailer and covers the complete analytical lifecycle: problem definition → data modelling → data generation → quality audit → analysis design → KPI framework → dashboard delivery.

---

*Prepared by Muhammad Danish · Portfolio Project · September 2026*  
*Dataset: Synthetic (no real personal or commercial data)*
