---
name: Connect a data source and classify it with ALTR
description: Register a Snowflake, Databricks or OLTP data source with ALTR, run an automated classification scan over it, and read the findings tree down to the classified column.
api: openapi/altr-mapi-openapi.yml
operations: [getDatabases, createDatabase, getDatabase, getDatabaseStatus, listDBs, retrieveJobStatusDB, retrieveColumnClassificationsDB, getClassificationList]
---

# Connect a data source and classify it

## Auth
Every ALTR REST call uses **HTTP Basic**: username = the API key name (`ALTR-…`), password = the API key
secret. Create the pair in the console at *Settings > Preferences > API > Add New* — the secret is shown
once. See `authentication/altr-authentication.yml`.

There is **no OAuth and no idempotency key**. Do not blind-retry a `POST`; see `conventions/altr-conventions.yml`.

## Steps

1. **List what is already connected** — `getDatabases` (`GET /databases` on
   `https://altrnet.live.altr.com/api`). Match on name before creating anything; ALTR has no
   create-or-get and no idempotency contract, so a retried create makes a second database.
2. **Connect the source** — `createDatabase` (`POST /databases`). For Snowflake specifically,
   `createSnowflakeConnection` (`POST /databases/snowflake/connect`) is the guided path, and
   `getSnowflakeAccounts` / `getSnowflakeAccountDatabases` enumerate what an already-linked Snowflake
   account exposes.
3. **Wait for the connection to come up** — poll `getDatabaseStatus` (`GET /databases/{id}/status`).
   Use `updateDatabaseStatus` (`PATCH /databases/{id}/status`) to force a re-sync rather than
   re-creating the database.
4. **Start a classification scan.** Two surfaces exist and they are not interchangeable:
   - Datastore Information Service: `startClassification` (`PUT /classification/v1/db/{databaseId}`)
     or `startClassificationMetastore` (`PUT /classification/v1/metastore/{databaseId}` for Databricks)
     in `openapi/altr-dis-openapi.yml`.
   - Classification Engine (`openapi/altr-classification-openapi.yml`, org-scoped host
     `https://{orgID}.classification.live.altr.com/v1`): `POST /jobs/snowflake`, `POST /jobs/oltp`,
     `POST /jobs/databricks`. **`POST /jobs` is marked deprecated in the spec — do not use it.**
     This specification declares no `operationId`s, so bind by method + path.
5. **Poll the job** — `retrieveJobStatusDB` (`GET /classification/v2/db/status/{databaseId}`) or
   `GET /jobs/{job_id}` on the Classification Engine. `GET /jobs/active` lists everything in flight.
6. **Read the findings tree**, one level at a time, on the Classification Engine:
   `GET /jobs/{job_id}/findings` → `…/databases/{database}/schemas` → `…/tables` → `…/columns` →
   `…/classifiers` → `…/lineage`. `GET /jobs/{job_id}/summary` is the rollup.
   The flat alternative is `retrieveColumnClassificationsDB`
   (`GET /classification/v2/db/column/type/{type}/{id}`) on DIS.
7. **Record human review decisions** (Human-in-the-Loop, shipped 2026-07-16) —
   `POST /jobs/{job_id}/decisions`, read with `GET /jobs/{job_id}/decisions`, revoke with
   `DELETE /jobs/{job_id}/decisions`, progress via `GET /jobs/{job_id}/review-status`.
   Finalize with `POST /jobs/{job_id}/report/confirm` (or `/cancel`).

## Rules
- **Pagination is not uniform.** `limit`/`offset` on most list endpoints, `cursor` on a few,
  `nextToken` on two, `contiguous_id` + `has_more` on notification integrations. Read the operation's
  own parameters — never assume.
- **Errors are not RFC 9457.** No `application/problem+json` anywhere. See `errors/altr-problem-types.yml`.
  Retry only `429`/`5xx`, with backoff; `400`/`401`/`403`/`404`/`409` will not succeed on retry.
- **Most services are org-scoped by subdomain**: `https://<ORG_ID>.<service>.live.altr.com`. Only
  `api.live.altr.com` and `altrnet.live.altr.com` are shared hosts.
