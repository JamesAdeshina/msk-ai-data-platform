# MSK-AI | Cloud Data Engineering & Analytics Platform

## Project Overview

MSK-AI is an end-to-end cloud data engineering platform designed to automate the ingestion, validation, transformation, storage, and analysis of Functional Movement Screen (FMS) research data.

The platform enables authorised researchers to upload weekly assessment datasets through a web interface. An event-driven AWS pipeline processes incoming records, performs data quality checks, and publishes validated data to Amazon Redshift for downstream analytics using Microsoft Power BI.

The project demonstrates practical data engineering principles, including serverless architecture, ETL/ELT development, data quality management, cloud data warehousing, pipeline observability, and analytics integration.

**Project status:** In development — MVP implementation.

## Business Problem

Musculoskeletal health research can involve repeated collection of movement assessment data across participants, research sites, and reporting periods.

Manual processing of these datasets introduces operational challenges:

- Inconsistent data formats and naming conventions.
- Duplicate participant identifiers and assessment records.
- Missing or invalid movement assessment scores.
- Discrepancies between recorded and calculated FMS totals.
- Delays in preparing research-ready datasets.
- Limited visibility into data processing failures.
- Manual updates to analytical reports.

MSK-AI aims to address these challenges through a centralised, automated data platform.

## Proposed Solution

The platform provides:

1. **Secure Data Ingestion:** Weekly CSV uploads through a web application.
2. **Automated Data Validation:** Schema checks, duplicate detection, score-range validation, and FMS total reconciliation.
3. **Data Transformation:** Standardisation of demographic and assessment fields, calculation of BMI, FMS composite scores, and bilateral asymmetry indicators.
4. **Data Quality Management:** Quarantine workflows, validation reports, and controlled reprocessing.
5. **Cloud Data Warehousing:** Curated analytical datasets stored in Amazon Redshift.
6. **Business Intelligence:** Power BI dashboards for assessment trends, movement performance, and data quality.
7. **Pipeline Monitoring:** Execution tracking, audit logging, and operational alerts.

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript |
| Authentication | Amazon Cognito |
| API | Amazon API Gateway |
| Storage | Amazon S3 |
| Processing | AWS Lambda, Python, pandas |
| Orchestration | AWS Step Functions |
| Data Warehouse | Amazon Redshift Serverless |
| Analytics | Microsoft Power BI |
| Monitoring | Amazon CloudWatch |
| Infrastructure | AWS SAM or Terraform |
| Version Control | Git, GitHub |
| CI/CD | GitHub Actions |

## Data Engineering Features

- Event-driven ingestion of weekly research datasets.
- Raw, validated, curated, and quarantined data zones.
- Automated schema and business-rule validation.
- Record-level data quality reporting.
- Idempotent batch processing to prevent accidental duplicate ingestion.
- FMS composite score reconciliation.
- Derived movement asymmetry and anthropometric metrics.
- Audit trails and processing-status monitoring.
- Separation of real clinical data and synthetic testing data.

## Data Provenance

The project originated from an exploratory FMS dataset containing 46 participant records.

Synthetic datasets were subsequently generated to support pipeline development and scalability testing.

Synthetic records are simulated and must never be presented as additional real participants or as evidence of clinical effectiveness.

Production research datasets and synthetic testing datasets are logically separated.

## Expected Business Value

- Reduce repetitive manual data preparation.
- Improve data quality and traceability.
- Standardise assessment reporting across research sites.
- Support more timely research analytics.
- Enable reproducible data processing.
- Establish a scalable foundation for future, independently validated predictive modelling.

## Current Scope

The initial MVP focuses on building and demonstrating a functioning ingestion-to-analytics pipeline using synthetic test data.

Predictive clinical risk assessment, automated treatment recommendations, and deployment with real patient data are outside the initial MVP scope.

## Project Deliverables

- Web-based data upload and administration interface.
- AWS serverless ingestion and transformation pipeline.
- Automated validation and quarantine system.
- Redshift analytical data model.
- Power BI research dashboard.
- Infrastructure and deployment documentation.
- End-to-end testing and demonstration evidence.

## Security and Responsible Use

This repository is intended to contain application code, infrastructure definitions, documentation, and non-sensitive demonstration data only.

Real participant records, credentials, AWS secrets, and identifiable health information must not be committed to GitHub.

The platform is a research data engineering demonstration and is not a validated clinical diagnostic or treatment recommendation system.


## Repository structure
msk-ai-data-platform/
│
├── frontend/                  # React web application
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── App.tsx
│   └── package.json
│
├── backend/
│   ├── api/                   # Upload and batch APIs
│   ├── lambdas/
│   │   ├── validate_upload/
│   │   ├── transform_fms/
│   │   └── load_warehouse/
│   └── shared/                # Shared validation logic
│
├── infrastructure/
│   └── template.yaml          # AWS SAM infrastructure
│
├── sql/
│   ├── create_tables.sql
│   └── analytics_views.sql
│
├── powerbi/                   # Dashboard documentation
├── tests/                     # Automated tests
├── data/
│   └── synthetic_samples/     # Synthetic demo data only
├── docs/
│   ├── architecture.md
│   ├── data_dictionary.md
│   └── deployment.md
│
├── .github/
│   └── workflows/
├── .gitignore
├── README.md
├── requirements.txt
└── LICENSE
