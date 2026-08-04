# Ocean Security

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
