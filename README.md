# Magaya (magaya)

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

Magaya is a logistics and supply chain software company. Its cloud Digital Freight Platform runs freight forwarding, warehouse management, US customs compliance, rate management, CRM, and a customer-facing digital experience portal. Magaya exposes the logistics objects inside a customer's system - **Shipments, Warehouse Receipts, Invoices, Items, and financial Transactions** - programmatically through the **Magaya API** (historically a SOAP/XML Web Service), the newer **Magaya Open API** (a collection of web services), and a **REST Digital Freight Portal API** inherited from the Qwyk acquisition.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/magaya/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/magaya/refs/heads/main/apis.yml)

## Access model (read this first)

Magaya's APIs are **gated, not open self-serve**:

- Using any Magaya API requires a **licensed Magaya subscription**. Pricing is quote-based (contact sales); there is no public API price sheet and no free API tier.
- The Magaya API and Open API run against the **customer's own tenant**. The base URL is per-tenant, of the form `https://SYSTEMID.magayacloud.com/api` (on-premises deployments expose an equivalent host on the customer's network), where `SYSTEMID` is the Magaya System ID.
- Authentication uses a **dedicated API user** (username/password) configured inside the Magaya system - separate from a normal login user. The Digital Freight Portal REST API instead uses **Auth0 machine-to-machine OAuth** clients.
- Reference documentation is publicly readable ([help.magaya.com](https://help.magaya.com/s/document-item?language=en_US&bundleId=magaya-api), [developer.qwykportals.com](https://developer.qwykportals.com/), [magaya.com/magaya-open-api](https://www.magaya.com/magaya-open-api/)), but there is **no open API key signup**.

Because there is no open self-serve reference to crawl, the REST paths in `openapi/`, `collections/`, and `apis.yml` are **honestly modeled** from Magaya's published object model rather than confirmed against a live open reference. The real operation names may follow Magaya's SOAP/XML Web Service conventions or the Open API web-service surface. `endpointsModeled` is flagged `true` in `review.yml`. Confirm exact operations, fields, and auth against the documentation for your Magaya edition and version before building.

## Tags

- Logistics
- Supply Chain
- Freight Forwarding
- Warehouse Management
- Shipping
- Customs
- Transportation

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs (modeled)

### Magaya Shipments API

Programmatic access to air, ocean, and ground shipments - list, retrieve, and create shipment records with consignee, shipper, routing, cargo, and milestone/tracking event data.

- **Human URL:** [https://www.magaya.com/magaya-open-api/](https://www.magaya.com/magaya-open-api/)
- **Base URL:** `https://SYSTEMID.magayacloud.com/api`

### Magaya Warehouse Receipts API

Warehouse receipts and the cargo pieces, weights, volumes, and inventory balances recorded as goods are received into a Magaya-managed warehouse.

- **Human URL:** [https://www.magaya.com/magaya-open-api/](https://www.magaya.com/magaya-open-api/)
- **Base URL:** `https://SYSTEMID.magayacloud.com/api`

### Magaya Invoices API

Accounts-receivable invoices with their line-item charges, currency, taxes, and links to the shipment or warehouse receipt being billed.

- **Human URL:** [https://www.magaya.com/magaya-open-api/](https://www.magaya.com/magaya-open-api/)
- **Base URL:** `https://SYSTEMID.magayacloud.com/api`

### Magaya Items API

Item and commodity master data - the parts, products, and packaging definitions referenced by shipments, warehouse receipts, and orders, plus inventory balances.

- **Human URL:** [https://www.magaya.com/magaya-open-api/](https://www.magaya.com/magaya-open-api/)
- **Base URL:** `https://SYSTEMID.magayacloud.com/api`

### Magaya Transactions API

Generic access to Magaya transaction documents - pickup orders, bookings, quotations, sales orders, purchase orders, and cargo releases - that share Magaya's common transaction envelope.

- **Human URL:** [https://www.magaya.com/magaya-open-api/](https://www.magaya.com/magaya-open-api/)
- **Base URL:** `https://SYSTEMID.magayacloud.com/api`

## Artifacts

- [OpenAPI (modeled)](openapi/magaya-openapi.yml)
- [Postman Collection](collections/magaya.postman_collection.json)
- [Open Collection](collections/magaya.opencollection.json)
- [Plans / Pricing](plans/magaya-plans-pricing.yml)
- [Rate Limits](rate-limits/magaya-rate-limits.yml)
- [FinOps](finops/magaya-finops.yml)
- [Review](review.yml)

## Common Properties

- [GitHub Organization](https://github.com/magaya-dev)
- [LinkedIn](https://www.linkedin.com/company/magaya-corporation-inc-)
- [Website](https://www.magaya.com/)
- [Documentation](https://help.magaya.com/s/document-item?language=en_US&bundleId=magaya-api)
- [API Reference](https://developer.qwykportals.com/)
- [Sign Up](https://www.magaya.com/start-here/)

## WebSocket review

Magaya does **not** expose a documented public WebSocket API. All Magaya programmatic surfaces are request/response (SOAP/XML Web Service, HTTP web services, and REST with Auth0 OAuth). See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
