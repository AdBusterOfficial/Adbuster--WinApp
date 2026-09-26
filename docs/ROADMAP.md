<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

<br>

# 🛣️ AdBuster — Project Roadmap

<br>

## 🎯 Current Focus: Reliable Operation and Behavioral Data

<br>

AdBuster is a free Windows application available for testing. The current prototype can be downloaded as a ZIP archive from this repository.

The application monitors television audio and can control the volume of compatible infrared devices in response to changing audio conditions. The project focuses on improving listening comfort while preserving user control and predictable system behavior.

AdBuster is being developed to explore context-aware audio control for TVs and other compatible devices.

At the center of the project is CEPA Logic (Context Event Pattern Analysis), a behavioral framework designed to evaluate contextual event patterns rather than react to isolated measurements. The framework analyzes relationships between audio characteristics, operating modes, detected events, system decisions, and historical observations recorded during operation.

The current development phase focuses on collecting and evaluating behavioral data in order to better understand how contextual patterns emerge during real-world use. These observations are used to identify situations that may require volume adjustments and to assess the consistency and predictability of system behavior.

The system records contextual information such as audio levels, operating modes, model outputs, detected events, and volume-control decisions. Behavioral data is stored locally in a SQLite database and used for analysis and development.

Automatic self-adjustment is not currently enabled.

No behavioral data is transmitted to external servers. All recorded information remains on the local device.

The prototype is offered for testing and feedback. Performance and compatibility may vary between systems and devices.

---

## 🧠 About CEPA Logic

CEPA Logic (Context Event Pattern Analysis) is the central research component of the AdBuster project.

Rather than relying solely on thresholds or individual measurements, CEPA is designed to evaluate combinations of contextual observations collected over time. The framework is intended to support more stable and predictable volume-control decisions by considering broader operating conditions instead of reacting to isolated events.

The current objective is to understand and validate contextual behavioral patterns observed during real-world operation before introducing any adaptive decision-making mechanisms.

---

## 📋 Development Principles

- Preserve the existing GUI, audio plot, calibration controls, and modular architecture.
- Prioritize predictable operation and safe volume control.
- Use real operating data to evaluate changes.
- Make and assess changes incrementally.
- Keep the user in control of system behavior.

---

## 🔭 Future Direction

Once enough reliable data has been collected and evaluated, the project may explore carefully controlled self-regulation.

Any future adaptive behavior should be based on validated contextual patterns and introduced only after its effects can be assessed.

The longer-term concept is a universal audio-control device for infrared-controlled TVs and other compatible equipment. This remains a concept for future exploration and is not a finished or currently available product.

---

## 🚧 Project Status

AdBuster is an ongoing research and development project.

The software should be considered experimental and is not presented as a finished commercial product. Features, behavior, compatibility, and performance may change as development continues.

Testing feedback and real-world observations are used to evaluate future improvements and development priorities.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>
