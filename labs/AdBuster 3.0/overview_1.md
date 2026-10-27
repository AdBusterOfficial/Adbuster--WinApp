# AdBuster 3.0 — Interface Overview
![AdBuster 3.0 Prototype](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AdBuster%203.0/screenshots/AdB_3.0_s02.png)

## Screenshot 2 Description

This screenshot shows the AdBuster 3.0 hybrid prototype during active audio monitoring, with automatic volume control enabled and the Broadlink TV controller connected.

The interface provides a real-time overview of the system's main components and current operating state.

## Interface Components

- **Live Sound Level** — displays the smoothed audio level and RMS measurement.
- **Ad Detection** — shows the ML model status and ad-like signal detection information.
- **Volume Target** — displays the active target level, adjustment band, and calibration controls.
- **TV Connection** — shows the Broadlink controller connection status and device configuration.
- **Signal Monitor** — plots recent audio levels against the target level.
- **Current Decision** — displays the current control decision and CEPA analysis.
- **Control Center** — provides microphone selection, manual TV commands, automatic-control status, and CSV export.

## Observed State

At the time of this screenshot:

- Automatic volume control is enabled.
- The Broadlink controller is connected.
- Audio monitoring is active.
- The ML model is still loading and waiting for the required audio samples.
- No TV command has been issued during the current session.

This screenshot documents the interface state at a particular point during prototype testing. It does not, by itself, establish the accuracy or reliability of automatic volume control.
