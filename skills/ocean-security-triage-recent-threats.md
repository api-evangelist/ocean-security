---
name: Triage recent email threats
description: Pull recent detected email threats from Ocean Security and drill into individual threats for SOC triage.
api: openapi/ocean-security-openapi.yml
operations: [listRecentThreats, getThreatById, getThreatsByInternetMessageId]
---

# Triage recent email threats

Use the Ocean Security API to review detected email threats and investigate individual attacks.

## Auth
- Every request requires the `X-Api-Key: <tenant-api-key>` header. There is no OAuth; the key is a
  static per-tenant secret — never expose it client-side.
- Base URL: `https://api.ocean.security` (all paths under `/api/v1/`).

## Steps
1. **List recent threats** — call `listRecentThreats` (`GET /api/v1/threats`). Bound the window with
   `minutes_ago` (default 7 days) and page with `page`. The response is the paginated envelope
   `{status, pagination:{page,page_size,total}, results:{items:[...]}}`.
2. **Inspect a threat** — for any item, call `getThreatById` (`GET /api/v1/threats/{id}`) to get the
   full `ThreatItem`: `subject`, `sender_email`/`sender_name`, `recipient_email`, `threat_type`,
   `source`, `detection_time`, `remediation_time`, and `threat_indicators[]`.
3. **Correlate by email** — when you have an Internet Message ID, call
   `getThreatsByInternetMessageId` (`GET /api/v1/threats/by_internet_message_id/{id}`) to find all
   threats sharing that message.

## Conventions & errors
- Pagination and time-window rules: see `conventions/ocean-security-conventions.yml`.
- Errors are `{"error": "<message>"}`; handle `401` (bad/missing key), `404` (unknown id), `400`
  (bad params), `500`. See `errors/ocean-security-problem-types.yml`.
- No idempotency keys and no webhooks — poll `listRecentThreats` on an interval to detect new threats.
