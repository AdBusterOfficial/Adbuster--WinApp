# CEPA Logic – ML Dynamic Threshold (AVG − 2) + Auto‑Refresh

## Overview
🔍 CEPA introduces an adaptive ML mode that uses **AVG** as a stable long‑term acoustic baseline.  
🔍 Instead of static presets or manual sliders, the ML threshold is calculated dynamically:

🔢 **ML Threshold = AVG − 2**

🔍 **AVG** is a smoothed average of ~20 minutes of audio input.  
🔍 This ensures the ML threshold remains stable, predictable, and resistant to short‑term fluctuations.

---

## Why AVG?
🧠 **AVG is not an ad detector or spike detector — it is the baseline.**  
🧠 AVG must remain stable so the ML threshold does not jump during loud scenes or temporary changes.  
🧠 It represents the real listening level over time.

### Key properties:
✅ resistant to loud scenes (does not raise the ML threshold)  
✅ resistant to sudden spikes (does not shift the baseline)  
✅ unaffected by short‑term noise (ignores temporary disturbances)  
✅ reflects real long‑term listening level (true room baseline)  

---

## Auto‑Refresh (every 5 minutes)
🔁 CEPA updates AVG every 5 minutes to keep the ML threshold aligned with the current acoustic environment.

### Behavior:
🔼 When the user increases volume → AVG rises slowly  
⏱️ After 5 minutes → ML threshold updates to **AVG − 2**  
🎧 CEPA stabilizes automatically without user intervention  

🔁 The system naturally adapts to real listening habits.

---

## Benefits
📊 stable ML threshold  
📊 no presets  
📊 no manual tuning  
📊 no drifting  
📊 reacts only to real deviations above baseline  
📊 automatically adapts to volume changes  
📊 predictable behavior  
📊 GUI always reflects the true ML threshold  

---

## Summary
📝 CEPA now operates as a fully adaptive stabilizer:

📝 dynamic threshold (AVG − 2)  
📝 auto‑refresh every 5 minutes  
📝 real acoustic baseline tracking  
📝 stable, predictable behavior  

📝 This upgrade significantly improves stability, responsiveness, and overall system intelligence.

---

## Demo
🎥 [![CEPA Demo](https://img.youtube.com/vi/0rtAsAu81tQ/0.jpg)](https://youtu.be/0rtAsAu81tQ?si=uZTkkQieed-2VwPm) 


