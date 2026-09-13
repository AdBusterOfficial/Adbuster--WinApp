![AdBuster Hybrid v13](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/hybrid/AdBuster_Hybrid_v13.png)


# 📘 AdBuster Hybrid Engine v13 — Behavioural Stabilization Core

The **AdBuster Hybrid Engine v13** is the next‑generation stabilization core used inside AdBuster PRO.  
It combines DSP smoothing, ML advertisement detection and CEPA Logic PRO into a unified behavioural system that reacts to audio the way a human would — calmly, predictably and with contextual awareness.

This document describes the behaviour of the hybrid engine **without exposing any proprietary code**.

---

## 🎧 Audio Block Processing  
The hybrid engine processes audio in **1024‑sample blocks**, converting raw amplitude into a stable loudness value.

DSP pipeline includes:
- amplitude → dB conversion  
- multi‑stage smoothing  
- spike reduction  
- compression artefact filtering  
- drift & trend awareness  

The engine reacts to **behaviour over time**, not momentary noise.

---

## 🟨 ML Layer — 4‑Feature AD Detector  
A lightweight ML model evaluates each audio block using four behavioural features and classifies the signal as:

- **AD (Advertisement)**  
- **MUSIC**  
- **NORMAL / DIALOG**

A stability hold mechanism prevents false triggers and ensures reliable advertisement detection.

---

## 🔵 CEPA Logic PRO — Behaviour Engine  
CEPA Logic PRO interprets loudness in context.  
It builds a perception model:

- adaptive baseline  
- diff (level vs baseline)  
- trend (5‑second slope)  
- drift detection  
- spike detection  
- context classification  

CEPA assigns intent:
- GOOD_LOUDNESS  
- BAD_LOUDNESS  
- NEUTRAL  

And transitions between behavioural states:
NORMAL • AD • MUSIC • DIALOG • TRANSITION_UP • TRANSITION_DOWN • RETURN

This defines how aggressively the hybrid engine responds.

---

## 🟧 Comfort Margins & Sensitivity  
The hybrid engine adjusts sensitivity dynamically:

- base comfort margin  
- AD margin (faster reactions)  
- dialog margin (dialog protection)  
- music margin (softer behaviour)

This prevents over‑correction and keeps reactions stable and human‑like.

---

## 🟥 Hybrid Action Layer  
Final decisions:

- **VOL_DOWN**  
- **VOL_UP**  
- **PASS**

Based on:
- diff vs margin  
- behavioural state  
- ML context  
- drift  
- stability controls  
- anti‑spam limits  
- return protection  

The hybrid engine avoids oscillations and ensures predictable behaviour.

---

## 📡 IR Dispatch — Safe Volume Control  
Commands are sent to the TV through a protected IR dispatcher with:

- cooldown limits  
- anti‑repeat protection  
- error blocking  
- action‑window limits  
- AD‑specific safety rules  

This prevents command spam and protects the TV from rapid volume changes.

---

## 🛠 Calibration & Day Profiles  
The hybrid engine supports adaptive threshold profiles:

- Morning  
- Afternoon  
- Evening  
- Night  

A 10‑second calibration mode automatically adjusts thresholds based on real ambient audio.

---

## 🖥 GUI & Monitoring  
AdBuster PRO provides a full GUI with:

- live loudness monitoring  
- AD indicator  
- threshold slider  
- calibration controls  
- status messages  
- Azure‑style theme  
- scrollable layout  

---

## 🔒 PRO Edition — Protected Logic  
This document describes **behaviour**, **architecture** and **decision flow** of the AdBuster Hybrid Engine v13.  
All implementation details remain protected under the AdBuster PRO license.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

