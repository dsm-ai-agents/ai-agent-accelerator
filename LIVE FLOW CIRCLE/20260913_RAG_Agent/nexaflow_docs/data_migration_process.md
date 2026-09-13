# Data Migration Process

## Metadata

- Category: Implementation
- Document Type: Process Guide
- Version: 2.2
- Status: Current
- Last Updated: 2026-06-30
- Authoritative: Yes
- Keywords: data migration, data import, legacy data, data mapping, data cleansing, test load, reconciliation, cutover, CSV import, records, migration tool, data quality, rollback
- Use When: Someone asks how data is moved into NexaFlow, what data can be migrated, how long migration takes, or how data quality is validated.

## Summary

Data migration is Phase 5 of the NexaFlow onboarding process and usually runs in weeks 3–4 of a standard 4–6 week enterprise implementation. This document explains what data is typically migrated, the six-step migration method, roles, data quality rules, validation and cutover. Migrations above 1 million records or from multiple legacy sources usually place a project on the complex 8–12 week track.

## Main Content

### What Gets Migrated

NexaFlow orchestrates work across systems, so most business records stay in their systems of record (ERP, CRM, HRIS). Migration usually covers:

| Data Type | Examples |
|---|---|
| In-flight work items | Open purchase requests, pending approvals, active cases, open onboarding tasks |
| Reference data | Supplier lists, cost centres, approval hierarchies, product catalogues, SLA rules |
| Historical run data | Past 12–24 months of process history for dashboards and AI agent context |
| Documents | Templates, policies and knowledge sources for AI agents |
| Workflow definitions | Rules from legacy tools (for example old BPM or RPA scripts), rebuilt as flows |

Legacy workflow logic is **rebuilt**, not automatically converted.

### Migration Scope by Package

| Package | Records Included | Sources | Migration Cycles |
|---|---|---|---|
| Enterprise Standard | Up to 1 million | 1–2 sources | 1 test load + 1 final load |
| Enterprise Complex | Above 1 million | Multiple legacy sources | Up to 3 test loads + final load |
| Professional Quick Start | Up to 50,000 | 1 source (CSV) | 1 load |

### The Six-Step Migration Method

**Step 1 — Inventory and Ownership (Week 1, during discovery)**
List every data set, its source system, volume, owner and whether it is needed at go-live. Data without a named owner is excluded until one is assigned.

**Step 2 — Mapping (Weeks 2–3)**
Map source fields to NexaFlow objects in a mapping workbook: field name, type, transformation rule, default value and validation rule. The customer data owner signs off the mapping.

**Step 3 — Extraction and Cleansing (Week 3)**
The customer extracts data (CSV, database export or API). NexaFlow's migration tool profiles the data and reports duplicates, missing mandatory fields, invalid dates and broken references. The customer fixes source data or approves transformation rules.

**Step 4 — Test Load (Week 3)**
A test load into Staging using full or representative data. Reconciliation compares record counts, sums of key numeric fields and a 5% random sample checked by business users.

**Step 5 — Final Load (Week 4)**
After test load sign-off, the final load runs, usually during a planned window before go-live. In-flight work items are frozen in the legacy system for a short cutover period (typically 24–48 hours).

**Step 6 — Validation and Sign-Off (Week 4)**
The customer confirms reconciliation results. Migration must be signed off before UAT is completed and before the go/no-go meeting.

### Data Quality Acceptance Criteria

| Check | Threshold |
|---|---|
| Record count match | 100% |
| Mandatory fields populated | 100% |
| Key numeric totals (e.g., invoice amounts) | Exact match |
| Random sample accuracy | At least 99.5% |
| Duplicate records | 0 after cleansing |

### Roles

| Role | Responsibility |
|---|---|
| NexaFlow Integration Engineer | Migration tooling, mapping workbook, test and final loads |
| Customer Data Owner | Approves mapping, fixes source data, signs off reconciliation |
| Customer IT | Provides extracts and database access |
| Business Users | Validate random samples |

### Security During Migration

- Files are transferred via encrypted SFTP or direct connector, never by email.
- Staging data is encrypted at rest (AES-256) and access is logged.
- Temporary migration files are deleted within 14 days of sign-off.
- For healthcare customers, PHI is migrated only after the BAA is signed.

### Rollback

If the final load fails reconciliation, the load is rolled back, the legacy system remains the system of record, and the go-live date is re-planned. Rollback procedures are rehearsed during the test load.

### Timeline Risks

| Risk | Impact |
|---|---|
| Poor source data quality | +1 to +3 weeks |
| Extracts delivered late | Day-for-day delay |
| More than 1M records or multiple sources | Project classified as complex (8–12 weeks) |
| Mapping changes after sign-off | Additional test load cycle (+1 week) |

## Key Facts

- Data migration is Phase 5, typically weeks 3–4 of a standard enterprise implementation.
- Standard package covers up to 1 million records from 1–2 sources.
- Six steps: inventory, mapping, extraction/cleansing, test load, final load, validation.
- Random sample accuracy must be at least 99.5%; record counts must match 100%.
- Large or multi-source migrations push onboarding to 8–12 weeks.

## Related Documents

- onboarding_guide.md
- implementation_timeline.md
- enterprise_setup.md
- integration_guide.md

## Retrieval Notes

Retrieve for questions about moving data into NexaFlow, legacy data, CSV import, data mapping, data quality checks, cutover or migration timeline risks. For a general enterprise onboarding process question, this file is supporting detail; the primary files are `onboarding_guide.md`, `implementation_timeline.md` and `enterprise_setup.md`.
