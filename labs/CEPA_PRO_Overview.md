# CEPA PRO — Full Engine Overview

CEPA PRO is a multi‑layer perception and decision engine that stabilizes TV loudness in real time.  
It does not rely on simple “loud/quiet” rules — instead, it analyzes context, trends, signal behavior, and user comfort to produce stable, human‑like automation decisions.

CEPA PRO consists of five layers:

- Perception  
- Intent  
- Comfort  
- Behaviour  
- Action  

Together, these layers form a complete loudness‑stabilization system.

---

## 📡 Perception Layer — Real‑Time Signal Analysis

The perception layer generates an event describing the current audio state:

- **level** — current loudness  
- **baseline** — adaptive reference point  
- **diff** — level minus baseline  
- **trend** — rising or falling over time  
- **context** — AD / DIALOG / MUSIC / NORMAL  
- **kind** — STABLE / SPIKE_SHORT / SPIKE_LONG / DRIFT_UP / DRIFT_DOWN  

CEPA PRO distinguishes:

- short impulses (**SPIKE_SHORT**)  
- long spikes (**SPIKE_LONG**)  
- slow upward drift (**DRIFT_UP**)  
- slow downward drift (**DRIFT_DOWN**)  

The baseline adapts dynamically — faster for large changes, slower for small ones.

---

## 🧠 Intent Layer — Understanding Loudness Intent

The intent layer classifies loudness as:

- **GOOD_LOUDNESS**  
- **BAD_LOUDNESS**  
- **NEUTRAL**

Depending on context:

- **AD** → BAD_LOUDNESS  
- **MUSIC** → GOOD_LOUDNESS for stable rise or short impulses  
- **DIALOG** → BAD_LOUDNESS for SPIKE_LONG, NEUTRAL for SPIKE_SHORT  
- **NORMAL** → BAD_LOUDNESS for SPIKE_LONG, NEUTRAL for SPIKE_SHORT  

CEPA PRO reacts only when the signal’s intent requires it.

---

## 🎚️ Comfort Layer — Margin Adjustment

The comfort layer modifies reaction margins:

- advertisements → margin tightens  
- music → margin expands  
- dialogue → margin stays stable and gentle  

User comfort influences how aggressively CEPA PRO reacts.

---

## 🔄 Behaviour Layer — State Machine

CEPA PRO uses a lightweight state machine:

- **NORMAL**  
- **AD**  
- **DIALOG**  
- **MUSIC**  
- **TRANSITION_UP**  
- **TRANSITION_DOWN**  
- **RETURN**

Examples:

- **AD** → highest priority  
- **DIALOG** → protect speech clarity  
- **MUSIC** → tolerant behavior  
- **DRIFT_UP** → switch to TRANSITION_UP  
- **RETURN** → stabilize after ads  

The state affects how CEPA PRO interprets events and margins.

---

## 🎨 Behaviour Zones — CEPA Stability Map

![CEPA Behaviour Zones](https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/Behaviour%20Zones.png)

CEPA Behaviour Zones illustrate how CEPA interprets signal stability:

- **Stable Zone** — predictable, steady behaviour  
- **Transition Zone** — sensitive, reactive changes  
- **Unstable Zone** — chaotic, erratic fluctuations  
- **High‑Risk Zone** — disruptive spikes  
- **Ads & Loud Bursts** — high‑priority suppression  

This diagram represents the behavioural states CEPA uses to stabilise loudness and guide real‑time decisions.

---

## 🧠 CEPA Logic — Real‑Time Decision Model

![CEPA Logic — Real-Time Decision](https://raw.githubusercontent.com/AdBusterOfficial/Adbuster--WinApp/main/labs/CEPA_real_time_decision.jpg)

CEPA Logic is the adaptive real‑time decision layer inside CEPA PRO.  
It operates continuously on the incoming audio signal, extracting MFCC, RMS and spectral features, classifying context (AD / NORMAL), and applying CEPA’s behaviour rules to determine whether to **trigger**, **hold**, or **ignore** a volume reaction.

### Core components:

- **Continuous signal feed** — real‑time audio monitoring  
- **Feature Extraction Layer** — MFCC, RMS, spectral metrics  
- **ML Classification** — AD / NORMAL context detection  
- **CEPA Decision Engine**  
  - loudness trend  
  - timing stability  
  - reaction history  
  - trigger / hold / ignore logic  
- **Reaction Control**  
  - IR volume control  
  - stabilization  
  - timing synchronization  

CEPA Logic ensures that every reaction is context‑aware, stable, and aligned with CEPA PRO’s behaviour model.  
It is the decision layer that connects perception, intent, comfort, and behaviour into a single, adaptive real‑time system powering AdBuster PRO.

---

## ⚙️ Action Layer — VOL_UP / VOL_DOWN Decisions

The action layer decides:

- **VOL_DOWN**  
- **VOL_UP**  
- **None**

Based on:

- margins (base / ad / dialog)  
- behaviour state  
- intent  
- diff  
- step delay  
- correction limits  

Decision rules:

- **diff > margin → VOL_DOWN**  
- **diff < -margin → VOL_UP**  
- **otherwise → no action**

CEPA PRO avoids chaotic volume changes by enforcing timing and frequency limits.

---

## 📌 Summary

CEPA PRO behaves like a real user:

- perceives the signal,  
- understands its intent,  
- respects comfort,  
- chooses a behavior state,  
- executes a controlled action.

This makes AdBuster PRO react not to raw loudness, but to:

- context,  
- trend,  
- signal behavior,  
- intent,  
- comfort,  
- baseline stability.

This is the complete, production‑ready CEPA PRO Overview.
