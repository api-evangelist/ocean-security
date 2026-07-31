---
name: Report security ROI and posture metrics
description: Pull Ocean Security ROI and posture metrics — hours saved, financial loss prevented, protected inboxes, threat trends, and top threats/targets.
api: openapi/ocean-security-openapi.yml
operations: [getHoursSavedMetric, getPreventedFinancialLoss, getProtectedInboxesCount, getThreatsOverTime, getTopThreatTypes, getTopTargetedEntities, getTopHighlightedThreats]
---

# Report security ROI and posture metrics

Assemble an executive email-security scorecard from the Ocean Security Metrics API.

## Auth
- `X-Api-Key: <tenant-api-key>` header. Base URL: `https://api.ocean.security`.
- All metrics endpoints accept a `days_ago` query param (default 30).

## Steps
1. **ROI figures**
   - `getHoursSavedMetric` (`GET /api/v1/metrics/hours_saved`) → estimated analyst hours saved.
   - `getPreventedFinancialLoss` (`GET /api/v1/metrics/prevented_loss`) → estimated USD loss prevented.
   - `getProtectedInboxesCount` (`GET /api/v1/metrics/protected_inboxes`) → unique protected inboxes.
2. **Trend**
   - `getThreatsOverTime` (`GET /api/v1/metrics/threats_over_time`) → threat counts grouped by day.
3. **Top lists (each returns top 5)**
   - `getTopThreatTypes` (`GET /api/v1/metrics/top_threat_types`).
   - `getTopTargetedEntities` (`GET /api/v1/metrics/top_targeted_entities`) → most-targeted users/groups.
   - `getTopHighlightedThreats` (`GET /api/v1/metrics/highlighted_threats`).

## Conventions & errors
- Metrics responses use the `{status, results}` envelope (non-paginated). See
  `conventions/ocean-security-conventions.yml`.
- Error envelope `{"error": "<message>"}`; see `errors/ocean-security-problem-types.yml`.
