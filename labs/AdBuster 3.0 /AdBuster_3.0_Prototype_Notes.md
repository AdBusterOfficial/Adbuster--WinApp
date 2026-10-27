<p align="center">
  <img src="https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/header.png">
</p>

<br>

# AdBuster 3.0 — Prototype Notes

## Overview

AdBuster 3.0 is an experimental hybrid prototype integrating audio monitoring, ML-based ad-like signal detection, CEPA logic, volume-target management, and Broadlink IR control in a single application.

The prototype combines these components to explore context-aware TV volume stabilization.

## Integrated Components

- Live microphone monitoring and RMS-based signal-level measurement.
- Existing four-feature ML model and CEPA logic.
- Time-of-day volume targets and manual calibration.
- Automatic and manual Broadlink IR control.
- Connection monitoring and safeguards for automatic volume adjustments.
- Local SQLite logging and CSV export for reviewing test results.

Raw microphone audio is not stored.

## Initial Test Observations

Initial logs from 25–26 October 2026 show that the integrated system can process audio samples, record detection and decision events, and issue volume-control requests through the local control service.

The logs also identified areas requiring further investigation:

- Audio-device errors and recovery.
- Availability of the local TV-control service.
- The relationship between ML detections, CEPA context, and audio-level thresholds.
- Validation of automatic volume adjustments under consistent test conditions.

The reviewed logs contain multiple code and configuration revisions. They therefore provide preliminary observations rather than results from a single controlled test.

## Current Test Configuration

- **Ad-context level gate:** 16 on a 0–60 scale.
- **Automatic volume down:** Level above target by more than 2 points for 2 seconds.
- **Automatic volume up:** Level below target by more than 2 points for 6 seconds.
- **Automatic control limit:** 20-second cooldown, maximum three steps per two minutes.
- **Manual volume repeat guard:** 0.5 seconds.
- **Calibration:** 20 seconds.
- **Default targets:** Morning 18, afternoon 20, evening 19, night 17.

These values describe the current test configuration and may change during development.

## Test Procedure

For comparable results, keep the configuration and target level consistent throughout each test session.

After each test session, the sample and event data are exported to CSV files, and the session duration and TV content are recorded. The exported files include historical records accumulated in the local database, not just data from the most recent session.

<br>



[← Back to AdBuster PRO Repository](https://github.com/AdBusterOfficial/Adbuster--WinApp)

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

<br>

<p align="center">
  <img src="https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/footer.png" alt="Footer" width="100%">
</p>

