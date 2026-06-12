# Geotab (geotab)

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
