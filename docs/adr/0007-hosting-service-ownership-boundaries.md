# ADR 0007: Hosting service ownership boundaries

**Status:** Accepted

## Decision
Railway is primary for persistent services; Vercel owns public web/edge delivery; Cloudflare owns media; Trigger.dev may own orchestration. Fly.io is not a parallel primary.

## Rationale
Resolve fragmented examples while retaining specialized services and explicit degradation boundaries. See ARCH-OPS-001.