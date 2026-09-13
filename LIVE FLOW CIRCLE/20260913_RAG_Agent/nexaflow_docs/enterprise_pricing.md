# Enterprise Pricing and Negotiation Guidelines

## Metadata

- Category: Pricing
- Document Type: Internal Sales Guidance
- Version: 3.0
- Status: Current
- Last Updated: 2026-07-01
- Authoritative: Yes (for Enterprise deal structure; list prices come from pricing_guide_v3.md)
- Keywords: enterprise pricing, custom quote, negotiation, deal desk, volume tiers, multi-year, ACV, minimum contract, implementation fee, price floor, concessions, procurement
- Use When: A seller needs to structure, quote or negotiate an Enterprise deal, or someone asks how Enterprise pricing scales with volume.

## Summary

Enterprise plans are custom-quoted starting from the $95 per user per month list price in `pricing_guide_v3.md`. This document explains how Enterprise quotes are built, the volume tiers, the minimum contract, what can and cannot be negotiated, and how to trade concessions for commitments. It is internal guidance for sales and deal desk teams and must not be shared with customers.

## Main Content

### How an Enterprise Quote Is Built

An Enterprise quote has four components:

1. **Platform subscription** — users × per-user price × 12 months.
2. **Usage allowance** — 500,000 workflow runs and 250,000 AI agent actions per month are included; larger committed volumes are priced in blocks.
3. **Add-ons** — single-tenant deployment, extended audit retention, extra sandboxes.
4. **One-time implementation** — $15,000 Standard (4–6 weeks) or $35,000 Complex (8–12 weeks).

### Volume Tiers (Per User / Month, Annual Billing)

| Committed Users | Target Price | Floor Without VP Approval |
|---|---|---|
| 100–249 | $95 | $86 |
| 250–499 | $89 | $80 |
| 500–999 | $82 | $74 |
| 1,000–2,499 | $75 | $68 |
| 2,500+ | Deal desk review | Deal desk review |

The "target price" is what sellers should quote first. The "floor" is the lowest price a Sales Manager can approve under `discount_policy.md`; anything below requires VP Sales approval.

### Minimum Contract

- Minimum 100 users.
- Minimum annual contract value (ACV): **$114,000** (100 users × $95 × 12).
- Customers below 100 users should be offered Professional unless they require an Enterprise-only feature (SCIM, custom roles, HIPAA BAA, data residency outside US/EU, single-tenant). In those cases the 100-user minimum still applies.

### Committed Usage Blocks

| Additional Monthly Runs (committed) | Price per 1,000 Runs |
|---|---|
| Up to 500,000 extra | $4.00 (standard overage) |
| 500,001–2,000,000 extra | $3.20 |
| Above 2,000,000 extra | $2.50 |

Committing volume in the contract is cheaper for the customer than paying overage and gives NexaFlow predictable revenue.

### What Can Be Negotiated

| Lever | Guidance |
|---|---|
| Per-user price | Within tier floor; below floor needs VP approval |
| Multi-year discount | 5% (2-year), 10% (3-year) — standard, no approval needed |
| Payment terms | Annual in advance is standard; quarterly billing allowed for ACV above $250,000 with a 3% uplift |
| Implementation fee | Up to 25% off the Standard package with Sales Manager approval; Complex package is not discountable |
| Ramp pricing | Allowed: e.g., 150 users in year 1 rising to 400 in year 2, priced at year-2 tier |
| Renewal cap | Default 7%; may be lowered to 5% for 3-year terms |
| Pilot | Paid 60-day pilot credited against year-1 subscription |

### What Cannot Be Negotiated

- Free implementation for Enterprise.
- Uptime SLA above 99.9%.
- Unlimited workflow runs without a committed volume.
- Price protection longer than 3 years.
- Monthly billing on Enterprise.

### Give-Get Principle

Never give a concession without getting something back. Examples:

- Give 5% extra discount → Get a 3-year term, a published case study, or signature by quarter end.
- Give reduced implementation fee → Get an executive sponsor and a committed go-live date.
- Give ramp pricing → Get a higher year-2 user commitment.

### Historical Note

Enterprise list price was $85 per user/month under Pricing Guide v2 (2025). That figure is **no longer valid** for new quotes. Existing customers on v2 contracts keep their price until renewal, then move to v3 tiers with the renewal cap applied. See `pricing_faq.md`.

### Deal Desk Checklist

1. Confirm user count, workflow volume and Enterprise-only requirements.
2. Choose Standard or Complex implementation based on integrations, migration volume and security review (see `implementation_timeline.md`).
3. Apply volume tier and multi-year discount.
4. Check any extra discount against `discount_policy.md` approval matrix.
5. Attach ROI summary and relevant case study before sending the proposal.

## Key Facts

- Enterprise starts at $95/user/month (annual), minimum 100 users, $114,000 minimum ACV.
- Volume tiers go down to $75 target for 1,000–2,499 users.
- Multi-year discounts: 5% for 2 years, 10% for 3 years.
- Complex implementation ($35,000) is not discountable.
- The old $85 Enterprise price from Pricing Guide v2 is outdated.

## Related Documents

- pricing_guide_v3.md
- discount_policy.md
- licensing_model.md
- proposal_template.md

## Retrieval Notes

Retrieve for Enterprise quote structure, volume pricing, minimum contract size, what is negotiable, ramp deals and deal desk steps. For base list prices always also retrieve `pricing_guide_v3.md`; for approval authority retrieve `discount_policy.md`.
