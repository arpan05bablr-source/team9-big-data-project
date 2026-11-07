# Team 9 - Agile Approach to the Big Data Project

Team members: Arpan, Vishal, Pranav, Abinash, Rupjeet, and Anil.

## Purpose

We use a lightweight Agile approach so the project produces working evidence at every checkpoint. The Amazon Data Engineer I posting defines the capability gaps, and each checkpoint is a small increment toward a rerunnable retail analytics pipeline.

## Backlog and increments

1. Bronze ingestion: load raw data reproducibly without business transformations.
2. Silver transformation: standardise data types, remove duplicates, classify cancellations, and preserve exceptions.
3. Quality checks: detect schema, null, duplicate, range, and reconciliation failures.
4. Gold model: create fact and dimension tables for sales and customer-value questions.
5. Dashboard and handover: provide clear metrics, governance notes, and rerun instructions.

## Team cadence

We hold one short weekly stand-up. Each member reports what they completed, what is blocked, and what they will do next. Tasks are assigned to an owner and reviewed by another member. Roles are Data Wrangler, Analyst, Storyteller, Governance Guardian, and Project Captain; roles rotate after Checkpoint 3.

## Definition of done

A task is done only when the code runs in the intended order, its output is checked, the rule is documented, and another member can explain or rerun it. For Checkpoint 3, bronze and silver tables must be created, exceptions preserved, quality results written down, and the notebook exported as an ipynb file.

## Feedback and adaptation

We test on a small sample before using the full dataset because Databricks Free Edition has daily compute limits. Feedback from each checkpoint is added to the backlog and converted into a concrete change for the next increment. If a requirement cannot be completed, we record the limitation rather than presenting an unverified result.

## Transparency and learning

The learning log records dated decisions, failures, fixes, and contributions. If an AI assistant helps with code or writing, the team records that use and reviews every line before submission. The team will not claim production-scale experience, Amazon operational data, or use of a proprietary ETL tool that was not actually used.
