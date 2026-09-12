# ⚙️ AdBuster PRO — Overview

AdBuster PRO is a lightweight real‑time audio stabilizer designed to keep TV volume consistent across different types of content.  
It monitors the incoming audio signal, detects sudden loudness changes, and adjusts the volume automatically according to user‑defined configuration.

---

## 🧠 Core Components

- **ML 4‑Feature Detector** — Classifies short audio segments as *NORMAL* or *AD* to identify abrupt loudness changes.
- **CEPA Logic Pro Engine** — Evaluates audio level, thresholds, time‑of‑day profiles, and ML flags to decide whether a volume adjustment is needed.
- **IR Safety Layer** — Prevents excessive or rapid IR commands, handles IR transmission errors, and ensures stable long‑term behavior.
- **Deadzone & Fallback Control** — Maintains stable volume when the signal drifts outside the expected range, using soft corrective actions.

---

## 🔧 General Behavior

AdBuster PRO:

- Analyzes the audio stream in real time  
- Detects abnormal loudness patterns  
- Decides whether a volume change is appropriate  
- Sends IR commands based on user configuration  
- Applies safety rules to keep adjustments smooth and controlled  
- Adapts thresholds to time‑of‑day or manual user input  

The reaction strength is fully configurable.  
AdBuster PRO does not enforce a fixed number of volume steps — the magnitude of each adjustment depends entirely on user preferences and environment.

---

## 🧩 Key Advantages

- Real‑time operation  
- Lightweight and efficient  
- Fully local processing  
- No cloud dependencies  
- Stable, predictable behavior  
- Flexible configuration for different environments  
- Designed to avoid unnecessary or disruptive volume changes  

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**

