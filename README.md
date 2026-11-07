# Big Data Project Work - Team 9 - Checkpoint 3

Team members: Arpan, Vishal, Pranav, Abinash, Rupjeet, and Anil.

## Project

Retail Transaction Data Warehouse and Quality-Assured Analytics Pipeline.

This repository contains Team 9's Checkpoint 3 artefacts for the Amazon Data Engineer I skill-gap project. The project uses the Online Retail II dataset from the UCI Machine Learning Repository under CC BY 4.0.

## Deliverables

- notebooks/checkpoint3_bronze_silver.ipynb - Databricks notebook for raw ingestion into bronze and cleaning into silver.
- docs/checkpoint3_progress_note.md - five-line progress note required by the student guide.
- docs/agile_approach.md - Agile approach write-up.

## Running the notebook

1. Download the Online Retail II workbook from UCI, convert the required worksheet to CSV locally, and upload the CSV to a Unity Catalog Volume.
2. Set source_path and the catalog/schema/table names in the notebook.
3. Run on a small sample first, then run the full dataset after the checks are understood.
4. Export the notebook as an .ipynb file and keep actual run results in the progress note.

The notebook intentionally does not invent row counts or test outcomes.

## Scope and limitations

The dataset is a retail-transaction proxy. It does not contain Amazon warehouse, fulfilment-centre, shipment, or delivery events. Customer IDs are treated as pseudonymous analytical keys; no attempt should be made to identify individuals.

## Suggested Git workflow

Use small commits, review notebook changes with a teammate, and record blockers and decisions in the learning log.
