# Roadie (roadie-io)

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
