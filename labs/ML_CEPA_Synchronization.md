# ML → CEPA Synchronization — Real‑Time Coordination

## 🤖 Overview
AdBuster PRO uses a dual‑engine architecture where ML defines the audio context and CEPA executes the behaviour.  
This synchronization ensures stable, human‑like reactions even during rapid transitions, spikes, or false ML triggers.

---

## 🎛️ ML & CEPA Roles

### 🧠 ML Context Engine
ML continuously classifies the audio into:
- 🟡 AD (Advertisement)  
- 🔵 MUSIC  
- ⚪ NORMAL (Dialog / Background)  

CEPA never acts blindly — it always receives ML context first:

`ml_flags = { "is_ad": ad_mode, "is_dialog": False, "is_music": is_music }`

### 🎚️ CEPA Behaviour Engine
CEPA uses ML context to decide:
- when to react  
- how strongly to react  
- when to stay passive  

---

## 🛡️ Stability & Filtering

### ⏱️ 0.25s ML Stability Hold
ML must remain stable for at least **0.25s** before CEPA accepts AD:

`ad_mode_ml = ml_hold >= 0.25`

This prevents:
- false AD triggers  
- sudden loudness drops  
- reactions to short bursts and spikes  

---

## 🔊 Ads & Loudness Control

### 🔒 Blocking Volume‑Up During Ads
When ML detects AD:
- CEPA **blocks VOL_UP**  
- CEPA **blocks upward drift**  

`if ad_mode_ml: return`

### ⬇️ Immediate Volume‑Down on Ads
During AD, CEPA reacts instantly:

`pending_cmds.append("VOL_DOWN")`

No threshold checks.  
No deadzone.  
No drift logic.  

---

## 🎵 Music Mode & Voice Protection

### 🎵 MUSIC Behaviour
In MUSIC mode, CEPA behaves softly but protects voice:

`ignore_voice = music_mode and abs(latest_gui - prev_gui) > 5`

If GUI detects voice:
- CEPA ignores MUSIC classification  
- prevents false drops on singing or loud speech  

---

## 🚫 SPIKE & ML Priority

### ⚡ SPIKE Disabled Under ML
When ML is active, SPIKE logic cannot override it:

`if ml_state: return False`

This prevents:
- SPIKE‑driven volume drops during ads  
- impulsive reactions to loud transitions  
- instability in high‑energy content  

---

## 🧩 Correction & Recovery

### 🧠 CEPA Corrects ML Mistakes
CEPA smooths and corrects ML behaviour:
- short AD → ignored by ML hold  
- false MUSIC → ignored by GUI heuristics  
- unstable transitions → stabilised by CEPA smoothing  

### 🔁 Recovery After Ads
When AD ends:
- fallback resets  
- drift resets  
- deadzone resets  
- CEPA returns to NORMAL behaviour  

---

## 📌 Summary
ML decides the **context**.  
CEPA decides the **behaviour**.

- ML → AD: instant DOWN, UP blocked, SPIKE blocked  
- ML → MUSIC: soft CEPA, voice‑aware protection  
- ML → NORMAL: full CEPA logic (threshold, deadzone, drift)  
- ML unstable: CEPA ignores ML  
- ML wrong: CEPA corrects ML  

This synchronization makes AdBuster PRO feel **human**, **predictable**, and **stable** in real‑time operation.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**


