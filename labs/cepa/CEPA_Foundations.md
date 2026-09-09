
# ⚙️ AdBuster PRO — CEPA Behavioural Logic  
## Foundations

CEPA behavioural logic is the decision engine inside AdBuster PRO.  
It does not modify audio. It interprets behaviour — and reacts deterministically, like a human with a remote.

This document outlines the core foundations behind CEPA Logic inside AdBuster PRO.

---

## 🧠 1. Behaviour Over Waveform

Traditional DSP systems react to raw amplitude.  
AdBuster PRO uses CEPA Logic to react to **behaviour patterns**:

- drift (slow upward movement)
- spikes (short or long)
- impact bursts
- stability zones
- context transitions
- correction history

This allows AdBuster PRO to understand *why* loudness changed, not just *how much*.

---

## 🎧 2. Real Acoustic Metrics

CEPA Logic operates on real, measurable acoustic features:

- **RMS** — perceived loudness  
- **STD** — chaotic behaviour  
- **DELTA** — sudden changes  
- **RANGE** — dynamic spread  

These metrics reflect true room acoustics — exactly what a human hears.

---

## 🔍 3. Contextual Interpretation

CEPA identifies the behavioural context of the signal inside AdBuster PRO:

- **NORMAL** — everyday content  
- **ADS** — compressed, loud, aggressive  
- **DIALOG** — speech with natural micro‑variation  
- **MUSIC** — wide dynamics, stable patterns  
- **TRANSITION_UP / DOWN** — context shifts  
- **RETURN** — stabilization phase  

Each context has its own reaction rules and safety limits.

---

## 📊 4. Trend & Stability Analysis

CEPA Logic evaluates how the signal behaves over time:

- rising trend  
- falling trend  
- stable trend  
- micro‑trend  
- trend reversal  
- drift confirmation  

This prevents chaotic reactions and ensures predictable behaviour inside AdBuster PRO.

---

## 🔧 5. Reaction Margin System

AdBuster PRO uses CEPA’s dynamic reaction margin instead of fixed thresholds:

- **tightening** when loudness drifts upward  
- **expansion** during stable or musical content  
- **reset** on context transitions  
- **lock** during ADS behaviour  

This makes the system sensitive when needed and relaxed when safe.

---

## 🛡️ 6. Safety Layer

CEPA enforces strict safety rules inside AdBuster PRO:

- only VOL_UP and VOL_DOWN  
- no MUTE, no POWER, no macros  
- cooldown + anti‑spam  
- dialogue protection  
- fallback during instability  
- deterministic IR behaviour  

This ensures automation is always safe and predictable.

---

## 🤖 7. ML Integration (Optional)

CEPA Logic works independently, but ML provides:

- AD vs NORMAL classification  
- behaviour hints  
- early ADS detection  
- stability validation  

ML is modular — AdBuster PRO remains fully functional even without it.

---

## 🔁 8. Unified Real‑Time Pipeline

AdBuster PRO operates inside a continuous loop:

Microphone → Acoustic Metrics → Behaviour Analysis → CEPA Decision → IR Control

Everything runs offline, locally, without cloud dependency.

---

## 🎯 Summary

CEPA behavioural logic inside AdBuster PRO is built on:

- real acoustic metrics  
- behaviour modelling  
- context detection  
- trend analysis  
- dynamic reaction margins  
- strict safety rules  
- optional ML validation  

It stabilizes loudness deterministically — exactly like a human with a remote, only faster and more consistent.

