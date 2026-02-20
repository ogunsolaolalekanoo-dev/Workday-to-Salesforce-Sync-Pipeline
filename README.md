# Workday → Salesforce Data Integration Pipeline

**Type:** Enterprise Data Engineering System  
**Domain:** HR → CRM Identity Reconciliation  
**Focus:** Deterministic identity resolution, schema normalization, and Salesforce-ready upsert exports

## Overview
This repository contains a reproducible pipeline that reconciles nested Workday Worker JSON with Salesforce contact records.  
It normalizes semi-structured HR exports, resolves identity via deterministic email matching, detects duplicates, and generates validated CREATE/UPDATE upsert files for safe Salesforce ingestion.

## Key Capabilities
- Parse and normalize nested Workday Worker JSON  
- Construct deterministic email identity sets (multi-field email reconciliation)  
- Match Workday workers to Salesforce contacts (exact-match intersection)  
- Classify **Create vs Update** records for controlled upsert processing  
- Detect potential duplicates / identity collisions  
- Generate Salesforce-ready exports (CSV + optional Excel audit copy)  
- Run validation checks (counts, duplicates, coverage, mismatches)

## Outputs
Typical outputs include:
- `Salesforce_Workday_Upsert.csv`
- `Contacts_CREATE.csv`
- `Contacts_UPDATE.csv`
- `Salesforce_Workday_Upsert.xlsx` (optional audit copy)

## Repository Structure
workday-salesforce-data-integration/
├── notebooks/
│ └── email_mapping_pipeline.ipynb
├── docs/
│ └── architecture.md
├── data/
│ ├── raw/
│ └── processed/
└── exports/


## Data Governance
- This repo does **not** include real PII.
- Use anonymized or synthetic samples only.
- Keep raw exports local and excluded via `.gitignore`.

## Tech Stack
Python, pandas, JSON processing, CSV/Excel exports, validation checks

## Notes
This project emphasizes **data integrity** and **safe enterprise ingestion**: deterministic identity resolution, duplication prevention, and validation before export.

# Architecture

## Inputs
- Workday Worker JSON export
- Salesforce Contacts export
- (Optional) Salesforce Accounts reference export

## Processing Stages
1. JSON parsing & normalization
2. Email identity set construction
3. Cross-system matching (Workday ↔ Salesforce)
4. Duplicate detection
5. Create vs Update classification
6. Export generation (CSV/Excel)
7. Validation summary

## Outputs
- Salesforce-ready CREATE/UPDATE upsert files
- Validation summary metrics
