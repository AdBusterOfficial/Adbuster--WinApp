
# Model Overview

This document provides a visual overview of the **model** used in the project  
and a preview of the **dataset** the model was trained on.

---

## Model (CSV Preview)

The image below shows the CSV data used as the **model input**.  
Each row contains extracted audio‑behaviour features followed by a label:

- **AD** – advertisement‑like behaviour  
- **NORMAL** – regular audio behaviour  

![model_csv](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/data.csv.png)

This CSV preview represents the structure of the model’s feature space.

---

## Dataset Preview (PKL Binary)

The following image shows the binary `.pkl` file.  
PKL files are not human‑readable — they contain serialized internal structures  
from the classifier and its training process.

![dataset_pkl](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/ad_detector.pkl.png)

The binary content includes internal references to sklearn and numpy modules,  
which is normal for serialized ML models.

Dataset file location:

```
ad_detector.pkl
```

---

## Loading the PKL File (Python Example)

```
from pickle import load

with open("ad_detector.pkl", "rb") as f:
    dataset = load(f)
```

---

## Summary

This page shows:
- the **model preview** (CSV with AD/NORMAL labels)
- the **dataset preview** (binary PKL file)
- a short explanation of how both components are used

