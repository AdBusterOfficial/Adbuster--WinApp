# ⚙️ AdBuster PRO — CEPA Behaviour Flow (Research Draft)

![CEPA Behaviour Flow](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AdBuster_CEPA_Behaviour_Flow.png)

---

## 🧩 Overview
This document describes the current **research and development stage** of the CEPA Logic PRO behaviour engine.  
The flow diagram above represents the internal logic used to stabilize loudness and prevent uncontrolled drift during live audio analysis.

---

## 🔄 Behaviour Flow Summary

| 🔸 Stage | 🔹 Function |
|-----------|-------------|
| 🎧 **Audio Input** | Captures real‑time amplitude and converts it into a normalized GUI level. |
| 🧠 **Context Detection (AD / Music / Normal)** | Identifies playback type and sets flags for advertisement, music, or normal content. |
| ⚙️ **CEPA FIRST** | Primary decision layer — executes immediate volume corrections when context triggers are detected. |
| 🛡️ **Anti‑Drift** | Prevents slow upward loudness drift when CEPA FIRST is inactive. Keeps long‑term stability. |
| 📉 **Threshold Correction** | Gradually adjusts sensitivity based on long‑term averages. Disabled during ADS, music, or manual mode. |
| 🔁 **Fallback** | Secondary safety layer — reacts when CEPA FIRST and Anti‑Drift are idle, ensuring recovery from sustained imbalance. |

---

## 🧠 Current Behaviour 
- **Manual mode** temporarily disables CEPA logic for user control.  
- **CEPA FIRST** handles fast reactions and context‑based corrections.  
- **Anti‑Drift** intercepts slow level rise above threshold (+0.5).  
- **Threshold correction** adapts sensitivity over time using hour buffer.  
- **Fallback** ensures stability when all other modules are idle.  
- **ADS and Music modes** have isolated logic paths to avoid false triggers.

---

## 💡 Research Notes
- The system now controls all unexpected loudness drift scenarios.  
- Each module operates independently but in a defined order.  
- The flow is stable and predictable under test conditions.  
- Further work: refine Anti‑Drift sensitivity and CEPA FIRST reaction margin.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

