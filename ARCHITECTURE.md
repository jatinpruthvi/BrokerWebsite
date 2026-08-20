# BrokerWebsite Architecture

**Normative source. Baseline:** `ea211228c57dc476f822c4eb0f731a5e457e0095`.

## Authority

This is the only normative product and architecture document. Topic documents and ADRs are non-normative; archived originals preserve extended examples and rationale. If any conflict exists, this file wins. Approved decisions change only by editing this file, normally with a superseding ADR.

## Product and trust

- **ARCH-PROD-001** Build an India real-estate aggregator based primarily on broker-partner inventory licensed under agreement. Never scrape or republish portal listings, media, descriptions, floor plans, or prices.
- **ARCH-PROD-002** Support Buy/Rent discovery by city, locality, property type, BHK, budget, area, and approved facets; cards/details expose price, media, location, area, freshness, broker, and RERA/provenance context.
- **ARCH-PROD-003** Support broker organizations, roles, draft/autosave, validated resumable media uploads, review, publication, lifecycle management, and audit history.
- **ARCH-PROD-004** Preserve saved listings, compare, saved searches, alerts, and accounts as approved capabilities, activated by phase gates.
- **ARCH-PROD-005** Leads use first-party forms and masked contact. Do not expose raw broker phone/email by default. Record consent, attribution, assignment, status, audit, and abuse controls.
- **ARCH-PROD-006** Public claims and structured data must be visible, attributable, current, and supported; never invent rankings, availability, verification, legal status, or prices.

## Public web, routes, and SEO

- **ARCH-SEO-001** Public pages are server-first: useful facts, headings, primary inventory, and ordinary links exist before client JavaScript. Interactive layers progressively enhance them.
- **ARCH-SEO-002** The accepted v8 route model supersedes older examples. Canonicals are ASCII, lowercase, hyphenated, and built by a typed registry. Families include `/buy/`, `/rent/`, city/locality/curated-intent routes, `/projects/{city}/{project}/`, `/properties/{city}/{locality}/{slug}-{stable-id}/`, `/brokers/{city}/{broker}/`, `/rera/{state}/{registration}/`, and `/guides/...`. The registry owns aliases, redirects, index policy, and canonical metadata.
- **ARCH-SEO-003** Durable entities and qualified curated intents may be indexed. Arbitrary filters, sort, map bounds, empty/thin combinations, compare, saved, account, and dashboard states are not indexable.
- **ARCH-SEO-004** Every indexable page has one intent owner, unique visible value, correct status, self-consistent canonical, crawlable parent/context links, sitemap eligibility, freshness, and structured data matching visible evidence.
- **ARCH-SEO-005** Partition sitemaps by entity/guide/media family; keep `lastmod` honest; automate robots, canonical, noindex, orphan, duplicate, soft-404, lifecycle, and schema checks. Redirect only to a genuine successor; otherwise use a useful unavailable state or 404/410.
- **ARCH-SEO-006** Maintain a visible entity graph joining organization, geography, project, property, broker, RERA, offer, media, and guides with stable JSON-LD `@id` values.
- **ARCH-SEO-007** Google Search Console, URL Inspection workflows, rendered-HTML/schema checks, and Core Web Vitals are the primary indexation control plane. Bing/IndexNow and AI-discovery telemetry are supplemental. `llms.txt` is optional and never replaces HTML, links, robots, or sitemaps.
- **ARCH-SEO-008** Earn off-page authority through original methodology/data, useful guides/tools, digital PR, relevant partnerships, and accurate profiles. Prohibit paid-link schemes, automated spam, fake reviews, and unsupported superlatives.
- **ARCH-SEO-009** Support Indian numbering, currency, addresses, jurisdiction-specific RERA terms, and verified language presentation. Localized names are display aliases; canonical URLs stay ASCII. Test font/language coverage before activation.

## Application architecture

