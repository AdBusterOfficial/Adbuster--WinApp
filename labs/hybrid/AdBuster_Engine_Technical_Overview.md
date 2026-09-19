
<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

<br>

# 🚀 AdBuster PRO — Hybrid Engine v13  
### Technical Overview & Behavioural Architecture

AdBuster PRO Hybrid Engine v13 is the next‑generation behavioural audio system powering the most 
advanced version of the AdBuster PRO TV volume stabilizer. Unlike traditional AGC, compressors or 
loudness normalizers, Hybrid Engine v13 does not modify the audio stream. Instead, it listens, 
interprets and reacts — analysing signal behaviour, detecting context using machine learning, and 
applying precise IR volume commands exactly the way a human would.

This engine is designed for real‑world viewing conditions: unpredictable dialogue levels, sudden 
music peaks, dynamic movie scenes and aggressive advertisement transitions. Hybrid Engine v13 
combines DSP feature extraction, ML advertisement detection and CEPA Logic PRO behavioural 
decision‑making into a unified, adaptive system that keeps loudness stable without degrading audio 
quality.

The goal of Hybrid Engine v13 is simple: deliver natural, human‑like volume behaviour that feels 
intuitive, consistent and comfortable — regardless of what content is playing.

---

## 🧩 What Makes Hybrid Engine v13 Unique?

### 🧠 Behavioural Decision‑Making (CEPA Logic PRO)
CEPA Logic PRO is the heart of the system.  
It observes how the audio behaves over time, detects trends, avoids over‑correction and applies 
single, meaningful volume steps with natural timing. CEPA behaves like a human adjusting the remote:
one step, pause, observe — never oscillating, never spamming commands.

CEPA understands context, stability windows, drift, dynamic transitions and content behaviour.  
This produces smooth, realistic loudness control instead of mechanical volume jumps.

---

### 🤖 ML‑Assisted Advertisement Detection
A lightweight 4‑feature ML classifier continuously evaluates the audio using RMS, STD, DELTA and RANGE.  
It identifies advertisement behaviour based on dynamic patterns rather than raw loudness.

With a rolling history and probability thresholding (0.60 / 4 hits), the engine reliably detects ads 
and switches into protective AD mode. This ensures that sudden commercial transitions never overpower 
regular content.

---

### 🚫 AD Mode — Protective Behaviour Layer
During advertisements, Hybrid Engine v13 applies a controlled VOL_DOWN step and blocks any attempt 
to raise volume. If CEPA would normally increase loudness but an ad is active, the system triggers 
a behavioural CEPA BLOCK — ensuring ads never dominate the listening experience.

AD mode is not a simple “mute” or “compress” function.  
It is a context‑aware protection layer that preserves natural audio flow while preventing loudness 
spikes.

---

### 🔬 DSP Behavioural Analysis
The engine extracts and smooths signal features to understand context: dialogue, ambient scenes, 
music peaks, quiet transitions and dynamic shifts. This DSP layer feeds both ML and CEPA, enabling 
stable, context‑aware behaviour.

Hybrid Engine v13 does not react to every spike — it reacts to **behaviour**, not noise.

---

### 📡 IR Command Dispatcher
Hybrid Engine v13 controls the TV using physical IR commands (VOL_UP / VOL_DOWN).  
It includes cooldown logic, anti‑bounce protection, action‑window limits and safety rules to prevent 
rapid or unwanted changes. All corrections are applied exactly as a human would — one step at a time.

This ensures compatibility with any TV, soundbar or receiver without touching the audio stream.

---

## 🎯 Summary

Hybrid Engine v13 is a hybrid DSP + ML + behavioural stabilizer that preserves audio quality, prevents 
advertisement loudness spikes and maintains consistent, human‑like volume across all content types.  
It is designed for 24/7 operation, adapting to user habits, room acoustics and content behaviour.

This document provides a full technical breakdown of the engine’s architecture, internal logic, 
decision flow and real‑time behaviour.

---

# 🔄 DSP → ML → CEPA — Signal Flow Diagram

The Hybrid Engine v13 processes every audio block through a three‑stage behavioural pipeline.
Each stage transforms the signal into increasingly meaningful information, ending in human‑like
volume decisions.

───────────────────────────────────────────────────────────────
🎧 1. DSP Layer — Behavioural Feature Extraction
───────────────────────────────────────────────────────────────
The DSP layer listens to raw audio and extracts four behavioural features:

• RMS   → signal energy  
• STD   → short‑term variability  
• DELTA → frame‑to‑frame change  
• RANGE → amplitude spread  

These four numbers describe **how the signal behaves**, not just how loud it is.

DSP outputs two types of data:
1) **Feature vector → [RMS, STD, DELTA, RANGE]** → sent to ML  
2) **Smoothed loudness → smooth_gui / level_smooth** → sent to CEPA

───────────────────────────────────────────────────────────────
🤖 2. ML Layer — Advertisement Classification
───────────────────────────────────────────────────────────────
The ML classifier receives ONLY the 4 DSP features:

    [RMS, STD, DELTA, RANGE]

It scales them, evaluates a 10‑sample rolling history, and produces:

• p_ad (probability of advertisement)  
• AD / NORMAL classification  
• AD hold state (0.50s)

ML outputs:
1) **ad_mode_ml** → “Is this an advertisement?”  
2) **ml_flags** → passed to CEPA

ML does NOT use GUI loudness.  
ML does NOT use thresholds.  
ML uses ONLY the 4 DSP features.

───────────────────────────────────────────────────────────────
🧠 3. CEPA Layer — Behavioural Decision Engine
───────────────────────────────────────────────────────────────
CEPA receives two inputs:

1) **Smoothed loudness**  
   → smooth_gui  
   → level_smooth  

2) **Context flags from ML**  
   → is_ad  
   → is_music  
   → is_dialog  

CEPA uses these to make human‑like decisions:

• VOL_DOWN (controlled, single step)  
• VOL_UP (only when safe)  
• CEPA BLOCK (if UP is attempted during ads)  
• anti‑drift corrections  
• fallback logic  
• stability window checks  

CEPA outputs:
• pending_cmds → IR dispatcher  
• cepa_ad_block → GUI indicator  
• behavioural corrections → 1 step at a time

───────────────────────────────────────────────────────────────
📡 4. IR Dispatcher — Physical Volume Control
───────────────────────────────────────────────────────────────
The IR dispatcher sends real VOL_UP / VOL_DOWN commands to the TV,
with safety layers:

• cooldown  
• anti‑bounce  
• action window limits  
• AD‑specific restrictions  

This ensures stable, human‑like volume behaviour without touching the audio stream.

───────────────────────────────────────────────────────────────
🎯 Summary
───────────────────────────────────────────────────────────────
DSP extracts behaviour → ML detects ads → CEPA decides → IR executes.

This pipeline is what makes Hybrid Engine v13 a **behavioural, ML‑assisted,
human‑like volume stabilizer** rather than a traditional DSP compressor.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>
