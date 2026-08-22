# Geotab (geotab)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Geotab is a fleet telematics platform providing the MyGeotab SDK and REST API for vehicle tracking, driver behavior monitoring, fuel management, ELD compliance, and route optimization. The MyGeotab API uses JSON-RPC 2.0 over HTTPS with session-token authentication, exposing a single versioned endpoint at /apiv1 that supports Get, Add, Set, and Remove operations across all fleet entities including devices, trips, fault data, and status data. The MyAdmin API provides reseller and partner access to manage databases, orders, and provisioning. Native SDK clients are available for JavaScript, .NET, Java, and Python, and the full SDK and sample code are published on GitHub.

APIs.json: https://raw.githubusercontent.com/api-evangelist/geotab/refs/heads/main/apis.yml

Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=geotab-api-evangelist&utm_content=repo

## Tags

- Fleet Management
- Telematics
- Vehicle Tracking
- ELD Compliance
- Driver Behavior
- Fuel Monitoring
- Route Optimization
- GPS Tracking
- IoT

## APIs

### MyGeotab API

The MyGeotab API provides JSON-RPC 2.0 access to all fleet telematics data including vehicle location, trip history, driver behavior, fault codes, fuel usage, HOS/ELD compliance records, and sensor data. It supports GetFeed for real-time data streaming and batch retrieval operations.

- Documentation: https://developers.geotab.com/myGeotab/introduction/
- API Reference: https://geotab.github.io/sdk/software/api/reference/
- Base URL: https://my.geotab.com/apiv1

### MyAdmin API

The MyAdmin API provides reseller and partner access to Geotab's administrative platform for managing databases, device provisioning, orders, billing, and account management. Access requires a MyAdmin account with the MyAdminApiUser role.

- Documentation: https://developers.geotab.com/myAdmin/introduction/index.html
- Rate Limits Guide: https://developers.geotab.com/myAdmin/guides/rateLimits/
- Base URL: https://myadmin.geotab.com/v2/MyAdminApi.ashx

## Plans / Rate Limits / FinOps

### Plans

Geotab offers two software plans sold through authorized resellers on a per-vehicle-per-month basis:

- **GO Core Plan** ($20-$30/vehicle/month): Real-time GPS tracking, trip history, exception alerts, basic routing, maintenance scheduling, basic IFTA, asset inspections, and MyGeotab API access.
- **GO Plan** ($30-$40/vehicle/month): Everything in GO Core plus advanced ELD/HOS compliance, AI safety scoring, predictive maintenance, full fuel monitoring, EV analytics, emissions reporting, and video telematics.

Hardware (GO telematics device) starts at approximately $130 per device (one-time).

Full details: [plans/geotab-plans-pricing.yml](plans/geotab-plans-pricing.yml)

### Rate Limits

**MyGeotab API:**
- Authenticate: 10 requests/minute per user+database
- GetFeed: 1 request/second per entity type per user+database
- Get results: 50,000 records per request maximum
- Responses over 500 MB trigger an Over Limit Error
- Rate limit headers: `X-Rate-Limit-Limit`, `X-Rate-Limit-Remaining`, `X-Rate-Limit-Reset`
- HTTP 429 with `Retry-After` header on exceeded limits

**MyAdmin API:**
- Global per-IP: 10,000 requests per 10 minutes
- Default: 5,000 requests/minute and 100,000 requests/hour
- /v2/MyAdminApi.ashx: 375/minute, 22,000/hour
- Data methods: 150,000 records/minute per method
- HTTP 429 on rate limit exceeded

Full details: [rate-limits/geotab-rate-limits.yml](rate-limits/geotab-rate-limits.yml)

### FinOps

Geotab uses a per-vehicle-per-month subscription model. The primary billing dimension is the count of active enrolled vehicles. Hardware is a one-time per-device cost. API calls are not billed separately and are included in the subscription. Enterprise fleets should negotiate volume pricing with authorized resellers.

Full details: [finops/geotab-finops.yml](finops/geotab-finops.yml)

## Timestamps

- Created: 2026-06-12
- Modified: 2026-06-12

## Common Properties

| Type | URL |
|------|-----|
| Website | https://www.geotab.com/ |
| Documentation | https://developers.geotab.com/ |
| GitHub Organization | https://github.com/Geotab |
| LinkedIn | https://www.linkedin.com/company/geotab |
| X | https://x.com/geotab |
| Blog | https://www.geotab.com/blog/ |
| Pricing | https://www.geotab.com/software-packages/ |

## Maintainers

- Kin Lane / kin@apievangelist.com
