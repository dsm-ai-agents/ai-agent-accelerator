# Enterprise Capabilities

## Metadata

- Category: Product
- Document Type: Capability Brief
- Version: 2.3
- Status: Current
- Last Updated: 2026-07-10
- Authoritative: Yes
- Keywords: enterprise, scalability, high availability, uptime SLA, single-tenant, data residency, governance, multi-workspace, center of excellence, sandbox, performance, workflow runs, dedicated support
- Use When: Someone asks whether NexaFlow can handle large-scale or complex enterprise requirements such as scale, availability, governance, data residency or dedicated environments.

## Summary

The Enterprise plan adds the scale, governance and deployment options large organisations need. This document describes performance and scalability limits, availability commitments, deployment models, multi-workspace governance, advanced AI controls and the enterprise support model. It describes what the product can do; the steps to configure these capabilities during onboarding are in `enterprise_setup.md`.

## Main Content

### Scalability and Performance

NexaFlow's execution engine scales horizontally, so throughput increases automatically as workload grows.

| Metric | Enterprise Capability |
|---|---|
| Included workflow runs | 500,000 per month (more available, see pricing) |
| Proven peak volume | 10 million runs per month in a single tenant |
| Concurrent runs | Up to 2,000 simultaneous runs per tenant (raisable) |
| Median step latency | Under 300 ms for native steps |
| API rate limit | 3,000 requests/minute, raisable |
| Users | Tested with 25,000 named users in one tenant |

Large batch jobs (for example, nightly processing of 200,000 invoices) are queued and processed in parallel with priority controls so interactive workflows are not slowed.

### Availability and Resilience

- **99.9% monthly uptime SLA** with service credits.
- Multi-availability-zone architecture with automated failover.
- RPO 1 hour, RTO 4 hours; optional cross-region disaster recovery.
- Planned maintenance windows are announced 7 days in advance and scheduled outside customer business hours.
- Public status page and incident notifications by email and webhook.

### Deployment Models

1. **Multi-tenant cloud (default)** — logically isolated tenant, fastest to provision.
2. **Single-tenant cloud (optional)** — dedicated compute and database for customers with strict isolation requirements. Provisioning adds roughly 1 week to environment setup.
3. **Data residency** — choose US, EU or APAC. All customer data, backups and logs remain in the selected region.

NexaFlow does not offer a fully self-hosted on-premise version. On-premise systems connect through the NexaFlow Relay agent.

### Governance for Large Organisations

- **Multiple workspaces** — separate spaces for Finance, HR, IT and regions, each with its own builders, connectors and approval rules.
- **Environment promotion** — Development → Staging → Production, with required approvals before a flow is published to Production.
- **Center of Excellence (CoE) controls** — central admins can publish approved templates, restrict which connectors each workspace may use and review all production changes.
- **Custom roles and SCIM** — fine-grained RBAC, automatically provisioned from the identity provider.
- **Change history** — every flow version, publisher and approver is recorded in the audit log.

### Advanced AI Controls

- Approved model lists and bring-your-own LLM keys.
- Policy templates for agent confidence thresholds (for example, route to a human below 85% confidence).
- PII redaction before model calls.
- Agent evaluation reports showing accuracy, overrides and drift over time.

### Enterprise Support Model

- Named Customer Success Manager (CSM).
- 24/7 support with 1-hour P1 response target.
- Dedicated implementation team: engagement manager, solution architect and integration engineer.
- 30 days of hypercare after go-live, then quarterly business reviews.
- Role-based training program for admins, builders and operators.

### Typical Enterprise Buyer Requirements Mapped

| Requirement | NexaFlow Answer |
|---|---|
| "We need SSO and automatic deprovisioning" | SAML/OIDC SSO + SCIM |
| "Our data must stay in the EU" | EU data residency (Frankfurt) |
| "We need 7-year audit retention" | Extendable audit log retention + SIEM streaming |
| "We must connect to on-prem SAP ECC" | NexaFlow Relay |
| "We process millions of transactions" | Proven 10M runs/month per tenant |
| "Business units must be separated" | Multiple workspaces with scoped RBAC |

## Key Facts

- 99.9% uptime SLA; RPO 1 hour, RTO 4 hours.
- Proven at 10 million runs per month in one tenant.
- Single-tenant option and US/EU/APAC data residency.
- No self-hosted on-premise version; on-prem systems connect via Relay.
- Enterprise includes named CSM, dedicated implementation team and 30-day hypercare.

## Related Documents

- product_overview.md
- security_overview.md
- feature_matrix.md
- enterprise_setup.md

## Retrieval Notes

Retrieve for questions about scale, uptime, SLA, single-tenant deployment, data residency, governance across business units, or "can NexaFlow handle enterprise volume". For how these capabilities are configured during onboarding, retrieve `enterprise_setup.md`.
