
<p align="center">
  <img src="https://github.com/user-attachments/assets/9af9e7e2-2091-43f6-bb97-bdb2a31181e1" width="200">
</p>

<h1 align="center">AdBuster 2.0 PRO – TV Volume Stabilizer</h1>

<p align="center">
  <!-- BADGES TUTAJ -->
  <img src="https://img.shields.io/badge/version-2.0-blue">
  <img src="https://img.shields.io/badge/platform-Windows-blue">
  <img src="https://img.shields.io/badge/python-3.10%2B-yellow">
  <img src="https://img.shields.io/badge/license-PRO%20%2F%20Proprietary-red">
  <img src="https://img.shields.io/badge/status-active-success">
  <img src="https://img.shields.io/badge/privacy-100%25%20offline-orange">
</p>

<p align="center">
  Offline audio stabilization engine powered by ML/AI and CEPA Logic.
</p>

<p align="center">
  A small Windows tool that lowers loud TV ads automatically and restores normal volume smoothly.
</p>

---

## 📌 Overview
AdBuster PRO is a lightweight Windows application that monitors TV audio in real time and automatically reduces the volume when loud commercials appear.  
When normal audio returns, the volume is restored smoothly and naturally.

No cloud.  
No accounts.  
No telemetry.  
No data collection.  
Everything runs locally on your PC.

---

## 🎯 Key Features
- 🔊 **Real‑time loudness detection**  
- 📉 **Automatic volume reduction during commercials**  
- 🔄 **Smooth volume restoration after ads**  
- 📡 **IR blaster support (Broadlink RM series)**  
- ⚙️ **Configurable thresholds and reaction times**  
- 🖥️ **Runs silently in the background**  
- 🔐 **Fully local — no internet required**

---

## 🛠️ How It Works
1. A microphone listens to the TV audio.  
2. When a sudden loudness spike is detected (typical for ads), AdBuster PRO decides whether to lower the volume.  
3. The app sends a command to the local Flask server (VolMaster).  
4. VolMaster forwards the IR command to the Broadlink device.  
5. Broadlink sends the IR signal to the TV.  
6. When audio returns to normal, the app restores the previous volume level.

All logic is processed locally — no cloud, no external servers.

---

## 🧩 Architecture Diagram (High‑Level)

Below is a simplified architecture diagram showing how the main components  
of AdBuster PRO interact. This diagram does not reveal internal algorithms  
or implementation details.

```
┌────────────────────────────┐
│        MICROPHONE          │
│    (raw audio signal)      │
└──────────────┬─────────────┘
               │ audio frames
               ▼
┌────────────────────────────┐
│        AUDIO ENGINE        │
│  RMS / mean / std / range  │
│   smoothing / GUI level    │
└──────────────┬─────────────┘
               │ features
               ▼
┌────────────────────────────┐
│       ML CONTROLLER        │
│      (ml_controller.py)    │
│ - collects RMS history     │
│ - calls ml_pro_update()    │
│ - confirms AD / NORMAL     │
│ - toggles ad_mode          │
└──────────────┬─────────────┘
               │ AD / NORMAL state
               ▼
┌────────────────────────────┐
│         CEPA ENGINE        │
│ - contextual analysis      │
│ - deadzone / stable zone   │
│ - spike detection          │
│ - anti-spam limits         │
│ - VOL_UP / VOL_DOWN        │
└──────────────┬─────────────┘
               │ decision
               ▼
┌────────────────────────────┐
│     AdBuster App Logic     │
│ - pending_cmds queue       │
│ - cooldown timers          │
│ - 2x up/down safety limits │
│ - sends HTTP commands      │
└──────────────┬─────────────┘
               │ HTTP GET /send?cmd=...
               ▼
┌────────────────────────────┐
│      VolMaster Server      │
│   (Flask API, port 5000)   │
└──────────────┬─────────────┘
               │ IR command
               ▼
┌────────────────────────────┐
│   Broadlink IR Blaster     │
│ (RM Mini / RM Pro series)  │
└──────────────┬─────────────┘
               │ infrared signal
               ▼
┌────────────────────────────┐
│      TV / Audio Device     │
│   (volume changes applied) │
└────────────────────────────┘

```

## 📸 Screenshots

