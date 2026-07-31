---
name: Manage the tenant allow/deny list
description: Add, list, update, and remove domain/IP/email entries on the Ocean Security tenant allow or deny list.
api: openapi/ocean-security-openapi.yml
operations: [listAllowDenyEntries, createAllowDenyEntry, updateAllowDenyEntry, deleteAllowDenyEntry]
---

# Manage the tenant allow/deny list

Curate the policy entries that allow or block senders for your Ocean Security tenant.

## Auth
- `X-Api-Key: <tenant-api-key>` header on every request. The acting key is recorded in the audit log.
- Base URL: `https://api.ocean.security`.

## Steps
1. **List entries** — `listAllowDenyEntries` (`GET /api/v1/settings/allow_deny_entries`). The `list`
   query param is required (`allow` | `deny`); page with `page` / `page_size` (default 50, max 200)
   and filter identifiers with `q`.
2. **Create an entry** — `createAllowDenyEntry` (`POST /api/v1/settings/allow_deny_entries`) with body
   `{entry_type, list, value, verdict_scope?, comment?}`. `entry_type` is `domain|ip|email_address`,
   `list` is `allow|deny`, `verdict_scope` is `global|graymail`. A duplicate or opposite-list
   collision returns `409`.
3. **Update an entry** — `updateAllowDenyEntry` (`PATCH /api/v1/settings/allow_deny_entries/{id}`).
   Only `list`, `verdict_scope`, and `comment` are mutable; omitted fields are unchanged.
4. **Delete an entry** — `deleteAllowDenyEntry` (`DELETE /api/v1/settings/allow_deny_entries/{id}`).
   The entry must belong to the caller's tenant.

## Conventions & errors
- No idempotency key: creating the same entry twice yields `409`, not a silent no-op — check for the
  entry first if you need idempotent behavior. See `conventions/ocean-security-conventions.yml`.
- Error envelope `{"error": "<message>"}`; see `errors/ocean-security-problem-types.yml`.
