
# CEPA Logic PRO — DIALOG Behaviour

This document shows how CEPA Logic PRO reacts to dialogue in real time.  
Dialogue behaves differently from music or ads, and CEPA Logic PRO is designed to detect and stabilize it with high precision.

---

## 📈 Real‑Time Example

**Current level:** 41  
**Baseline:** 36  
**Difference:** +5  
**Context:** DIALOG  
**Kind:** SPIKE_LONG  
**Decision margin:** 5.0  
**Decision:** VOL_DOWN  

CEPA interprets this as BAD_LOUDNESS — a long, unwanted spike during speech.  
It applies the dialogue margin (5.0), evaluates the difference, and determines that corrective action is required.

Since 5 > 5.0, CEPA executes VOL_DOWN through the IR server, reducing the TV volume.

---

## 🧠 Behaviour Explanation

In DIALOG context, CEPA Logic PRO focuses on:

- keeping speech clear and stable,  
- preventing sudden loud bursts,  
- reacting to long spikes that disrupt intelligibility,  
- maintaining consistent loudness across spoken content.

SPIKE_LONG indicates that the loudness increase is not momentary but sustained.  
CEPA responds by applying the dialogue‑specific margin, which is tuned to preserve clarity without over‑reacting to natural speech dynamics.

This ensures that dialogue remains comfortable and intelligible.

---

## ⚙️ Decision Logic Summary

CEPA evaluates:

- baseline (expected dialogue level),  
- current level,  
- difference,  
- behaviour kind (SPIKE_LONG),  
- context (DIALOG),  
- decision margin.

Only when difference exceeds the margin does CEPA apply a correction.

This prevents unnecessary volume changes while still catching disruptive spikes.

---

## 📌 Summary

This example demonstrates how CEPA Logic PRO stabilizes dialogue — reacting only when long spikes occur and maintaining clear, consistent speech.
