# Data Model (Non-normative)

> [ARCHITECTURE.md](../ARCHITECTURE.md) wins. Expands ARCH-DATA-001–007, ARCH-SEO-002/006, and ARCH-SEC-004.

`User` joins `BrokerOrganization` through role-bearing `BrokerMembership`; `BrokerProfile` is public identity. `City`/`Locality` own aliases and geography. `Project` links developer, locality, and RERA records. Stable `Listing` identity owns versions, facts, state, point, submitter, project/locality, and ordered `MediaAsset`s.

`SourceObservation` preserves source class, jurisdiction, URL/reference, retrieval time, parser version, raw hash/snapshot reference, normalized values, confidence, and review/publication state. Public facts retain field-level provenance instead of overwriting history.

Listings move through draft, pending-review, active, temporarily-unavailable, sold/rented, expired, archived, and deleted. `AuditEvent` captures actor/time/reason. `Lead` joins user, target, attribution, consent, masked-contact workflow, assignment, and status. `SavedItem`, `SavedSearch`, `Alert`, and `Comparison` are private. `SlugAlias` preserves redirects; `SeoPageRegistry` owns route, intent/entity, index policy, canonical target, quality, sitemap group, and timestamps.

PostgreSQL is authoritative; PostGIS stores points/boundaries; FTS/trigram launch search. Redis is never authoritative. Media binaries live in Cloudflare but metadata/provenance remains relational. Embeddings are derived, versioned, rebuildable, and cannot replace canonical fields.