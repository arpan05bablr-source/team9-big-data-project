# Team 9 Data Governance Note

## Dataset and licence

The project uses the UCI Online Retail II dataset. The source is credited to the UCI Machine Learning Repository and is distributed under the Creative Commons Attribution 4.0 International licence. The final submission should retain the source link and attribution: https://archive.ics.uci.edu/dataset/502/online+retail+ii.

## Privacy and responsible use

The customer identifier is treated as a pseudonymous analytical key. It is used only to calculate repeat-purchase, recency, frequency, and monetary-value measures. The project does not attempt to identify individuals, infer sensitive attributes, or publish customer-level identifiers. Dashboard outputs should use aggregates or segment labels rather than individual customer records.

## Data quality controls

The pipeline preserves the source in bronze, standardises fields in silver, and records invalid rows separately. The quality log checks required columns, duplicate business rows, positive quantity, positive unit price, and row reconciliation. Cancelled invoices and rows with invalid business fields are excluded from sales KPIs but remain traceable in the exceptions output.

## Bias and limitations

The data represents historical transactions from one online retailer and should not be treated as a representative sample of all retail customers. It does not contain marketing exposure, fulfilment events, product cost, returns context beyond invoice conventions, or customer demographics. RFM segments describe observed transaction behaviour; they do not prove customer intent, future value, or causation. Recommendations should therefore be used for prioritisation and hypothesis generation, followed by business validation.

## Access and reproducibility

The source file is stored in the team’s Databricks Volume and is referenced by the notebook through the Volume path. The repository stores code, documentation, and notebook outputs—not the full source dataset. Team members should run the notebook with the same catalog/schema configuration and record the final row counts, quality results, and model metrics in the learning log.
