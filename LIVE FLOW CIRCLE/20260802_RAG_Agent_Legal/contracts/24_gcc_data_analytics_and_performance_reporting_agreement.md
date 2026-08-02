---
document_id: GCC-DEMO-024
document_type: GCC Data Analytics and Performance Reporting Agreement
title: GCC Data Analytics and Performance Reporting Agreement - Alder & Finch and MetricSpring
main_category: managed_gcc_operations
knowledge_group: Managed GCC Operations & Transformation
gcc_lifecycle_stage: operate_and_transform
subcategory: gcc_data_analytics_performance_reporting
status: active
effective_date: 2026-05-15
expiration_date: 2028-05-14
jurisdiction: Tamil Nadu, India
governing_law: India
consulting_firm: MetricSpring Analytics Services Private Limited
service_provider: MetricSpring Analytics Services Private Limited
client: Alder & Finch Retail plc
client_headquarters_country: United Kingdom
india_location: Chennai
currency: GBP
contract_value: 456000
risk_level: medium
renewal_type: fixed_term
confidentiality_level: restricted
source_type: synthetic_demo_contract
rag_tags:
  - category:managed_gcc_operations
  - lifecycle:operate_and_transform
  - contract-type:data-analytics-reporting
  - geography:chennai
  - topic:executive-dashboards
  - topic:data-quality
  - topic:headcount-analytics
  - topic:cost-reporting
  - topic:ai-governance
---

# GCC Data Analytics and Performance Reporting Agreement

> **Synthetic demo document.** The parties, persons, data, metrics, addresses, and commercial arrangements below are fictitious and intended solely for a RAG knowledge-base demonstration. This is not an executable agreement or professional advice.

This Agreement is entered into on 15 May 2026 by **Alder & Finch Retail plc**, a fictitious United Kingdom retailer (**Client**), and **MetricSpring Analytics Services Private Limited**, a fictitious company at 23 OMR Digital Campus, Chennai 600096 (**Provider**).

The Client operates a Chennai GCC and wishes to consolidate workforce, cost, hiring, service, and productivity data into governed management reporting.

## 1. Term

The Agreement begins on the Effective Date and continues for 24 months. It expires without automatic renewal unless the parties sign an extension.

## 2. Services

The Provider shall design, implement, and operate:

- an executive GCC scorecard;
- dashboards for headcount, attrition, hiring funnel, workforce diversity, employee lifecycle, and spans of control;
- dashboards for operating cost, budget variance, seat cost, vendor spend, and forecast;
- service-performance dashboards for HR, finance, IT, workplace, and procurement;
- a controlled metric catalogue and data dictionary;
- automated data ingestion from approved sources;
- data-quality monitoring and exception workflows;
- monthly management packs and quarterly insight reports; and
- authorized ad hoc analysis within the included capacity.

The initial sources are Workday test tenant, Greenhouse recruitment system, Oracle Fusion finance system, ServiceNow, workplace access reports, and approved spreadsheets. Adding systems requires change control.

## 3. Deliverables and milestones

| Milestone | Due date |
|---|---|
| Discovery and source assessment | 12 June 2026 |
| Metric catalogue v1 | 10 July 2026 |
| Data model and security design | 31 July 2026 |
| Pilot dashboards | 28 August 2026 |
| User acceptance completion | 25 September 2026 |
| Production go-live | 1 October 2026 |

The Provider shall supply architecture diagrams, source mappings, transformation rules, refresh schedules, role matrix, test evidence, operating manual, and dashboard guide.

## 4. Acceptance

The Client has ten Business Days to test a milestone against documented requirements. It shall accept or provide a specific defect list. A milestone is deemed accepted if the Client uses it in production for 20 Business Days without reporting a Severity 1 or Severity 2 defect.

The Provider shall correct Severity 1 and Severity 2 acceptance defects without charge. Minor cosmetic issues do not prevent acceptance and shall be placed in the backlog.

## 5. Metric governance

Each published metric must identify its definition, owner, source, refresh frequency, transformation logic, unit, permitted breakdowns, and known limitations. A Metric Governance Council with representatives from Client Finance, HR, GCC Operations, and the Provider shall approve material definition changes.

