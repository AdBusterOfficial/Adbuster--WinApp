# CEPA Logic – Threshold Evolution (Dynamic AVG − 2 → Calibrated + Auto‑Correction)

## 1. Previous Design – Dynamic ML Threshold (AVG − 2)

In the earlier CEPA Logic design, the ML threshold was fully dynamic:

- **ML Threshold = AVG − 2**
- AVG was a smoothed ~20‑minute acoustic baseline
- AVG was refreshed every 5 minutes
- The threshold followed long‑term listening habits automatically

This model required no user calibration — the system adapted itself over time.

---

## 2. Current Design – Calibrated Threshold + Auto‑Correction (±1)

In the current implementation (NR 5), the threshold is no longer computed as `AVG − 2`.  
Instead, it is **calibrated by the user** via the GUI slider and then gently corrected by the system.

### Key properties:

- The user sets the threshold manually using the slider.
- The system stores this value as `latest_threshold`.
- A long‑term buffer (`hour_buffer`) tracks the smoothed GUI level.
- An auto‑correction mechanism adjusts the threshold by **±1** when needed:

```python
if avg < latest_threshold - 1:
    latest_threshold -= 1
elif avg > latest_threshold + 1:
    latest_threshold += 1

