# Operations (Non-normative)

> [ARCHITECTURE.md](../ARCHITECTURE.md) wins. Expands ARCH-OPS-001–004 and ARCH-DATA-007.

Vercel delivers public Next.js/edge behavior. Railway is the primary persistent service platform and connectivity boundary for PostgreSQL/Redis and workers. Cloudflare R2/Stream owns media. Trigger.dev may orchestrate durable jobs. Document credentials, regions, health, timeout/retry, data flow, and degradation for each; do not operate Fly.io as a parallel primary.

Define SLOs/error budgets for pages, search, leads, upload, and jobs. Use OpenTelemetry, Sentry, Pino, Web Vitals, and privacy-safe product/search signals. Alert on availability, latency, zero-result anomalies, lead/media failures, stale RERA/sitemaps, queue depth, and backup health.

Jobs need idempotency, bounded retry, audit/correlation, dead-letter/manual replay. PostgreSQL needs pooling, encrypted PITR backups, restore drills, migration rehearsal, and measured replicas. Releases need previews, CI gates, expand-contract migrations, health checks, rollback, feature flags, and kill switches. Incident runbooks cover severity, command, communication, containment, recovery, and postmortem; test provider degradation while retaining static/list/search fallbacks.