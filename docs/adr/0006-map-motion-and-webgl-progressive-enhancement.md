# ADR 0006: Map, motion, and WebGL progressive enhancement

**Status:** Accepted

## Decision
MapLibre/list and restrained product motion are baseline. deck.gl, GSAP, Lenis, and R3F/Drei are approved bounded enhancements with device/accessibility gates, fallbacks, and kill switches.

## Rationale
Retain advanced visuals without making search depend on GPU or animation. See ARCH-WEB-006/007 and ARCH-PHASE-004.