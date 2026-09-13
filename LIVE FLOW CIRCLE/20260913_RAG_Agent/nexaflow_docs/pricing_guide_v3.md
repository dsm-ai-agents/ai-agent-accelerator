# Pricing Guide v3

## Metadata

- Category: Pricing
- Document Type: Official Price List
- Version: 3.0
- Status: Current — supersedes Pricing Guide v2
- Last Updated: 2026-07-01
- Authoritative: Yes — this is the single source of truth for NexaFlow list prices
- Keywords: pricing, price list, Starter plan, Professional plan, Enterprise plan, per user, annual billing, monthly billing, annual discount, usage limits, workflow runs, overage, implementation fee, add-ons
- Use When: Someone asks what a plan costs, what is included in the price, annual vs monthly billing, usage limits, overage or implementation fees.

## Summary

Pricing Guide v3 is the current and authoritative NexaFlow price list, effective 1 July 2026. It defines three plans — Starter, Professional and Enterprise — priced per user per month, with a discount for annual billing. It also lists usage allowances, overage rates, implementation fees and add-ons. Any price that differs from this document (for example, figures from Pricing Guide v2) is outdated.

## Main Content

### Plan Prices (USD)

| Plan | Annual Billing (per user / month) | Monthly Billing (per user / month) | User Range |
|---|---|---|---|
| Starter | $29 | $35 | 5–25 users |
| Professional | $59 | $71 | 10–250 users |
| Enterprise | From $95 (custom quote) | Not available | 100+ users |

- **Annual billing saves roughly 17%** compared with monthly billing (equivalent to two months free).
- Enterprise is sold on annual or multi-year contracts only. Minimum Enterprise contract: 100 users, which is **$114,000 per year** at list price.
- Multi-year commitments receive additional discounts: **5% for a 2-year term and 10% for a 3-year term**, applied on top of annual pricing. Rules are in `discount_policy.md`.

### Usage Allowances

| Allowance | Starter | Professional | Enterprise |
|---|---|---|---|
| Workflow runs / month | 5,000 | 50,000 | 500,000 |
| Active AI agents | 2 | 15 | Unlimited |
| AI agent actions / month | 1,000 | 20,000 | 250,000 |
| Active workflows | 20 | 200 | Unlimited |
| Storage | 10 GB | 100 GB | 1 TB |

Unused runs do not roll over to the next month.

### Overage Rates

| Item | Starter | Professional | Enterprise |
|---|---|---|---|
| Additional 1,000 workflow runs | $10 | $6 | $4 |
| Additional 1,000 AI agent actions | $20 | $12 | $8 |
| Additional 100 GB storage | $25 | $20 | $15 |

Customers receive an alert at 80% and 100% of their allowance. Starter workflows pause at 120% of the allowance until the customer upgrades or buys a run pack; Professional and Enterprise continue running and are billed overage monthly in arrears.

### Implementation and Services Fees

| Package | Price | Applies To | Scope |
|---|---|---|---|
| Self-serve onboarding | Free | Starter | Online academy and templates |
| Quick Start | $5,000 (optional) | Professional | 2-week guided setup, up to 3 integrations |
| Enterprise Standard Implementation | $15,000 | Enterprise | 4–6 week guided implementation, up to 5 integrations, up to 1 million migrated records |
| Enterprise Complex Implementation | $35,000 | Enterprise | 8–12 week implementation for more than 5 integrations, large data migrations, single-tenant or extended security review |
| Additional solution architect time | $250 / hour | Professional, Enterprise | Custom flows or advanced agents |

Implementation fees are one-time, invoiced at contract signature, and are not discountable beyond the limits in `discount_policy.md`. Timeline details are in the Implementation documents (`implementation_timeline.md`).

### Add-Ons

| Add-On | Price |
|---|---|
| Premium connector pack (SAP, Oracle Fusion, Workday) — Professional only | $1,000 / month |
| Single-tenant deployment — Enterprise | +20% of annual subscription |
| Extended audit log retention (up to 7 years) — Enterprise | $6,000 / year |
| Additional sandbox environment | $500 / month |
| Premium training (custom on-site workshop) | $4,000 per day |

### Worked Examples

**Professional, 60 users, annual billing:** 60 × $59 × 12 = **$42,480 per year**. Optional Quick Start: $5,000.

**Enterprise, 250 users, annual billing at list:** 250 × $95 × 12 = **$285,000 per year**, plus $15,000 standard implementation. A 3-year term reduces the subscription by 10% to $256,500 per year.

### Billing Terms

- Payment terms: annual in advance; Net 30.
- Prices exclude applicable taxes.
- Users can be added at any time and are prorated to the renewal date.
- Renewal price increases are capped at 7% per year for Enterprise contracts.

## Key Facts

- Starter $29, Professional $59, Enterprise from $95 per user/month on annual billing.
- Monthly billing: Starter $35, Professional $71; Enterprise is annual-only.
- Annual billing saves ~17%; multi-year adds 5% (2-year) or 10% (3-year).
- Enterprise implementation: $15,000 (4–6 weeks) or $35,000 complex (8–12 weeks).
- This document supersedes Pricing Guide v2 in all cases.

## Related Documents

- enterprise_pricing.md
- discount_policy.md
- licensing_model.md
- pricing_faq.md

## Retrieval Notes

Always retrieve this file for any question about prices, plan costs, annual vs monthly billing, usage allowances, overage or implementation fees. If another document shows a different price, this document wins. Pair with `enterprise_pricing.md` for Enterprise negotiation and with `discount_policy.md` for discount approval rules.
