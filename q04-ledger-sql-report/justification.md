# Justification

The T-A-G (Task, Action, Goal) framework was applied by structuring the prompt around a clear analytical reporting objective, explicit SQL generation requirements and a business-oriented reporting outcome.

## Task

The task section defines the main responsibility of the model:
generate a PostgreSQL query for the Ledger monthly transaction report requested by Jennifer Parker.

This establishes the reporting context, the database schema and the business constraints required for accurate SQL generation.

## Action

The action section explicitly instructs the model to:
- use PostgreSQL syntax;
- apply date filtering logic;
- group by month and category;
- convert cents to BRL;
- round monetary values;
- sort results correctly;
- generate production-readable SQL.

These instructions guide the model toward generating an operational analytics query instead of a generic SQL example.

## Goal

The goal section defines the business objective:
provide Jennifer Parker with a reliable monthly transaction reporting query without requiring her to manually write SQL.

This component ensures the generated query remains:
- accurate;
- readable;
- production-safe;
- aligned with the expected reporting logic and business date range.

The goal also reinforces that the output must support executive reporting needs while preserving database query correctness.
