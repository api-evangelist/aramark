---
name: aramark-record-service-execution
description: Write service-execution data back to Aramark Marko — customer counts, equipment and prep temperatures, waste and photos — and know which of those writes can be taken back.
api: Aramark Marko Platform
generated: '2026-09-04'
method: generated
source: openapi/aramark-service-openapi.json, openapi/aramark-service-results-openapi.json, conventions/aramark-conventions.yml
operations:
  - getCustomerCount
  - putCustomerCount
  - getEquipment
  - putEquipmentTemperature
  - getTemperaturePrep
  - putTemperaturePrep
  - getTemperatureCooling
  - putTemperatureCooling
  - getWasteResults
  - putResultsWaste
  - deleteResultsWaste
  - getPhotos
  - putPhotos
  - deletePhotos
  - putServiceResult
  - putServiceResults
---

# Record service execution in Marko

The Service API is the only substantial write surface Marko publishes: 41 of its 216 documented operations mutate state, and most of them live here. Read this section before writing anything, because the platform gives you almost no safety net.

## What you do not get

- **No idempotency.** There is no `Idempotency-Key` header, no client-supplied request id, and no replay-protection language anywhere in the 60 published contracts. A retried write is a second write.
- **No dry run.** There is no preview or validate-only mode.
- **No stated reversal window.** Some writes have a delete; none of them publishes how long you have. Do not assume one.

## Steps

1. **Read the current value first.** Every write here has a matching read: `getCustomerCount`, `getEquipment`, `getTemperaturePrep`, `getTemperatureCooling`, `getWasteResults`, `getPhotos`. Because there is no idempotency key, the read is your only way to tell a lost response from a write that did not happen.
2. **Write.**
   - Customer count: `putCustomerCount` — `PUT https://marko.aramark.net/v1/service/customer/count`
   - Equipment temperature: `putEquipmentTemperature` — `PUT /v1/service/equipment/temperature`
   - Prep temperature: `putTemperaturePrep` — `PUT /v1/service/temperature/prep`
   - Cooling temperature: `putTemperatureCooling` — `PUT /v1/service/temperature/cooling`
   - Waste: `putResultsWaste` — `PUT /v1/service/results/waste`
   - Photos: `putPhotos` — `PUT /v1/service/photos`
   - Menu item results: `putServiceResults` — `PUT https://marko.aramark.net/v1/service/results/{service_menu_item_id}` (Service Results API)
3. **Verify with the matching read.** Do not treat a 200 as proof on its own — confirm `status` is `Success` and then re-read.
4. **Reverse only what has a reversal.**
   - `deleteResultsWaste` — `DELETE /v1/service/results/waste` undoes a waste entry.
   - `deletePhotos` — `DELETE /v1/service/photos` removes photos.
   - Everything else — customer counts, all three temperature writes, food bank activity, site journal, site pin, menu items — has **no** documented reversal. The only correction path is another write with the corrected value.

## Rules

- The PUT-shaped writes are idempotent by HTTP semantics, but Aramark does not commit to that anywhere. Treat repeated PUTs as safe-by-verb and repeated POSTs (`postSiteRequest`, `postLogRequest`) as unsafe.
- `postSiteRequest` creates a site request and `putSiteRequest` updates one; there is no cancel operation. Get the payload right the first time.
- Errors arrive two ways. A gateway 401/404 is `{"fault":{"faultstring":...,"detail":{"errorcode":...}}}`. An application failure can arrive as HTTP 200 with `status: "Error"`. Branch on both.
