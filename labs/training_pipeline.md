# Audio‑ML Training Pipeline — AdBuster PRO / CEPA Logic

This document describes the full training pipeline used to build and deploy the audio‑ML classifier for AdBuster PRO (CEPA Logic).  
The process is clean, consistent, and fully aligned with CEPA’s stability requirements.

---

## Overview

The training pipeline consists of six stages:

1. Dataset preparation  
2. Feature extraction  
3. Dataset assembly  
4. Model training  
5. Testing and validation  
6. Deployment

A clean dataset, proper WAV formatting and a consistent workflow ensure a stable and reliable CEPA‑driven ad‑detection model.

---

## 1. Prepare Your Dataset

Organize your audio samples into two categories:

- **ADS** — only advertisements  
- **NORMAL** — movies, music, dialogue, silence, programs

If your samples are MP3, convert them to WAV first to avoid compression artifacts that negatively affect MFCC, RMS and spectral features.

---

## 2. Extract Audio Features

Generate a feature set containing:

- MFCC  
- RMS  
- Spectral metrics (centroid, rolloff, etc.)

These features form the numerical representation used by the classifier.

---

## 3. Build the Training Dataset

Combine the extracted features with AD/NORMAL labels into a structured dataset.  
This dataset is used as input for the training stage.

---

## 4. Train the Model

Run the training pipeline to produce the final machine‑learning classifier.  
The output is the model used by AdBuster PRO for real‑time ad detection.

---

## 5. Test and Validate

Evaluate:

- prediction stability  
- false positives  
- CEPA reaction timing  
- behaviour on real audio samples

Validation ensures the model performs reliably in live conditions.

---

## 6. Deploy

Place the trained model in the system’s ML directory and restart AdBuster PRO.  
The classifier becomes active immediately and CEPA begins real‑time detection.

---

## Summary

A clean dataset, proper WAV conversion and a consistent pipeline result in a stable and reliable CEPA‑driven ad‑detection model.

---

## Training Pipeline Diagram

*(The diagram below illustrates the full CEPA/AdBuster PRO audio‑ML workflow.)*

![Training Pipeline Diagram](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/AdBuster_CEPA_ML_Training-pipeline.jpg)


