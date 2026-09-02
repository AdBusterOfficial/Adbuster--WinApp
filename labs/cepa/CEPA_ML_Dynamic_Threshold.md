
# CEPA Logic – ML Dynamic Threshold (AVG − 2) + Auto‑Refresh

## Overview
🔍 This update introduces a dynamic ML threshold mechanism inside the CEPA framework.  
🔍 **AVG does not replace AdBuster PRO** — it only provides a stable long‑term baseline for threshold calculation.

🔢 **ML Threshold = AVG − 2**

🔍 **AVG** is a smoothed ~20‑minute acoustic baseline.  
🔍 It keeps the ML threshold stable and predictable, while **AdBuster PRO continues to detect ads, spikes and anomalies using the trained model (`ad_detector.pkl`).**

---

## Why AVG?
🧠 AVG is **not** an ad detector.  
🧠 AVG is **not** responsible for reacting to spikes.  
🧠 AVG is **only** the long‑term baseline used to compute the ML threshold.

### Key properties of using AVG as a baseline:
✅ resistant to loud scenes (does not shift the threshold)  
✅ resistant to sudden spikes (ads do not distort the baseline)  
✅ unaffected by short‑term noise  
✅ reflects the real long‑term listening level  

🔁 These properties ensure that the ML threshold remains stable, so AdBuster PRO can react consistently to any deviation above or below that threshold.

---

## Auto‑Refresh (every 5 minutes)
🔁 AVG is refreshed every 5 minutes to keep the ML threshold aligned with the current listening environment.

### Behavior:
🔼 When the user increases volume → AVG rises slowly  
⏱️ After 5 minutes → ML threshold updates to **AVG − 2**  
🎧 CEPA adjusts automatically without user interaction  

🔁 This mechanism ensures the threshold follows real listening habits while AdBuster PRO continues to detect and correct deviations above or below that threshold.

---

## What AdBuster PRO Still Does
🧩 Nothing has been removed from the original AdBuster design:

🔊 detects ads  
⚡ detects sudden volume spikes  
🎚️ stabilizes volume in real time  
🧠 uses the trained ML model **`ad_detector.pkl`**  
🔄 runs full behaviour logic (**ADS, MUSIC, NORMAL, TALK, FALLBACK, etc.**)  
📡 reacts to deviations above the dynamic ML threshold  

The dynamic threshold simply makes these reactions **more accurate and more stable**.

---

## Benefits of the new threshold system
📊 stable ML threshold  
📊 predictable behaviour logic  
📊 improved ad/spike detection accuracy  
📊 no drifting  
📊 automatic adaptation to volume changes  
📊 GUI always reflects the true ML threshold  
📊 AdBuster PRO continues to operate exactly as before — now with a smarter threshold  

---

## Summary
📝 CEPA now provides a dynamic, environment‑aware threshold:

📝 **AVG = long‑term baseline**  
📝 **ML Threshold = AVG − 2**  
📝 **AdBuster PRO = detection + stabilization (unchanged)**  
📝 **ad_detector.pkl = still fully active**  
📝 **Behaviour Logic = still fully active**  

📝 The upgrade improves stability and responsiveness without removing any part of the original AdBuster ML system.

---

## Demo
🎥 [![CEPA Demo](https://img.youtube.com/vi/0rtAsAu81tQ/0.jpg)](https://youtu.be/0rtAsAu81tQ?si=uZTkkQieed-2VwPm)
