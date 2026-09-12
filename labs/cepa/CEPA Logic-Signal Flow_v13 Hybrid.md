# CEPA Logic PRO — Signal Flow (v13 Hybrid)

![CEPA Logic PRO — Signal Flow (v13 Hybrid)](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/CEPA%20Logic%20PRO-Signal%20Flow%20(v13%20Hybrid).png)

### 🤖 Overview
CEPA Logic PRO is the behavioural engine inside AdBuster PRO.  
It transforms raw audio into structured perception, intent, behaviour, comfort margins and final volume actions.  
This multi‑layer architecture ensures stable, human‑like reactions even during rapid transitions, spikes or noisy content.

### 🎧 Audio Input Pipeline
Every 1024‑sample audio block is processed through:
- amplitude → dB_raw  
- RAW_DISPLAY smoothing  
- SMOOTH_GUI  
- LEVEL_SMOOTH  

The result is a stable `LEVEL` value forwarded into CEPA for analysis.

### 🟨 ML Context Integration
Machine Learning continuously classifies the audio into:
- 🟡 AD (Advertisement)  
- 🔵 MUSIC  
- ⚪ DIALOG / NORMAL  

CEPA always receives ML context first, ensuring correct interpretation of loudness, spikes and transitions.

### 🔵 Perception Layer — Signal Understanding
CEPA constructs a detailed perception model:
- adaptive baseline  
- diff (level − baseline)  
- trend (5s slope)  
- spike detection (short / long)  
- drift detection (up/down)  
- context classification  

This layer converts raw audio into structured behavioural information.

### 🟣 Intent Layer — Meaning of Loudness
CEPA interprets perception and assigns intent:
- GOOD_LOUDNESS  
- BAD_LOUDNESS  
- NEUTRAL  

Examples:
- AD → BAD_LOUDNESS  
- MUSIC + upward drift → GOOD_LOUDNESS  
- DIALOG + spike_long → BAD_LOUDNESS  

Intent determines whether CEPA should react, soften behaviour or stay passive.

### 🟩 Behaviour Layer — CEPA State Machine
CEPA transitions between behavioural states:
NORMAL, AD, MUSIC, DIALOG, TRANSITION_UP, TRANSITION_DOWN, RETURN

These states define CEPA’s “mode of thinking” and control how aggressively it responds.

### 🟧 Comfort Layer — Dynamic Margins
CEPA adjusts sensitivity based on context:
- base_margin  
- ad_margin  
- dialog_margin  

Examples:
- AD → margin decreases → faster VOL_DOWN  
- MUSIC → margin increases → softer behaviour  
- DIALOG → margin increases → dialog protection  

This layer ensures comfort and prevents over‑reaction.

### 🟥 Action Layer — Final Decision
CEPA makes the final loudness decision:
- diff > margin → VOL_DOWN  
- diff < −margin → VOL_UP  
- otherwise → PASS  

With stability controls:
step_delay, anti‑spam, hard_limit, RETURN protection, dialog protection

### 📡 Output — IR Command Dispatch
CEPA returns:
"VOL_DOWN", "VOL_UP", or None

The callback sends the command to the TV.

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

