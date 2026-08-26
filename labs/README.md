
# AdusterML Research Labs

This directory contains **research-only materials** used during development and prototyping of the offline AdusterML machine learning pipeline.  
Nothing in this folder is part of the main AdBuster PRO application.

---

## 📄 Research Dataset — `data.csv`

`data.csv` is a MFCC‑based feature dataset generated from a small, controlled set of audio samples (AD vs NORMAL).  
It exists solely for:

- validating MFCC feature stability,  
- testing RandomForest behavior,  
- demonstrating the offline DSP → ML workflow,  
- serving as a baseline for future dataset expansion.

This is **not** production data.

---

## 🧠 Research Model — `ad_detector.pkl`

`ad_detector.pkl` is a **research-only RandomForest model** trained inside the offline AdusterML pipeline.

It was generated using:

- 29 MFCC‑based audio features  
- a 300‑tree RandomForest (depth‑limited, bootstrap‑stable)  
- a controlled AD/NORMAL dataset

Model link:  
[📦 Download ad_detector.pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/ad_detector.pkl)

This model is **not** used in AdBuster PRO.  
It serves only as a prototype for testing binary audio classification and future multi‑class logic.

---

## 🧪 Research Summary

An offline ML pipeline was developed for AdBuster PRO — covering the full workflow from raw audio samples to a fully trained RandomForest model.

The workflow includes:

- audio recording  
- MFCC feature extraction  
- CSV dataset generation  
- RandomForest model training  
- model export (`ad_detector.pkl`)

Initial evaluation shows:

- **87% accuracy**  
- **0.87 weighted F1-score**  
- **perfect recall for AD detection**

These results confirm that the MFCC feature space and RandomForest decision paths form a stable baseline for future research.

---

## 📷 Research Screenshot

![AdusterML Data Builder](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/AdusterML_data_builder.png)

---

## 📌 Purpose of this folder

The `labs/` directory is a **sandbox for experimentation**, used to:

- test offline DSP/ML workflows,  
- validate feature extraction logic,  
- prototype future multi‑class audio detection,  
- store temporary research artifacts.

It is intentionally separated from the main application codebase.