The Provider shall not silently alter historic definitions. Where a definition changes, reports shall show the effective date and, where practicable, restate comparatives or disclose the break in series.

Examples include:

- **Active Headcount:** workers active in the HR system at reporting cut-off, excluding contingent workers unless separately shown;
- **Voluntary Attrition:** voluntary leavers divided by average active employees on a trailing-12-month basis;
- **Cost per Seat:** eligible operating costs divided by average occupied seats; and
- **Time to Fill:** calendar days from approved requisition to accepted offer.

## 6. Data responsibility and quality

The Client owns source data and is responsible for its underlying accuracy, lawful collection, and business meaning. The Provider is responsible for accurate extraction, transformation, reconciliation, and presentation according to approved rules.

The Provider shall run completeness, validity, uniqueness, consistency, and timeliness checks. A source-to-report variance above 0.5% for financial totals or 1.0% for workforce counts is a material exception requiring investigation.

The Provider shall maintain a quality log showing source, owner, impact, status, workaround, and target resolution. It may label a report “provisional” where unresolved source defects materially affect interpretation.

## 7. Refresh and support Service Levels

| Service measure | Target |
|---|---|
| Daily operational dashboards | Refreshed by 8:00 a.m. IST |
| Monthly finance dashboard | Refreshed by Business Day 8 |
| Dashboard availability | 99.7% monthly |
| Severity 1 response | 20 minutes |
| Severity 1 workaround | 4 hours |
| Standard data-quality alert | 1 Business Day |
| Approved user access request | 2 Business Days |
| Monthly pack delivery | Business Day 10 |

Targets exclude approved maintenance, unavailable source systems, and inaccurate source data if promptly reported. A critical miss earns a 2.5% credit of the monthly run fee, capped at 10%.

## 8. Access and permitted use

Access shall follow least privilege and Client-approved roles. Executive compensation and identifiable employee relations data shall be restricted to named HR and executive users. Country and function leaders may view only authorized populations.

The Client may share aggregated dashboards with its Affiliates. Raw or personally identifiable data may not be shared outside the approved group without privacy and security review.

The Provider shall log dashboard access and privileged changes for 365 days. Quarterly access reviews are required.

## 9. Privacy

The Provider processes personal data only under Client instructions. Workforce dashboards shall use aggregation and suppression where a population contains fewer than seven individuals, unless authorized for legitimate HR administration.

The Provider shall support access, correction, deletion, and objection requests; notify the Client of any request within one Business Day; and not respond independently unless required by law.

Any international data transfer requires prior approval and an appropriate transfer mechanism. A personal-data incident must be notified within four hours of confirmation.

## 10. Analytics and AI restrictions

Predictive attrition, performance scoring, automated employment recommendations, facial recognition, emotion inference, and individual productivity ranking are outside scope. They may not be introduced through ordinary change control; they require a separate impact assessment and written executive approval.

The Provider shall not use Client Data to train shared or public AI models. Approved generative-AI summaries must run in an isolated enterprise environment, cite the underlying dashboard, carry a human-review indicator, and must not make employment decisions.

## 11. Charges

The Client shall pay:

- GBP 78,000 for implementation, payable 20% at commencement, 30% at pilot, 30% at acceptance, and 20% at go-live; and
- GBP 15,750 per month for managed reporting from go-live.

The indicative total contract value is GBP 456,000. Monthly fees include 12 dashboards, six source integrations, one monthly pack, one quarterly insight report, and 40 ad hoc analyst hours.

Additional analyst time is GBP 85 per hour. New source integrations and material dashboard redesign require a change order. Invoices are payable within 30 days.

## 12. Governance

During implementation, project leads meet weekly. After go-live, service reviews occur monthly and the Metric Governance Council meets quarterly. The Provider shall maintain a backlog, release calendar, data-quality register, decision log, and security-risk register.

Production changes require documented testing, approval, rollback planning, and release notes. Emergency fixes may be made to restore service but must be retrospectively documented within one Business Day.

