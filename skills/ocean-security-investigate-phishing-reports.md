---
name: Investigate SONAR phishing reports
description: Review user-reported phishing (SONAR), drill into individual reports, and track verdict mix and resolution time.
api: openapi/ocean-security-openapi.yml
operations: [listPhishingReports, getPhishingReportById, getPhishingReportsByOriginalEmailInternetMessageId, getAggregatedVerdicts, getPhishingReportsMttr]
---

# Investigate SONAR phishing reports

Work with Ocean Security SONAR — the surface for employee-reported phishing.

## Auth
- `X-Api-Key: <tenant-api-key>` header. Base URL: `https://api.ocean.security`.

## Steps
1. **List reports** — `listPhishingReports` (`GET /api/v1/sonar/phishing-reports`). Bound with
   `minutes_ago` (default 30 days) and page with `page`.
2. **Open a report** — `getPhishingReportById` (`GET /api/v1/sonar/phishing-reports/{id}`) returns a
   `PhishingReportItem`: `subject`, `sender`, `reporter`, `reasoning`, `verdict`, `report_date`, and
   the two Internet Message IDs (`original_email_internet_message_id`, `report_internet_message_id`).
   `verdict` is one of `unknown|spam|malicious|safe|allowed|denied|simulation|graymail|no_analysis`.
3. **Group by original email** — `getPhishingReportsByOriginalEmailInternetMessageId`
   (`GET /api/v1/sonar/phishing-reports/by_original_email_internet_message_id/{internet_message_id}`)
   returns every report of the same original email (multiple users may report it).
4. **Measure the queue** — `getAggregatedVerdicts`
   (`GET /api/v1/sonar/phishing-reports/aggs/verdicts`) for counts by verdict, and
   `getPhishingReportsMttr` (`GET /api/v1/sonar/phishing-reports/aggs/mttr`) for average
   analysis time in seconds.

## Conventions & errors
- Cross-reference a report to detected threats via Internet Message ID (see
  `data-model/ocean-security-data-model.yml`).
- Error envelope `{"error": "<message>"}`; see `errors/ocean-security-problem-types.yml`.
