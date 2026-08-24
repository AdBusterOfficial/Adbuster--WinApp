
# Model Overview

This document provides a visual overview of the training dataset (`data.csv`)  
and the classifier model (`ad_detector.pkl`) used in the project.

---

## Training Dataset (CSV)

The dataset consists of behaviour‑extracted numerical features followed by a label:  
**AD** (advertisement‑like behaviour) or **NORMAL** (regular audio behaviour).

Below is a preview of the CSV file:

![data.csv](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/data.csv.png)

The full dataset is stored offline and only a preview is included here.

---

## Classifier Model (PKL)

The image below shows the binary model file.  
PKL files are not human‑readable, so a visual preview is provided instead.

![ad_detector.pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/ad_detector.pkl.png)

The model contains an offline‑trained classifier used to distinguish between  
**AD** and **NORMAL** audio behaviour segments.

Model file location:

```
ad_detector.pkl
```

---

## Loading the Model (Python Example)

```
from pickle import load

with open("ad_detector.pkl", "rb") as f:
    model = load(f)
```

---

## Summary

This page shows:
- a visual preview of the training dataset (`data.csv`)
- a visual preview of the classifier model (`ad_detector.pkl`)
- a short explanation of how the model is used
