# Objection Handling Guide

## Metadata

- Category: Sales
- Document Type: Sales Enablement Guide
- Version: 3.2
- Status: Current
- Last Updated: 2026-07-12
- Authoritative: Yes
- Keywords: objections, objection handling, too expensive, price objection, budget, security concerns, AI risk, competitor, build in-house, timing, implementation risk, change management, ROI, responses
- Use When: A seller needs to respond to a prospect objection such as price, security, AI trust, competitors, timing or implementation risk.

## Summary

This guide gives recommended responses to the most common objections NexaFlow sellers hear. Each objection includes what is usually behind it, a response framework, proof points and what not to say. The general method is: acknowledge, clarify, respond with evidence, and confirm. Discounts mentioned in any response must follow `discount_policy.md`.

## Main Content

### The ACRC Method

1. **Acknowledge** — show you heard the concern without arguing.
2. **Clarify** — ask a question to find the real issue.
3. **Respond** — address the real issue with evidence.
4. **Confirm** — check the concern is resolved and agree the next step.

---

### Objection 1: "It's too expensive."

**What is usually behind it:** no agreed ROI, comparing to a cheaper point tool, budget already allocated elsewhere, or a negotiation tactic.

**Clarifying questions:**
- "Too expensive compared to what — another vendor, your budget, or the value you expect?"
- "If price were not a factor, is NexaFlow the right solution?"

**Response framework:**
1. **Return to the cost of the problem.** "You told us your team spends about 60 hours a week on manual steps. At a $45 loaded hourly cost that is over $140,000 a year — before counting errors and delays."
2. **Show payback.** Typical NexaFlow payback is 6–9 months. Build the ROI with their numbers.
3. **Use a proof point.** "ManufacturingCo cut manual work by 40%; Acme saves 20 hours a week."
4. **Right-size, don't discount first.** Offer a phased scope (fewer users or workflows in year 1, ramp pricing), or the Professional plan if Enterprise-only features are not needed.
5. **Trade, don't give.** If a discount is required, exchange it for a multi-year term (5% for 2 years, 10% for 3 years), a case study, or signature by a date — within `discount_policy.md` limits.

**What not to say:** "I can get you 30% off today." Leading with discount devalues the product and needs VP approval anyway.

---

### Objection 2: "We have security concerns."

**Clarifying question:** "Which area worries your security team most — data storage, access control, AI use of data, or compliance?"

**Response:**
- SOC 2 Type II and ISO 27001 certified; GDPR compliant; HIPAA BAA available on Enterprise.
- AES-256 encryption at rest, TLS 1.2+ in transit, optional customer-managed keys.
- SSO, SCIM, custom RBAC and immutable audit logs with SIEM streaming.
- Offer the Trust Center package (SOC 2 report, CAIQ) under NDA and a call with NexaFlow's security team.
- Proof: FinServe Capital (regulated lender) and HealthPlus Medical Group (HIPAA) both passed detailed security reviews.

**Next step:** start the security review now — it protects the implementation timeline. See `security_overview.md`.

---

### Objection 3: "We don't trust AI to make decisions."

**Response:**
- AI agents in NexaFlow work inside defined workflows with only the tools they are granted.
- Confidence thresholds route uncertain cases to humans; approvals can be required for any action.
- Every agent input, output and decision is logged and auditable.
- Customer data is never used to train models.
- Start with "AI assists, human approves" and increase automation as accuracy is proven.

---

### Objection 4: "We can build this ourselves."

**Clarifying question:** "Who would maintain the integrations and AI components two years from now?"

**Response:** Internal builds carry hidden costs: integration maintenance when APIs change, security reviews, audit logging, monitoring and key-person risk. NexaFlow provides 200+ maintained connectors, governance and 99.9% uptime. Offer to compare the three-year total cost of ownership.

---

### Objection 5: "We already use [lightweight automation tool / RPA]."

**Response:** Lightweight tools work for simple app-to-app tasks but lack enterprise RBAC, audit logs, environments and scale. RPA bots break when screens change. NexaFlow can coexist: keep simple automations, move critical cross-system processes to a governed platform.

---

### Objection 6: "Implementation will take too long / disrupt our team."

**Response:**
- Standard enterprise implementation is 4–6 weeks; complex deployments are 8–12 weeks.
- RetailMax went live in 4 weeks, before holiday peak.
- The customer's project lead needs about 50% of their time; most users need only short training (approvers watch a 10-minute video).
- 30 days of hypercare follows go-live.

---

### Objection 7: "Now is not the right time."

**Clarifying question:** "What would need to be true for this to become a priority?"

**Response:** Quantify the cost of waiting (monthly cost of manual work). Offer a paid 60-day pilot credited to the subscription, or align the start date with their budget cycle while completing the security review now.

---

### Objection 8: "Your competitor quoted us less."

**Response:** Compare scope, not just price: included workflow runs, AI agents, SSO/SCIM, audit log retention, SLA and implementation. Ask to see what is included. A competitive displacement discount of up to 15% for year 1 exists but requires VP Sales approval.

## Key Facts

- Use ACRC: Acknowledge, Clarify, Respond, Confirm.
- For "too expensive": return to cost of the problem, show 6–9 month payback, right-size scope, and trade any discount for commitment.
- Multi-year discounts: 5% (2-year), 10% (3-year); larger discounts follow the approval matrix.
- Security response relies on SOC 2 Type II, ISO 27001, HIPAA BAA, RBAC and audit logs.
- Standard implementation 4–6 weeks counters "takes too long".

## Related Documents

- sales_playbook.md
- discount_policy.md
- security_overview.md
- customer_faq.md

## Retrieval Notes

Retrieve whenever a seller asks "how do I respond if a prospect says…" — price, too expensive, budget, security, AI trust, build vs buy, competitors, timing or implementation risk. Pair with `discount_policy.md` for discount limits and `security_overview.md` for detailed security facts.
