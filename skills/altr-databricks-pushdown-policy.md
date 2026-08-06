---
name: Apply a tag-based governance policy to Databricks with ALTR
description: Connect a Databricks metastore to ALTR and apply a PUSHDOWN masking policy against a raw column tag, which is the opposite convention to Snowflake.
api: openapi/altr-unified-policy-openapi.yml
operations: [getDatabases, createDatabase, createPolicy, createGrantPolicyDatabricks, createRule, getRules, startClassificationMetastore]
---

# Apply a tag-based governance policy to Databricks

## Auth
HTTP Basic — API key name / key secret.

## Steps

1. **Connect the metastore** — `createDatabase` (`POST /databases` on MAPI) with a Databricks
   connection payload; confirm with `getDatabases` and note the integer database id.
2. **Classify it** (optional but usual) — `startClassificationMetastore`
   (`PUT /classification/v1/metastore/{databaseId}`, `openapi/altr-dis-openapi.yml`) or the
   Classification Engine's `POST /jobs/databricks`. Databricks classification is GDLP-only.
3. **Create the policy** — `createPolicy` (`POST /policy`) with, and this is the part that gets missed:
   - `policy_type="PUSHDOWN"` — the API **rejects `"TAG"` for Databricks**
   - `database_ids=[<id>]` as a **list**, even for a single database
   - `tag` as the **raw column tag string** — there is no `connect_tag` step for Databricks and
     Databricks tags never appear in the tag list operations
   `createGrantPolicyDatabricks` (`POST /policy/grant/databricks`) covers the grant-shaped variant.
4. **Attach rules** — `createRule` (`POST /policy/{policy_id}/rules`); verify with `getRules`.
5. The dedicated alpha surface for this is `openapi/altr-dbx-tag-policy-openapi.yml`
   (`registerDatabricksTagPolicy`-class operations under `/v1/alpha`). **It is labelled alpha in its own
   spec description and may change or be removed entirely** — prefer the Unified Policy API.

## Rules
- Snowflake does the opposite: **omit** `database_ids` and let `policy_type` default to `TAG`.
- No idempotency key; check `getPolicies` before creating.
- The alpha Databricks host is issued by ALTR support — the spec's `servers[]` entry is a placeholder,
  not a resolvable hostname.
