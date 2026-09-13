# Sales Playbook

## Metadata

- Category: Sales
- Document Type: Sales Playbook
- Version: 4.0
- Status: Current
- Last Updated: 2026-07-08
- Authoritative: Yes
- Keywords: sales playbook, ICP, ideal customer profile, buyer personas, discovery questions, qualification, MEDDPICC, sales stages, messaging, value proposition, ROI positioning, competitors, next steps
- Use When: A seller needs to know who to target, how to run discovery, how to qualify an opportunity, what the sales stages are, or how to position NexaFlow's value.

## Summary

This playbook defines how NexaFlow sells: the ideal customer profile, buyer personas, core messaging, discovery questions, qualification criteria and sales stages from first meeting to signature. It links to specialised documents for objections (`objection_handling.md`), demos (`demo_script.md`), proposals (`proposal_template.md`) and pricing (`pricing_guide_v3.md`).

## Main Content

### Ideal Customer Profile (ICP)

| Attribute | Ideal Fit |
|---|---|
| Company size | 500–10,000 employees |
| Industries | Manufacturing, financial services, healthcare, retail, professional services |
| Systems | 3+ core business systems (ERP, CRM, HRIS, ITSM) that do not talk to each other |
| Pain signal | Manual handoffs, spreadsheets, email approvals, SLA misses, audit findings |
| Operations maturity | Named process owners; some existing automation (scripts, RPA) that is hard to maintain |
| Budget | $40,000–$500,000 annual software budget for operations tooling |
| Buying trigger | Growth without headcount, ERP migration, new compliance requirements, M&A integration |

**Poor fit:** companies under 50 employees wanting only simple app-to-app automation, or buyers seeking a fully on-premise product (NexaFlow is cloud-only).

### Buyer Personas

| Persona | Cares About | Key Message |
|---|---|---|
| COO / VP Operations (economic buyer) | Cost, capacity, SLAs | "Add capacity without adding headcount." |
| CIO / Head of IT | Security, governance, integration sprawl | "One governed platform instead of scattered scripts." |
| CFO / Finance leader | ROI, payback, controls | "Payback typically in 6–9 months with full audit trails." |
| Process owner (champion) | Daily pain, team workload | "Your team stops copy-pasting and chasing approvals." |
| Security / Compliance | Risk, data privacy, AI governance | "SOC 2 Type II, ISO 27001, HIPAA BAA, logged AI decisions." |

### Core Messaging

**Positioning statement:** NexaFlow is the AI operations platform that lets mid-sized and enterprise companies automate cross-system business processes with governed AI agents — live in weeks, not quarters.

**Three value pillars:**
1. **Speed to value** — standard enterprise implementation in 4–6 weeks.
2. **AI you can govern** — every agent decision logged, with human approval gates.
3. **Enterprise-ready** — security certifications, RBAC, audit logs, 200+ integrations, 99.9% SLA.

**Proof points:** 40% reduction in manual work (ManufacturingCo), 35% faster processing (FinServe), 20 hours saved per week (Acme), 30% fewer errors (RetailMax).

### Discovery Questions

**Current state**
- Walk me through the process from start to finish. Where does it start and who touches it?
- Which systems are involved, and where is data re-keyed?
- How many requests or transactions go through this process each month?

**Pain and impact**
- How long does it take today, and how long should it take?
- How many hours per week does your team spend on manual steps?
- What happens when something goes wrong — errors, SLA misses, audit findings?

**Priorities and urgency**
- Why solve this now? What happens if nothing changes in 12 months?
- Is there a deadline — peak season, audit, system migration?

**Decision process**
- Who else will be involved in evaluating and approving this?
- What does your security review process look like, and how long does it usually take?
- How have you bought similar software before?

**Technical fit**
- Do you need SSO, SCIM, audit log retention or data residency?
- Are any systems on-premise?

### Qualification Criteria (MEDDPICC)

| Letter | Question to Answer | Minimum to Advance Past Stage 2 |
|---|---|---|
| Metrics | What measurable outcome will they achieve? | At least one quantified pain (hours, days, error rate) |
| Economic Buyer | Who signs? | Identified by name |
| Decision Criteria | How will they choose? | Documented |
| Decision Process | Steps to purchase | Mapped, including security review |
| Paper Process | Legal and procurement steps | Understood before Stage 4 |
| Identify Pain | Why now? | Clear business impact |
| Champion | Who sells internally for us? | Named champion with access to EB |
| Competition | Who else? | Known alternatives, including "do nothing" |

### Sales Stages

| Stage | Name | Exit Criteria |
|---|---|---|
| 1 | Discovery | Pain and process documented |
| 2 | Qualification | MEDDPICC minimums met |
| 3 | Solution Demo | Tailored demo delivered (`demo_script.md`); champion confirms fit |
| 4 | Business Case & Security | ROI agreed; security review started |
| 5 | Proposal | Proposal sent (`proposal_template.md`) with pricing from `pricing_guide_v3.md` |
| 6 | Negotiation | Terms agreed within `discount_policy.md` |
| 7 | Closed Won | Signed; handoff to implementation within 2 business days |

Typical Enterprise sales cycle: 60–120 days. Professional: 21–45 days.

### ROI Positioning

Build ROI with the customer, using their numbers:
- Hours saved × loaded hourly cost (default assumption $45/hour if unknown).
- Error reduction × cost per error (rework, write-offs, penalties).
- Faster cycle time × revenue or customer impact.

Typical NexaFlow customers reach payback in **6–9 months**.

### Competitive Landscape

| Alternative | How to Position |
|---|---|
| Lightweight app-to-app tools | Fine for simple tasks; lack governance, RBAC, audit logs and enterprise scale |
| Legacy RPA suites | Brittle screen-scraping and high maintenance; NexaFlow uses APIs and AI agents |
| In-house scripts | Hidden maintenance cost and key-person risk |
| Do nothing | Quantify cost of manual work per year |

### Next-Step Recommendations After Each Meeting

- After discovery → book tailored demo with process owner and IT.
- After demo → run ROI workshop and send security package.
- After ROI → introduce implementation lead to discuss timeline.
- Always end with a dated next step in the calendar.

## Key Facts

- ICP: 500–10,000 employees with 3+ disconnected core systems.
- Qualification uses MEDDPICC; champion and economic buyer must be named by Stage 2.
- Three value pillars: speed to value, governed AI, enterprise-ready.
- Typical payback: 6–9 months; Enterprise sales cycle 60–120 days.
- Start security review in Stage 4 to protect implementation timelines.

## Related Documents

- objection_handling.md
- demo_script.md
- proposal_template.md
- customer_faq.md

## Retrieval Notes

Retrieve for ICP, target customers, personas, discovery questions, qualification, sales stages, messaging, ROI positioning or competitive positioning. For responses to specific objections retrieve `objection_handling.md`; for demo flow retrieve `demo_script.md`.
