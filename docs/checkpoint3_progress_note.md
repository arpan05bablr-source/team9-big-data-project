# Team 9 - Checkpoint 3 Progress Note

Team members: Arpan, Vishal, Pranav, Abinash, Rupjeet, and Anil.

1. We created a Databricks notebook that reads the uploaded Online Retail II CSV into a bronze Delta table with source-file metadata and an ingestion timestamp.
2. The silver transformation standardizes column names and data types, removes exact duplicate records, and preserves invalid or incomplete records in an exceptions table.
3. We added repeatable checks for required columns, duplicate rows, null customer identifiers, non-positive quantities or prices, and bronze-to-silver row reconciliation.
4. The notebook has been prepared for a small-sample test; replace this sentence with the actual run status and counts from the Team 9 workspace.
5. Next, we will validate the full run, complete the gold warehouse tables, and build the dashboard; the main risks are Databricks quota limits and the dataset's missing or cancelled transactions.
