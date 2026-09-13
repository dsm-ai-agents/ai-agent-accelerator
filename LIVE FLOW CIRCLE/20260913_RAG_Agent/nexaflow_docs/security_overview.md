# Security Overview

## Metadata

- Category: Product
- Document Type: Security & Compliance Overview
- Version: 5.1
- Status: Current
- Last Updated: 2026-05-22
- Authoritative: Yes
- Keywords: security, compliance, SOC 2 Type II, ISO 27001, GDPR, HIPAA, encryption, SSO, SAML, OIDC, MFA, SCIM, RBAC, role-based access, audit logs, penetration testing, data retention, AI data usage
- Use When: Someone asks about security certifications, encryption, identity and access management, audit logs, AI data privacy, or needs to answer a security questionnaire.

## Summary

NexaFlow is built for regulated and security-conscious organisations. The platform is SOC 2 Type II and ISO 27001 certified, supports GDPR, and offers HIPAA-ready deployments with a Business Associate Agreement on Enterprise. This document covers infrastructure security, encryption, identity (SSO, MFA, SCIM), role-based access control, audit logs and how customer data is handled by AI agents.

## Main Content

### Certifications and Compliance

| Standard | Status |
|---|---|
| SOC 2 Type II | Certified, audited annually (latest report: March 2026) |
| ISO/IEC 27001:2022 | Certified |
| GDPR | Compliant; Data Processing Agreement available to all customers |
| HIPAA | Supported on Enterprise with signed BAA |
| CCPA | Compliant |
| Penetration testing | Independent third-party test twice a year; summary available under NDA |

SOC 2 reports and the standard security questionnaire (CAIQ) are shared through the NexaFlow Trust Center after an NDA is signed.

### Infrastructure

- Hosted on AWS in US (Virginia), EU (Frankfurt) and APAC (Sydney) regions.
- Production runs across multiple availability zones with automated failover.
- Recovery Point Objective (RPO): 1 hour. Recovery Time Objective (RTO): 4 hours.
- Encrypted backups are retained for 35 days.
- Employee production access requires hardware MFA, is time-bound and is logged.

### Encryption

- **In transit:** TLS 1.2 or higher for all traffic.
- **At rest:** AES-256 for databases, file storage and backups.
- **Secrets:** connector credentials stored in a dedicated vault.
- **Customer-managed keys (CMK):** available on Enterprise via AWS KMS.

### Identity and Authentication

- **MFA** is available on all plans and can be enforced by admins.
- **Single Sign-On** via SAML 2.0 or OpenID Connect on Professional and Enterprise. Tested with Okta, Microsoft Entra ID, Ping Identity and Google Workspace.
- **SCIM 2.0 provisioning** (Enterprise) automatically creates, updates and deactivates users from the identity provider.
- **Session controls** include idle timeout and IP allowlisting (Enterprise).

### Role-Based Access Control (RBAC)

NexaFlow uses role-based access control across flows, agents, connectors and data.

Default roles (Professional and Enterprise):

1. **Owner** — full control including billing and security settings.
2. **Admin** — manages users, roles, connectors and environments.
3. **Builder** — creates and edits flows and agents in permitted workspaces.
4. **Operator** — runs flows, handles approvals and exception queues.
5. **Viewer** — read-only access to dashboards and run history.

Enterprise customers can create **custom roles** with granular permissions (for example "can approve payments over $10,000 but cannot edit flows"). Permissions can be scoped by workspace, so finance flows are invisible to HR builders. Starter includes three fixed roles (Admin, Builder, Viewer).

### Audit Logs

Audit logs record who did what and when: logins, SSO events, permission changes, flow edits and publishes, connector credential changes, API key usage, agent decisions and data exports.

- Starter: not available.
- Professional: 90-day retention, CSV export.
- Enterprise: 1-year retention by default, extendable up to 7 years; real-time streaming to SIEM tools (Splunk, Datadog, Microsoft Sentinel).
- Audit logs are immutable and cannot be edited or deleted by customer admins.

### AI Agent Data Handling

- Customer data is **never used to train** foundation models.
- LLM providers are contractually bound to zero data retention.
- Enterprise customers may bring their own LLM key or restrict agents to an approved model list.
- Agents can only access tools and connectors explicitly granted to them, and every agent action is written to the audit log.
- PII redaction can be applied before content is sent to a model.

### Data Retention and Deletion

Run data is retained according to plan settings (configurable on Enterprise). On contract termination, customer data is deleted within 30 days and a deletion certificate is available on request.

### Security Reviews During Sales and Onboarding

Most enterprise buyers run a vendor security review. A standard review (questionnaire + SOC 2 report) typically takes 1–2 weeks. Reviews needing custom contract terms, on-site assessments or penetration test coordination take longer and are a common reason onboarding moves into the extended 8–12 week timeline (see `implementation_timeline.md`).

## Key Facts

- SOC 2 Type II, ISO 27001, GDPR; HIPAA with BAA on Enterprise.
- AES-256 at rest, TLS 1.2+ in transit, customer-managed keys on Enterprise.
- SSO (SAML/OIDC) on Professional+; SCIM and custom roles on Enterprise.
- Audit logs: 90 days (Professional), 1–7 years with SIEM streaming (Enterprise).
- Customer data is never used to train AI models.

## Related Documents

- feature_matrix.md
- enterprise_capabilities.md
- enterprise_setup.md
- objection_handling.md

## Retrieval Notes

Retrieve for any question about security, compliance certifications, encryption, SSO, MFA, SCIM, RBAC, audit logs, AI data privacy or security questionnaires. Combine with `feature_matrix.md` if the question is plan-specific, and with `objection_handling.md` if a salesperson asks how to respond to a security concern.
