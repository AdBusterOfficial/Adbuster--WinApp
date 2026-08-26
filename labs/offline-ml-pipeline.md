## Research Summary

Today I completed a full offline ML pipeline for AdBuster PRO — from raw audio samples to a fully trained RandomForest model.

Using a controlled dataset (AD vs NORMAL) and 29 MFCC‑based features, the model was trained with a 300‑tree RandomForest (depth‑limited, bootstrap‑stable). The result is a clean, non‑overfitted classifier with consistent impurity reduction across trees and reliable separation of AD/NORMAL audio conditions.

The entire workflow — recording, feature extraction, CSV generation, model training and deployment — now runs fully offline inside AdusterML, producing a stable `ad_detector.pkl` ready for production use in AdBuster PRO.

Initial evaluation shows an 87% accuracy and a weighted F1‑score of 0.87, with perfect recall for AD detection — confirming that the model generalizes well even on a small, controlled dataset. These results validate the stability of the MFCC‑based feature space and the consistency of the RandomForest decision paths, making the current `ad_detector.pkl` a reliable baseline for further dataset expansion and future multi‑class audio logic.

## Research Screenshot

![AdusterML Data Builder](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/AdusterML_data_builder.png)


