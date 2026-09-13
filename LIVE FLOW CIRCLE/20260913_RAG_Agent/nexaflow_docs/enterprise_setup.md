# Enterprise Setup Guide

## Metadata

- Category: Implementation
- Document Type: Technical Setup Guide
- Version: 2.8
- Status: Current
- Last Updated: 2026-07-20
- Authoritative: Yes
- Keywords: enterprise setup, environment setup, tenant provisioning, SSO configuration, SAML, SCIM, role mapping, custom roles, workspaces, data residency, single-tenant, Relay installation, security review, go-live checklist, enterprise onboarding
- Use When: Someone asks how an Enterprise tenant is configured during onboarding, what IT and security teams need to do, or what enterprise-specific steps affect the onboarding timeline.

## Summary

This guide covers the Enterprise-specific technical setup that happens during onboarding, mainly in Phase 3 (Environment Setup) and Phase 4 (Integration Configuration) of the nine-phase process in `onboarding_guide.md`. It explains tenant provisioning, SSO and SCIM, workspace and role design, security review, Relay installation and the go-live checklist. In a standard 4–6 week implementation, environment setup is completed in week 2; single-tenant deployments, strict data residency or extended security reviews move projects toward the 8–12 week track described in `implementation_timeline.md`.

## Main Content

### Step 1: Pre-Kickoff Security Review (Starts at Signature)

Enterprise customers almost always run a vendor security review. To avoid delaying the project:

1. NexaFlow shares the SOC 2 Type II report, ISO 27001 certificate and CAIQ questionnaire via the Trust Center on the day of signature.
2. The customer security team submits additional questions within 5 business days.
3. Standard reviews complete in 1–2 weeks, running in parallel with discovery and design.
4. Reviews requiring on-site assessments, custom penetration testing or HIPAA BAA negotiation take 3–6 weeks and classify the project as complex.

### Step 2: Tenant Provisioning (Week 2)

| Decision | Options | Timeline Impact |
|---|---|---|
| Deployment | Multi-tenant (default) or single-tenant | Single-tenant adds ~1 week |
| Region | US (Virginia), EU (Frankfurt), APAC (Sydney) | None if chosen before kickoff |
| Environments | Development, Staging, Production | Included |
| Encryption keys | NexaFlow-managed or customer-managed (AWS KMS) | CMK adds 2–3 days of customer IT work |

The region cannot be changed after data is loaded without a migration project.

### Step 3: Single Sign-On (Week 2)

1. Customer identity admin creates a SAML 2.0 or OIDC application in Okta, Microsoft Entra ID, Ping or Google Workspace.
2. NexaFlow provides the ACS URL and entity ID; the customer returns metadata.
3. Test with 3–5 pilot users in Development.
4. Enforce SSO for all users and disable password login (break-glass admin account retained).

Typical effort: 2–5 business days of the customer identity team's time.

### Step 4: SCIM Provisioning and Role Mapping (Week 2)

- Enable SCIM 2.0 from the identity provider to automatically create, update and deactivate users.
- Map identity provider groups to NexaFlow roles, for example:

| IdP Group | NexaFlow Role | Workspace |
|---|---|---|
| NF-Platform-Admins | Admin | All |
| NF-Finance-Builders | Builder | Finance |
| NF-Finance-AP-Team | Operator | Finance |
| NF-Leadership | Viewer | All |

- Create custom roles if needed (for example "Payment Approver over $10,000").
- Deactivation in the IdP removes NexaFlow access within 40 minutes.

### Step 5: Workspace and Governance Design (Weeks 1–2)

- One workspace per business unit or major process area.
- Decide which connectors each workspace may use.
- Configure promotion rules: flows move Development → Staging → Production with required approval.
- Nominate Center of Excellence (CoE) admins who approve production changes.

### Step 6: Network and Relay Setup (Weeks 2–3, if needed)

For on-premise systems:
1. Customer provisions a Linux or Windows VM (2 vCPU, 8 GB RAM) or Docker host.
2. Allow outbound TLS 443 to the NexaFlow region endpoint; no inbound ports needed.
3. Install two Relay instances for high availability.
4. Register Relays in the Admin Console and test connectivity.

Relay setup requires network and security approvals and commonly adds 1–2 weeks.

### Step 7: Audit and Compliance Configuration

- Set audit log retention (1 year default, up to 7 years).
- Configure SIEM streaming to Splunk, Datadog or Microsoft Sentinel.
- Enable IP allowlisting and session timeout policies.
- Configure PII redaction and approved AI model list for Agent Studio.

### Step 8: Enterprise Go-Live Checklist

- [ ] Security review approved and documented
- [ ] SSO enforced; SCIM provisioning verified
- [ ] Roles and workspace permissions reviewed by customer security
- [ ] All in-scope integrations tested in Staging with production credentials
- [ ] Data migration reconciled and signed off
- [ ] UAT signed off with zero open critical defects
- [ ] Failure alerts routed to on-call channels
- [ ] Audit log streaming confirmed
- [ ] Rollback plan documented
- [ ] Go/no-go meeting held 2 business days before cutover
- [ ] Hypercare contacts and schedule shared

### Enterprise Setup and the Overall Timeline

| Scenario | Environment Setup Duration | Overall Timeline |
|---|---|---|
| Multi-tenant, SSO + SCIM, standard review | Week 2 | 4–6 weeks |
| Single-tenant or customer-managed keys | Weeks 2–3 | 6–8 weeks |
| Single-tenant + Relay + extended security review | Weeks 3–5 | 8–12 weeks |

## Key Facts

- Security review should start at contract signature; standard reviews take 1–2 weeks.
- Environment setup (tenant, SSO, SCIM, roles) happens in week 2 of a standard implementation.
- Single-tenant deployment adds about 1 week; Relay setup commonly adds 1–2 weeks.
- IdP groups map to NexaFlow roles and workspaces via SCIM.
- Standard enterprise onboarding is 4–6 weeks; complex setups push it to 8–12 weeks.

## Related Documents

- onboarding_guide.md
- implementation_timeline.md
- security_overview.md
- enterprise_capabilities.md

## Retrieval Notes

Retrieve for enterprise onboarding questions involving SSO, SCIM, roles, workspaces, data residency, single-tenant setup, Relay installation, security review or the go-live checklist. For "what is the enterprise onboarding process and timeline", retrieve this file together with `onboarding_guide.md` and `implementation_timeline.md`.
