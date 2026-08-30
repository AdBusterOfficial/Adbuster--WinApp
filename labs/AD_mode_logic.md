# AD MODE Logic — AdBuster PRO

Below is the full logic of the **AD MODE** in AdBuster PRO.  
This mechanism is responsible for detecting advertisements in the audio stream and instantly suppressing their loudness before the listener feels the spike.

![AD MODE Logic](labs/AD_mode_logic.png)

---

## 🔍 Overview

**AD MODE** is activated when ML detects an advertisement in the audio.  
The system switches into a protection mode, blocking volume increase and enforcing stable, comfortable CEPA behaviour.

---

## 🟦 NORMAL MODE (no ad detected)

- `DETECT_AD() == NORMAL`  
- `ad_mode = False`  
- CEPA works in standard mode  
- Dialog + music are allowed  
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
  - Ad-volume suppression  
  - Fast reaction to ads  
  - CEPA resumes after ad

---

## 📘 Notes

This logic is a core part of CEPA 2.0 PRO and forms the foundation for stable, predictable system behaviour during advertisement segments.

