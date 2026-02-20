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
