# Implementation Timeline

## Metadata

- Category: Implementation
- Document Type: Timeline & Planning Reference
- Version: 3.1
- Status: Current
- Last Updated: 2026-07-15
- Authoritative: Yes
- Keywords: implementation timeline, onboarding timeline, how long, weeks, go-live date, project plan, standard implementation, complex implementation, 4-6 weeks, 8-12 weeks, milestones, schedule risks, delays
- Use When: Someone asks how long implementation or onboarding takes, when go-live can happen, what happens each week, or what makes a project take longer.

## Summary

A standard NexaFlow Enterprise implementation takes **4–6 weeks** from kickoff to go-live, followed by 30 days of hypercare. Complex deployments typically take **8–12 weeks**, depending on the number of integrations, the volume of data migration, security review requirements and stakeholder availability. This document gives the week-by-week plan, milestones and the criteria used to classify a project as standard or complex. Phase descriptions are in `onboarding_guide.md`.

## Main Content

### Standard Enterprise Timeline (4–6 Weeks)

| Week | Phase | Key Activities | Milestone |
|---|---|---|---|
| Week 1 | 1. Discovery and Requirements | Kickoff, process workshops, system inventory, success metrics | Requirements signed off (end of week 1) |
| Weeks 1–2 | 2. Solution Design | Workflow and agent design, roles, integration architecture | Solution Design approved |
| Week 2 | 3. Environment Setup | Tenant provisioning, SSO, SCIM, workspaces, roles | Environments ready |
| Weeks 2–3 | 4. Integration Configuration | Connect up to 5 systems, field mapping, build flows in Dev | Integrations working in Dev |
| Weeks 3–4 | 5. Data Migration | Cleanse, map, test load, full migration (up to 1M records) | Migration validated |
| Weeks 4–5 | 6. Testing | SIT, UAT in Staging, defect fixing | UAT sign-off |
| Week 5 | 7. User Training | Admin, builder, operator and approver training | Training complete |
| Weeks 5–6 | 8. Go-Live | Go/no-go meeting, cutover, production promotion | Live in Production |
| +30 days | 9. Post-Launch Support | Hypercare, adoption tracking, CSM handover | Hypercare exit review |

Simple projects with few integrations and minimal migration go live at the end of week 4. Most standard projects go live in week 5 or 6.

### Complex Enterprise Timeline (8–12 Weeks)

| Weeks | Phase |
|---|---|
| Weeks 1–2 | Discovery and requirements (multiple business units or regions) |
| Weeks 2–3 | Solution design, security review in parallel |
| Weeks 3–4 | Environment setup (single-tenant or data residency adds ~1 week), Relay installation |
| Weeks 4–6 | Integration configuration (6+ systems, custom APIs, on-premise) |
| Weeks 5–8 | Data migration (above 1M records, multiple migration cycles) |
| Weeks 7–10 | Testing, including performance and security testing |
| Weeks 9–11 | Training by role and region, often in waves |
| Weeks 10–12 | Go-live (sometimes phased by business unit) |
| +30 days | Hypercare |

### Standard vs Complex: Classification Criteria

A project is planned as **complex (8–12 weeks)** if any two of the following apply, or if any one applies at large scale:

| Factor | Standard (4–6 weeks) | Complex (8–12 weeks) |
|---|---|---|
| Integrations | Up to 5 pre-built connectors | 6+ integrations, custom APIs, or on-premise via Relay |
| Data migration | Up to 1 million records, one source | Over 1 million records or multiple legacy sources |
| Security review | Standard questionnaire + SOC 2 (1–2 weeks) | Custom security assessment, penetration test coordination, HIPAA BAA, regulator requirements |
| Deployment | Multi-tenant, standard region | Single-tenant, customer-managed keys, strict data residency |
| Scope | 1–2 business units | Multiple business units, regions or languages |
| Stakeholder availability | Dedicated project lead and timely UAT | Limited availability, many approvers, change freezes |

Complex projects use the $35,000 Complex Implementation package; standard projects use the $15,000 Standard package (see `pricing_guide_v3.md`).

### Critical Path and Dependencies

1. **Security review** must be approved before production credentials are issued; start it at contract signature, not at kickoff.
2. **SSO configuration** depends on the customer's identity team and often takes 2–5 business days of their time.
3. **Sandbox access** for each integrated system must be available by the start of week 2.
4. **Data extracts** must be delivered by the start of week 3.
5. **UAT testers** must be booked for weeks 4–5.

A delay in any of these moves the go-live date by at least the same amount.

### Most Common Reasons Timelines Slip

| Cause | Typical Impact |
|---|---|
| Security review not started early | +2 to +4 weeks |
| Integration sandbox unavailable | +1 to +2 weeks |
| Poor data quality found during test load | +1 to +3 weeks |
| Stakeholders unavailable for workshops or UAT | +1 to +2 weeks |
| Scope added after design sign-off | +1 week per major workflow |

### How to Communicate Timelines to Customers

- Quote "4–6 weeks for a standard enterprise implementation" only after checking the classification criteria.
- For regulated industries (financial services, healthcare) or on-premise systems, set expectations at 8–12 weeks.
- Always state that 30 days of hypercare follow go-live.
- Never promise a go-live date before discovery is complete.

## Key Facts

- Standard enterprise implementation: 4–6 weeks from kickoff to go-live.
- Complex deployments: 8–12 weeks.
- Main drivers of complexity: integrations, data migration volume, security review and stakeholder availability.
- 30-day hypercare follows every enterprise go-live.
- Security review should start at contract signature to protect the timeline.

## Related Documents

- onboarding_guide.md
- enterprise_setup.md
- data_migration_process.md
- integration_guide.md

## Retrieval Notes

Retrieve for any question about duration: "how long does onboarding take", "typical implementation timeline", "when can we go live", "why would it take 12 weeks". For what happens inside each phase also retrieve `onboarding_guide.md`; for enterprise technical setup retrieve `enterprise_setup.md`. Case studies contain example timelines but are not the authoritative source.
