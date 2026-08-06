---
name: Search ALTR audits and produce a compliance audit report
description: Search Snowflake query audits, sidecar audits and platform system audits, then define, trigger, download and sign off a structured ALTR audit report.
api: openapi/altr-mapi-openapi.yml
operations: [postQuerySystemaudits, getQuerySystemaudits, getSystemAudits, patchSystemaudits, getAnomalies, getAnomalyDetails, archiveAnomaly]
---

# Search audits and produce a compliance report

## Auth
HTTP Basic — API key name / key secret.

## Audit searches — three different services, all async search-then-fetch

1. **Platform / system audits** (MAPI, `https://altrnet.live.altr.com/api`):
   `postQuerySystemaudits` (`POST /systemaudits/query/start`) returns a token; fetch with
   `getQuerySystemaudits` (`GET /systemaudits/query/result/{token}`). The unpaged list is
   `getSystemAudits` (`GET /systemaudits`); `patchSystemaudits` (`PATCH /systemaudits/read`) marks read.
2. **Snowflake query audits** (`openapi/altr-query-audits-openapi.yml`,
   `https://api.live.altr.com/v1/query-audits`): `POST /search` returns a `search_uuid`;
   fetch with `GET /results/{search_uuid}`. No `operationId`s declared — bind by method + path.
3. **Sidecar (OLTP) audits** (`openapi/altr-sidecar-audit-openapi.yml`,
   `https://{orgID}.sc-control.live.altr.com/v1`): `POST /audits` → `GET /audits/{search_uuid}`.
   Repository-name filtering was added 2026-07-24.

All three are **trigger-then-poll**. Do not treat the search POST as returning results.

## Audit reports (`openapi/altr-audit-report-openapi.yml`, `https://{orgID}.audit-report.live.altr.com/v1`)

This specification declares no `operationId`s; bind by method + path.

1. `POST /audit-reports/definitions/` — create a report definition (what to report on, on what schedule).
2. `POST /audit-reports/definitions/{definition_id}/trigger` — generate on demand.
3. `GET /audit-reports/definitions/{def_id}/instances/` — list generated instances;
   `GET …/instances/{inst_id}` reads one.
4. `GET …/instances/{inst_id}/download` — returns a download URL (PDF or CSV).
5. **Review workflow**: `POST …/comments/` (+ `/pin`, `/unpin`) and
   `POST …/sign_off`; read with `GET …/sign_off` (yours) and `GET …/sign_offs` (all).
6. `DELETE /audit-reports/definitions/{definition_id}` archives; `POST …/restore` brings it back —
   note that **delete is an archive, not a destroy**.

## Anomalies and thresholds (MAPI)
`getAnomalies` (`GET /anomalies`), `getAnomalyDetails` (`GET /anomalies/{id}`),
`addAnomalyNote` (`POST /anomalies/{id}/note`), `archiveAnomaly` (`PATCH /anomalies/{id}/archive`).
Thresholds that raise them: `getThresholds`, `createThreshold`, `putThreshold`, `thresholdSetEnabled`
and the `/thresholds/{id}/…` sub-resources.

## Rules
- Audit search results are org-scoped and time-bounded; always pass an explicit window.
- `429` is declared on these endpoints — back off and retry; nothing else 4xx is retryable.
- Report definitions are the compliance artifact of record. Archive rather than delete, and prefer
  sign-off over informal approval.
