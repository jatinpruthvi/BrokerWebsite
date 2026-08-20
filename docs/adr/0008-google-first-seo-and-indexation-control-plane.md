# ADR 0008: Google-first SEO and indexation control plane

**Status:** Accepted

## Decision
Use the v8 route/index model and Google Search Console, inspection, rendered-data, schema, and Web-Vitals workflows as primary controls. Bing, IndexNow, and AI tools are supplemental.

## Rationale
Explicit ownership and quality telemetry prevent faceted index bloat; no platform guarantees ranking. See ARCH-SEO-002–008.