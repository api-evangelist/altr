---
name: Run a data access request and approval in ALTR
description: Submit a request for access to governed data, route it for approval, and act on the decision — the human-in-the-loop path an agent should take instead of widening a policy itself.
api: openapi/altr-unified-policy-openapi.yml
operations: [createAccessRequest, getAccessRequests, getAccessRequestById, approveAccessRequest, denyAccessRequest, cancelAccessRequest, createAccessManagementPolicySnowflake, createAccessManagementPolicyOltp, updateAccessManagementPolicySnowflake, triggerAccessManagementPolicyCheck, getUserGroups]
---

# Run a data access request and approval

## Auth
HTTP Basic — API key name / key secret. The key's own user group determines whether it may approve.

## Steps

1. **Submit the request** — `createAccessRequest` (`POST /accessRequest` on
   `https://api.live.altr.com/v1/unified-policy/management/`).
2. **Find it again** — `getAccessRequests` (`GET /accessRequest`) to list, `getAccessRequestById`
   (`GET /accessRequest/{id}`) to read one.
3. **Decide** — `approveAccessRequest` (`PUT /accessRequest/{id}/approve`) or
   `denyAccessRequest` (`PUT /accessRequest/{id}/deny`). The requester withdraws with
   `cancelAccessRequest` (`PUT /accessRequest/{id}/cancel`).
4. **Underlying access-management policies**, if you are building the surface rather than using it:
   `createAccessManagementPolicySnowflake` (`POST /policy/accessManagement/snowflake`),
   `createAccessManagementPolicyOltp` (`POST /policy/accessManagement/oltp`),
   `updateAccessManagementPolicySnowflake`
   (`PUT /policy/accessManagement/snowflake/{policy_id}`), and
   `triggerAccessManagementPolicyCheck` (`PUT /policy/accessManagement/triggerCheck/{policy_id}`)
   to force re-evaluation.
5. **Grants on Snowflake roles** are a separate API — `openapi/altr-rbac-openapi.yml`
   (`https://api.live.altr.com/v1/rbac`, no `operationId`s declared, bind by method + path).

## Rules
- **This is the escalation path.** An agent asked to "give someone access" should raise an access
  request, not rewrite a masking policy — approval is a human decision and ALTR models it explicitly.
- Approve/deny/cancel are `PUT` state transitions, not idempotent creates; read the current state
  with `getAccessRequestById` before transitioning, and treat a `409` as "already decided".
- Everything here is written to the system audit log — see the audit skill.