- **ARCH-WEB-001** Use Next.js 16 App Router, compatible React, TypeScript strict mode, stable Turbopack, Cache Components, explicit cache profiles/tags, and Suspense where appropriate. Keep a documented stable rendering/build fallback for incompatible dependencies; do not use Next.js 15 experimental PPR configuration.
- **ARCH-WEB-002** Server Components/server fetching own initial public data. Typed route handlers/procedures own boundaries. TanStack Query owns interactive remote state, URL parameters own canonical filters, and Zustand is limited to ephemeral UI state.
- **ARCH-WEB-003** Use Tailwind v4 plus semantic CSS tokens and owned shadcn/Radix compound components. Meet WCAG 2.2 AA keyboard, focus, contrast, dialog, and announcement behavior.
- **ARCH-WEB-004** UX is search-first and mobile-first. Conventional autocomplete/filter controls are primary; cmdk is optional. Preserve share/refresh/back behavior and explicit loading, empty, error, recovery, and status feedback.
- **ARCH-WEB-005** Images use Cloudflare R2/CDN transformations, responsive derivatives, dimensions/placeholders, validation, provenance, moderation, and EXIF controls. Video uses Cloudflare Stream/HLS with posters, captions/transcripts where applicable, retry, and low-bandwidth fallback.
- **ARCH-WEB-006** MapLibre, server clustering/viewport search, and an accessible list are baseline. deck.gl heatmap/scatter/grid remains approved but gated by target-device evidence. Core discovery never depends on WebGL.
- **ARCH-WEB-007** CSS and one React motion layer serve product UI. GSAP/ScrollTrigger, Lenis, and R3F/Drei remain approved for bounded marketing/detail surfaces with dynamic loading, 2D/static fallback, reduced-motion/data behavior, budgets, and kill switches.

## Data, search, and RERA

- **ARCH-DATA-001** PostgreSQL 16+ is the system of record; PostGIS handles geography, full-text and `pg_trgm` deterministic search, Prisma typed access, and reviewed isolated SQL specialized indexes. Redis is limited to rate limits, coordination, and measured hot caches.
- **ARCH-DATA-002** Canonical entities include User, BrokerOrganization, BrokerMembership, BrokerProfile, City, Locality, Project, Listing, ListingVersion, MediaAsset, ReraRecord, SourceObservation, SavedItem, SavedSearch, Alert, Comparison, Lead, ConsentRecord, AuditEvent, SlugAlias, and SeoPageRegistry.
- **ARCH-DATA-003** Listing states are draft, pending review, active, temporarily unavailable, sold/rented, expired, archived, and deleted. Preserve stable identity/version history. Publication requires rights, required fields, moderation, and provenance/freshness review.
- **ARCH-DATA-004** Launch normalized deterministic PostgreSQL search with locality aliases, Indian-address normalization, facets, typo tolerance, explainable ranking, and an adapter for future engines.
- **ARCH-DATA-005** pgvector, embeddings, natural-language parsing, semantic similarity, and LLM features stay approved but inactive until data quality, privacy, evaluation, relevance, latency, cost, security, and fallback gates pass. Generated output is never an unreviewed public fact.
- **ARCH-DATA-006** RERA ingestion is source-specific and activates only after legal/terms and reliability review. Store jurisdiction, source URL/reference, retrieval time, parser version, raw hash/snapshot reference, normalized values, confidence, freshness, and manual-review/publication state. Public availability alone is not permission.
- **ARCH-DATA-007** RERA, media, alerts, notification, embedding, cache, sitemap, and IndexNow jobs are idempotent, retryable, observable, auditable, and recoverable through dead-letter/manual replay.

## Security, privacy, and operations

- **ARCH-SEC-001** Use a verified Better Auth production integration with secure sessions, organization roles, magic links, 2FA/recovery, least privilege, step-up controls, and gated WebAuthn/passkeys.
- **ARCH-SEC-002** Apply CSP, HSTS, Permissions Policy, secure/HttpOnly/SameSite cookies, CSRF defense, validation/authorization, secret isolation, WAF/bot controls, and per-IP/account/broker/route limits.
- **ARCH-SEC-003** Uploads require quotas, MIME/content verification, malware scanning, metadata handling, moderation, and signed access. Redact contacts, credentials, exact user location, and sensitive raw searches from telemetry.
- **ARCH-SEC-004** Record purpose, consent, and retention for accounts, alerts, saved activity, and leads; support access/correction/deletion. Collect only necessary personal data and prevent masked-contact bypass.
- **ARCH-OPS-001** Railway is the primary persistent platform for services, PostgreSQL/Redis connectivity, and workers. Vercel owns public Next.js/edge delivery; Cloudflare owns media; Trigger.dev may own orchestration. Fly.io is not a parallel primary. Document credentials, health, failure, and degradation boundaries.
- **ARCH-OPS-002** Use OpenTelemetry, Sentry, Pino, privacy-aware product/search analytics, and route/device/network Web Vitals. Define SLOs, error budgets, alerts, runbook owners, incident response, and postmortems.
- **ARCH-OPS-003** CI includes typecheck, lint, unit/integration/E2E, axe, visual, URL/metadata/schema/indexability, dependency/secret/supply-chain, migration, low-end Android/4G, reduced-motion/data, and non-WebGL tests.
- **ARCH-OPS-004** Use pooling, encrypted backups/PITR, restore drills, safe expand-contract migrations, measured replicas, previews, health gates, rollback, feature flags, and kill switches.

