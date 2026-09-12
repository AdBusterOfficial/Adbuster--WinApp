# 📘 AdBuster PRO — Hybrid Stabilization System (v13 PRO)

AdBuster PRO is a full real‑time audio stabilization system designed to control TV volume intelligently.  
It combines DSP smoothing, ML advertisement detection, behavioural CEPA Logic PRO, fallback safety layers and IR command dispatch — creating a stable, human‑like volume controller.

---

## 🎧 Audio Input & DSP Smoothing
AdBuster PRO processes audio in 1024‑sample blocks and converts raw amplitude into a stable loudness value.

The DSP pipeline includes:
- amplitude → dB conversion  
- multi‑stage smoothing  
- spike reduction  
- compression artefact filtering  
- drift & trend awareness  

This ensures the system reacts to **behaviour**, not momentary noise.

---

## 🟨 ML Engine — 4‑Feature Advertisement Detector
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

This defines how aggressively AdBuster PRO should react.

---

## 🟧 Comfort Margins & Sensitivity Control
AdBuster PRO adjusts sensitivity dynamically:

- base comfort margin  
- AD margin (faster reactions)  
- dialog margin (dialog protection)  
- music margin (softer behaviour)

This prevents over‑correction and keeps reactions stable and human‑like.

---

## 🟥 Hybrid Action Layer — Final Decision
The hybrid engine decides:

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

This ensures predictable behaviour without oscillations.

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
AdBuster PRO supports adaptive threshold profiles:

- Morning  
- Afternoon  
- Evening  
- Night  

A 10‑second calibration mode automatically adjusts thresholds based on real ambient audio.

---

## 🖥 GUI & Monitoring
The system includes a full GUI with:

- live loudness monitoring  
- AD indicator  
- threshold slider  
- calibration controls  
- status messages  
- Azure‑style theme  
- scrollable layout  

---

## 🔒 PRO Edition — Protected Logic
This document describes **behaviour**, **architecture** and **decision flow** of the AdBuster PRO Hybrid System.  
All implementation details remain protected under the AdBuster PRO license.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

