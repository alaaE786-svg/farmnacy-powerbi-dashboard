# Project Description: Farmnacy Pharma Performance Dashboard

## 1. Overview

Farmnacy is a three-page Power BI dashboard that analyzes pharmaceutical sales. It helps a sales manager see total performance, compare product lines and channels, and identify the top products and customers.

> The data used is sample data for learning and portfolio purposes. It is not real company data.

## 2. Objective

Turn raw sales records into a clear, interactive report that answers:

1. How much did we sell, and how many units?
2. Which product lines and products drive revenue?
3. How do sales change from month to month?
4. Which sales channel (STORE, RETAIL, Tender) contributes the most?
5. Which customers and territories matter most?

## 3. Target Audience

- Sales managers
- Sales and marketing analysts
- Management reviewing monthly performance

## 4. Data

A single flat table (`Table3`) with the main fields below.

| Field | Description |
|---|---|
| SALES VALUE | Sales amount of the transaction |
| SALES UNITS | Number of units sold |
| CUSTOMER NAME | Customer or account name |
| Territory | Sales territory |
| EGPI Product Name | Product name |
| Line Name | Product line (Line 1 to Line 5, CVM, Tender) |
| SALES TYPE | Sales channel (STORE, RETAIL, Tender) |
| Month | Transaction date, used for Quarter, Month and Day filtering |

Period covered: January to March.

## 5. DAX Measures

```dax
Total Sales     = SUM(Table3[SALES VALUE])
Total units     = SUM(Table3[SALES UNITS])
Total customers = DISTINCTCOUNT(Table3[CUSTOMER NAME])
Total Products  = DISTINCTCOUNT(Table3[EGPI Product Name])
Total Territory = DISTINCTCOUNT(Table3[Territory])
```

## 6. Report Pages

### Overview
Entry page with the dashboard title and navigation buttons to the other pages.

### Sales
- Cards: Total units, Total Sales, Avg Order Value
- Waterfall: sales by product line
- Bar chart: sales by customer
- Pie chart: sales by sales type
- Line chart: sales by month

### Product & Customer
- Cards: Total customers, Total Territory, Total Products
- Bar charts: sales by product name
- Treemap: sales by customer
- Table: customer performance (sales, units, products)

## 7. Interactivity

- Slicers: Line Name, Quarter, Month, Day
- "Clear all slicers" button on every analysis page
- Page navigation buttons
- Cross-filtering between visuals

## 8. Key Findings

- Total sales reached 109M with about 3M units across 47 products and 46 territories.
- February was the peak month at 44M, about 34% above January (32.8M). March fell to 32.1M.
- The STORE channel generated 67.85% of sales (74M), RETAIL 31.73% (35M).
- Line 2 was the largest product line at 37M, roughly one third of total sales.
- Top products: Lamifen cr. 15gm (15.6M), Flacort 30mg 20 tab. (10.5M), Aqua plus 100ml (9.0M).

## 9. Design Decisions

- Green theme matching the pharma domain.
- Consistent layout across pages: navigation on top, slicers on the left, visuals on the right.
- Clear titles on every chart and data labels on all key visuals.

## 10. Limitations

- Data covers three months only, so no year-over-year comparison.
- The model is a single flat table, not a star schema.

## 11. Future Improvements

- Build a star schema with Fact_Sales, Dim_Date, Dim_Customer and Dim_Product.
- Add a Date table and month-over-month growth measures.
- Add Top N customers and a drill-through page.
- Add tooltip pages for products and customers.

## 12. Tools

Power BI Desktop, DAX.
