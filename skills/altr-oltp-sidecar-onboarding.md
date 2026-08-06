---
name: Onboard an OLTP database behind the ALTR sidecar
description: Register an agent, a repository and a sidecar, bind a listener port to the repo, and confirm the estate is healthy — the path for PostgreSQL, MySQL, SQL Server, Oracle and MongoDB.
api: openapi/altr-sidecar-repo-config-openapi.yml
operations: []
---

# Onboard an OLTP database behind the ALTR sidecar

> The Sidecar/Agent Configuration, Telemetry and Access Tokens specifications declare **no
> `operationId`s**. Every reference below is method + path against
> `https://{orgID}.sc-control.live.altr.com/v1`, exactly as ALTR publishes it.

## Auth
HTTP Basic for the control plane. Sidecar components themselves obtain short-lived tokens from the
Access Tokens API (`openapi/altr-access-tokens-openapi.yml`).

## Steps

1. **Register an agent** — `POST /agents`; list with `GET /agents`, read `GET /agents/{agent_id}`.
2. **Give the agent work** — `POST /agents/{agent_id}/tasks`; list `GET /agents/{agent_id}/tasks`.
3. **Register the repository** (the OLTP database) — `POST /repos`; read `GET /repos/{repo_name}`.
4. **Create the service user ALTR connects with** — `POST /repos/{repo_name}/serviceusers`.
   The org-wide view is `GET /serviceusers`, and the standalone Service User Service
   (`openapi/altr-service-user-openapi.yml`) adds credential handling:
   `POST /services/{service}/users/{userID}/auth/keypair`,
   `POST /services/{service}/users/{userID}/auth/password`, and a test task at
   `POST /services/{service}/users/{userID}/auth/{auth}/{authid}/test` whose result you poll at
   `GET …/test/latest`.
5. **Add the human users** that will connect through the proxy — `POST /repos/{repo_name}/users`.
6. **Create the sidecar** — `POST /sidecars`.
7. **Register a listener port** — `POST /sidecars/{sidecar_id}/ports`; list `GET /sidecars/{sidecar_id}/ports`.
8. **Bind the repo to (sidecar, port)** —
   `POST /sidecars/{sidecar_id}/bindings/ports/{port}/repos/{repo_name}`. This is the step that puts
   traffic through ALTR. Verify with `GET /sidecars/{sidecar_id}/bindings` and
   `GET /repos/{repo_name}/bindings`.
9. **Confirm health** (`openapi/altr-sidecar-telemetry-openapi.yml`, same host):
   `GET /agents/{agent_id}/instances`, `GET /sidecars/{sidecar_id}/instances`,
   `GET /agents/{agent_id}/task-telemetry`, `GET /tasks/{task_id}/task-telemetry`.
10. **Govern it** — apply an OLTP access-management policy
    (`POST /policy/accessManagement/oltp`, Unified Policy API) and classify the repo with
    `POST /jobs/oltp` on the Classification Engine.

## Rules
- **Order matters**: agent → repo → service user → sidecar → listener port → binding. A binding
  against a port that is not registered will fail.
- Teardown is the reverse, and ALTR names it `disconnect`, not `delete`, in the tool surface —
  `DELETE /sidecars/{sidecar_id}/bindings/…` before `DELETE /sidecars/{sidecar_id}`.
- Supported OLTP engines as of the 2026 release notes: PostgreSQL, MySQL 8.0, SQL Server, Oracle
  (including passthrough mode) and MongoDB.
- No idempotency key anywhere. List before you create.
