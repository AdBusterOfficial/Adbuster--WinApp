<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

<br>

# AdBuster — Project Roadmap

## Current focus: reliable operation and behavioral data

AdBuster is currently a free Windows application available for testing. The basic prototype can be downloaded as a ZIP archive from this repository.

AdBuster is a Windows application that monitors television audio and can control the volume of compatible infrared devices in response to changing audio conditions. The project focuses on improving listening comfort while preserving user control and predictable system behavior.

The application is being developed to explore context-aware audio control for TVs and other compatible devices. Its current focus is reliable operation and passive collection of behavioral data. The system records contextual observations such as audio levels, operating modes, model outputs, detected events, and volume-control decisions. These records help identify patterns in how the application behaves during real-world use.

Behavioral data is stored locally in a SQLite database and used for analysis and development. Automatic self-adjustment is not currently enabled.

No behavioral data is transmitted to external servers. All recorded information remains on the local device.

AdBuster explores an approach to audio control that, in my experience, is not commonly available in this form. The prototype is offered for testing and feedback; its performance and compatibility may vary between systems and devices.

## Development principles

- Preserve the existing GUI, audio plot, calibration controls, and modular architecture.
- Prioritize predictable operation and safe volume control.
- Use real operating data to evaluate changes.
- Make and assess changes incrementally.
- Keep the user in control of system behavior.

## Future direction

Once enough reliable data has been collected and evaluated, the project may explore carefully controlled self-regulation. Any future adaptive behavior should be based on validated contextual patterns and introduced only after its effects can be assessed.

The longer-term concept is a universal audio-control device for infrared-controlled TVs and other compatible equipment. This is a concept for future exploration, not a finished or currently available product.

## Project status

AdBuster is an ongoing development project. The downloadable ZIP contains a basic Windows prototype provided free of charge for testing.

The software should be considered experimental and is not presented as a finished commercial product. Features, behavior, compatibility, and performance may change as development continues.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>
