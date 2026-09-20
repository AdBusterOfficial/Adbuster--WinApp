<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

<br>

# 📘 Stable Hybrid Engine v13 — Real‑World System Behavior Report

AdBuster Hybrid Engine v13 demonstrates stable, predictable and fully logical real‑time volume‑control behavior.  
The engine integrates three coordinated layers — **DSP**, **ML 4‑feature**, and **CEPA Logic PRO** — working together to maintain a comfortable loudness zone regardless of ads, music, or sudden signal spikes.

---

## 🔵 1. ML Layer — Stable AD‑LIKE Detection

The 4‑feature ML model analyzes every audio frame (RMS, STD, DELTA, RANGE) and produces an advertisement‑likeness probability `p_ad`.

Real‑world logs show:

- `p_ad` consistently between **0.65–0.86**
- stable **hits 4–7**
- repeated messages: **HIGH PROBABILITY — AD‑LIKE CONTENT**

This confirms the model reacts only to **repeatable advertisement patterns**, not random noise.

Key thresholds:

- **ML_AD_PROB_THRESHOLD = 0.65**
- **ML_AD_REQUIRED = 4**
- **ML_AD_HISTORY_MAX = 12**

These ensure stable, noise‑resistant detection with no false positives.

Every confirmed event is logged as:

[ML EVENT] AD detected (4-feature)

---

## 🟧 2. AD Hold — Logical Advertisement State Retention

After detecting AD‑LIKE content, the system maintains the AD state for:

- **AD_HOLD_SECONDS = 0.50**

This prevents CEPA from losing the advertisement state during momentary dips in `p_ad`.  
The recording shows AD‑LIKE being held consistently throughout the entire ad segment.

---

## 🟨 3. CEPA Logic PRO — Stable Volume Regulation

CEPA operates with:

- **latest_threshold = 19**
- **deadzone = 8**
- **stable_zone = 7**

This wide comfort zone ensures:

- no reaction to small signal fluctuations  
- no unnecessary corrections  
- stable volume around **12–13**  
- no drops to 11  
- no jumps to 14 without reason  

CEPA reacts only when appropriate:

- 🔥 **Advertisement → immediate single VOL_DOWN**
- 🔥 **Normal content → no aggressive corrections**
- 🔥 **Music → CEPA ignores rapid changes (music_mode)**

CEPA avoids UP/DOWN loops, oscillations, jitter and instability — behaving like a **stable regulator**, not a reactive automaton.

---

## 🟩 4. IR Dispatcher — Safe TV Command Handling

IR logs confirm:

- no repeated commands  
- no command spam  
- safety blocks functioning correctly  
- only single, logical commands sent  

Safety mechanisms:

- **Global 1.2s block**
- **Anti‑Bounce UP block**
- **AD limit VOL_DOWN**
- **Action limit window**

These ensure the TV is never overloaded with IR commands.

---

## 🟪 5. Overall System Stability

The recording demonstrates:

- ML detects AD‑LIKE consistently  
- CEPA reacts only when necessary  
- IR sends safe, single commands  
- volume stays within a comfortable range  
- no oscillations  
- no false AD detections  
- no unnecessary corrections  
- smooth, predictable operation  

This is exactly what defines **Hybrid Engine v13**:

> **A stable, logical, predictable and noise‑resistant real‑time volume stabilization system.**

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>
