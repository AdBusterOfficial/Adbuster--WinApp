
# CEPA Logic – Threshold Evolution (Dynamic AVG − 2 → Calibrated Baseline + Manual Override + Auto‑Correction)

## 1. Previous Design – Dynamic ML Threshold (AVG − 2)

In the earlier CEPA Logic design, the ML threshold was fully dynamic:

- ML Threshold = AVG − 2
- AVG was a smoothed ~20‑minute acoustic baseline
- AVG was refreshed every 5 minutes
- The threshold followed long‑term listening habits automatically

This model required no user calibration — the system adapted itself over time.

---

## 2. Current Design – Calibrated Threshold + Auto‑Correction (±1)

In the current NR 5 implementation, the threshold is no longer computed as `AVG − 2`.  
Instead, it is defined by **calibration** and optionally adjusted by the **GUI slider**.

### Key properties:

- The system performs initial **calibration**, which sets the baseline threshold.
- The user may override this value using the GUI slider.
- The system stores the active threshold as `latest_threshold`.
- A long‑term buffer (`hour_buffer`) tracks the smoothed GUI level.
- CEPA applies small automatic corrections (±1) when needed:

```python
if avg < latest_threshold - 1:
    latest_threshold -= 1
elif avg > latest_threshold + 1:
    latest_threshold += 1
```

This keeps the threshold aligned with long‑term listening conditions without replacing user calibration.

---

## 3. Calibration and Manual Slider (Hybrid Model)

The threshold in NR 5 is not defined solely by the slider.  
The system first performs **calibration**, which establishes the initial baseline threshold used by CEPA Logic.

After calibration:

- the GUI slider provides manual override,
- CEPA enters manual mode for a short period (e.g., 3 seconds),
- during manual mode, automatic correction is paused,
- after timeout, CEPA resumes auto‑correction (±1) based on `hour_buffer`.

This results in a hybrid threshold model:

1. Calibration-defined baseline  
2. Manual override via slider  
3. Gentle auto‑correction (±1) for long‑term stability

The system no longer uses the fixed formula `AVG − 2`; instead, it relies on **calibration + manual control + auto‑stabilization**.

---

## 4. Manual Mode (GUI Override)

When the user moves the slider:

- CEPA switches to manual mode,
- the threshold is set directly to the slider value,
- automatic correction pauses for a short period,
- CEPA resumes normal operation automatically.

Manual mode does not replace CEPA Logic — it only provides temporary user control.

---

## 5. What AdBuster PRO Still Does

Regardless of the threshold model, AdBuster PRO still:

- detects ads  
- detects sudden volume spikes  
- stabilizes volume in real time  
- uses the trained ML model (`ad_detector.pkl`)  
- runs full behaviour logic (ADS, MUSIC, NORMAL, TALK, FALLBACK, etc.)  
- reacts to deviations above or below the active threshold  

The change affects how the threshold is defined, not the core detection and stabilization logic.

---

## 6. Summary

- The original CEPA Logic used a dynamic ML threshold: `AVG − 2` with auto‑refresh.  
- The current NR 5 implementation uses a calibrated threshold:  
  - baseline from calibration,  
  - optional manual override via slider,  
  - auto‑correction (±1) for stability.  
- CEPA Logic remains environment‑aware, but the threshold now depends on calibration, not a fixed AVG‑based formula.

This document reflects the real behaviour of the current NR 5 implementation, while acknowledging the previous dynamic design.
