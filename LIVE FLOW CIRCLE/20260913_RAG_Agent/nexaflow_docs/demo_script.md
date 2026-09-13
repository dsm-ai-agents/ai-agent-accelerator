# Demo Script

## Metadata

- Category: Sales
- Document Type: Demo Script
- Version: 3.1
- Status: Current
- Last Updated: 2026-07-22
- Authoritative: Yes
- Keywords: demo, demo script, product demo, demo flow, discovery recap, tell-show-tell, Flow Builder demo, Agent Studio demo, Command Center, security demo, next steps, demo environment
- Use When: A seller or solutions engineer is preparing or running a NexaFlow product demo, or asks what the demo flow and talking points should be.

## Summary

This script defines the standard 45-minute NexaFlow solution demo used at Stage 3 of the sales process. It follows a tell-show-tell structure built around the prospect's own process discovered earlier. It includes preparation steps, a timed agenda, talking points for each section, handling questions during the demo and recommended next steps.

## Main Content

### Demo Principles

1. **Never demo without discovery.** Use the process, systems and numbers from the discovery call.
2. **Show their process, not every feature.** One end-to-end workflow beats a feature tour.
3. **Tell-show-tell.** Say what they will see, show it, then connect it to their pain.
4. **Lead with the outcome.** Start with the dashboard showing results, then show how it is built.
5. **Stop and check.** Pause after each section: "How does this compare to how you do it today?"

### Preparation Checklist (48 Hours Before)

- [ ] Discovery notes reviewed; pain metrics written on one slide
- [ ] Demo tenant configured with the prospect's name, logo and relevant connectors (Salesforce, SAP, ServiceNow, etc.)
- [ ] One end-to-end workflow built that mirrors their process
- [ ] Sample documents loaded for the AI extraction agent (invoice, application form or referral)
- [ ] Command Center dashboard populated with realistic data
- [ ] Attendee list confirmed: who is the champion, economic buyer, IT, security?
- [ ] Relevant case study selected (manufacturing → ManufacturingCo, finance → FinServe, healthcare → HealthPlus, retail → RetailMax, services → Acme)

### Standard 45-Minute Agenda

| Time | Section | Owner |
|---|---|---|
| 0–5 min | Introductions and discovery recap | Account Executive |
| 5–10 min | The outcome: Command Center dashboard | Solutions Engineer |
| 10–25 min | End-to-end workflow with AI agent | Solutions Engineer |
| 25–32 min | Integrations and API | Solutions Engineer |
| 32–38 min | Security, governance and audit logs | Solutions Engineer |
| 38–42 min | Implementation approach and customer proof | Account Executive |
| 42–45 min | Questions and next steps | Account Executive |

### Section 1: Discovery Recap (0–5 min)

**Say:** "Last time you told us [process] takes [X days], your team spends [Y hours per week] on manual steps, and [pain, e.g., audit findings]. Today we'll show how that process runs in NexaFlow. Did we get that right? Anything changed?"

Getting agreement on the pain makes the rest of the demo relevant.

### Section 2: The Outcome — Command Center (5–10 min)

**Show:** dashboard with cycle time, volume, SLA status, exceptions queue and hours saved.
**Say:** "This is what your operations leader would see on day 30: every request, where it's stuck, and how much time automation saved."

### Section 3: End-to-End Workflow (10–25 min)

**Show, in order:**
1. **Trigger** — a new request arrives (email with attachment, Salesforce update or form).
2. **AI agent** — Agent Studio extracts fields from the document; show confidence scores and a low-confidence field routed to a human.
3. **Business rules** — branching by value, region or risk.
4. **Approval** — approver approves directly in Microsoft Teams or Slack (highlight: approvers need no paid license).
5. **System update** — record created in the ERP/CRM automatically.
6. **Exception** — show an error routed to the operator queue with context.
7. **Flow Builder** — open the canvas to show how a business analyst built and versions it.

**Tell:** "That process took [X days] with manual re-keying. Here it took minutes, with a human involved only where judgement is needed."

### Section 4: Integrations and API (25–32 min)

**Show:** connector library filtered to their systems; a REST call triggering the flow; webhook configuration.
**Say:** "You mentioned [systems]. All have pre-built connectors. For your on-premise [system], NexaFlow Relay connects without opening inbound firewall ports."

### Section 5: Security and Governance (32–38 min)

**Show:** Admin Console — SSO settings, role-based access with a custom role, workspace separation, audit log entries for a flow publish and an AI agent decision, environment promotion Dev → Staging → Production.
**Say:** "Your security team will ask who changed what and why the AI decided something. Here is that evidence, immutable and exportable to your SIEM."

### Section 6: Implementation and Proof (38–42 min)

**Say:** "A standard enterprise implementation takes 4–6 weeks, from discovery to go-live, followed by 30 days of hypercare. More complex projects with many integrations or detailed security reviews take 8–12 weeks."
Share the matching case study headline (for example "ManufacturingCo reduced manual work by 40% and went live in 6 weeks").

### Handling Questions During the Demo

- Pricing question early → "Happy to cover that; let's make sure it fits first, and I'll walk through options at the end." Do not quote prices from memory — use `pricing_guide_v3.md`.
- Feature you do not have → say so honestly and note it; never fake it.
- Deep technical question → capture it and schedule a technical session.
- Objections → use `objection_handling.md`.

### Recommended Next Steps

| Demo Outcome | Next Step |
|---|---|
| Strong fit, champion engaged | ROI workshop within 1 week + send security package |
| IT/security concerns | Technical deep-dive with solutions architect and security team |
| Economic buyer absent | Executive summary demo (20 minutes) for economic buyer |
| Unclear priority | Revisit discovery; quantify cost of inaction |
| Wants to test | Scoped paid 60-day pilot credited to subscription |

Always confirm a dated next step before the call ends and send a recap email within 24 hours.

## Key Facts

- Standard demo: 45 minutes, tell-show-tell, built on the prospect's own process.
- Start with the Command Center outcome, then show the end-to-end workflow with an AI agent.
- Show security: SSO, RBAC, audit logs, environment promotion.
- State implementation as 4–6 weeks standard, 8–12 weeks complex.
- Always end with a dated next step and a recap within 24 hours.

## Related Documents

- sales_playbook.md
- objection_handling.md
- proposal_template.md
- product_overview.md

## Retrieval Notes

Retrieve when someone asks how to run or prepare a demo, what to show, the demo agenda or what to do after a demo. For product details shown in the demo retrieve Product documents; for objections raised during the demo retrieve `objection_handling.md`.
