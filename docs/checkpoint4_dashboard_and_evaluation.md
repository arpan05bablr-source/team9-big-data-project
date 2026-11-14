# Checkpoint 4 Dashboard and Evaluation Plan

Team 9's final analytical layer turns the validated silver table into gold tables, dashboard views, and an interpretable customer-segmentation model.

## Medallion pipeline

| Layer | Table | Purpose |
|---|---|---|
| Bronze | `workspace.default.retail_project_bronze` | Preserve the source CSV with ingestion timestamp and source metadata. |
| Silver | `workspace.default.retail_project_silver` | Standardise fields, cast types, remove duplicate business rows, and calculate line value. |
| Silver exceptions | `workspace.default.retail_project_silver_exceptions` | Preserve rows that fail required-field, date, quantity, or price rules. |
| Quality log | `workspace.default.retail_project_quality_log` | Record schema, duplicate, range, and reconciliation checks. |
| Gold | `workspace.default.retail_project_gold_daily_country` | Daily revenue, units, orders, customers, and products by country. |
| Gold | `workspace.default.retail_project_gold_monthly` | Monthly revenue, units, orders, customers, and average order value. |
| Gold | `workspace.default.retail_project_gold_country` | Country ranking and revenue share. |
| Gold | `workspace.default.retail_project_gold_product` | Product revenue, units, orders, customers, and average unit price. |
| Gold | `workspace.default.retail_project_gold_customer_rfm` | Customer recency, frequency, monetary value, and product breadth. |
| Gold model | `workspace.default.retail_project_rfm_model_evaluation` | Candidate `k` values, silhouette score, training cost, and customer count. |
| Gold model | `workspace.default.retail_project_rfm_segments` | Customer cluster assignments and RFM features. |

## Dashboard questions

The dashboard should answer these questions without requiring the audience to inspect the notebook:

1. **How does revenue change over time?** Use the monthly gold table as a line chart and include orders and average order value as supporting measures.
2. **Which countries and products contribute the most revenue?** Use a ranked country bar chart and a top-product table or bar chart.
3. **Which customer groups should receive different actions?** Use the RFM segment summary with customer count, average recency, average frequency, average monetary value, and revenue share.

## KPI definitions

- **Total revenue:** sum of `line_value` for valid, positive, non-cancelled sales.
- **Total orders:** distinct `invoice_id` values after the same sales filter.
- **Known customers:** distinct non-null customer IDs in valid sales.
- **Average order value:** total revenue divided by total orders.
- **Revenue share:** group revenue divided by total valid sales revenue.

## Model evaluation

The notebook evaluates KMeans models for `k = 2` through `k = 6` after standardising recency, frequency, and monetary value. It stores:

- **Silhouette score:** separation and cohesion of the clusters. Higher is better.
- **Within-set sum of squared error:** compactness of the clusters. Use it with the silhouette score to identify the elbow rather than choosing the largest `k` automatically.
- **Cluster size range:** smallest and largest cluster counts. A zero-sized cluster fails the acceptance rule.
- **Business interpretability:** cluster summaries must show materially different recency, frequency, or monetary patterns that can be explained in plain language.

The selected model is accepted only when the silhouette score is positive, every cluster has at least one customer, and the segment summary supports a clear business interpretation. The notebook prints the selected `k` and silhouette score after execution; the final report must copy the executed values rather than inventing them.

## Governance and limitations

The dataset is licensed under CC BY 4.0 and must be credited to the UCI Machine Learning Repository. Customer IDs are pseudonymous analytical keys. The team must not attempt to identify people. Revenue is a transaction proxy and does not represent warehouse, fulfilment, shipment, or delivery performance. Cancelled invoices and invalid records are excluded from sales KPIs and remain available in the exceptions table for audit.
