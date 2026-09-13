# Case Study: Acme Consulting Group

## Metadata

- Category: Case Studies
- Document Type: Customer Case Study
- Version: 1.2
- Status: Approved for external use
- Last Updated: 2026-03-09
- Authoritative: Yes (for Acme results)
- Keywords: case study, professional services, consulting, client onboarding, project setup, resource staffing, timesheets, invoicing, 20 hours saved per week, 25% faster onboarding, Salesforce, NetSuite, Microsoft Teams
- Use When: Someone needs a professional services or consulting customer example, proof of faster client onboarding, or evidence of hours saved.

## Summary

Acme Consulting Group, a 1,200-person professional services firm, used NexaFlow to automate client onboarding, project setup and billing handoffs across Salesforce, NetSuite and Microsoft Teams. The implementation took 5 weeks on the standard Enterprise track. Acme now onboards new clients 25% faster and its project operations team saves 20 hours per week.

## Main Content

### Customer Profile

| Attribute | Detail |
|---|---|
| Industry | Professional services (management and technology consulting) |
| Headquarters | Chicago, USA, with offices in London and Singapore |
| Employees | 1,200 |
| Plan | Enterprise, 150 Full Users |
| Systems | Salesforce, Oracle NetSuite, Microsoft Teams, SharePoint, DocuSign |
| Go-live | November 2025 |

### The Problem

Every time Acme won a new engagement, a chain of manual tasks began. Sales operations re-keyed deal details from Salesforce into NetSuite, the project management office created SharePoint folders and Teams channels by hand, and resource managers chased partners by email to confirm staffing. Conflict-of-interest checks sat in shared inboxes.

The results:
- New client onboarding took an average of **8 business days** from signed statement of work to project kickoff.
- The 6-person project operations team spent roughly **20 hours per week** on copy-paste work and chasing approvals.
- Around 1 in 12 projects started with incorrect billing rates, causing invoice disputes.
- Partners had no visibility into where onboarding was stuck.

### The Implementation

Acme followed NexaFlow's standard nine-phase enterprise onboarding process and went live in **5 weeks**.

| Week | Activity |
|---|---|
| 1 | Discovery workshops with sales ops, PMO, finance and risk |
| 1–2 | Solution design for three priority workflows |
| 2 | Environment setup with Microsoft Entra ID SSO and SCIM |
| 2–3 | Salesforce, NetSuite, Teams, SharePoint and DocuSign connectors configured |
| 3–4 | Migration of 1,400 active client records and rate cards |
| 4 | UAT with 12 business users |
| 5 | Role-based training and go-live |

The project stayed on the standard track because all five systems had pre-built connectors and the data migration was small.

### The Solution

**Key workflows automated:**

1. **Client onboarding** — when a Salesforce opportunity is marked Closed Won, NexaFlow creates the customer and project in NetSuite, generates the SharePoint folder structure and Teams channel, and sends the welcome pack.
2. **Conflict check** — an AI agent in Agent Studio summarises the client, related entities and prior engagements, and routes the result to the risk team for approval in Teams.
3. **Resource staffing requests** — staffing requests are sent to resource managers with skills and availability; approvals happen in Teams.
4. **Rate card validation** — billing rates are checked against the signed SOW before the project is opened for time entry.
5. **Kickoff readiness dashboard** — partners see each new client's onboarding status in Command Center.

### Measurable Results

| Metric | Before | After | Change |
|---|---|---|---|
| Client onboarding time | 8 business days | 6 business days | **25% faster onboarding** |
| Manual work in project operations | ~20 hours/week | Near zero | **20 hours saved per week** |
| Projects starting with billing rate errors | 1 in 12 | 1 in 50 | **~80% fewer rate errors** |
| Conflict-check turnaround | 2 days | 4 hours | 75% faster |

Payback on the subscription and implementation fee was achieved in about **7 months**.

### Customer Quote

"We used to measure onboarding in emails. Now partners open a dashboard and see exactly where every new client stands." — Director of Project Operations, Acme Consulting Group

### Lessons Learned

- Starting with three workflows kept the project on the 4–6 week track.
- Letting the AI agent prepare conflict-check summaries, while keeping human approval, built trust with the risk team.
- Retiring the old onboarding spreadsheet in week 2 after go-live drove adoption.

## Key Facts

- Professional services firm, 1,200 employees, Enterprise plan.
- 25% faster client onboarding (8 days to 6 days).
- 20 hours saved per week for the project operations team.
- Implementation took 5 weeks on the standard track.
- Payback in about 7 months.

## Related Documents

- case_study_finserve.md
- case_study_retailmax.md
- sales_playbook.md
- implementation_timeline.md

## Retrieval Notes

Retrieve for professional services or consulting references, "faster client onboarding" proof points, "hours saved per week" examples or Salesforce + NetSuite automation stories. Not an authoritative source for general implementation timelines — use `implementation_timeline.md` for that.
