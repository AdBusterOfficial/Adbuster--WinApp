
# AdBuster 3.0 Prototype Notes

## Purpose

AdBuster 3.0 is an integrated prototype for real-world testing. It brings live audio monitoring, ad-like signal analysis, CEPA decision support, time-of-day targets, and Broadlink TV volume control into one application. The prototype is being refined through logged observation rather than presented as a finished production system.

## What is integrated

- A live microphone meter based on block RMS, with a fixed 0–60 chart scale and a ten-second history.
- The existing four-feature ad model and CEPA logic working alongside target-level rules.
- Separate saved targets for morning, afternoon, evening, and night, with a 20-second calibration flow.
- Automatic and manual Broadlink controls, a connection watchdog, cooldown and command-rate limits.
- Local sample and event logging in SQLite, plus paired CSV exports for later review. Raw microphone audio is not stored.

## First observations from the logs

The reviewed database covers 25–26 October 2026 and contains 55,891 samples and 7,592 events. It includes several code and settings revisions, so the full period should not be treated as one controlled test.

- The `rms-v3` meter accounts for 44,215 samples. Only five level readings and seven raw readings were zero, which is a strong improvement over the earlier meter records in the same database.
- The event log records 348 automatic command reservations. VolMaster returned an accepted result for 343; four requests timed out under an older 0.8-second timeout, and one reservation has no matching result. The later records use a 20-second automatic cooldown.
- The logs contain 102 manual requests. Seventy-nine were accepted. Other entries show earlier 60-second and one-second manual guards, so they do not represent the current 0.5-second manual repeat guard.
- The ML model recorded 253 confirmed-detection sample rows, while only five rows entered `AD` context. The level gate was subsequently changed to 16. There were no further confirmed detections after the restart in the reviewed period, so the effect of the new threshold still needs a suitable test.
- Sixteen audio errors report `Invalid device`, clustered around 21:20–21:22 UTC. The sample log also records `server_connected=0` in about 19% of `rms-v3` samples. This means the local VolMaster status endpoint did not respond in those samples; it does not by itself prove that the Broadlink device was disconnected.

The logs confirm that the integrated command path can reach VolMaster and record its responses. They also identify the next reliability and tuning areas: audio-device recovery, local service availability, and validation of the lower ad-context level gate.

## Current test settings

- Ad context level gate: 16 on the 0–60 meter scale.
- Automatic volume down: more than 2 points above target for 2 seconds.
- Automatic volume up: more than 2 points below target for 6 seconds.
- Automatic cooldown: 20 seconds, with a maximum of three automatic steps per two minutes.
- Manual volume repeat guard: 0.5 seconds.
- Calibration duration: 20 seconds.
- Default targets: morning 18, afternoon 20, evening 19, and night 17. The reviewed `settings.json` has a calibrated evening target of 17.54.

For comparable tests, keep these settings and the active target fixed during each session. Export both CSV files after a session and record the time period and TV content. The export contains historical data accumulated in the local database, not just the latest session.
