# Integration Guide

## Metadata

- Category: Product
- Document Type: Technical Guide
- Version: 2.6
- Status: Current
- Last Updated: 2026-06-18
- Authoritative: Yes
- Keywords: integrations, connectors, NexaFlow Connect, REST API, GraphQL, webhooks, Salesforce, SAP, Workday, ServiceNow, NexaFlow Relay, on-premise, authentication, OAuth, API keys, rate limits
- Use When: Someone asks which systems NexaFlow integrates with, how the API works, how on-premise systems connect, or how integrations are authenticated.

## Summary

NexaFlow connects to business systems through NexaFlow Connect (200+ pre-built connectors), a generic REST connector, the Nexa API, webhooks and the NexaFlow Relay on-premise agent. This guide lists supported systems, explains each integration method, and covers authentication, limits and best practices. Integration configuration during onboarding is scheduled in `implementation_timeline.md`.

## Main Content

### Integration Methods

| Method | Best For | Plans |
|---|---|---|
| Pre-built connectors | Popular SaaS and ERP systems | All (25 on Starter) |
| Generic REST connector | Any system with a REST API | Professional, Enterprise |
| Nexa API (REST / GraphQL) | Developers triggering flows or reading data | All (read-only on Starter) |
| Webhooks (inbound and outbound) | Real-time event notifications | All (limits vary) |
| NexaFlow Relay | On-premise databases, file shares, legacy apps | Enterprise |
| SFTP / file drop | Batch CSV or EDI files | Professional, Enterprise |

### Supported Systems (Selected)

**CRM:** Salesforce Sales Cloud and Service Cloud, HubSpot, Microsoft Dynamics 365 CRM, Zoho CRM
**ERP & Finance:** SAP S/4HANA, SAP ECC (via Relay), Oracle NetSuite, Oracle Fusion, Microsoft Dynamics 365 Finance, QuickBooks Online, Xero, Coupa
**HR:** Workday, SAP SuccessFactors, BambooHR, ADP Workforce Now
**ITSM & Service:** ServiceNow, Jira Service Management, Zendesk, Freshdesk
**Collaboration:** Slack, Microsoft Teams, Google Workspace, Microsoft 365 (Outlook, SharePoint, OneDrive)
**Data:** Snowflake, BigQuery, PostgreSQL, SQL Server, MySQL, Oracle Database
**Identity:** Okta, Microsoft Entra ID (Azure AD), Ping Identity (used for SSO and SCIM)
**Documents:** DocuSign, Adobe Acrobat Sign, Box, Dropbox

SAP, Oracle Fusion and Workday connectors are classified as premium connectors: an add-on on Professional and included on Enterprise.

### The Nexa API

- **REST API** — resources for flows, runs, agents, users, roles and audit events. JSON over HTTPS.
- **GraphQL API** — query run history and dashboard metrics efficiently (Professional and Enterprise).
- **Authentication** — OAuth 2.0 client credentials for server-to-server use; personal API keys for testing. Keys are scoped to roles and can be rotated or revoked from the Admin Console.
- **Rate limits** — 60 requests/minute (Starter), 600 (Professional), 3,000 (Enterprise, raisable on request).
- **Versioning** — the API is versioned in the URL (`/v3/`). Deprecated versions receive 12 months' notice.
- **SDKs** — official Python and JavaScript/TypeScript SDKs.

### Webhooks

Outbound webhooks send signed (HMAC-SHA256) event payloads when a run starts, completes, fails or waits for approval. Inbound webhooks give each flow a unique URL that can trigger it. Failed deliveries retry with exponential backoff for up to 24 hours.

### NexaFlow Relay (On-Premise Agent)

The Relay is a lightweight agent installed inside the customer network (Linux or Windows, or as a Docker container). It opens an outbound-only TLS connection to NexaFlow, so no inbound firewall ports are required. It supports on-premise databases, SAP ECC, file shares and internal HTTP services. Enterprise customers commonly deploy two Relay instances for high availability. Relay installation usually needs the customer's network and security teams, which is one reason integration-heavy projects can extend beyond the standard implementation timeline.

### Credential Security

Connector credentials are encrypted with AES-256 and stored in a dedicated secrets vault. Enterprise customers can use customer-managed keys. Credentials are never shown again after being saved. See `security_overview.md`.

### Integration Best Practices

1. Create a dedicated service account in each connected system with least-privilege permissions.
2. Build and test in the Development environment first, using sandbox instances of the target systems.
3. Map fields and data owners before configuration; unclear field mapping is the top cause of integration delays.
4. Enable failure alerts to Slack or Teams for every production flow.
5. Keep the number of integrations in the first go-live phase small (typically 3–5) and add more after launch.

### Integration Complexity and Timelines

In the standard enterprise implementation, integration configuration happens in weeks 2–3. Projects with more than five integrations, on-premise systems via Relay, or custom API work are treated as complex and typically move into the 8–12 week range. The authoritative timeline is in `implementation_timeline.md`.

## Key Facts

- 200+ pre-built connectors; premium connectors include SAP, Oracle Fusion and Workday.
- REST and GraphQL APIs, OAuth 2.0, Python and JS SDKs.
- NexaFlow Relay connects on-premise systems with outbound-only connections (Enterprise).
- Webhooks are HMAC-signed and retried for 24 hours.
- More than five integrations usually makes an implementation "complex" (8–12 weeks).

## Related Documents

- product_overview.md
- security_overview.md
- implementation_timeline.md
- enterprise_setup.md

## Retrieval Notes

Retrieve for questions about supported systems ("do you integrate with SAP/Workday?"), API capabilities, webhooks, authentication, rate limits or on-premise connectivity. For the schedule of integration work during onboarding, also retrieve `implementation_timeline.md`.