## Phases and activation

- **ARCH-PHASE-001** Phase 1 is contract-ready foundation: canonical entities/routes/index policy, design/accessibility, server-first shells, deterministic search, broker/listing/media core, masked leads, baseline security/CI/observability/deployment. Contract-ready means interfaces, schemas, adapters, and fallbacks exist—not that advanced features are active.
- **ARCH-PHASE-002** Phase 2 activates trustworthy supply/discovery: expanded qualified public pages, legally reviewed RERA sources, alerts, MapLibre clustering, authority operations, and operational scaling.
- **ARCH-PHASE-003** Phase 3 independently activates vector/LLM search, deck.gl, richer motion/Lenis/3D, broader localization, and higher-scale search only after gates. Deferral is not deletion.
- **ARCH-PHASE-004** Every gated capability needs owner, hypothesis, prerequisites, device/accessibility/privacy/security review, measurable success, staged exposure, and rollback/kill switch. Failure retains the stable fallback.

## Provenance and planned archive destinations

All 19 source Markdown files at the frozen commit are represented; originals remain untouched in this batch.

| Source | Material preserved | Planned archive destination |
|---|---|---|
| `ARCHIVE_INDEX.md` | prior archive inventory | `docs/archive/source/ARCHIVE_INDEX.md` |
| `README.md` | repository/product context | `docs/archive/source/README.md` |
| `plan.md` | product, stack, data, UI baseline | `docs/archive/source/plan.md` |
| `final-technical-stack-review.md` | server-first simplification, budgets, cautions | `docs/archive/reviews/final-technical-stack-review.md` |
| `final-three-phase-architecture.md` | controlling three-phase synthesis | `docs/archive/final/final-three-phase-architecture.md` |
| `three-phase-execution-appendix.md` | phase deliverables/gates | `docs/archive/appendices/three-phase-execution-appendix.md` |
| `off-page-authority-google-first-appendix.md` | earned authority operations | `docs/archive/appendices/off-page-authority-google-first-appendix.md` |
| `recommendation-v1.md` | original comprehensive baseline | `docs/archive/recommendations/recommendation-v1.md` |
| `recommendation-v2.md` | complete capability retention | `docs/archive/recommendations/recommendation-v2.md` |
| `recommendation-v3.md` | crawlable IA/index control | `docs/archive/recommendations/recommendation-v3.md` |
| `recommendation-v4.md` | page-authority/entity graph | `docs/archive/recommendations/recommendation-v4.md` |
| `recommendation-v5.md` | production/security/observability | `docs/archive/recommendations/recommendation-v5.md` |
| `recommendation-v6.md` | India localization/data refinements | `docs/archive/recommendations/recommendation-v6.md` |
| `recommendation-v7.md` | reviewed feedback candidate | `docs/archive/recommendations/recommendation-v7.md` |
| `v7-feedback-decision-report.md` | v7 accept/reject rationale | `docs/archive/reviews/v7-feedback-decision-report.md` |
| `v7-accepted-feedback-appendix.md` | accepted v7 corrections | `docs/archive/appendices/v7-accepted-feedback-appendix.md` |
| `recommendation-v8.md` | latest route/SEO candidate | `docs/archive/recommendations/recommendation-v8.md` |
| `v8-seo-feedback-decision-report.md` | v8 accept/reject rationale | `docs/archive/reviews/v8-seo-feedback-decision-report.md` |
| `v8-accepted-seo-appendix.md` | accepted route/index policy | `docs/archive/appendices/v8-accepted-seo-appendix.md` |

Extended examples and historical alternatives remain in these originals and will be cross-linked after archival.