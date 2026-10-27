
# AdBuster 3.0 — Hybrid Prototype

An isolated experimental build exploring hybrid behavioural stabilization for TV volume control.

AdBuster 3.0 integrates the existing trained ad-detection model, CEPA logic, audio feature extraction, volume-target management, and Broadlink IR control into a single application window. The original project files remain unchanged.

This laboratory prototype focuses on integrating these components and observing their behaviour under controlled testing conditions.

For the experimental scope, initial observations, configuration details, and follow-up items, see [AdBuster 3.0 Prototype Notes](AdBuster_3.0_Prototype_Notes.md).

## Quick Start

1. Install Python 3.10+ and the dependencies listed in `requirements.txt`.
2. Run `Start.bat` to launch AdBuster and its local TV-control service.
3. Wait for `TV CONTROLLER CONNECTED`, verify the Broadlink IP and MAC addresses, and connect the controller.
4. Click `START LISTENING` to begin audio analysis and enable automatic volume control.
5. Use the manual IR controls when needed. Click `STOP LISTENING` to pause automatic control.

The application provides volume, mute, and power commands through the Broadlink controller.

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

## Device Configuration

The prototype uses a copy of the Broadlink IP/MAC configuration and IR codes from the source project.

Configuration, logs, and runtime data are maintained within the prototype folder, allowing it to run separately from the existing application.

## Experimental Status

AdBuster 3.0 is an experimental laboratory build intended for integration testing and behavioural evaluation. Its implementation and observed behaviour should be assessed against the actual source code and test results.

See [AdBuster 3.0 Prototype Notes](AdBuster_3.0_Prototype_Notes.md) for further technical details.