## 1. AdBuster PRO – Main Interface (A)
![AdBuster PRO – Main UI A](https://github.com/user-attachments/assets/ed7a78b9-ce35-45b2-8649-b8c81b22ce54)

## 2. AdBuster PRO – Main Interface (B)
![AdBuster PRO – Main UI B](https://github.com/user-attachments/assets/7759397f-512e-4bb3-aa04-ad17a88b15ca)

## 3. CEPA Setup – Personalization Wizard
![CEPA Setup](https://github.com/user-attachments/assets/151b605e-613f-4db7-9b64-b563d2a3eeb4)

## 4. AdBuster ML PRO – Machine Learning Panel
![AdBuster ML PRO](https://github.com/user-attachments/assets/918031dd-67c9-4e87-8f1d-8ba32a104473)

## 5. VolMaster – Broadlink Server
![VolMaster Server](https://github.com/user-attachments/assets/91e95bbd-05d1-4c6a-84a6-dcb276ccf96e)

## 6. Full Application View – All Modules Working Together
![Full App View](https://github.com/user-attachments/assets/5de05bd7-acf5-4345-872b-0c55b403f451)

## 7. Demo Video (15 seconds)

Short demo recorded quickly on a phone — quality is low, but it clearly shows how the app reacts to loudness spikes and sends IR volume commands.

▶️ Download the video:  
https://github.com/AdBusterOfficial/Adbuster--WinApp/releases/latest/download/AdBuster_demo.mp4

---

## 8. Documentation
➡️ Full documentation is available in the [docs](docs) folder.

---

## 9. CEPA Logic License

This repository includes an additional proprietary license covering the **CEPA Logic**
(Contextual Event Pattern Analysis Logic) analytical framework.

For full terms, see the dedicated license file:

➡️ [CEPA_LOGIC_LICENSE.txt](./CEPA_LOGIC_LICENSE.txt)

---

## 10. CEPA Logic — Technical Overview
A full technical explanation of how CEPA Logic works — including decision flow, contextual evaluation, human‑like behavior model, data processing pipeline and real‑world examples — is available in a dedicated document:

➡️ [CEPA_Logic_Overview.txt](CEPA_Logic_Overview.txt)

This file contains:

- detailed description of CEPA architecture  
- explanation of all decision types (BOOST, BLOCK, DELAY, SMOOTH, ALLOW)  
- real‑time data flow  
- human‑reaction analogy  
- example code  
- step‑by‑step event walkthrough  

---

## 11. For Investors & Partners

AdBuster 2.0 PRO is a unique offline technology that combines real‑time microphone analysis,
contextual CEPA logic, on‑device machine learning and Broadlink IR control to automatically
stabilize TV audio. The system works on any Windows PC or laptop and supports virtually any
IR‑based TV.

**Opportunities:**
- Licensing for TV, audio and smart‑home manufacturers  
- Integration with streaming platforms and media devices  
- Unique IP: CEPA + ML + IR control pipeline  
- Open to commercial proposals and partnership discussions.

---

## 12. Support & Contributions

AdBuster 2.0 PRO is an independent R&D project developed with passion, countless hours of testing, and a strong focus on offline privacy‑first technology.

If you find this project useful, you can support its development in several ways:

### ☕ Support the project
<p align="center">
  <img src="https://github.com/user-attachments/assets/cc58417d-c23a-4a4a-a3da-c0e5a4111b29" width="200">
</p>

- Donate via PayPal (QR code above)
- Buy me a coffee
- Share the project with others
- Star the repository ⭐

### 🤝 Contribute
- Report issues
- Suggest new features
- Propose integrations (TV, audio, smart‑home, IR devices)
- Help test compatibility with Broadlink IR devices

Every form of support helps the project grow and evolve.

Thank you for being part of the journey.

---

## 13. Changelog

### v2.0 — Current Release
- Added ML/AI PRO mode
- Added CEPA Logic integration
- Added Broadlink IR control (VolMaster)
- Improved real‑time audio stabilizer
- Added 10‑second audio plot visualization
- New UI layout and redesigned modules
- Full offline processing (no cloud, no telemetry)

### v1.5
- Improved volume detection accuracy
- Added basic CEPA logic
- Added early Broadlink IR tests
- UI improvements

### v1.0
- Initial release of AdBuster PRO
- Basic real‑time volume stabilizer
- First working Windows build

---

## 14. Roadmap

### CEPA Logic v2
A redesigned decision‑making engine with improved context awareness, better handling of borderline audio states, and more adaptive thresholds. The goal is to make CEPA less binary and more “human‑like” in how it reacts to dynamic audio environments.

### ML Auto‑Training Mode
A local, offline training pipeline that allows the model to refine itself based on the user’s environment. The system will collect short audio snapshots, classify them, and update the model without sending any data outside the device.

### Multi‑Device IR Support
Extended IR control layer supporting multiple TVs, soundbars, receivers and Broadlink‑compatible devices. The goal is to allow users to define multiple profiles and switch between them dynamically.

### Enhanced Broadlink Integration
A more robust IR communication layer with improved retry logic, faster command dispatching, and better handling of Broadlink device discovery. This includes support for additional Broadlink models and improved error recovery.

### New UI Modules
Additional interface components for monitoring, diagnostics and customization:
- real‑time CEPA decision graph  
- ML confidence visualizer  
- IR command monitor  
- advanced audio calibration panel  

---

📩 **Contact:**  
[Official Contact Form](https://sites.google.com/view/adbuster-winapp/contact?authuser=0)


© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.
