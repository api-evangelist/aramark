---
name: aramark-daily-operations-snapshot
description: Pull an intra-day operating picture for one Aramark site — revenue, performance, POS sales, labor and food waste — from the Marko APIs, all keyed on a single org_value.
api: Aramark Marko Platform
generated: '2026-09-04'
method: generated
source: openapi/aramark-operational-daily-openapi.json, openapi/aramark-pos-daily-sales-openapi.json, openapi/aramark-labor-daily-openapi.json, openapi/aramark-daily-food-waste-tracking-openapi.json, openapi/aramark-financial-daily-account-summary-openapi.json
operations:
  - getRevenueSnapshot
  - getPerformanceSnapshotByOrgValue
  - getDailySalesByOrgValue
  - getDailySelfServiceSalesByOrgValue
  - getDailyLaborSummary
  - getDailyLaborForecast
  - getDailyFoodWasteByOrgValue
  - getFinancialSummaryByOrgValue
---

# Daily operations snapshot for one Aramark site

Assembles the numbers a district or profit-center manager looks at during the day. Each call is a separate Marko API with its own base path, but they all take the same `org_value`.

## Before you start

Resolve `org_value` first — see `aramark-resolve-org-scope`. Every call needs the `apikey` header.

## Steps

1. **Revenue so far today.** `getRevenueSnapshot` — `GET https://marko.aramark.net/v1/operational/daily/revenue/snapshot/{org_value}`.
2. **Performance against plan.** `getPerformanceSnapshotByOrgValue` — `GET https://marko.aramark.net/v1/operational/daily/performance/snapshot/{org_value}`.
3. **Point-of-sale sales.** `getDailySalesByOrgValue` — `GET https://marko.aramark.net/v1/pos/daily/sales/{org_value}`. For unattended and kiosk revenue call `getDailySelfServiceSalesByOrgValue` — `GET https://marko.aramark.net/v1/pos/daily/self_service/{org_value}`.
4. **Labor.** `getDailyLaborSummary` — `GET https://marko.aramark.net/v1/labor/daily/summary/{org_value}` — and `getDailyLaborForecast` — `GET https://marko.aramark.net/v1/labor/daily/forecast/{org_value}` — to compare actual against forecast.
5. **Food waste.** `getDailyFoodWasteByOrgValue` — `GET https://marko.aramark.net/v1/service/daily/food_waste/{org_value}`.
6. **Close the day against the ledger.** `getFinancialSummaryByOrgValue` — `GET https://marko.aramark.net/v1/financial/daily/account_summary/{org_value}` — the GFF daily summary.

## Rules

- Send `bypass-cache: true` on the snapshot calls. These are intra-day figures and a cached read defeats the purpose.
- Read `status` on every response. `count` tells you how many records came back; `Not Found` inside a 200 means the site reported nothing for that day, which is different from an error.
- Marko publishes no rate limits and no rate-limit response headers. Poll conservatively and back off on any non-200 rather than relying on a documented retry signal, because there is none.
- All reads. Nothing here writes.
