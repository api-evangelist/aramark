---
name: aramark-resolve-org-scope
description: Resolve which parts of the Aramark organization hierarchy your Marko API key can see, and turn that into the org_value identifiers every other Marko API needs.
api: Aramark Marko Platform
generated: '2026-09-04'
method: generated
source: openapi/aramark-profile-user-openapi.json, openapi/aramark-organization-hierarchy-openapi.json, openapi/aramark-organization-hierarchy-v2-openapi.json, openapi/aramark-organization-profit-center-core-details-openapi.json
operations:
  - getMyRole
  - getMyHierarchy
  - getMyProfitCenters
  - getMyDistricts
  - getMyRegions
  - getMyLocations
  - getMyClients
  - getFinancialHierarchy
  - getFinancialFlatHierarchyV2
  - getProfitCenterDetailsCoreByOrgValue
---

# Resolve your Aramark org scope

Almost every Marko operation is parameterised by `org_value` — a single identifier that names one node of the Aramark organization hierarchy (division, region, district, line of business, business unit, client, location, sub location, profit center). You cannot read labor, POS, revenue or waste figures without one, and the values you are allowed to use depend on the key you hold. Do this first.

## Before you start

- Every request needs the `apikey` header. Keys are issued per registered application on the Marko Developer Portal after an approval step.
- Production base hosts differ per API. This flow touches three: `https://marko.aramark.net/v1/profile/user`, `https://marko.aramark.net/v1/organization/hierarchy`, and `https://marko.aramark.net/v2/organization`.
- Every response is `{"status": "Success" | "Error" | "Not Found", "count": n, "<collection>": [...]}`. Check `status` — an application error arrives inside an HTTP 200.

## Steps

1. **Find out who you are.** `getMyRole` (`GET /v1/profile/user/my_role`). The role determines which levels of the hierarchy the rest of this flow will return.
2. **Get the scope in one call.** `getMyHierarchy` (`GET /v1/profile/user/my_hierarchy`) returns the hierarchy your key is entitled to.
3. **Narrow to the level you actually need.** Use whichever matches your question:
   - `getMyClients` (`GET /v1/profile/user/my_clients`)
   - `getMyRegions` (`GET /v1/profile/user/my_regions`)
   - `getMyDistricts` (`GET /v1/profile/user/my_districts`)
   - `getMyLocations` (`GET /v1/profile/user/my_locations`)
   - `getMyProfitCenters` (`GET /v1/profile/user/my_profit_centers`)
4. **Walk the financial hierarchy from a known node.** `getFinancialHierarchy` (`GET /v1/organization/hierarchy/financial/{org_value}`). Prefer the v2 contract, `getFinancialFlatHierarchyV2` (`GET /v2/organization/hierarchy/flat/financial/{org_value}`), when you want a flat list and both new and legacy org values in one response.
5. **Confirm the node before you use it.** `getProfitCenterDetailsCoreByOrgValue` (`GET /v1/organization/profit_center/core/{org_value}`) returns the core attributes of a profit center so you can verify you are pointed at the site you meant.

## Rules

- Send `bypass-cache: true` when you need the current hierarchy rather than the cached one — this matters after a reorganisation.
- A 401 comes back as an Apigee fault, not the Marko envelope: `{"fault":{"faultstring":"Failed to resolve API Key variable request.header.apikey","detail":{"errorcode":"steps.oauth.v2.FailedToResolveAPIKey"}}}`. That means the header is missing or the key is not provisioned for this API product, not that the org_value is wrong.
- A 404 whose body says `messaging.adaptors.http.flow.ApplicationNotFound` means the gateway has no proxy at that path — the API product is not routed in production. It is not a data-not-found answer.
- These are all reads. Nothing in this flow mutates state.
