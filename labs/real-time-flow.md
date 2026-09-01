
# Real‑Time Flow Behind Behaviour‑Based Volume Control

![Real‑time flow diagram](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/real%E2%80%91time%20flow%20behind.png)

## Overview
This diagram illustrates the behaviour‑driven real‑time volume control pipeline used inside AdBuster PRO.  
Instead of reacting directly to loudness, the system evaluates how the audio behaves — its stability, transitions, compression artefacts and dynamic movement.  
This behaviour‑first approach ensures predictable and stable reactions, even when the incoming audio is chaotic.

The pipeline combines deterministic feature extraction, lightweight classification and CEPA Logic, which acts as a contextual decision layer governing when the system should adjust volume, hold state or wait for clarity.

---

## Pipeline Breakdown

### Microphone Input
Raw audio frames captured from the environment.  
These frames naturally contain instability: spikes, dips, compression artefacts and sudden transitions.

### Behavioural Feature Extraction
Deterministic features describing how the signal moves, not how loud it is.  
Extracted metrics include:
- RMS  
- Dynamics  
- Compression pattern  
- Stability  

These features form the behavioural profile of each frame.

### Normalization
A scaler normalizes all extracted features.  
This ensures the classifier receives consistent input regardless of moment‑to‑moment variability.

### Lightweight Classifier
A compact model evaluates each frame and labels it as:
- stable  
- unstable  

The classifier provides context, not final decisions.

### CEPA Decision Layer
CEPA interprets the classifier’s output in real time, considering:
- trend  
- timing stability  
- reaction history  
- contextual clarity  

Based on this, CEPA declares:
- **Adjust** — apply a volume correction  
- **Hold** — maintain current state  
- **Wait** — defer action until the environment stabilizes  

### Broadlink IR Output
Only when CEPA determines that the environment is meaningful, the IR module executes the actual volume command.

---

## Purpose
This behaviour‑driven pipeline ensures that AdBuster PRO reacts only to meaningful changes in the audio environment.  
It avoids false triggers from random spikes or noise, providing deterministic, stable and predictable loudness control — even when the audio itself is unstable.
