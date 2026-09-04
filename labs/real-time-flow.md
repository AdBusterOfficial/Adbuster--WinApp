
# Real‑Time Flow — Behaviour‑Based Volume Control

![Real‑time flow diagram](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/real%E2%80%91time%20flow%20behind.png)

## 🤖 Overview
This diagram illustrates the behaviour‑driven real‑time volume control pipeline inside AdBuster PRO.  
Instead of reacting to loudness, the system evaluates how the audio behaves — its stability, transitions, compression artefacts and dynamic movement.  
This behaviour‑first approach ensures predictable and stable reactions, even when the incoming audio is chaotic.

The pipeline combines deterministic feature extraction, lightweight classification and CEPA Logic, which acts as a contextual decision layer governing when the system should adjust volume, hold state or wait for clarity.

---

## 🎛️ Pipeline Breakdown

### 🎤 Microphone Input
Raw audio frames captured from the environment.  
They naturally contain instability: spikes, dips, compression artefacts and sudden transitions.

### 📊 Behavioural Feature Extraction
Deterministic features describing how the signal moves, not how loud it is.  
Extracted metrics include:
- RMS  
- Dynamics  
- Compression pattern  
- Stability  

These features form the behavioural profile of each frame.

### 📐 Normalization
A scaler normalizes all extracted features, ensuring consistent classifier input regardless of moment‑to‑moment variability.

### 🧩 Lightweight Classifier
Evaluates each frame and labels it as:
- stable  
- unstable  

The classifier provides context — not final decisions.

### 🧠 CEPA Decision Layer
CEPA interprets classifier output in real time, considering:
- trend  
- timing stability  
- reaction history  
- contextual clarity  

CEPA declares:
- **Adjust** — apply a volume correction  
- **Hold** — maintain current state  
- **Wait** — defer action until the environment stabilizes  

### 📡 Broadlink IR Output
Only when CEPA determines the environment is meaningful, the IR module executes the actual volume command.

---

## 📌 Purpose
This behaviour‑driven pipeline ensures that AdBuster PRO reacts only to meaningful changes in the audio environment.  
It avoids false triggers from random spikes or noise, providing deterministic, stable and predictable loudness control — even when the audio itself is unstable.

This diagram complements other CEPA behaviour modules:
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
