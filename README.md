# YourMembership (yourmembership)

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

YourMembership is an association management system (AMS) and membership management platform for professional associations, nonprofits, clubs, and other member-based organizations. It covers member records and profiles, dues and membership types, events and registration, online community, e-commerce/store, fundraising, an online career center (YMCareers job board), and learning. YourMembership is owned by **Community Brands** and now operates under **Momentive Software** (the Personify portfolio).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/yourmembership/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/yourmembership/refs/heads/main/apis.yml)

## Public API status

YourMembership **does** expose a documented developer API, but access is **license/partner gated** — this entry documents it honestly rather than as an open, self-serve API.

- **YM REST API** — base `https://ws.yourmembership.com`, OAuth-authenticated (via `POST /Ams/Authenticate`), with a Swagger UI (`/swagger-ui/`) and a metadata document (`/metadata`). Endpoints live under `/Ams`. Customers must **license the REST API** before an integration partner (e.g. Higher Logic) can connect, and the Swagger UI/metadata return **HTTP 403** to anonymous callers — so the full reference is not publicly enumerable.
- **Legacy XML API (v2.00)** — an XML/RPC API reached with a secret API key, described as available to customers at no additional cost. Community SDKs exist in Ruby ([ECHOInternational/your_membership](https://github.com/ECHOInternational/your_membership)) and PHP ([QuorumUS/ym-api](https://github.com/QuorumUS/ym-api)). Its method groups (Session/Auth, People/Profile, Events, system-admin exports, Store orders) are the most detailed public evidence of the data model.
- **YMCareers API** — a separate REST API for the job-board / career-center product, base `https://api.careerwebsite.com/v1`, JSON responses, authenticated with an `API_ACCESS_TOKEN` (15-minute) or a non-expiring `X-API-KEY`. Publicly documented at [api-doc.careerwebsite.com](https://api-doc.careerwebsite.com/); credentials are requested from `YMPartnerReps@momentivesoftware.com`.

**Confirmed endpoints:** `POST /Ams/Authenticate`, the `MemberProfile` endpoint (ReadContacts), and the `People` endpoint (ReadContact), plus the YMCareers resource areas. The **Events, Certifications, Content/Community, and Commerce/Sales** operations catalogued here are **honestly modeled** (`endpointsModeled: true`) from documented platform capability and the legacy XML API — they are not copied from a public spec, and exact paths/shapes will differ. Confirm against the licensed Swagger UI before building.

**WebSocket:** No documented public WebSocket (or SSE) API exists on any YourMembership surface. All documented APIs are request/response over HTTPS. See `review.yml`.

## Tags

- Membership Management
- Association Management
- AMS
- Nonprofit
- Events
- Careers
- Community Brands
- Momentive Software

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### YourMembership Members API

Read and manage member and contact records — member lists, profiles, account details, custom fields, membership types, and groups — via the REST `MemberProfile` and `People` endpoints under `/Ams`. OAuth-authenticated after `POST /Ams/Authenticate`. Requires licensing the REST API.

- **Human URL:** [https://www.yourmembership.com/api/](https://www.yourmembership.com/api/)
- **Base URL:** `https://ws.yourmembership.com`

### YourMembership Events API

Retrieve events, event details, and event registrations (the YM Events module). Grounded in the documented Events capability; specific REST paths are modeled.

- **Human URL:** [https://www.yourmembership.com/api/](https://www.yourmembership.com/api/)
- **Base URL:** `https://ws.yourmembership.com`

### YourMembership Certifications API

Track member certifications, credentials, and continuing-education (CE) credits tied to a member record. A standalone public certifications API is not separately documented, so this surface is honestly modeled.

- **Human URL:** [https://www.yourmembership.com/api/](https://www.yourmembership.com/api/)
- **Base URL:** `https://ws.yourmembership.com`

### YMCareers API

REST API for the YMCareers online career center / job board. JSON over `https://api.careerwebsite.com/v1`, authenticated with an `API_ACCESS_TOKEN` (15-minute) or non-expiring `X-API-KEY`. Covers job search, lead generation, location autocomplete, job-seeker activity (resume uploads, applications, job alerts), recruiter registration, and event reporting.

- **Human URL:** [https://api-doc.careerwebsite.com/](https://api-doc.careerwebsite.com/)
- **Base URL:** `https://api.careerwebsite.com/v1`

### YourMembership Content and Community API

Access online-community and content constructs — groups/subgroups, member messaging (in-box, read/unread status), journals/content, and media. Grounded in documented community/messaging capability; specific REST paths are modeled.

- **Human URL:** [https://www.yourmembership.com/api/](https://www.yourmembership.com/api/)
- **Base URL:** `https://ws.yourmembership.com`

### YourMembership Commerce and Sales API

Retrieve e-commerce and financial data — YM Store orders and status (open, processed, shipped, closed, cancelled), transactions, dues payments, and donation/fundraising exports. Grounded in the documented store-order and system-admin export calls of the legacy XML API; REST paths are modeled.

- **Human URL:** [https://www.yourmembership.com/api/](https://www.yourmembership.com/api/)
- **Base URL:** `https://ws.yourmembership.com`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/yourmembership)
- [Website](https://www.yourmembership.com)
- [Documentation](https://www.yourmembership.com/api/)
- [Plans](plans/yourmembership-plans-pricing.yml)
- [Rate Limits](rate-limits/yourmembership-rate-limits.yml)
- [Fin Ops](finops/yourmembership-finops.yml)

## Pricing

YourMembership does not publish list pricing; it is sold as an annual, quote-based SaaS subscription through sales. Third-party reviews estimate roughly $3,000–$20,000/year plus one-time implementation (~$2,000–$5,000) and optional add-ons. The developer API is not a standalone metered product: the XML API is included for customers, the REST API is a licensed capability, and the YMCareers API is bundled with the YMCareers product. See `plans/yourmembership-plans-pricing.yml`.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
