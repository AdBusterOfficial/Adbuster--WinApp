
# Audio‑ML Training Pipeline — AdBuster PRO / CEPA Logic

![Training Pipeline Diagram](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AdBuster_CEPA_ML_Training-pipeline.jpg)

## 🤖 Overview
This document describes the full training pipeline used to build and deploy the audio‑ML classifier for **AdBuster PRO (CEPA Logic)**.  
The workflow is designed to be clean, deterministic and fully aligned with CEPA’s stability requirements.  
A consistent dataset, proper WAV formatting and structured feature extraction ensure a reliable and predictable ad‑detection model.

---

## 🎛️ Pipeline Breakdown

### 📂 1. Dataset Preparation
Organise your audio samples into two categories:
- **ADS** — advertisement‑only audio  
- **NORMAL** — movies, music, dialogue, silence, programs  

If your samples are MP3, convert them to WAV to avoid compression artefacts that negatively affect MFCC, RMS and spectral features.

---

### 📊 2. Feature Extraction
Generate a deterministic feature set containing:
- MFCC  
- RMS  
- Spectral metrics (centroid, rolloff, etc.)  

These features form the numerical representation used by the classifier.

---

### 🧱 3. Dataset Assembly
Combine extracted features with **AD/NORMAL** labels into a structured dataset.  
This dataset becomes the input for the training stage.

---

### 🧠 4. Model Training
Run the training pipeline to produce the final machine‑learning classifier.  
The output is the model used by AdBuster PRO for real‑time ad detection.

---

### 🔍 5. Testing & Validation
Evaluate:
- prediction stability  
- false positives  
- CEPA reaction timing  
- behaviour on real audio samples  

Validation ensures the model performs reliably in live conditions.

---

### 🚀 6. Deployment
Place the trained model in the system’s ML directory and restart AdBuster PRO.  
The classifier becomes active immediately and CEPA begins real‑time detection.

---

## 📌 Summary
A clean dataset, proper WAV conversion and a consistent pipeline result in a stable and reliable CEPA‑driven ad‑detection model.  
This workflow ensures deterministic behaviour, predictable reactions and high stability across diverse audio environments.

