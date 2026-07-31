# Ocean Security

Ocean Security (Ocean) is an AI-native, agentic email security platform that stops targeted,
AI-powered email attacks — phishing, business email compromise (BEC), impersonation, and financial
fraud — that surface-level detection tools miss. Its autonomous investigation engine, Ray, reviews
every inbound email in real time (sender, content, links, technical infrastructure, and business
context) to decide whether a message can be trusted, and pairs deep investigation with autonomous
SOC triage and real-time employee inbox guidance. Founded in Israel and backed by Lightspeed
Venture Partners.

Backed by: lightspeed-venture-partners

## API

Ocean publishes a stable **v1 REST API** for threat detection and security metrics.

- Developer portal / docs: https://docs.ocean.security/
- API reference: https://docs.ocean.security/api-reference/introduction
- Base URL: `https://api.ocean.security` (paths under `/api/v1/`)
- Auth: `X-Api-Key` header (static per-tenant API key)
- Trust Center: https://trust.ocean.security/

### Resource areas (20 operations)
- **Threats** — list recent threats, get by ID, get by Internet Message ID.
- **SONAR** — user-reported phishing: list/get reports, group by Internet Message ID, verdict
  aggregates, mean time to resolution.
- **Settings** — tenant allow/deny list entries (create, list, update, delete).
- **Metrics** — hours saved, financial loss prevented, protected inboxes, threats over time,
  top threat types / targeted entities / highlighted threats.

## Enriched artifacts (API Evangelist enrichment pipeline, 2026-07-20)

Assembled OpenAPI (`openapi/`), plus `authentication/`, `conventions/`, `errors/`, `lifecycle/`,
`conformance/`, `data-model/`, `agentic-access/`, `mcp/` (candidate), `overlays/`, `well-known/`,
`security/` (domain security), `llms/`, and four packaged Agent Skills under `skills/`.
