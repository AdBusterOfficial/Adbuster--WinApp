# AD MODE Logic — AdBuster PRO

Below is the full logic of the **AD MODE** in AdBuster PRO.  
This mechanism detects advertisements in the audio stream and instantly suppresses their loudness before the listener feels the spike.

![AD MODE Logic](labs/AD_mode_logic.png)

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
- Final behaviour:  
  - Smooth volume control  
  - Stable CEPA response  
  - Balanced fallback

---

## 🟨 AD MODE (ad detected)

- `DETECT_AD() == AD`  
- `ad_mode = True`  
- CEPA blocks **VOL_UP**  
- Fallback: **ONLY DOWN**  
- Final behaviour:  
  - Ad‑volume suppression  
  - Fast reaction to ads  
  - CEPA resumes after ad

---

## 📘 Notes

This logic is a core part of CEPA 2.0 PRO and ensures predictable, stable behaviour during advertisement segments.
