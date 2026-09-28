
<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

---

<br>

# AdBuster 2.0 PRO

A prototype for TV volume stabilization.

AdBuster 2.0 PRO is a Windows-based prototype that explores how real-time audio analysis can be combined with automated TV volume control.

The system monitors audio through a microphone, evaluates loudness patterns, and can control TV volume through a Broadlink infrared device when configured by the user.

## How It Works

1. A microphone captures the TV audio for analysis.
2. AdBuster evaluates loudness changes and audio behaviour in real time.
3. When predefined conditions are met, the system may trigger a volume reduction.
4. If a compatible Broadlink device is configured, an infrared volume command can be sent to the TV.
5. When audio returns to normal conditions, the previous volume level can be restored.

The computer and Broadlink device must be connected to the same local network. Either Wi-Fi or Ethernet may be used.

## Technology Areas

The prototype combines several experimental components:

- Real-time microphone audio analysis
- CEPA-based behavioural logic
- Machine-learning components
- Broadlink infrared device integration

Machine-learning models can be trained offline using collected feature data. Model training is not performed during live audio monitoring.

## Privacy

AdBuster does not store raw microphone recordings such as WAV files.

The application may collect derived acoustic measurements for research, testing, and model-development purposes. These measurements are numerical data and do not contain audio recordings.

No data is uploaded to cloud services. Processing is performed locally on the user's device.

## Project Status

AdBuster 2.0 PRO is an experimental prototype intended for testing and evaluation.

Performance may vary depending on:

- microphone quality,
- TV audio characteristics,
- environmental conditions,
- Broadlink device configuration.

Feedback and testing results are welcome.

## Distribution

The public PRO package contains compiled application files and supporting resources.

Source code is not included.

Use of the software is governed by the AdBuster PRO License Agreement.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>
