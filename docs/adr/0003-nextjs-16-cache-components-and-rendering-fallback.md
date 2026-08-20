# ADR 0003: Next.js 16 Cache Components and rendering fallback

**Status:** Accepted

## Decision
Use Next.js 16 App Router, Turbopack, Cache Components, and explicit cache boundaries/tags, with a documented stable rendering/build fallback. Reject obsolete experimental PPR configuration.

## Rationale
Preserve streaming/caching goals without binding production to superseded flags; correctness and compatibility win. See ARCH-WEB-001.