## 13. Personnel and subcontractors

The Provider shall assign a Product Owner, Data Architect, Analytics Lead, Data Engineer, and Support Lead. Replacement of the Product Owner or Architect requires 15 Business Days’ notice where practicable.

Cloud hosting and visualization vendors listed in the architecture are approved subcontractors. New subprocessors require 30 days’ notice. The Provider remains responsible for their performance.

## 14. Security

The Provider shall use encryption, multifactor authentication, secrets management, environment separation, vulnerability scanning, annual penetration testing, secure coding review, endpoint management, backups, and monitored logs.

Production data may not be copied to development. Test data must be synthetic or masked. Critical vulnerabilities shall be mitigated within 72 hours and high vulnerabilities within 15 days.

The Provider shall notify a suspected security incident within two hours and provide daily status reports until containment.

## 15. Intellectual property

The Client owns Client Data, approved metric definitions, Client-specific data models, bespoke dashboard layouts, and paid reports. The Provider retains its generic connectors, reusable code libraries, visualization patterns, templates, and analytic methods.

The Provider grants the Client a perpetual internal-use license to embedded Provider Background Materials. Open-source components remain subject to their licenses and shall be identified.

## 16. Confidentiality

Each party shall protect confidential technical, financial, operational, and personal information using reasonable safeguards and use it only for this Agreement. Disclosure is limited to need-to-know personnel, Affiliates, auditors, and advisers bound by comparable duties.

Exceptions apply to information public without breach, previously known, independently developed, lawfully obtained, or legally compelled. Obligations survive seven years; trade secrets remain protected while legally confidential.

## 17. Audit and records

The Provider shall retain source-to-report control evidence, release records, access reviews, and service reports for seven years. The Client may audit relevant controls annually on ten Business Days’ notice and following a material incident.

The Provider shall provide current security certifications and remediation summaries on request, subject to confidentiality restrictions.

## 18. Warranties

The Provider warrants professional performance, conformity with specifications, and reasonable accuracy of transformations based on supplied data. It shall correct reproducible defects at no charge.

Analytics are decision support only. The Provider does not warrant business outcomes, forecast accuracy, employee behavior, cost savings, or error-free source systems.

## 19. Liability and indemnity

The Provider indemnifies the Client against third-party IP claims concerning Provider-created deliverables and claims caused by Provider unlawful processing of personal data. The Client indemnifies the Provider for claims arising from unlawful Client instructions or Client-provided content.

Neither party is liable for indirect or consequential loss. Aggregate liability is capped at fees paid or payable in the prior 12 months, doubled for confidentiality, privacy, security, or IP indemnity. Fraud and wilful misconduct are uncapped.

## 20. Continuity

The Provider shall back up configuration daily and retain monthly snapshots for 12 months. Critical reporting service shall recover within four hours with no more than four hours of configuration-data loss. Continuity is tested annually.

## 21. Termination and exit

Either party may terminate for uncured material breach after 30 days or insolvency. The Client may terminate for convenience after go-live with 90 days’ notice.

At exit, the Provider shall supply data extracts, metric catalogue, transformation logic, source mappings, code owned by the Client, dashboard exports, backlog, access list, and operational documentation. Eighty exit hours are included. The Provider shall delete Client Data within 45 days, except legally retained backups, and certify deletion.

## 22. Governing law and general

Indian law governs. Disputes unresolved by executives after 20 Business Days shall be arbitrated by one arbitrator seated in Chennai, in English, under the Arbitration and Conciliation Act, 1996.

Neither party may assign without consent except to an Affiliate or business successor. The Provider is an independent contractor. Force majeure excuses affected performance subject to notice, mitigation, and continuity measures. This Agreement is the entire agreement and amendments must be signed.

## Signatures

For **Alder & Finch Retail plc**  
Name: Harriet Cole (fictitious), Director of Global Business Services  
Date: 15 May 2026

For **MetricSpring Analytics Services Private Limited**  
Name: S. Nivedha Rao (fictitious), Chief Executive Officer  
Date: 15 May 2026

