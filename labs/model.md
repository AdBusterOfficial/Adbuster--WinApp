# Model Overview

This document provides a visual overview of the classifier model (`ad_detector.pkl`)  
and the training dataset (`data.csv`) used in the project.

---

## Classifier Model (PKL)

The image below shows the binary model file.  
PKL files are not human‑readable, so a visual preview is provided instead.

<br>

![ad_detector.pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/ad_detector.pkl.png)

**Model file location:**  
`ad_detector.pkl`  
*This file contains the trained classifier used to detect AD vs NORMAL behaviour.*

---

## What the Model Contains

The `ad_detector.pkl` file stores a trained **RandomForestClassifier** used to
distinguish between **AD** (advertisement‑like behaviour) and **NORMAL** audio behaviour.

### Input Features
The model expects numerical behaviour‑extracted features, such as:
- short‑window RMS energy
- long‑window RMS energy
- peak amplitude behaviour
- combined energy metrics
- behaviour ratios (short/long windows)

These features are computed offline from audio segments and represent how the
signal behaves over time.

### Output
The classifier produces a single label:
- **AD** — behaviour consistent with advertisement‑like loudness patterns  
- **NORMAL** — regular audio behaviour

### Training
The model was trained on the dataset shown above (`data.csv`), using:
- supervised learning  
- balanced AD/NORMAL samples  
- behaviour‑based numerical features  
- Random Forest ensemble for robustness and stability  

The PKL file contains:
- the trained model parameters  
- the decision trees  
- preprocessing metadata  
- feature ordering required for correct inference

This allows the application to load the model and perform offline classification
without requiring any external dependencies or cloud services.

---

## Training Dataset (CSV)

The dataset consists of behaviour‑extracted numerical features followed by a label:  
**AD** (advertisement‑like behaviour) or **NORMAL** (regular audio behaviour).

Below is a preview of the CSV file:

![data.csv](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/data.csv.png)

*This preview shows the structure of the data used to train the classifier.*

---

## Loading the Model (Python Example)

```
from pickle import load

with open("ad_detector.pkl", "rb") as f:
    model = load(f)
```

---

## Model Limitations

While the `ad_detector.pkl` classifier is effective for behaviour‑based AD detection,
it has several important limitations:

### Behaviour‑Only Analysis
The model does **not** analyse audio content or semantics.  
It relies purely on numerical behaviour features (RMS, peaks, ratios).  
This means it detects *patterns typical for advertisements*, not the actual audio meaning.

### No Real‑Time Training
The model is trained offline and cannot update itself during runtime.  
Any improvements require retraining and exporting a new PKL file.

### Feature Order Dependency
The classifier expects features in the **exact same order** as in `data.csv`.  
Changing column order or adding new features will break inference unless the model is retrained.

### Limited Generalization
The model performs well on behaviour patterns similar to the training dataset.  
Unusual audio sources or extreme processing may reduce accuracy.

### No Confidence Scores Exposed
The PKL contains probability outputs internally, but the current application
does not expose confidence levels (e.g., 0.87 AD).  
Only the final AD/NORMAL label is used.

### Offline‑Only
The model runs fully offline and does not use cloud‑based enhancements,
which improves privacy but limits large‑scale learning.

These limitations are typical for lightweight, behaviour‑based classifiers
and do not affect the stability of the AdBuster workflow.

---

## Summary

This page shows:
- a visual preview of the classifier model (`ad_detector.pkl`)
- a visual preview of the training dataset (`data.csv`)
- a short explanation of how both components are used

---

## Future Improvements

Several enhancements could be considered for future versions of the classifier:

### Expanded Feature Set
Additional behaviour‑based features (e.g., spectral metrics, transient detection,
dynamic range indicators) could improve classification accuracy.

### Confidence Score Output
Exposing the model’s probability output (e.g., AD = 0.87) would allow the
application to make more nuanced decisions instead of binary labels.

### Retraining Pipeline
A dedicated training pipeline could automate:
- dataset updates
- feature extraction
- model retraining
- PKL export

This would simplify future improvements and ensure consistent model quality.

### Real‑Time Adaptation
Although the current model is offline‑only, future versions could incorporate
lightweight online learning or adaptive thresholds based on recent behaviour.

### Feature Normalization
Adding normalization or scaling steps could improve robustness across
different audio sources and recording environments.

### Model Architecture Exploration
While Random Forest is stable and reliable, future experiments could evaluate:
- gradient boosting models
- lightweight neural networks
- hybrid behaviour‑content approaches

These may offer better generalization on diverse audio patterns.

These improvements are optional and not required for the current AdBuster workflow,
but they outline possible directions for future development.

---
