---
name: Create a tag-based dynamic masking policy in ALTR
description: Connect a Snowflake tag to ALTR, create a masking policy against it, and attach per-role masking rules so each role sees a different level of the data.
api: openapi/altr-unified-policy-openapi.yml
operations: [getPolicies, createPolicy, createPolicyWithRules, getPolicyById, createRule, getRules, getRuleById, updateRule, updateBatchRules, deleteRule, deletePolicy, getUserGroups, retrieveTagsList, retrieveTagDetails]
---

# Create a tag-based dynamic masking policy

## Auth
HTTP Basic — API key name as username, key secret as password. See `authentication/altr-authentication.yml`.

## Steps

1. **Find the roles you will write rules for.** ALTR calls them *user groups* in MAPI and in the
   console, and *roles* in the MCP tool surface — same objects.
   `getUserGroups` (`GET /usergroups` on `https://altrnet.live.altr.com/api`).
2. **Find the tag.** `retrieveTagsList` (`GET /tags/v1/tags/groups/list`) and `retrieveTags`
   (`GET /tags/v2/tags/list`) in `openapi/altr-dis-openapi.yml`; details via `retrieveTagDetails`
   (`GET /tags/v2/tags/details/{tagId}`) or `retrieveTagGroupDetails`. `getListOfTags` (`GET /tags`)
   on MAPI is the equivalent list.
   To register a new Snowflake tag with ALTR, use the Tag Masking API
   (`openapi/altr-tag-masking-openapi.yml`, `PUT /tag/{tag-group-id}` — no `operationId`s declared).
3. **Check for an existing policy first** — `getPolicies` (`GET /policy` on
   `https://api.live.altr.com/v1/unified-policy/management/`). There is no idempotency key; creating
   twice creates two policies.
4. **Create the policy** — `createPolicy` (`POST /policy`), or `createPolicyWithRules`
   (`POST /policy/withRules`) to create the policy and its rules in one call.
5. **Attach rules** — `createRule` (`POST /policy/{policy_id}/rules`), one per role, each mapping a
   role and a tag value to a masking policy level in the **10000–10009** range. Batch edits go through
   `updateBatchRules` (`PATCH /policy/{policy_id}/rules/batch`).
6. **Verify** — `getPolicyById` (`GET /policy/{policy_id}`) and `getRules`
   (`GET /policy/{policy_id}/rules`). Policy ids take the form `TAG#<id>`.
7. **Amend or remove** — `updateRule` (`PATCH /policy/{policy_id}/rules/{rule_id}`),
   `deleteRule` (`DELETE …`), `deletePolicy` (`DELETE /policy/{policy_id}`).

## Rules
- **Snowflake tags and Databricks tags are different things.** A Snowflake tag is a first-class ALTR
  object with a `tag_group_id`. A Databricks tag is a raw string you pass into `createPolicy` together
  with `policy_type="PUSHDOWN"` and a `database_ids` list — see the Databricks skill.
- **Masking levels are 10000–10009**; the meaning of each level is documented at
  https://docs.altr.com/features/data-access-controls/data-masking/masking-types/
- No `Idempotency-Key`. Read before you write, and reconcile a `409` rather than retrying it.
