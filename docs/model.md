# Model Overview

This document provides a visual overview of the classifier model (`ad_detector.pkl`)  
and the training dataset (`data.csv`) used in the project.

---

## Classifier Model (PKL)

The image below shows the binary model file.  
PKL files are not human‑readable, so a visual preview is provided instead.

<br>

![ad_detector.pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/ad_detector.pkl.png)

**Model file location:**  
`ad_detector.pkl`  
*This file contains the trained classifier used to detect AD vs NORMAL behaviour.*

---

## Training Dataset (CSV)

The dataset consists of behaviour‑extracted numerical features followed by a label:  
**AD** (advertisement‑like behaviour) or **NORMAL** (regular audio behaviour).

Below is a preview of the CSV file:

![data.csv](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/data.csv.png)

*This preview shows the structure of the data used to train the classifier.*

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
- a visual preview of the classifier model (`ad_detector.pkl`)
- a visual preview of the training dataset (`data.csv`)
- a short explanation of how both components are used
