# Licensing Model

## Metadata

- Category: Pricing
- Document Type: Licensing Policy
- Version: 3.0
- Status: Current
- Last Updated: 2026-07-01
- Authoritative: Yes
- Keywords: licensing, named user, user types, builder, operator, viewer license, approver, service accounts, API users, true-up, license transfer, contract term, upgrades, downgrades
- Use When: Someone asks what counts as a user, how licenses are counted, whether viewers or approvers need licenses, or how to add, remove, upgrade or downgrade licenses.

## Summary

NexaFlow is licensed per named user per month, with usage allowances for workflow runs and AI agent actions. Not every person who touches a workflow needs a paid license: lightweight approvers and viewers are handled differently from builders and operators. This document explains license types, how users are counted, true-ups, upgrades and downgrades. Prices themselves are defined in `pricing_guide_v3.md`.

## Main Content

### Licensing Principles

1. **Named users** — a license is assigned to one identified person and cannot be shared.
2. **Usage allowances** — each plan includes workflow runs and AI agent actions; usage above allowance is billed as overage.
3. **Per-tenant** — licenses belong to one NexaFlow tenant (organisation).

### License Types

| License Type | Who | Counts as Paid User? | Plans |
|---|---|---|---|
| Full User | Builders, Admins, Operators working exception queues | Yes | All |
| Viewer | Read-only dashboard access | Free up to 3× the number of Full Users | Professional, Enterprise |
| Approver | People who only approve/reject tasks via email, Slack or Teams | Free, unlimited | All |
| External Participant | Suppliers, customers or candidates completing a form in a flow | Free, unlimited | Professional, Enterprise |
| Service Account / API User | System integrations using the Nexa API | Free (5 on Professional, 25 on Enterprise) | Professional, Enterprise |

Example: a finance department with 20 people building and operating flows, 60 managers who view dashboards and 300 employees who approve expenses in Teams needs **20 Full User licenses** only (60 viewers is within the free 3× allowance of 60).

### Minimum and Maximum Users

| Plan | Minimum | Maximum |
|---|---|---|
| Starter | 5 | 25 |
| Professional | 10 | 250 |
| Enterprise | 100 | No maximum |

A Professional customer that grows beyond 250 Full Users must move to Enterprise at renewal, or mid-term if they exceed 275 users.

### Adding and Removing Users

- **Adding users:** allowed any time. New licenses are prorated to the contract renewal date.
- **Reassigning licenses:** a license can be moved from a departing employee to a new one at no cost. SCIM (Enterprise) does this automatically.
- **Removing users:** the license count cannot drop below the contracted number during the term. Reductions take effect at renewal.

### True-Up

Enterprise contracts include a **quarterly true-up**. If the number of active Full Users exceeds the contracted count, the extra users are invoiced at the contracted per-user price, prorated. Professional customers are billed automatically when users are added.

### Upgrades and Downgrades

| Change | When Allowed | Pricing Effect |
|---|---|---|
| Starter → Professional | Any time | Prorated credit for unused Starter term |
| Professional → Enterprise | Any time | Prorated credit; Enterprise implementation fee applies |
| Enterprise → Professional | Renewal only | Enterprise-only features are removed |
| Professional → Starter | Renewal only | Must fit within 25 users and Starter limits |

### Contract Terms

- Starter and Professional: monthly or annual.
- Enterprise: 1, 2 or 3 years; annual billing in advance.
- Auto-renewal applies unless either party gives 60 days' written notice.

### Sandbox and Non-Production Use

Development and Staging environments do not consume additional licenses. Workflow runs in non-production environments do not count toward allowances, up to 10% of the production allowance.

### Partner and Agency Use

Consulting partners building flows on behalf of a customer use the customer's licenses or a free Partner Builder seat (maximum 3 per tenant, Enterprise only).

### Common Licensing Questions

- **Do approvers need a license?** No — approve/reject via email, Slack or Teams is free.
- **Do AI agents need a license?** No. Agents are limited by the plan's active-agent count and agent-action allowance, not user licenses.
- **Can we share one login among a team?** No. Shared logins breach the license terms and break audit trails.

## Key Facts

- Licensed per named Full User per month, plus usage allowances.
- Approvers and external participants are free and unlimited.
- Viewers are free up to 3× the Full User count (Professional and Enterprise).
- Enterprise has a 100-user minimum and quarterly true-ups.
- Downgrades happen only at renewal.

## Related Documents

- pricing_guide_v3.md
- enterprise_pricing.md
- pricing_faq.md
- feature_matrix.md

## Retrieval Notes

Retrieve when the question is about who needs a license, license counts, viewers/approvers, service accounts, true-ups, adding or removing users, or upgrade/downgrade rules. For actual prices retrieve `pricing_guide_v3.md`.
