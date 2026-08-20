# ADR 0012: Phase boundaries preserve approved capabilities

**Status:** Accepted

## Decision
Distinguish contract-ready foundations from activated features. Deferral of vector/LLM search, deck.gl, richer motion/3D, localization, or scale infrastructure does not remove approval; activation requires explicit gates.

## Rationale
This resolves sources that alternately demanded every feature immediately or removed advanced capability. Stable fallbacks ship first; approved features retain contracts, owners, and evidence gates. See ARCH-PHASE-001–004.