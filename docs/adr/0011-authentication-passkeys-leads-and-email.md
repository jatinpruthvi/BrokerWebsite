# ADR 0011: Authentication, passkeys, leads, and email

**Status:** Accepted

## Decision
Use verified Better Auth with secure sessions, roles, magic links/2FA/recovery, and gated passkeys. Leads remain first-party/masked; email and alerts require consent, audit, abuse, and delivery controls.

## Rationale
Strong broker security and low-friction access coexist without exposing raw contacts or ungoverned messaging. See ARCH-SEC-001/004 and ARCH-PROD-005.