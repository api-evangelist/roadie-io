# Roadie (roadie-io)

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

Roadie is **managed Backstage** - a fully hosted internal developer portal (IDP) and software catalog delivered as SaaS. Teams get the Backstage software catalog, TechDocs, Scaffolder software templates, Tech Insights scorecards, and 75+ plugins without operating Backstage themselves. Roadie is the commercial product built on the open-source Backstage framework (Apache 2.0); it is operated by Larder Software Limited.

Roadie exposes a public REST API at `https://api.roadie.so/api`, authenticated with a Bearer token (User Token or Service Token) created in the Roadie Administration UI. The API lets you read software catalog entities, push Roadie-managed entities and idempotent entity sets into the catalog, run Scaffolder templates, and query Tech Insights facts, checks, and scorecards. Roadie also ships six agent-native MCP servers over the same API base.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/roadie-io/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/roadie-io/refs/heads/main/apis.yml)

## Access Model (Honest Notes)

- **Roadie is a paid, managed SaaS product**, not open source. The underlying Backstage framework is free and open source; Roadie's value is the hosted, upgraded, supported portal.
- The **public REST API is available on Cloud Hosted Roadie**. REST API access is called out as a Growth-tier capability on Roadie's pricing page, so programmatic use of `api.roadie.so` may require a higher plan tier. Verify with Roadie.
- Pricing is **per contributing developer per month** (developers who write tracked code; non-coding users can log in free). Observed rates and tiers change - reconcile against [roadie.io/pricing](https://roadie.io/pricing/).
- The **Catalog read endpoints** follow the upstream Backstage Software Catalog API shape. The **roadie-entities and entity-set endpoints** are Roadie's own ingestion API. **Scaffolder v2** and **Tech Insights v1** base paths are confirmed from Roadie docs.
- **TechDocs endpoints** in the OpenAPI are **modeled from the Backstage TechDocs API** and flagged as such; confirm availability on your tenant.
- Individual request/response **schemas in the OpenAPI are modeled** from Roadie + Backstage documentation (Roadie's live reference is a JS-rendered Scalar app), not a Roadie-published OpenAPI file. Confirmed base URLs, auth, and endpoint paths are grounded in the sources listed in `review.yml`.
- **No public WebSocket API** is documented. The only push transport is the Scaffolder task `eventstream` (Server-Sent Events); MCP servers use streamable HTTP. See `review.yml`.

## Tags

- Software Catalog
- Internal Developer Portal
- Backstage
- Developer Experience
- IDP

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Roadie Catalog API

Read the Backstage software catalog in your Roadie tenant - list, query, and fetch entities (Components, APIs, Systems, Resources, Groups, Users, Templates) by name or filter, and aggregate entity facets.

- **Human URL:** [https://roadie.io/docs/api/catalog/](https://roadie.io/docs/api/catalog/)
- **Base URL:** `https://api.roadie.so/api/catalog`

### Roadie Entity Push API

Programmatically populate the software catalog without YAML - POST/GET/DELETE individual Roadie-managed entities, and idempotently create or replace complete entity sets with PUT so a scheduled job keeps the catalog in sync with an external system of record.

- **Human URL:** [https://roadie.io/docs/api/entity-push-api/](https://roadie.io/docs/api/entity-push-api/)
- **Base URL:** `https://api.roadie.so/api/catalog/roadie-entities`

### Roadie Scaffolder API

Backstage software templates as an API - list actions, dry-run a template, execute a template with input values and secrets, and poll or stream task status. The self-service "golden path" surface of the portal.

- **Human URL:** [https://roadie.io/docs/api/templates/](https://roadie.io/docs/api/templates/)
- **Base URL:** `https://api.roadie.so/api/scaffolder/v2`

### Roadie Tech Insights API

Query Tech Insights over the catalog - retrieve facts for entities, list and run checks, and read scorecards that measure maturity, security, and ownership quality.

- **Human URL:** [https://roadie.io/docs/api/techinsights/](https://roadie.io/docs/api/techinsights/)
- **Base URL:** `https://api.roadie.so/api/tech-insights/v1`

### Roadie TechDocs API

Technical documentation (docs-like-code) surface - fetch TechDocs metadata and built static documentation assets for a catalog entity. Modeled from the Backstage TechDocs API.

- **Human URL:** [https://roadie.io/docs/getting-started/technical-documentation/](https://roadie.io/docs/getting-started/technical-documentation/)
- **Base URL:** `https://api.roadie.so/api/techdocs`

### Roadie MCP Servers

Six agent-native Model Context Protocol servers over the Roadie API - api-docs-query, backend-config, catalog-decorators, rich-catalog-entity, scaffolder-use, and tech-insights-facts - for AI agents to discover API docs, read rich catalog entities, and run scaffolder templates under Roadie's permission model.

- **Human URL:** [https://roadie.io/docs/api/roadie-mcp/](https://roadie.io/docs/api/roadie-mcp/)
- **Base URL:** `https://api.roadie.so/api/mcp/v1`

## Common Properties

- [Authentication](authentication/roadie-io-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/roadiehq)
- [Website](https://roadie.io)
- [Documentation](https://roadie.io/docs/)
- [Plans](plans/roadie-io-plans-pricing.yml)
- [Rate Limits](rate-limits/roadie-io-rate-limits.yml)
- [Fin Ops](finops/roadie-io-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
