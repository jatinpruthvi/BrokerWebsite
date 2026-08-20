# ADR 0005: Search evolution and LLM/vector gates

**Status:** Accepted

## Decision
Launch deterministic PostgreSQL FTS/trigram/locality search behind an adapter. Retain vector, semantic, and LLM capabilities but activate only after quality, privacy, evaluation, relevance, latency, cost, and fallback gates.

## Rationale
Normalized reliable data precedes semantic value. Approved capability is preserved without becoming an unmeasured dependency or public-fact generator. See ARCH-DATA-004/005.