# Customer Onboarding Guide

## Metadata

- Category: Implementation
- Document Type: Process Guide
- Version: 3.1
- Status: Current
- Last Updated: 2026-07-15
- Authoritative: Yes
- Keywords: onboarding, onboarding process, implementation phases, enterprise onboarding, kickoff, discovery, solution design, environment setup, integration configuration, data migration, testing, UAT, training, go-live, hypercare, roles and responsibilities
- Use When: Someone asks what the onboarding process is, what happens in each phase, who is involved, or what the customer must provide.

## Summary

This guide describes how new NexaFlow customers are onboarded, from contract signature to post-launch support. Enterprise customers follow a nine-phase guided implementation that typically takes 4–6 weeks, while complex deployments take 8–12 weeks. The week-by-week schedule is defined in `implementation_timeline.md`, and Enterprise-specific technical setup (SSO, SCIM, workspaces, data residency) is covered in `enterprise_setup.md`.

## Main Content

### Onboarding Paths by Plan

| Plan | Onboarding Path | Typical Duration |
|---|---|---|
| Starter | Self-serve: online academy, templates, in-app checklist | 1–3 days |
| Professional | Self-serve or optional Quick Start package ($5,000) | 2 weeks with Quick Start |
| Enterprise | Guided implementation (required) | 4–6 weeks standard; 8–12 weeks complex |

The rest of this guide focuses on the Enterprise guided implementation.

### The Enterprise Onboarding Process: Nine Phases

**Phase 1 — Discovery and Requirements**
A kickoff meeting within 5 business days of contract signature introduces both teams. The NexaFlow solution architect runs discovery workshops to document the processes in scope, systems to integrate, data to migrate, security requirements, success metrics and the target go-live date. Output: signed-off Requirements Document.

**Phase 2 — Solution Design**
The solution architect designs the workflows, AI agents, workspace structure, roles and integration architecture. The customer reviews and approves the Solution Design Document. Changes after sign-off go through a change request.

**Phase 3 — Environment Setup**
NexaFlow provisions the tenant in the chosen region with Development, Staging and Production environments. The customer's IT team configures SSO, and for Enterprise, SCIM provisioning and role mapping. Details in `enterprise_setup.md`.

**Phase 4 — Integration Configuration**
The integration engineer connects the in-scope systems (up to 5 in the standard package) using service accounts, maps fields and builds the flows in Development. On-premise systems require installing NexaFlow Relay.

**Phase 5 — Data Migration**
Historical or reference data (for example open purchase requests, supplier lists or active cases) is cleansed, mapped, test-loaded and then migrated. The standard package covers up to 1 million records. See `data_migration_process.md`.

**Phase 6 — Testing**
System integration testing (SIT) is run by NexaFlow; user acceptance testing (UAT) is run by the customer's business users in Staging using real scenarios. Go-live requires zero open critical defects and UAT sign-off.

**Phase 7 — User Training**
Role-based training for admins, builders, operators and approvers, delivered live and through the NexaFlow Academy. See `training_and_adoption.md`.

**Phase 8 — Go-Live**
Flows are promoted to Production following a go-live checklist and cutover plan, usually mid-week with a rollback plan ready. A go/no-go meeting is held 2 business days before cutover.

**Phase 9 — Post-Launch Support (Hypercare)**
30 days of hypercare after go-live: daily check-ins in week 1, twice-weekly afterwards, priority defect resolution and a handover to the named Customer Success Manager. The hypercare period is **in addition to** the 4–6 week implementation window.

### Roles and Responsibilities

| NexaFlow | Customer |
|---|---|
| Engagement Manager — plan, status, risks | Executive Sponsor — decisions, priority, escalation |
| Solution Architect — discovery and design | Project Lead — day-to-day coordination (about 50% time) |
| Integration Engineer — connectors, migration | IT/Identity Admin — SSO, SCIM, network, Relay |
| Trainer — role-based training | Process Owners — requirements and UAT |
| Customer Success Manager — adoption after launch | Security Team — security review and approvals |

### What the Customer Must Provide

- A named executive sponsor and project lead before kickoff.
- Access to sandbox instances of each system to be integrated.
- Service accounts with required permissions.
- Sample and full data extracts for migration.
- Security questionnaire responses and approvals.
- UAT testers available during testing weeks.

### Governance

- Weekly status meeting and written status report (RAG status: red/amber/green).
- Steering committee every two weeks for Enterprise projects.
- Risks that threaten the go-live date are escalated within 2 business days.

### What Slows Onboarding Down

The most common causes of delay are late security review approval, unavailable sandbox systems, unclear data ownership, and business stakeholders not available for workshops or UAT. When these factors apply from the start, the project is planned on the complex 8–12 week track.

## Key Facts

- Enterprise onboarding has nine phases: discovery, solution design, environment setup, integration configuration, data migration, testing, training, go-live, post-launch support.
- Standard enterprise timeline: 4–6 weeks; complex deployments: 8–12 weeks.
- Kickoff occurs within 5 business days of signature.
- 30-day hypercare follows go-live.
- Customers must supply a sponsor, project lead, sandbox access and UAT testers.

## Related Documents

- implementation_timeline.md
- enterprise_setup.md
- data_migration_process.md
- training_and_adoption.md

## Retrieval Notes

Retrieve for "what is the onboarding process", "what happens after we sign", "implementation phases", "who is involved in onboarding" and "what do we need to provide". For the week-by-week duration also retrieve `implementation_timeline.md`; for SSO/SCIM/workspace configuration during enterprise onboarding also retrieve `enterprise_setup.md`. Pricing and case study files are not needed for process questions.
