## AdBuster Research Labs — R&D Branch

![AdBuster Hardware Concept](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/Banner_NEW_GOLD_labs.png)

This directory contains research‑only materials used during development and prototyping of the offline AdBuster machine learning pipeline.  
Nothing in this folder is part of the main AdBuster PRO application.

The image above is a **fictional hardware concept** — a futuristic vision of how AdBuster could look as a dedicated CEPA‑powered device.

---

### 🎧 CEPA Behaviour Examples
The AdBuster lab also contains behaviour previews showing how CEPA PRO reacts in real time:

- [CEPA_ads_behaviour.md](./CEPA_ads_behaviour.md)
- [AD_mode_logic.md](./AD_mode_logic.md)
- [fallback_logic.md](./fallback_logic.md)
- [mode_ML-Auto_on.md](./mode_ML-Auto_on.md)
- [CEPA_music_behaviour.md](./CEPA_music_behaviour.md)
- [CEPA_dialog_behaviour.md](./CEPA_dialog_behaviour.md)
- [music_mode_logic.md](./music_mode_logic.md)
- [CEPA_normal_behaviour.md](./CEPA_normal_behaviour.md)

### 🔵 Core Research Files
The core research files contain the main DSP/ML prototypes used during development of the offline AdBuster pipeline, 
including training workflows, feature extraction logic, model evaluation, and CEPA PRO decision‑flow experiments.

- [training_pipeline.md](./training_pipeline.md)
- [model.md](./model.md)
- [ad_detection_upgrade.md](./ad_detection_upgrade.md)
- [CEPA_PRO_Overview.md](./CEPA_PRO_Overview.md)
- [Behaviour_Zones.md](./Behaviour_Zones.md)
- [CEPA_RealTimeDecision_v2.md](./CEPA_RealTimeDecision_v2.md)
- [real-time-flow.md](./real-time-flow.md)

### 📦 Other Markdown Files
- [README.md](./README.md)

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

![AdusterML Data Builder](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/AdusterML_data_builder.png)

---

## 🔍 Why Metrics Differ Between Runs

This section explains why evaluation results may differ from the metrics shown in the upgrade analysis:  
- [ AD Detection Upgrade](./ad_detection_upgrade.md)

Small research datasets naturally produce fluctuating accuracy and F1‑scores between runs, especially when AD and NORMAL classes are imbalanced or highly variable.

### 🔹 1. Small Dataset Sensitivity
With limited samples, even minor changes in train/test splits can significantly affect metrics.  
Small datasets do **not** represent full real‑world variability, so results fluctuate more than in large‑scale ML pipelines.

### 🔹 2. Random Train/Test Splits
Each evaluation uses a different random split unless explicitly fixed.  
This changes:

- how many AD samples land in training vs testing  
- how many NORMAL samples land in training vs testing  
- the balance between classes  

Different splits → different metrics.

### 🔹 3. Class Difficulty Differences
The AD class is more uniform and has stronger MFCC signatures.  
The NORMAL class is more diverse and harder to model.

This naturally leads to:

- **higher AD precision/recall**  
- **lower NORMAL precision/recall**  
- overall accuracy shifting depending on class distribution in the test set

### 🔹 4. RandomForest Variability
RandomForest uses:

- bootstrap sampling  
- random feature selection  
- tree‑level randomness  

Even with the same dataset, the ensemble can produce slightly different decision boundaries between runs.

### 🔹 5. MFCC Feature Variability
MFCC features are stable but still sensitive to:

- sample length  
- noise floor  
- slight differences in preprocessing  

This can shift decision paths in the RandomForest.

---

## 🔹 Summary
Differences such as:

- **87% → 80% accuracy**  
- **0.87 → 0.80 weighted F1‑score**  
- class‑level changes (AD 0.83 vs NORMAL 0.74)

are **normal and expected** for a small research dataset.  
They do **not** indicate a problem with the model — they simply reflect the statistical nature of ML evaluation at early R&D stages.

---

## 📌 Purpose of this folder

The `labs/` directory is a sandbox for experimentation, used to:

- test offline DSP/ML workflows,  
- validate feature extraction logic,  
- prototype future multi‑class audio detection,  
- store temporary research artifacts.  

This folder contains research artifacts only and is not part of the AdBuster PRO WinApp release.

---

## 📦 Prototype Download — AdBuster v2.0

The standalone AdBuster prototype (v2.0) is available as a public release containing the early build and open technical documentation:

**➡️ [AdBuster v2.0 Prototype Release](https://github.com/AdBusterOfficial/Adbuster--WinApp/releases/tag/v2.0)**

This version includes the prototype application and non‑proprietary documentation used during early development.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="840">
</p>
