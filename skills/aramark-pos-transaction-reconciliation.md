---
name: aramark-pos-transaction-reconciliation
description: Reconcile a day of Aramark point-of-sale activity by pulling checks, line items, tenders, discounts, taxes, service charges and adjustments for one org_value from the Marko POS APIs.
api: Aramark Marko Platform
generated: '2026-09-04'
method: generated
source: openapi/aramark-pos-transactions-openapi.json, openapi/aramark-pos-daily-sales-openapi.json, openapi/aramark-pos-items-openapi.json
operations:
  - getPOSDevices
  - getTransactionChecks
  - getTransactionCheckLineItems
  - getTransactionItems
  - getTransactionTenders
  - getTransactionDiscounts
  - getTransactionServiceCharges
  - getTransactionTaxes
  - getTransactionAdjustments
  - getRealTimeItemSales
  - getDailySalesByOrgValue
  - getPOSItems
---

# Reconcile a day of Aramark POS activity

The POS Transactions API decomposes a day into seven parallel collections rather than one nested document. Reconciliation means pulling each one for the same `org_value` and date window and tying them back to the daily sales total.

## Steps

1. **Establish the control total.** `getDailySalesByOrgValue` — `GET https://marko.aramark.net/v1/pos/daily/sales/{org_value}`. This is the figure the detail has to add up to.
2. **List the devices in scope.** `getPOSDevices` — `GET https://marko.aramark.net/v1/pos/devices`.
3. **Pull the checks.** `getTransactionChecks` — `GET https://marko.aramark.net/v1/pos/transactions/checks/{org_value}`. Use `start_date_time` and `end_date_time` to bound the window, and `page`/`size` to page — this is one of the few Marko surfaces that paginates.
4. **Pull the components, all keyed on the same org_value and window.**
   - `getTransactionCheckLineItems` — `/v1/pos/transactions/check/line_items/{org_value}`
   - `getTransactionItems` — `/v1/pos/transactions/items/{org_value}`
   - `getTransactionTenders` — `/v1/pos/transactions/tenders/{org_value}`
   - `getTransactionDiscounts` — `/v1/pos/transactions/discounts/{org_value}`
   - `getTransactionServiceCharges` — `/v1/pos/transactions/service_charges/{org_value}`
   - `getTransactionTaxes` — `/v1/pos/transactions/taxes/{org_value}`
   - `getTransactionAdjustments` — `/v1/pos/transactions/adjustments/{org_value}`
5. **Resolve item identifiers.** `getPOSItems` — `GET https://marko.aramark.net/v1/pos/items` — to turn item ids in the line items into names.
6. **Spot-check live.** `getRealTimeItemSales` — `GET https://marko.aramark.net/v1/pos/real_time/item_sales/{org_value}` — when you need to see the current day rather than a closed one.

## Rules

- Page every transaction call with `page` and `size`, and keep reading until `count` is satisfied. These are the largest collections on the platform.
- Send `bypass-cache: true` for same-day reconciliation; leave it off for closed days so you get the cached read.
- `status` inside a 200 can be `Not Found`. For a site that did not trade that day this is the normal answer, not a failure.
- The POS contracts declare a `smoke` request header. It is an Aramark test flag, not a consumer feature — do not send it.
- All reads. Nothing in this flow mutates state.
