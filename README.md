# Fashion Supplier Performance Analytics

An end-to-end data analytics project exploring supplier performance, purchasing, production, product quality, delivery delays, and inventory management in the fashion industry.

The project uses Python, PostgreSQL, SQL, and Power BI to organize operational data, measure performance, and identify areas that may need attention.

---

## Dashboard Preview

### 1. Executive Overview

<img width="1536" height="1024" alt="Fashion Supplier Performance Dashboard" src="https://github.com/user-attachments/assets/52a2be21-b92b-48fe-bf30-4011915d3329" />

### 2. Supplier Performance

<img width="1536" height="1024" alt="Fashion Supplier Performance Dashboard" src="https://github.com/user-attachments/assets/cc8b0cc1-442e-4eb6-9b4b-794e5fa4e713" />

### 3. Operations & Inventory

<img width="1536" height="1024" alt="Fashion Supplier Operations and Inventory Dashboard" src="https://github.com/user-attachments/assets/74585be7-3048-49c8-bcf3-c7d142078bec" />

> **Dashboard preview:** These images are design references. The displayed metrics, charts, and supplier rankings are illustrative and have not been verified against the project dataset. They are not evidence of actual Power BI results.

---

## Project Overview

Fashion retailers depend on reliable suppliers, consistent product quality, timely deliveries, and effective inventory planning.

This project explores how operational data can help answer practical business questions:

- Which suppliers deliver orders on time?
- Where are delivery delays occurring?
- Which suppliers or product categories have higher defect rates?
- How is purchasing spend distributed across suppliers?
- How long does production take?
- Which products experience low stock or stockouts?
- How does inventory change over time?

The aim is to build a structured analytical workflow, from raw data to business reporting.

## Tools & Technologies

- **Python:** Data processing, cleaning, validation, and analysis
- **Pandas & NumPy:** Data manipulation and exploratory analysis
- **PostgreSQL:** Relational data storage
- **SQL:** Joins, aggregations, CTEs, window functions, and reporting queries
- **Power BI:** Interactive dashboards and reporting
- **DAX:** KPI calculations and analytical measures
- **Git & GitHub:** Version control and project documentation

---

## Dataset

The project dataset represents a fictional fashion retail sourcing operation.

**Data period:** January 1, 2024 – December 31, 2025  
**Extract date:** December 31, 2025  
**Currency:** USD  
**Random seed:** 42

All operational records, suppliers, products, and figures are synthetic and intended for learning and demonstration.

The dataset is designed to represent common sourcing and supply chain scenarios, including partial shipments, delivery delays, production batches, inspections, inventory movements, and data quality issues.

### Dataset Scope

| Entity | Planned / Approximate Scale |
|---|---:|
| Suppliers | 40 |
| Products | 150 |
| Purchase orders | Approximately 10,000 |
| Purchase order items | Approximately 15,000–25,000 |
| Production batches | Generated from order quantities |
| Quality inspections | Generated from completed production |
| Deliveries | Includes partial shipments |
| Inventory snapshots | 105 weekly/period records per product |

Actual record counts should be confirmed from the generated files.

---

## Data Files

The project is organized into the following layers:

```text
Fashion-Supplier-Performance-Analytics/
│
├── data/
│   ├── raw/
│   │   ├── suppliers.csv
│   │   ├── products.csv
│   │   ├── supplier_products.csv
│   │   ├── purchase_orders.csv
│   │   ├── purchase_order_items.csv
│   │   ├── production_batches.csv
│   │   ├── quality_inspections.csv
│   │   ├── deliveries.csv
│   │   ├── inventory_snapshots.csv
│   │   └── _dq_injection_manifest.csv
│   │
│   └── processed/
│       └── [cleaned datasets]
│
├── scripts/
│   ├── generate_data.py
│   └── validate_data.py
│
├── notebooks/
│   └── [EDA notebook]
│
├── sql/
│   ├── schema.sql
│   ├── analytical_queries.sql
│   └── [data loading scripts, if used]
│
├── docs/
│   ├── data_dictionary.md
│   ├── kpi_definitions.md
│   └── power_bi_guide.md
│
├── requirements.txt
└── README.md
```

The structure above is the intended layout. Update filenames if the final repository uses different names.

---

## Data Model

The dataset contains the following main tables.

| Table | Description |
|---|---|
| `suppliers` | Supplier details and sourcing information |
| `products` | Product information, categories, and planning parameters |
| `supplier_products` | Approved supplier-product combinations |
| `purchase_orders` | Purchase order headers |
| `purchase_order_items` | Products and quantities ordered |
| `production_batches` | Production runs linked to order items |
| `quality_inspections` | Quality inspection events |
| `deliveries` | Shipment and receipt records |
| `inventory_snapshots` | Periodic inventory balances and movements |

### Main Relationships

- One supplier can have multiple purchase orders.
- One purchase order can contain multiple order items.
- Products can be sourced from multiple approved suppliers.
- One purchase order item can have multiple production batches.
- A production batch can have multiple inspection events.
- One purchase order item can have multiple deliveries.
- Each inventory snapshot represents one product for one reporting period.

**Important:** Deliveries are linked to purchase order items, not individual production batches.

---

## Business KPIs

The following metrics are planned for analysis and reporting.

