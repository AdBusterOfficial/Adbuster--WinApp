# AD MODE Logic — AdBuster PRO

### 🎯 Purpose
The AD MODE module is responsible for protecting the listener from sudden loudness spikes caused by advertisements.  
It is one of the core components of CEPA Logic in AdBuster PRO.

![AD MODE Logic — AdBuster PRO](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AD_mode_logic.png)

---

## 🔍 Overview

**AD MODE** activates when ML detects an advertisement.  
The system switches into protection mode, blocking volume increases and enforcing stable CEPA behaviour.

---

## 🟦 NORMAL MODE (no ad detected)

- `DETECT_AD() == NORMAL`  
- `ad_mode = False`  
- CEPA operates in standard mode  
- Dialog + music allowed  
- Fallback: **UP + DOWN**

**Final behaviour:**
- Smooth volume control  
- Stable CEPA response  
- Balanced fallback

---

## 🟨 AD MODE (ad detected)

- `DETECT_AD() == AD`  
- `ad_mode = True`  
- CEPA blocks **VOL_UP**  
- Fallback: **ONLY DOWN**

**Final behaviour:**
- Ad‑volume suppression  
- Fast reaction to ads  
- CEPA resumes after ad

---

## 📘 Notes

This logic is a core part of CEPA 2.0 PRO and ensures predictable, stable behaviour during advertisement segments.

---

## 📌 Purpose of This Diagram

The AD MODE Logic diagram is part of the CEPA PRO documentation and illustrates how AdBuster PRO reacts to advertisement segments in real time.  
It complements other CEPA behaviour diagrams:

- MUSIC Behaviour  
- DIALOG Behaviour  
- NORMAL Behaviour  
- ADS Behaviour  
- AD MODE Logic  
- Fallback Logic  
- Music Mode Logic  

Together, these diagrams form a complete overview of CEPA’s real‑time decision system and describe how CEPA Logic maintains stable, predictable behaviour across all audio environments.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

