# Case Study: HealthPlus Medical Group

## Metadata

- Category: Case Studies
- Document Type: Customer Case Study
- Version: 1.0
- Status: Approved for external use
- Last Updated: 2026-05-14
- Authoritative: Yes (for HealthPlus results)
- Keywords: case study, healthcare, hospital, clinics, patient referrals, prior authorization, patient intake, HIPAA, BAA, EU data residency, Epic, 45% faster referrals, 22 hours saved per week, complex implementation
- Use When: Someone needs a healthcare reference, a HIPAA-compliant deployment example, or proof of faster referral and prior authorization processing.

## Summary

HealthPlus Medical Group, a multi-specialty provider with 14 clinics and 6,000 staff, used NexaFlow to automate patient referrals, prior authorization requests and new patient intake. Because of HIPAA requirements, a Business Associate Agreement and integration with its electronic health record system, the project followed the complex implementation track and went live in 11 weeks. HealthPlus now processes referrals 45% faster and cut its referral coordinators' manual work from 22 to about 4 hours per week.

## Main Content

### Customer Profile

| Attribute | Detail |
|---|---|
| Industry | Healthcare (multi-specialty medical group) |
| Locations | 14 clinics and 1 ambulatory surgery center |
| Employees | 6,000 |
| Plan | Enterprise, 260 Full Users, HIPAA BAA, US region |
| Systems | Epic EHR (via NexaFlow Relay and HL7/FHIR APIs), Microsoft 365, ServiceNow, fax-to-email gateway, payer portals |
| Go-live | March 2026 |

### The Problem

Referrals from outside physicians arrived by fax, e-referral portals and phone. Coordinators re-typed patient demographics and clinical notes into the EHR, checked insurance eligibility manually, and submitted prior authorization requests through several payer portals.

- Average time from referral received to appointment scheduled: **9 days**.
- Referral coordinators spent about **22 hours per week** collectively on re-keying and status chasing.
- About 18% of prior authorization requests were initially denied for missing documentation.
- Patients called repeatedly to ask about referral status, overloading clinic front desks.

### The Implementation

HealthPlus followed NexaFlow's nine-phase onboarding process on the **complex track (11 weeks)**. Complexity drivers were the HIPAA BAA negotiation, a detailed security and privacy review, EHR integration through NexaFlow Relay, and training for staff across 14 clinics.

| Weeks | Activity |
|---|---|
| 1–2 | Discovery with referral management, revenue cycle, privacy office and IT |
| 1–4 | Security and privacy review; BAA signed in week 4 |
| 2–3 | Solution design, including PHI redaction rules for AI agents |
| 3–5 | Environment setup, SSO + SCIM, Relay installation in hospital data center |
| 5–7 | Integrations: Epic (FHIR), fax gateway, Microsoft 365, ServiceNow, payer portals |
| 6–8 | Migration of 180,000 open and recent referral records (after BAA) |
| 8–10 | Testing, including privacy testing and clinical workflow validation |
| 9–11 | Training in waves by clinic; go-live clinic by clinic over two weeks |
| +30 days | Hypercare |

### The Solution

**Key workflows automated:**

1. **Referral intake** — an AI extraction agent reads faxed and portal referrals, extracts demographics, diagnosis codes and referring provider, and creates a referral in the EHR for coordinator review.
2. **Insurance eligibility check** — the workflow verifies coverage automatically and flags issues before scheduling.
3. **Prior authorization packets** — an agent assembles required clinical documentation per payer rules and highlights missing items before submission.
4. **Patient status notifications** — patients receive SMS and email updates when a referral is received, approved and scheduled.
5. **Referral leakage dashboard** — Command Center shows referrals not scheduled within 5 days.

### Measurable Results

| Metric | Before | After | Change |
|---|---|---|---|
| Referral-to-scheduled time | 9 days | 5 days | **45% faster referral processing** |
| Coordinator manual work | ~22 hours/week | ~4 hours/week | **18 hours saved (net) per week** |
| Initial prior auth denials for missing documents | 18% | 11% | 39% reduction |
| Patient status calls to front desks | ~1,100/month | ~450/month | 59% fewer calls |

### Customer Quote

"Our coordinators now spend their time with patients and physicians instead of fax machines — and our privacy office was involved from day one." — VP Patient Access, HealthPlus Medical Group

### Lessons Learned

- Engaging the privacy office before kickoff avoided rework on AI agent PHI rules.
- Migrating PHI only after the BAA was signed kept the project compliant but added two weeks, which was planned for.
- Clinic-by-clinic go-live let early clinics coach later ones.

## Key Facts

- Healthcare provider, 14 clinics, 6,000 staff, Enterprise with HIPAA BAA.
- 45% faster referral processing (9 days to 5 days).
- Coordinator manual work cut from 22 to about 4 hours per week.
- Complex implementation: 11 weeks due to HIPAA, BAA and EHR integration.
- 59% fewer patient status calls.

## Related Documents

- case_study_finserve.md
- security_overview.md
- enterprise_setup.md
- objection_handling.md

## Retrieval Notes

Retrieve for healthcare, hospital, clinic, HIPAA or patient referral examples. Useful with `security_overview.md` when a prospect asks for proof of HIPAA-compliant deployments. Not the authoritative source for standard implementation timelines.
