# CEPA Logic — Real‑Time Decision v2

![CEPA Logic — Real-Time Decision v2](https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/labs/CEPA_real_time_decision.jpg)

## 🤖 Overview
This diagram illustrates the real‑time behaviour engine used inside **AdBuster PRO**.  
CEPA Logic interprets the audio environment deterministically, ensuring that loudness control remains stable, predictable and context‑aware.  
The ML classifier provides only the initial context (**AD / NORMAL**), while CEPA evaluates the behaviour of the signal and determines how the system should react.

---

## 🎛️ Real‑Time Decision Model

### 📡 Continuous Signal Feed
Real‑time RMS, MFCC and spectral metrics extracted from the incoming audio.  
These metrics describe the behaviour and stability of the signal.

### 📊 Feature Extraction Layer
Deterministic feature set used for:
- ML context  
- behaviour analysis  
- trend evaluation  

This layer provides CEPA with a stable behavioural profile of the audio.

### 🧩 ML Classification (AD / NORMAL)
The classifier provides high‑level context:
- **AD** — advertisement‑like behaviour  
- **NORMAL** — stable, non‑ad behaviour  

It does *not* decide the reaction — it only labels the frame.

### 🧠 CEPA Decision Engine
CEPA evaluates:
- loudness trend  
- timing stability  
- reaction history  
- contextual consistency  

Based on this, CEPA declares:
- **Trigger** — execute a reaction  
- **Hold** — maintain current state  
- **Ignore** — discard unstable or unclear frames  

### ⚙️ Reaction Control
Behaviour‑driven loudness control:
- IR volume commands  
- stabilization  
- timing synchronization  

CEPA ensures reactions are reversible, stable and deterministic.

### 🔄 Continuous Adaptation
CEPA updates its internal state based on behaviour patterns.  
This prevents false triggers and ensures predictable behaviour even in unstable audio conditions.

---

## 📌 Purpose
This model ensures that AdBuster PRO reacts only to meaningful behavioural changes, not random spikes or noise.  
It provides deterministic, context‑aware loudness control without relying on predictive ML behaviour.

It complements other CEPA behaviour modules:
- MUSIC Behaviour  
- DIALOG Behaviour  
- NORMAL Behaviour  
- ADS Behaviour  
- AD MODE Logic  
- Fallback Logic  
- Music Mode Logic  

Together, these diagrams form a complete overview of CEPA’s real‑time decision system.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**
