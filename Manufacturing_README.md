# Manufacturing Analysis Workbook

A 12-month procurement cost analysis for a $300M-revenue steel door manufacturer, built from raw purchase order line items for a single galvalume steel coil supplier. The project identifies concrete cost optimization opportunities across material rates, freight, fuel surcharges, and order sizing.

Delivered as both an Excel case study workbook and a reproducible Python / Jupyter notebook that walks through the full analysis with commentary.

---

## What's in here

| File | Description |
|---|---|
| `Manufacturing_Analysis_Workbook.ipynb` | **Main deliverable.** Python / pandas notebook that loads the raw PO data, cleans it, and walks through four sections of analysis with commentary, tables, and visualizations. |
| `Manufacturing Case Study - Analysis.xlsx` | Source Excel workbook containing the purchase order line item data plus case study framing. |

---

## The project

### Business context

A steel door manufacturer generating ~$300M in annual revenue, purchasing galvalume and aluminum coil stock from a single supplier across 12 months (April 2023 – March 2024). Total procurement spend for the period exceeded $35M, with material costs alone representing 87.8% of that.

The question: **where can we find real, defensible cost savings in this procurement relationship?**

### Data

Roughly 1,000+ purchase order line items pulled from the supplier's invoice records. Each row captures:

- Invoice metadata — invoice date, PO number, ship-to city
- Material specs — part number, gauge / thickness, paint finish
- Quantity — linear feet, weight in pounds
- Rate components — material rate, emboss rate, freight rate, fuel surcharge %
- Expense totals — product cost, emboss cost, freight cost, fuel surcharge, line total

### Stack

- **Python / pandas / numpy** for all data transformation
- **openpyxl** for reading the source Excel workbook
- **Jupyter** for the narrative analysis notebook

---

## Analysis sections

The notebook is organized into four focused investigations:

**Section A — Spending Overview.** Monthly expense trends by category. Establishes the baseline: $35.3M total spend, 87.8% material, 9.1% freight + fuel combined. Reveals a striking 15:1 peak-to-trough seasonal volume ratio that drives everything else.

**Section B — Location & Freight Analysis.** Ship-to city as a cost driver. Nashville vs. Sacramento freight rates differ by $9.02 per 100 lbs — a geographic spread large enough to justify reconsidering routing or carrier selection.

**Section C — Part Number & Material Analysis.** 91.3% of total spend flows through just two part numbers, meaning any rate negotiation should focus there. Aluminum carries a 3.5× premium over galvalume. Same-gauge (0.019″) stock shows a $20 per 100 lbs rate spread purely from paint finish, and small orders get hit with a $12 per 100 lbs penalty versus large orders — suggesting consolidation savings.

**Section D — Rate Trends & Fuel Surcharges.** Seasonal material rate swings and a fuel surcharge outlier of 329.5% on one invoice that warrants a direct conversation with the supplier.

---

## Key findings

| Finding | Value |
|---|---|
| Total spend (12 months) | $35.3M |
| Material as % of total | 87.8% |
| Freight + fuel combined | $3.2M (9.1%) |
| Peak-to-trough volume ratio | 15 : 1 |
| Nashville vs. Sacramento freight gap | $9.02 per 100 lbs |
| Top 2 parts concentration | 91.3% of spend |
| Aluminum cost premium | 3.5× galvalume rate |
| Same-thickness rate spread (paint finish) | $20 per 100 lbs |
| Small order penalty vs. large | $12 per 100 lbs |
| Fuel surcharge outlier (investigation flag) | 329.5% |

---

## Running the notebook

```bash
pip install pandas numpy openpyxl jupyter

jupyter notebook Manufacturing_Analysis_Workbook.ipynb
```

The notebook reads directly from `Manufacturing Case Study - Analysis.xlsx` in the same directory. Run all cells top to bottom — each section is self-contained and produces inline tables and charts.

---

## Notes on methodology

- **Single-supplier scope.** All findings apply to this one galvalume coil relationship. Multi-supplier benchmarking would require additional data.
- **Rate units are per 100 lbs (CWT)** throughout, matching standard steel industry pricing conventions.
- **Fuel surcharges are percentages of base freight**, not dollar amounts — worth remembering when comparing outliers.
- **Concentration risk cuts both ways.** 91.3% of spend in two SKUs gives strong negotiation leverage but also creates supply chain fragility worth flagging to leadership.

---

## About

Portfolio project by Zachari ([@SundayKoi](https://github.com/SundayKoi)) demonstrating applied procurement analytics — translating raw transactional data into specific, dollar-quantified recommendations for cost reduction.
