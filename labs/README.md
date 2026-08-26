
# Adbuster Research Labs

This directory contains research-only materials used during development and prototyping of the offline AdBuster machine learning pipeline.
Nothing in this folder is part of the main AdBuster PRO application.

---

## 📄 Research Dataset — `data.csv`

`data.csv` is a MFCC‑based feature dataset generated from a small, controlled set of audio samples (AD vs NORMAL).

**Download:**  
[📦 data.csv](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/data.csv)

It exists solely for:

- validating MFCC feature stability,
- testing RandomForest behavior,
- demonstrating the offline DSP → ML workflow,
- serving as a baseline for future dataset expansion.

This is **not** production data.

---

## 🧠 Research Model — `ad_detector.pkl`

`ad_detector.pkl` is a research-only RandomForest model trained inside the offline AdusterML pipeline.

It was generated using:

- 29 MFCC‑based audio features  
- a 300‑tree RandomForest (depth‑limited, bootstrap‑stable)  
- a controlled AD/NORMAL dataset  

**Download:**  
[📦 ad_detector.pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/ad_detector.pkl)

This model is **not** used in AdBuster PRO.  
It serves only as a prototype for testing binary audio classification and future multi‑class logic.

---

## ⚙️ How `data.csv` Was Generated

The dataset was created entirely offline inside AdusterML using the following workflow:

1. Recording short audio samples (AD and NORMAL conditions)  
2. Extracting 29 MFCC‑based features from each sample  
3. Normalizing and structuring the feature vectors  
4. Exporting all processed samples into a single `data.csv` file  

This CSV serves as the input for training the research RandomForest model (`ad_detector.pkl`).

---

## ⚠️ Limitations

- The dataset is small and controlled (AD vs NORMAL only)  
- The model is not optimized for real‑world audio variability  
- It is not intended for production use inside AdBuster PRO  
- It serves only as a baseline for future multi‑class audio logic  

---

## 🔭 Future Research Directions

- Expanding the dataset with more diverse audio conditions  
- Adding multi‑class classification (music, speech, noise, AD types)  
- Testing alternative feature spaces (spectral contrast, chroma, tonnetz)  
- Evaluating lightweight models for real‑time inference  

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

The `labs/` directory is a sandbox for experimentation, used to:

- test offline DSP/ML workflows,  
- validate feature extraction logic,  
- prototype future multi‑class audio detection,  
- store temporary research artifacts.  

This folder contains research artifacts only and is not part of the AdBuster PRO WinApp release.