| KPI | Purpose |
|---|---|
| On-Time Delivery Rate | Measures supplier delivery reliability |
| Average Delivery Delay | Measures delivery delays |
| Defect Rate | Measures defective units found during inspection |
| Inspection Coverage | Shows how much production was inspected |
| Purchase Spend | Tracks procurement expenditure |
| Open Overdue Quantity | Highlights outstanding overdue quantities |
| Production Cycle Time | Measures production duration |
| Stockout Events | Tracks inventory availability issues |
| Inventory Value | Estimates the value of available stock |
| Inventory Movement | Tracks receipts, issues, and stock balances |

KPI calculations must follow the definitions in `docs/kpi_definitions.md`.

### KPI Considerations

- Partial deliveries should be handled correctly.
- Cancelled quantities should not be counted as active commitments.
- Open overdue orders should remain visible.
- Uninspected goods must not be treated as defect-free.
- Multiple shipments must not inflate purchasing spend.
- Inventory balances must reconcile with recorded movements.
- Inventory turnover should only be reported if suitable consumption or cost-of-goods data is available.

---

## Project Workflow

### 1. Data Generation

Generate the operational datasets using Python with a fixed random seed.

### 2. Data Cleaning

Inspect missing values, duplicates, inconsistent formatting, and invalid records.

Document the cleaning decisions and preserve the original raw files.

### 3. Exploratory Data Analysis

Explore supplier performance, purchasing trends, delivery delays, product quality, production time, and inventory patterns.

### 4. PostgreSQL & SQL Analysis

Load the cleaned datasets into PostgreSQL and use analytical SQL queries to compare suppliers, products, categories, and reporting periods.

### 5. Power BI Reporting

Build an interactive report with three pages:

**Executive Overview**
- Main performance KPIs
- Monthly purchasing trends
- Delivery reliability
- Supplier comparisons

**Supplier Performance**
- Supplier scorecard
- Delivery delays
- Quality defect rates
- Supplier purchasing spend

**Operations & Inventory**
- Inventory trends
- Stockout indicators
- Production cycle time
- Inventory movement
- Operational issues

### 6. Findings & Recommendations

Document the patterns found in the data and explain which operational areas may need further investigation.

Recommendations will be based on calculated results rather than assumed business outcomes.

---

## Data Quality & Validation

The raw datasets may contain deliberately introduced data quality issues.

The validation workflow should check:

- Primary key uniqueness
- Foreign key integrity
- Missing and duplicate records
- Date consistency
- Order and cancellation quantities
- Production status and quantity rules
- Inspection quantity limits
- Shipment and receipt consistency
- Inventory reconciliation
- Cross-table quantity reconciliation

The validation script should report the affected records and failed rules.

Raw data should remain unchanged during cleaning.

---

## Running the Project

### Requirements

- Python 3.10+ (or the version specified in the project environment)
- PostgreSQL
- Jupyter Notebook
- Power BI Desktop
- Git

### 1. Clone the repository

```bash
git clone https://github.com/2KRISHNAYADAV/Fashion-Supplier-Performance-Analytics.git

cd Fashion-Supplier-Performance-Analytics
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

### 3. Generate the dataset

```bash
python scripts/generate_data.py
```

### 4. Validate the data

```bash
python scripts/validate_data.py
```

### 5. Continue with analysis

Open the EDA notebook and follow the documented cleaning and analysis workflow.

Load the cleaned datasets into PostgreSQL using the project schema and loading instructions.

Run the analytical SQL queries and compare the results with the Python analysis.

### 6. Open Power BI

Import the prepared tables into Power BI Desktop.

Follow the data model, relationship, KPI, and dashboard instructions in `docs/power_bi_guide.md`.

Build the report manually using the verified data.

---

## Limitations

- The dataset is synthetic and does not represent actual retail operations.
- The business scenario is simplified to a single distribution center.
- All financial amounts use USD.
- There are no invoices or payment transaction records.
- No pre-2024 purchase orders are included.
- Shipments are not linked to individual production batches.
- Quality inspection results represent samples, not necessarily every produced unit.
- Inventory issues are used as a demand proxy; they are not actual sales.
- Inventory valuation depends on the selected costing assumptions.

These limitations should be considered when interpreting the analysis.

---

## Future Improvements

- Add a sales dataset to study demand and replenishment.
- Introduce demand forecasting using historical consumption data.
- Compare supplier lead times and variability.
- Improve inventory replenishment analysis.
- Add supplier risk indicators.
- Expand the analysis to multiple distribution centers.
- Add automated data quality reporting.
- Improve dashboard drill-through and supplier-level analysis.

---

## About This Project

This project was created to practice data analysis and build a practical portfolio project around fashion sourcing and supply chain operations.

It focuses on understanding the data, defining useful metrics, checking data quality, and presenting results clearly.

**Project status:** Update this section as the project progresses.

**Author:** Krishna Yadav  
**GitHub:** [2KRISHNAYADAV](https://github.com/2KRISHNAYADAV)  
**LinkedIn:** [Krishna Yadav](https://linkedin.com/in/krishna203ker)  
**Portfolio:** [er-krishna-yadav.vercel.app](https://er-krishna-yadav.vercel.app)

---

*Data is synthetic. Dashboard previews are illustrative design references, not verified analytical results.*
