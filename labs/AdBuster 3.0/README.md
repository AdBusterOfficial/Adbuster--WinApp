![AdBuster 3.0 Prototype](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AdB_3.0%20prototype.png)

<br>

# AdBuster 3.0 — Hybrid Prototype

An isolated experimental build exploring hybrid behavioural stabilization for TV volume control.

AdBuster 3.0 integrates the existing trained ad-detection model, CEPA logic, audio feature extraction, volume-target management, and Broadlink IR control into a single application window. The original project files remain unchanged.

This laboratory prototype focuses on integrating these components and observing their behaviour under controlled testing conditions.

For the experimental scope, initial observations, configuration details, and follow-up items, see [AdBuster 3.0 Prototype Notes](AdBuster_3.0_Prototype_Notes.md).


## Prototype Demo

[![AdBuster 3.0 — Hybrid Prototype Demo](https://img.youtube.com/vi/jprODtEdIpo/0.jpg)](https://youtu.be/jprODtEdIpo?si=p3QyttgQVAapupnH)

This video presents the first demonstration of the AdBuster 3.0 hybrid prototype and its integrated components.


## Hybrid Analysis

The prototype combines:

- **Audio analysis** — RMS-based signal-level measurement and smoothing.
- **ML ad detection** — the existing four-feature model.
- **CEPA logic** — contextual analysis supporting volume-control decisions.
- **Volume-target management** — separate target levels for four daily periods, with manual adjustment and calibration.
- **IR control** — Broadlink-based TV commands with connection monitoring and safety limits.

Automatic volume corrections depend on target-level conditions and timing rules. CEPA suggestions are subject to these conditions rather than triggering volume changes directly.

## Calibration

Calibration measures the median audio level over a 20-second period and sets the active period's target two points above the measured median.

Calibration does not issue a volume command. Each daily period maintains its own target, and the active target changes automatically according to local time.

The slider adjusts the target level, not the TV volume directly.

## Safety and Data

- Automatic volume corrections are subject to timing and rate limits.
- Manual volume commands follow separate safeguards.
- Automatic corrections pause when the controller is disconnected and during the defined reconnection or calibration intervals.
- Audio is analysed locally; raw audio is not saved.
- Session data, analysis samples, decisions, and command events are stored locally in `data/session.sqlite3`.
- CSV export provides detailed sample data and a separate event log.

The ML model detects ad-like audio patterns; it does not independently identify dialogue or classify music in this simplified build.

## Experimental Status

AdBuster 3.0 is an experimental laboratory build intended for integration testing and behavioural evaluation. Its implementation and observed behaviour should be assessed against the actual source code and test results.

---

[← Back to AdBuster PRO Repository](https://github.com/AdBusterOfficial/Adbuster--WinApp)

---

<br>

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

<br>

<p align="center">
  <img src="https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/footer.png" alt="Footer" width="100%">
</p>

