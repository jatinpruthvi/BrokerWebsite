# ADR 0004: URL state and client data boundaries

**Status:** Accepted

## Decision
Canonical filters live in URL parameters. Server Components own initial public data, TanStack Query interactive remote state, and Zustand ephemeral UI only.

## Rationale
Share, refresh, and back navigation remain correct while duplicate state/fetching is constrained. See ARCH-WEB-002/004.