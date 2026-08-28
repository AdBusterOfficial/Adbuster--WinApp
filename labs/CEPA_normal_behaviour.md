# CEPA Logic PRO — NORMAL Behaviour

This document shows how CEPA Logic PRO reacts to rising loudness during NORMAL content (dialogue, shows, movies).  
Unlike MUSIC mode, NORMAL behaviour focuses on stabilizing loudness and preventing unwanted drift.

---

## Real‑Time Example

**Current TV level:** 42  
**Baseline:** 35  
**Difference:** +7  
**Trend:** rising  
**Context:** NORMAL  
**Kind:** DRIFT_UP  
**Reaction margin:** 2.25  
**Decision:** VOL_DOWN  

CEPA interprets this as undesirable loudness.  
Because the signal is drifting upward, CEPA tightens its reaction margin from 3.0 → 2.25 to increase sensitivity.

Since 7 > 2.25, CEPA decides that corrective action is required.

The command VOL_DOWN is sent to the IR server, and the TV volume decreases.

---

## Behaviour Explanation

In NORMAL context, CEPA Logic PRO focuses on:

- maintaining stable loudness,  
- preventing gradual drift,  
- reacting quickly to rising trends,  
- keeping dialogue and show audio consistent.

DRIFT_UP is treated as a behaviour state indicating that loudness is increasing over time.  
CEPA responds by narrowing its reaction margin, making it more likely to intervene.

This ensures that the audio stays comfortable and predictable without sudden jumps.

---

## Decision Logic Summary

CEPA evaluates:

- baseline (expected loudness),  
- current level,  
- difference,  
- trend,  
- context,  
- behaviour kind,  
- reaction margin.

Only when difference > margin does CEPA execute a volume correction.

This prevents over‑reacting to small fluctuations while still catching real loudness drift.

---

## Summary

This example demonstrates how CEPA Logic PRO stabilizes loudness during NORMAL content — reacting only when drift becomes significant and maintaining consistent listening comfort.

