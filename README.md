# Aramark (aramark)

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


Aramark is a Fortune 500 food, facilities and uniform services company. Its Marko platform is a data and AI layer over Aramark operations, published as 60 documented REST APIs on an Apigee gateway at marko.aramark.net and catalogued on the Marko Developer Portal. The surface spans the full Aramark organization hierarchy (division, region, district, line of business, business unit, client, location, sub location, profit center), point-of-sale transactions and daily sales, labor scheduling and daily labor, inventory and purchasing, product, recipe and nutrition data, service execution, food waste and IoT temperature monitoring. Aramark publishes every OpenAPI document itself, in JSON and YAML, in the public aramarkservicesinc/markoapis GitHub repository, and renders each one in an in-page RapiDoc console. Access is gated: you register an application, choose API products, and a per-application apikey is issued on approval.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/aramark/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/aramark/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **APIs profiled:** 60
- **Documented operations:** 216 across 191 paths
- **Contract source:** Aramark publishes every OpenAPI itself at [github.com/aramarkservicesinc/markoapis](https://github.com/aramarkservicesinc/markoapis) and renders each one on its own portal page. All 60 specs in `openapi/` are verbatim harvests; `openapi/_original/` holds the untouched bytes.
- **Production gateway:** `https://marko.aramark.net` (Apigee). Probed 2026-09-04: 43 of the 60 documented production base paths answered HTTP 401 `steps.oauth.v2.FailedToResolveAPIKey` (proxy live, key required); 17 answered HTTP 404 `ApplicationNotFound` (documented but not routed in production) — see `lifecycle/aramark-lifecycle.yml`.
- **Authentication:** `apikey` request header, issued per registered application after portal approval.

## Tags

- Food Services
- Facilities Management
- Uniform Services
- Data Platform
- Point of Sale
- Labor
- Inventory
- Recipes and Nutrition
- Organization Hierarchy
- Fortune 500
- Apigee
- Hospitality

## Timestamps

- **Created:** 2026-03-26
- **Modified:** 2026-09-04

## APIs

| API | Docs | Production base | Ops |
|---|---|---|---|
| Aramark Marko Alerts | [docs](https://marko-developers.aramark.net/doc/alerts) | `https://marko.aramark.net/v1/alerts` | 4 |
| Aramark Marko Ask Marko | [docs](https://marko-developers.aramark.net/doc/ask-marko) | `https://marko.aramark.net/v1/ask` | 1 |
| Aramark Marko Business Unit Core Details | [docs](https://marko-developers.aramark.net/doc/business-unit-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Calendar | [docs](https://marko-developers.aramark.net/doc/calendar) | `https://marko.aramark.net/v1` | 3 |
| Aramark Marko Catering | [docs](https://marko-developers.aramark.net/doc/catering) | `https://marko.aramark.net/v1/catering` | 1 |
| Aramark Marko Daily Food Waste Tracking | [docs](https://marko-developers.aramark.net/doc/daily-food-waste-tracking) | `https://marko.aramark.net/v1/service/daily` | 2 |
| Aramark Marko District Core Details | [docs](https://marko-developers.aramark.net/doc/district-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Division Core Details | [docs](https://marko-developers.aramark.net/doc/division-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Financial Daily Account Summary | [docs](https://marko-developers.aramark.net/doc/financial-daily-account-summary) | `https://marko.aramark.net/v1/financial/daily` | 1 |
| Aramark Marko Growth | [docs](https://marko-developers.aramark.net/doc/growth) | `https://marko.aramark.net/v1/growth` | 1 |
| Aramark Marko GSC GPO | [docs](https://marko-developers.aramark.net/doc/gsc-gpo-0) | `https://marko.aramark.net/v1/gsc_gpo` | 1 |
| Aramark Marko Inventory | [docs](https://marko-developers.aramark.net/doc/inventory) | `https://marko.aramark.net/v1/inventory` | 6 |
| Aramark Marko IoT | [docs](https://marko-developers.aramark.net/doc/iot) | `https://marko.aramark.net/v1/iot` | 2 |
| Aramark Marko Labor Daily | [docs](https://marko-developers.aramark.net/doc/labor-daily) | `https://marko.aramark.net/v1/labor/daily` | 4 |
| Aramark Marko Labor Employee | [docs](https://marko-developers.aramark.net/doc/labor-employee) | `https://marko.aramark.net/v1/labor/employee` | 4 |
| Aramark Marko Labor Manager Employees | [docs](https://marko-developers.aramark.net/doc/labor-manager-employees) | `https://marko.aramark.net/v1/labor/manager` | 1 |
| Aramark Marko Labor Schedule | [docs](https://marko-developers.aramark.net/doc/labor-schedule) | `https://marko.aramark.net/v1/labor/schedule` | 2 |
| Aramark Marko Line of Business Core Details | [docs](https://marko-developers.aramark.net/doc/line-business-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Location Core Details | [docs](https://marko-developers.aramark.net/doc/location-core-details) | `https://marko.aramark.net/v1/organization` | 6 |
| Aramark Marko Marko Users | [docs](https://marko-developers.aramark.net/doc/marko-users) | `https://marko.aramark.net/v1/marko` |  |
| Aramark Marko Operational Daily | [docs](https://marko-developers.aramark.net/doc/operational-daily) | `https://marko.aramark.net/v1/operational/daily` | 2 |
| Aramark Marko Organization | [docs](https://marko-developers.aramark.net/doc/organization) | `https://marko.aramark.net/v1` | 3 |
| Aramark Marko Organization Brands | [docs](https://marko-developers.aramark.net/doc/organization-brands) | `https://marko.aramark.net/v1/organization` | 1 |
| Aramark Marko Organization Clients | [docs](https://marko-developers.aramark.net/doc/organization-clients) | `https://marko.aramark.net/v1/organization` | 1 |
| Aramark Marko Organization Hierarchy | [docs](https://marko-developers.aramark.net/doc/organization-hierarchy) | `https://marko.aramark.net/v1/organization/hierarchy` | 1 |
| Aramark Marko Organization Hierarchy V2 | [docs](https://marko-developers.aramark.net/doc/organization-hierarchy-v2) | `https://marko.aramark.net/v2/organization` | 1 |
| Aramark Marko Organization Profit Center Core Details | [docs](https://marko-developers.aramark.net/doc/organization-profit-center-core-details) | `https://marko.aramark.net/v1/organization` | 10 |
| Aramark Marko Organization Suppliers | [docs](https://marko-developers.aramark.net/doc/organization-suppliers) | `https://qa-marko.aramark.net/v1/organization` | 1 |
| Aramark Marko Point of Sale | [docs](https://marko-developers.aramark.net/doc/point-sale) | `https://marko.aramark.net/v1/pos` | 9 |
| Aramark Marko POS Daily Product Ranking | [docs](https://marko-developers.aramark.net/doc/pos-daily-product-ranking) | `https://marko.aramark.net/v1/pos/daily/product` | 2 |
| Aramark Marko POS Daily Sales | [docs](https://marko-developers.aramark.net/doc/pos-daily-sales) | `https://marko.aramark.net/v1/pos/daily` | 2 |
| Aramark Marko POS Items | [docs](https://marko-developers.aramark.net/doc/pos-items) | `https://marko.aramark.net/v1/pos` | 1 |
| Aramark Marko POS Transactions | [docs](https://marko-developers.aramark.net/doc/pos-transactions) | `https://marko.aramark.net/v1/pos` | 11 |
| Aramark Marko Product | [docs](https://marko-developers.aramark.net/doc/product) | `https://qa-marko.aramark.net/v1` | 9 |
| Aramark Marko Product Recipe | [docs](https://marko-developers.aramark.net/doc/product-recipe) | `https://marko.aramark.net/v1/product/recipe` | 2 |
| Aramark Marko Product Items | [docs](https://marko-developers.aramark.net/doc/product-retail-items) | `https://qa-marko.aramark.net/v1/product` | 6 |
| Aramark Marko Profile App | [docs](https://marko-developers.aramark.net/doc/profile-app) | `https://marko.aramark.net/v1/profile/app` | 2 |
| Aramark Marko Profile User | [docs](https://marko-developers.aramark.net/doc/profile-user) | `https://marko.aramark.net/v1/profile/user` | 7 |
| Aramark Marko Recipe Decorations | [docs](https://marko-developers.aramark.net/doc/recipe-decorations) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Region Core Details | [docs](https://marko-developers.aramark.net/doc/region-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Security | [docs](https://marko-developers.aramark.net/doc/security) | `https://marko.aramark.net/v1/security` | 2 |
| Aramark Marko Service | [docs](https://marko-developers.aramark.net/doc/service) | `https://marko.aramark.net/v1/service` | 39 |
| Aramark Marko Service Areas | [docs](https://marko-developers.aramark.net/doc/service-areas) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Service Areas V2 | [docs](https://marko-developers.aramark.net/doc/service-areas-v2) | `https://marko.aramark.net/v2` | 2 |
| Aramark Marko Service Inventory | [docs](https://marko-developers.aramark.net/doc/service-inventory) | `https://marko.aramark.net/v1/service` | 3 |
| Aramark Marko Service Meal Periods | [docs](https://marko-developers.aramark.net/doc/service-meal-periods) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Service Menu Items | [docs](https://marko-developers.aramark.net/doc/service-menu-items) | `https://marko.aramark.net/v1/service_menu_items` | 2 |
| Aramark Marko Service Menus | [docs](https://marko-developers.aramark.net/doc/service-menus) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Service Production Areas | [docs](https://marko-developers.aramark.net/doc/service-production-areas) | `https://marko.aramark.net/v1/service` | 1 |
| Aramark Marko Service Production Departments | [docs](https://marko-developers.aramark.net/doc/service-production-departments) | `https://marko.aramark.net/v1/service` | 1 |
| Aramark Marko Service Recipe | [docs](https://marko-developers.aramark.net/doc/service-recipe) | `https://marko.aramark.net/v1/service` | 2 |
| Aramark Marko Service Recipes V2 | [docs](https://marko-developers.aramark.net/doc/service-recipes-v2) | `https://marko.aramark.net/v2/service/recipe` | 2 |
| Aramark Marko Service Results | [docs](https://marko-developers.aramark.net/doc/service-results) | `https://marko.aramark.net/v1/service` | 2 |
| Aramark Marko Service V3 | [docs](https://marko-developers.aramark.net/doc/service-v3) | `https://marko.aramark.net/v3/service` | 2 |
| Aramark Marko Service Weekly Overproduction | [docs](https://marko-developers.aramark.net/doc/service-weekly-overproduction) | `https://marko.aramark.net/v1/service/weekly` | 2 |
| Aramark Marko Sites | [docs](https://marko-developers.aramark.net/doc/sites) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Sub Location Core Details | [docs](https://marko-developers.aramark.net/doc/sub-location-core-details) | `https://marko.aramark.net/v1/organization` | 4 |
| Aramark Marko Sub Locations | [docs](https://marko-developers.aramark.net/doc/sub-locations) | `https://marko.aramark.net/v1` | 1 |
| Aramark Marko Units of Measure | [docs](https://marko-developers.aramark.net/doc/units-measure) | `https://marko.aramark.net/v1/recipe` | 1 |
| Aramark Marko Vendor | [docs](https://marko-developers.aramark.net/doc/vendor) | `https://qa-marko.aramark.net/v1` | 1 |

## Artifacts

| Artifact | Method | What it records |
|---|---|---|
| `openapi/` (60 + `_original/`) | searched | Verbatim first-party OpenAPI 3.0/3.0.1 and Swagger 2.0 contracts. |
| `overlays/` (60) | generated | OpenAPI Overlay 1.0.0 adding the production server each contract names in prose but omits from `servers[]`, plus the harvest and probe record. |
| `authentication/` | searched | apikey header scheme, the portal approval flow, and the live 401 that proves enforcement. |
| `conventions/` | derived | Response envelope, `bypass-cache`, pagination, idempotency (`none`) and reversibility (`documented`). |
| `errors/` | derived | Two distinct error envelopes — the Apigee fault and the in-200 `status` field. |
| `data-model/` | derived | 222 entities, 76 relationships, and the `org_value` pivot the whole platform turns on. |
| `lifecycle/` | probed | URI versioning across v1/v2/v3, no deprecation policy, and the production availability probe. |
| `conformance/` | derived | What the contracts do and do not conform to; no domain standard is declared and none exists to declare. |
| `sandbox/` | searched | The in-page RapiDoc console and the published qa/dev hosts. |
| `skills/` (4) | generated | Packaged Agent Skills grounded in real operationIds. |
| `llms/` | generated | llms.txt for the whole platform. |
| `well-known/` | probed | Every `/.well-known/` path on five hosts — all 404. No pointer is emitted for an absence. |
| `mcp/` | derived | A candidate tool list only. Aramark ships no MCP server, so this is wired as `X-MCPServerCandidate`, not `MCPServer`. |
| `packages/` | searched | No first-party SDK exists in any registry — an honest zero. |
| `plans/`, `rate-limits/` | searched | Nothing published. Recorded as `plan_count: 0` and `limit_count: 0` with the URLs that were checked. |
| `security/` | probed | TLS, HSTS, SPF and DMARC across three hosts. No security.txt, no bug bounty, no trust center. |

## Common Properties

- [DeveloperPortal](https://marko-developers.aramark.net/)
- [Portal](https://marko-developers.aramark.net/)
- [Documentation](https://marko-developers.aramark.net/catalog)
- [APIReference](https://marko-developers.aramark.net/catalog)
- [GettingStarted](https://marko-developers.aramark.net/faqs)
- [FAQ](https://marko-developers.aramark.net/faqs)
- [SignUp](https://marko-developers.aramark.net/user/register)
- [Login](https://marko-developers.aramark.net/user/login)
- [Blog](https://marko-developers.aramark.net/blog)
- [GitHubOrganization](https://github.com/aramarkservicesinc)
- [SourceCode](https://github.com/aramarkservicesinc/markoapis)
- [Support](https://www.aramark.com/contact-us)
- [TermsOfService](https://www.aramark.com/terms-conditions)
- [PrivacyPolicy](https://www.aramark.com/privacy-policy)
- [LinkedIn](https://www.linkedin.com/company/aramark)
- [Website](https://www.aramark.com/)
- [AgenticAccess](agentic-access/aramark-agentic-access.yml)
- [DomainSecurity](security/aramark-domain-security.yml)
- [Authentication](authentication/aramark-authentication.yml)
- [APIKeys](authentication/aramark-authentication.yml)
- [Conventions](conventions/aramark-conventions.yml)
- [ErrorCatalog](errors/aramark-problem-types.yml)
- [DataModel](data-model/aramark-data-model.yml)
- [Lifecycle](lifecycle/aramark-lifecycle.yml)
- [Conformance](conformance/aramark-conformance.yml)
- [Sandbox](sandbox/aramark-sandbox.yml)
- [Console](sandbox/aramark-sandbox.yml)
- [Packages](packages/aramark-packages.yml)
- [X-MCPServerCandidate](mcp/aramark-mcp.yml)
- [AgentSkill](skills/_index.yml)
- [LLMsTxt](llms/aramark-llms.txt)
- [RateLimits](rate-limits/aramark-rate-limits.yml)
- [Plans](plans/aramark-plans-pricing.yml)
- [FinOps](finops/aramark-finops.yml)
- [Examples](examples/)
- [SpectralRules](https://raw.githubusercontent.com/api-evangelist/aramark/refs/heads/main/rules/aramark-spectral-rules.yml)
- [Vocabulary](https://raw.githubusercontent.com/api-evangelist/aramark/refs/heads/main/vocabulary/aramark-vocabulary.yaml)
- [JSONLD](https://raw.githubusercontent.com/api-evangelist/aramark/refs/heads/main/json-ld/aramark-marko-api-context.jsonld)
- [Overlay](overlays/)

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
