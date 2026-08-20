# Security and Privacy (Non-normative)

> [ARCHITECTURE.md](../ARCHITECTURE.md) wins. Maps ARCH-SEC-001–004, ARCH-PROD-005/006, and ARCH-DATA-006.

Use least-privilege user, broker, reviewer, and administrator roles; secure rotated sessions; verified recovery; and step-up checks. Activate passkeys/2FA only with tested recovery and compatibility. Protect browser/server boundaries with CSP, HSTS, Permissions Policy, secure cookies, CSRF defenses, validation, authorization, rate/bot controls, and isolated secrets.

Uploads use signed flows, quotas, MIME/content checks, malware scanning, EXIF handling, moderation, and immutable provenance. Leads remain first-party and masked; store consent version/time, purpose, attribution, assignment, and audit state. Minimize personal data, define retention, and support access/correction/deletion. Redact credentials, contacts, exact location, and sensitive raw searches from logs/traces/analytics.

RERA collection/republication is enabled per source only after terms/legal and reliability review defining storage, attribution, refresh, takedown, and publication rules. Public availability is not automatic permission.