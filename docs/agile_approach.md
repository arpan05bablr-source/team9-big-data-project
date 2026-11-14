# Team 9 Agile Process for the Big Data Project

Team members: Arpan, Vishal, Pranav, Abinash, Rupjeet, and Anil.

Project repository: https://github.com/arpan05bablr-source/team9-big-data-project

## Project objective

Team 9 is building a repeatable retail analytics pipeline using the UCI Online Retail II dataset. The project is developed incrementally so that each milestone produces working evidence, receives review, and informs the next set of tasks. Our Agile process covers the complete project from initial understanding of the problem through ingestion, transformation, quality assurance, analytical modelling, reporting, and final handover.

## Backlog and product increments

The backlog is organised around outcomes rather than isolated code tasks. Each item has a clear acceptance condition, an owner, a peer reviewer, and a place where the evidence will be recorded.

| Project increment | Main outcome | Acceptance evidence |
|---|---|---|
| 1. Discovery and scope | Define the business problem, dataset, assumptions, risks, and success criteria. | Project scope, dataset description, assumptions, and milestone plan |
| 2. Data ingestion | Load the source file reproducibly into the Databricks environment without applying business transformations. | Source file in the Unity Catalog Volume, bronze Delta table, and ingestion metadata |
| 3. Data transformation | Standardise names and types, clean text, identify cancellations, calculate line values, and remove duplicate business rows. | Silver Delta table, documented transformation rules, and sample output |
| 4. Quality and exceptions | Detect schema, null, range, duplicate, and reconciliation problems while preserving rejected records. | Exceptions table, repeatable quality log, and recorded test results |
| 5. Analytical model | Create trusted fact and dimension outputs that support sales, product, country, and customer analysis. | Gold tables, business definitions, and validation queries |
| 6. Reporting and handover | Present useful findings and make the solution understandable and rerunnable by another student. | Dashboard or report, README, Agile write-up, limitations, and run instructions |

## Agile workflow

At the start of an increment, the team clarifies the expected outcome and breaks it into small tasks. Tasks are prioritised by dependency and risk: ingestion and schema decisions come before transformations, transformations come before quality checks, and trusted data comes before reporting. The team keeps the notebook and documentation aligned so that the repository remains the shared source of truth.

Each task follows the same flow:

1. Define the task and its acceptance condition.
2. Assign an owner and a peer reviewer.
3. Implement the smallest useful change.
4. Run the code on a controlled sample and inspect the output.
5. Review the code, counts, exceptions, and documentation.
6. Record the result, decision, or blocker and move the item to done only when the acceptance condition is met.

## Team cadence and responsibilities

The team uses a short weekly coordination meeting. Each member reports completed work, the next task, and any blocker. Between meetings, work is split into small notebook, validation, or documentation changes so that progress can be reviewed frequently. The person who makes a change is not the only person responsible for accepting it: another member checks the code, output, and explanation before the item is marked complete.

Responsibilities are shared across five activities:

1. Data preparation: source files, schema, naming, and ingestion.
2. Transformation: cleaning, typing, deduplication, and business rules.
3. Validation: quality checks, counts, exceptions, and reconciliation.
4. Documentation: progress notes, limitations, and run instructions.
5. Review and coordination: integration, peer review, and submission readiness.

Responsibilities can rotate between milestones so that every member understands the full pipeline rather than only one layer.

## Definition of done

A project task is done only when the code runs in the intended order, its output is checked, the rule is documented, and another member can explain or rerun it. For the complete project, this means:

- the source and assumptions are documented;
- the bronze, silver, and later gold outputs are reproducible;
- invalid or incomplete records are visible rather than silently discarded;
- quality checks are repeatable and their results are recorded;
- analytical outputs answer the agreed project questions;
- the README explains the environment, paths, dependencies, and run order; and
- the final repository and submission files match the work that was actually completed.

## Testing, feedback, and adaptation

The team runs a small sample before a full-data run to identify schema, parsing, and logic errors quickly and to manage Databricks Free Edition limits. The same checks are rerun after each material change. A failed check becomes a specific backlog item rather than being ignored. The team records the cause, fix, rerun result, and any remaining limitation in the progress note.

During the bronze and silver increment, the sample run produced 10,634 bronze rows, 10,353 clean silver rows, 273 exception rows, and 8 duplicate business rows removed during deduplication. The initial reconciliation check exposed that duplicate removal was not included in the equation; the team corrected the quality-check logic so that clean rows, exceptions, and duplicates removed are all accounted for. This illustrates how testing feedback is used to improve the pipeline before the next increment.

## Risks, constraints, and communication

Databricks Free Edition compute and storage limits make sample-first execution and clear run notes important. The dataset represents retail transactions; it does not contain Amazon warehouse, fulfilment, shipment, or delivery events. The team will therefore describe the result as a retail transaction analytics pipeline and will not claim operational Amazon data or production-scale performance.

The repository is the shared source of truth for the notebook, README, progress note, and Agile approach. Changes are kept small and committed with clear messages. Blockers, failed checks, decisions, scope changes, and contributions are recorded so that the final submission explains how the complete project was developed.
