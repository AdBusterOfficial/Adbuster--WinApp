
# CEPA Logic – ML Dynamic Threshold (AVG − 2) + Auto‑Refresh

## Overview
🔍 This version introduces a fully adaptive ML-based stabilization mode that uses the real acoustic baseline of the room to determine the operating threshold.  
🔍 Instead of static presets or manual sliders, CEPA now calculates the threshold dynamically:

🔢 ML Threshold = AVG − 2  

🔍 AVG is the smoothed average of the last ~20 minutes of audio input.  
🔍 This makes CEPA responsive to real listening conditions while remaining stable and predictable.

---

## Why AVG?
🧠 The AVG value represents the true acoustic baseline of the room.  
🧠 It is slow, stable, and resistant to sudden spikes (ads, loud scenes, transitions).  
🧠 This allows CEPA to react only to meaningful deviations instead of temporary fluctuations.

### Key properties:
✅ resistant to loud scenes  
✅ resistant to sudden spikes  
✅ unaffected by short-term noise  
✅ reflects real listening level over time  

---

## Auto‑Refresh (every 5 minutes)
🔁 To keep the ML threshold aligned with the current environment, CEPA now performs an automatic refresh every 5 minutes.

### Behavior:
🔼 If the user increases volume → AVG slowly rises  
⏱️ After 5 minutes → ML threshold updates to the new AVG − 2  
🎧 CEPA stabilizes at the new level without manual intervention  

🔁 This creates a fully adaptive system that follows the user’s listening habits naturally.

---

## Benefits
📊 no static presets  
📊 no manual tuning  
📊 no drifting  
📊 reacts only to real deviations  
📊 stays aligned with the actual room acoustics  
📊 adapts automatically when the user changes volume  
📊 stable fallback behavior  
📊 smooth GUI reflects the true ML threshold  

---

## Summary
📝 CEPA now operates as a true adaptive stabilizer:

📝 dynamic threshold (AVG − 2)  
📝 auto‑refresh every 5 minutes  
📝 real acoustic baseline tracking  
📝 stable, predictable behavior  

📝 This upgrade significantly improves stability, responsiveness, and user experience.

---

## Demo
🎥 [![CEPA Demo](https://img.youtube.com/vi/0rtAsAu81tQ/0.jpg)](https://youtu.be/0rtAsAu81tQ?si=uZTkkQieed-2VwPm)
