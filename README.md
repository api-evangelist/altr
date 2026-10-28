# ALTR

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ALTR is a unified data security platform that discovers, classifies, masks, tokenizes and monitors sensitive data across Snowflake, Databricks and OLTP databases (PostgreSQL, MySQL, SQL Server, Oracle, MongoDB). The platform combines automated data classification, tag-based and column-based dynamic data masking, role-based access control, access-approval workflows, database activity monitoring with alerting, format-preserving encryption, and both vaulted and PCI-scoped critical tokenization. Everything the console does is exposed through a large public REST surface — a Management API plus purpose-built classification, policy, RBAC, tagging, audit, telemetry and sidecar-configuration services — alongside an official open-source MCP server, a Terraform provider and a Node.js Shield SDK. Founded in 2018 and headquartered in Austin, Texas.

**Areas:** Data Security · Data Governance · Data Masking · Tokenization · Data Classification · Access Control · Snowflake · Databricks · format-preserving-encryption · Database Activity Monitoring · RBAC · PII

## ALTR on APIs.io

Everything profiled for ALTR is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/altr/](https://apis.io/providers/altr/)** — or go straight to one of the APIs or properties below.

### APIs (69)

- [Vaulted Tokenization API](https://apis.io/apis/altr/vaulted-tokenization-api/) — Tokenizes and detokenizes sensitive data through ALTR's token vault for analytics and transactional workloads, including bring-your-own-key. The public…
- [Key Management API (KMA)](https://apis.io/apis/altr/key-management-api-kma/) — Manages the keys and tweaks used for ALTR Format-Preserving Encryption (FPE). The reference is served per organization at…
- [ALTR MCP Server](https://apis.io/apis/altr/altr-mcp-server/) — Official open-source Model Context Protocol server published by ALTR, exposing 156 tools across 13 domains (databases, tags, policies, classification,…
- [ALTR Access Request API](https://apis.io/apis/altr/altr-access-request-api/) — The access_request API from ALTR — 5 operation(s) for access_request.
- [ALTR Administrators API](https://apis.io/apis/altr/altr-administrators-api/) — Operations about administrators
- [ALTR Agent API](https://apis.io/apis/altr/altr-agent-api/) — The Agent API from ALTR — 2 operation(s) for agent.
- [ALTR Agent Tasks API](https://apis.io/apis/altr/altr-agent-tasks-api/) — The Agent Tasks API from ALTR — 2 operation(s) for agent tasks.
- [ALTR Agents API](https://apis.io/apis/altr/altr-agents-api/) — The Agents API from ALTR — 2 operation(s) for agents.
- [ALTR Alerts API](https://apis.io/apis/altr/altr-alerts-api/) — The Alerts API from ALTR — 4 operation(s) for alerts.
- [ALTR Managed Collections API](https://apis.io/apis/altr/altr-altr-managed-collections-api/) — The ALTR Managed Collections API from ALTR — 8 operation(s) for altr managed collections.
- [ALTR Anomalies API](https://apis.io/apis/altr/altr-anomalies-api/) — Operations about anomalies
- [ALTR Applications API](https://apis.io/apis/altr/altr-applications-api/) — Operations about applications
- [ALTR Auth API](https://apis.io/apis/altr/altr-auth-api/) — The Auth API from ALTR — 3 operation(s) for auth.
- [ALTR Auto Tagging API](https://apis.io/apis/altr/altr-auto-tagging-api-api/) — The Auto Tagging API API from ALTR — 10 operation(s) for auto tagging api.
- [ALTR Batch API](https://apis.io/apis/altr/altr-batch-api/) — The batch API from ALTR — 3 operation(s) for batch.
- [ALTR Classification API](https://apis.io/apis/altr/altr-classification-api/) — Operations about data classification
- [ALTR Classification Jobs API](https://apis.io/apis/altr/altr-classification-jobs-api/) — The Classification Jobs API from ALTR — 21 operation(s) for classification jobs.
- [ALTR Classifiers API](https://apis.io/apis/altr/altr-classifiers-api/) — The Classifiers API from ALTR — 5 operation(s) for classifiers.
- [ALTR Collections API](https://apis.io/apis/altr/altr-collections-api/) — The Collections API from ALTR — 5 operation(s) for collections.
- [ALTR Comments API](https://apis.io/apis/altr/altr-comments-api/) — The Comments API from ALTR — 3 operation(s) for comments.
- [ALTR Configuration API](https://apis.io/apis/altr/altr-configuration-api/) — Configuration information for the ALTRNet
- [ALTR Control Plane API](https://apis.io/apis/altr/altr-control-plane-api/) — The Control Plane API from ALTR — 1 operation(s) for control plane.
- [ALTR Data API](https://apis.io/apis/altr/altr-data-api/) — Protected, Governed, Tokenized, and FPE Columns Endpoints
- [ALTR Data Discovery API](https://apis.io/apis/altr/altr-data-discovery-api/) — Data Classification/Tagging job endpoints
- [ALTR Data Masking API](https://apis.io/apis/altr/altr-data-masking-api/) — Access to column info around available masking types
- [ALTR Data Tagging API](https://apis.io/apis/altr/altr-data-tagging-api/) — Information around tagged columns
- [ALTR Databases API](https://apis.io/apis/altr/altr-databases-api/) — Operations about data sources
- [ALTR Databricks Tag Policy API](https://apis.io/apis/altr/altr-databricks-tag-policy-api/) — Operations related to applying tag-based governance policies to Databricks
- [ALTR Definitions API](https://apis.io/apis/altr/altr-definitions-api/) — The Definitions API from ALTR — 4 operation(s) for definitions.
- [ALTR Instances API](https://apis.io/apis/altr/altr-instances-api/) — The Instances API from ALTR — 3 operation(s) for instances.
- [ALTR Integrations API](https://apis.io/apis/altr/altr-integrations-api/) — The Integrations API from ALTR — 3 operation(s) for integrations.
- [ALTR Maskingpolicies API](https://apis.io/apis/altr/altr-maskingpolicies-api/) — Operations related to masking policies
- [ALTR Me API](https://apis.io/apis/altr/altr-me-api/) — Operations related to the currently logged in administrator
- [ALTR Metadata API](https://apis.io/apis/altr/altr-metadata-api/) — Operations related to the currently logged in users metadata and current organizations metadata.
- [ALTR Organization API](https://apis.io/apis/altr/altr-organization-api/) — Operations about organization
- [ALTR Plan API](https://apis.io/apis/altr/altr-plan-api/) — Operations related to the features the organization has
- [ALTR Policy API](https://apis.io/apis/altr/altr-policy-api/) — The policy API from ALTR — 13 operation(s) for policy.
- [ALTR Query Audits API](https://apis.io/apis/altr/altr-query-audits-api-api/) — The Query Audits API API from ALTR — 2 operation(s) for query audits api.
- [ALTR Query Dashboard API](https://apis.io/apis/altr/altr-query-dashboard-api-api/) — The Query Dashboard API API from ALTR — 2 operation(s) for query dashboard api.
- [ALTR RBAC API](https://apis.io/apis/altr/altr-rbac-api-api/) — The RBAC API API from ALTR — 11 operation(s) for rbac api.
- [ALTR Refresh Tag Value Job API](https://apis.io/apis/altr/altr-refresh-tag-value-job-api/) — The Refresh Tag Value Job API from ALTR — 2 operation(s) for refresh tag value job.
- [ALTR Repo Users API](https://apis.io/apis/altr/altr-repo-users-api/) — The Repo Users API from ALTR — 2 operation(s) for repo users.
- [ALTR Repos API](https://apis.io/apis/altr/altr-repos-api/) — The Repos API from ALTR — 2 operation(s) for repos.
- [ALTR Rowaccess API](https://apis.io/apis/altr/altr-rowaccess-api/) — Operations related to row access policy
- [ALTR Rules API](https://apis.io/apis/altr/altr-rules-api/) — The Rules API from ALTR — 6 operation(s) for rules.
- [ALTR SCIM API](https://apis.io/apis/altr/altr-scim-api/) — Operations related to SCIM
- [ALTR Service Users API](https://apis.io/apis/altr/altr-service-users-api/) — The Service Users API from ALTR — 3 operation(s) for service users.
- [ALTR Setup Guide API](https://apis.io/apis/altr/altr-setup-guide-api/) — Operations about the setup-guide
- [ALTR Sidecar API](https://apis.io/apis/altr/altr-sidecar-api/) — The Sidecar API from ALTR — 2 operation(s) for sidecar.
- [ALTR Sidecar Audit API](https://apis.io/apis/altr/altr-sidecar-audit-api-api/) — The Sidecar Audit API API from ALTR — 2 operation(s) for sidecar audit api.
- [ALTR Sidecar Listener Port and Repo bindings API](https://apis.io/apis/altr/altr-sidecar-listener-port-and-repo-bindings-api/) — The Sidecar Listener Port and Repo bindings API from ALTR — 3 operation(s) for sidecar listener port and repo bindings.
- [ALTR Sidecar Listeners API](https://apis.io/apis/altr/altr-sidecar-listeners-api/) — The Sidecar Listeners API from ALTR — 2 operation(s) for sidecar listeners.
- [ALTR Sidecars API](https://apis.io/apis/altr/altr-sidecars-api/) — The Sidecars API from ALTR — 2 operation(s) for sidecars.
- [ALTR Sign Off API](https://apis.io/apis/altr/altr-sign-off-api/) — The Sign-Off API from ALTR — 2 operation(s) for sign-off.
- [ALTR Snowflake Metadata API](https://apis.io/apis/altr/altr-snowflake-metadata-api-api/) — The Snowflake Metadata API API from ALTR — 13 operation(s) for snowflake metadata api.
- [ALTR SSO API](https://apis.io/apis/altr/altr-sso-api/) — Operations related to Single Sign-On
- [ALTR Subscriptions API](https://apis.io/apis/altr/altr-subscriptions-api/) — The Subscriptions API from ALTR — 3 operation(s) for subscriptions.
- [ALTR Systemaudits/query API](https://apis.io/apis/altr/altr-systemaudits-query-api/) — Operations related to asynchronously querying system audits
- [ALTR Tag Masking API](https://apis.io/apis/altr/altr-tag-masking-api-api/) — The Tag Masking API API from ALTR — 3 operation(s) for tag masking api.
- [ALTR Tags API](https://apis.io/apis/altr/altr-tags-api/) — Operations related to tags
- [ALTR Task API](https://apis.io/apis/altr/altr-task-api/) — The Task API from ALTR — 2 operation(s) for task.
- [ALTR Tasks API](https://apis.io/apis/altr/altr-tasks-api/) — The Tasks API from ALTR — 3 operation(s) for tasks.
- [ALTR Thresholds API](https://apis.io/apis/altr/altr-thresholds-api/) — Operations about thresholds
- [ALTR Unsubscribe API](https://apis.io/apis/altr/altr-unsubscribe-api/) — The Unsubscribe API from ALTR — 1 operation(s) for unsubscribe.
- [ALTR Users API](https://apis.io/apis/altr/altr-users-api/) — The Users API from ALTR — 3 operation(s) for users.
- [ALTR Utility API](https://apis.io/apis/altr/altr-utility-api/) — Access DIS job and third party import information.
- [ALTR API Keys API](https://apis.io/apis/altr/altr-api-keys-api/) — Operations about ApiKeys
- [ALTR system Audits API](https://apis.io/apis/altr/altr-system-audits-api/) — Operations related to system audits
- [ALTR User Groups API](https://apis.io/apis/altr/altr-user-groups-api/) — Operations related to user groups

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Altr Events Webhooks](https://apis.io/asyncapis/altr/altr-events-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [altr](https://apis.io/servers/altr/altr/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Altr Agentic Access](https://apis.io/agentic-access/altr/altr-agentic-access/)

#### Collections (66)

Postman and Open Collection request collections.

- [Unified Policy Access Request API](https://apis.io/collections/altr/open-altr-access-request-api/)
- [ALTR Management Administrators API](https://apis.io/collections/altr/open-altr-administrators-api/)
- [ALTR Telemetry Agent API](https://apis.io/collections/altr/open-altr-agent-api/)
- [ALTR Sidecar/Agent Configuration Agent Tasks API](https://apis.io/collections/altr/open-altr-agent-tasks-api/)
- [ALTR Sidecar/Agent Configuration Agents API](https://apis.io/collections/altr/open-altr-agents-api/)
- [ALTR DAM Alerting Alerts API](https://apis.io/collections/altr/open-altr-alerts-api/)
- [ALTR Classification Engine ALTR Managed Collections API](https://apis.io/collections/altr/open-altr-altr-managed-collections-api/)
- [ALTR Management Anomalies API](https://apis.io/collections/altr/open-altr-anomalies-api/)
- [ALTR Management Apikeys API](https://apis.io/collections/altr/open-altr-apikeys-api/)
- [ALTR Management Applications API](https://apis.io/collections/altr/open-altr-applications-api/)
- [Service User Service Auth API](https://apis.io/collections/altr/open-altr-auth-api/)
- [Auto Tagging Auto Tagging API API](https://apis.io/collections/altr/open-altr-auto-tagging-api-api/)
- [Critical Tokenization V2 Batch API](https://apis.io/collections/altr/open-altr-batch-api/)
- [ALTR Management Classification API](https://apis.io/collections/altr/open-altr-classification-api/)
- [ALTR Classification Engine Classification Jobs API](https://apis.io/collections/altr/open-altr-classification-jobs-api/)
- [ALTR Classification Engine Classifiers API](https://apis.io/collections/altr/open-altr-classifiers-api/)
- [ALTR Classification Engine Collections API](https://apis.io/collections/altr/open-altr-collections-api/)
- [ALTR Audit Report Comments API](https://apis.io/collections/altr/open-altr-comments-api/)
- [ALTR Management Configuration API](https://apis.io/collections/altr/open-altr-configuration-api/)
- [Access Tokens Control Plane API](https://apis.io/collections/altr/open-altr-control-plane-api/)
- [ALTR Management Data API](https://apis.io/collections/altr/open-altr-data-api/)
- [ALTR Datastore Information Service Data Discovery API](https://apis.io/collections/altr/open-altr-data-discovery-api/)
- [ALTR Datastore Information Service Data Masking API](https://apis.io/collections/altr/open-altr-data-masking-api/)
- [ALTR Datastore Information Service Data Tagging API](https://apis.io/collections/altr/open-altr-data-tagging-api/)
- [ALTR Management Databases API](https://apis.io/collections/altr/open-altr-databases-api/)
- …and 41 more published on APIs.io

#### Overlays (21)

OpenAPI overlays, including conversational phrasing for each operation.

- [Altr Access Tokens Overlay](https://apis.io/overlays/altr/altr-access-tokens-overlay/)
- [Altr Audit Report Overlay](https://apis.io/overlays/altr/altr-audit-report-overlay/)
- [Altr Auto Tagging Overlay](https://apis.io/overlays/altr/altr-auto-tagging-overlay/)
- [Altr Classification Overlay](https://apis.io/overlays/altr/altr-classification-overlay/)
- [Altr Critical Tokenization Overlay](https://apis.io/overlays/altr/altr-critical-tokenization-overlay/)
- [Altr Dam Alerting Overlay](https://apis.io/overlays/altr/altr-dam-alerting-overlay/)
- [Altr Dbx Tag Policy Overlay](https://apis.io/overlays/altr/altr-dbx-tag-policy-overlay/)
- [Altr Dis Overlay](https://apis.io/overlays/altr/altr-dis-overlay/)
- [Altr Mapi Overlay](https://apis.io/overlays/altr/altr-mapi-overlay/)
- [Altr Notification Integration Overlay](https://apis.io/overlays/altr/altr-notification-integration-overlay/)
- [Altr Query Audits Overlay](https://apis.io/overlays/altr/altr-query-audits-overlay/)
- [Altr Query Dashboard Overlay](https://apis.io/overlays/altr/altr-query-dashboard-overlay/)
- [Altr Rbac Overlay](https://apis.io/overlays/altr/altr-rbac-overlay/)
- [Altr Service User Overlay](https://apis.io/overlays/altr/altr-service-user-overlay/)
- [Altr Sidecar Audit Overlay](https://apis.io/overlays/altr/altr-sidecar-audit-overlay/)
- [Altr Sidecar Repo Config Overlay](https://apis.io/overlays/altr/altr-sidecar-repo-config-overlay/)
- [Altr Sidecar Telemetry Overlay](https://apis.io/overlays/altr/altr-sidecar-telemetry-overlay/)
- [Altr Snowflake Metadata Overlay](https://apis.io/overlays/altr/altr-snowflake-metadata-overlay/)
- [Altr Tag Masking Overlay](https://apis.io/overlays/altr/altr-tag-masking-overlay/)
- [Altr Tag Refresh Overlay](https://apis.io/overlays/altr/altr-tag-refresh-overlay/)
- [Altr Unified Policy Overlay](https://apis.io/overlays/altr/altr-unified-policy-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Altr Authentication](https://apis.io/security/altr/altr-authentication/)
- [Altr Domain Security](https://apis.io/security/altr/altr-domain-security/)
- [Altr Trust Center](https://apis.io/security/altr/altr-trust-center/)
- [Altr Vulnerability Disclosure](https://apis.io/security/altr/altr-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Altr Plans Pricing](https://apis.io/plans/altr/altr-plans-pricing/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://altr.com/)
- [Documentation](https://docs.altr.com/)
- [Getting started](https://docs.altr.com/account-and-api/creating-an-altr-account/)
- [API reference](https://docs.altr.com/account-and-api/api/)
- [Pricing](https://altr.com/pricing/)
- [Sign up](https://altrnet.live.altr.com/api/auth/organization_register)
- [Support](https://docs.altr.com/support/)
- [Changelog](https://docs.altr.com/en/what-s-new.html)
- [Blog](https://altr.com/news/)
- [Security](https://trust.altr.com/)
- [Compliance](https://trust.altr.com/)
- [Terms of service](https://altr.com/info/altr-solutions-inc-terms-of-service/)
- [Privacy policy](https://altr.com/privacy-policy-2/)
- [GitHub](https://github.com/altrsoftware)

## API Evangelist rating

**Kin Score 59.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 60.0 |
| Contract governance | 4.5 |
| Operational transparency | 36.8 |
| Developer ergonomics | 73.2 |
| Access clarity | 53.9 |

**Agent readiness 48.1** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 35.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/altr/](https://apis.io/providers/altr/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ALTR: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/altr/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
