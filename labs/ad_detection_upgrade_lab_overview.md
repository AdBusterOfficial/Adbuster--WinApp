# AD Detection Upgrade — Lab Overview

This document describes an experimental AD‑detection model developed inside the AdBuster lab.  
The model was trained on a **small sample dataset** and serves as an exploratory test of new AD‑detection behaviour.  
It is **not part of the AdBuster PRO 2.0 prototype** and is not intended for production use.  
This branch exists purely for research and validation purposes.

---

## 📊 Model Metrics (Preview)

The image below presents the current evaluation results of the experimental model:

![AD Detection Upgrade](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/AD_detection_upgrade.png)

### Main Metrics
- **Accuracy:** 0.80  
- **F1‑Score:** 0.80  

These values reflect balanced performance across both AD and NORMAL classes, considering the limited dataset size.

---

## 🔍 Class‑Level Breakdown

### AD Class
- **Precision:** 0.83  
- **Recall:** 0.83  
- **F1‑Score:** 0.83  

The AD class shows strong consistency, indicating that the model reliably identifies advertisement segments within the test sample.

### NORMAL Class
- **Precision:** 0.74  
- **Recall:** 0.74  
- **F1‑Score:** 0.74  

The NORMAL class performs slightly lower, which is expected due to the small dataset and early‑stage nature of this experiment.

---

## 🧪 Purpose of This Experiment

This model is part of our ongoing work inside the **AdBuster lab**.  
Its goal is to validate new approaches to AD‑detection logic and CEPA behaviour before integrating any improvements into future versions of AdBuster PRO.

Key objectives:
- Test alternative feature extraction paths  
- Validate behaviour stability on real‑time audio  
- Explore next‑generation CEPA reaction patterns  
- Identify weaknesses in NORMAL‑class discrimination  
- Provide a baseline for future dataset expansion  

---

## 📁 Repository Notes

- This experiment is stored in the **existing `labs/` section** of the repository.  
- It is not connected to the main AdBuster PRO 2.0 prototype.  
- The **source code is protected under the PRO license** and is not included here.  
- Only documentation, metrics, and behaviour notes are provided.

---

## 📌 Summary

This AD‑detection upgrade is a **preview‑stage research model**.  
It demonstrates the direction of the next generation of AdBuster’s audio‑ML engine, but it is not a final or production‑ready component.  
Further development will continue as part of the AdBuster lab’s ongoing research.
