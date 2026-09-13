<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

---

<br>

# 🧠 CEPA Logic PRO v13 — Context‑Aware Behaviour Engine

CEPA Logic PRO v13 is not a simple volume regulator.  
It is a full behavioural engine that reacts to audio **based on context**, not just loudness.  
Hybrid Engine v13 uses DSP + ML + CEPA layers to understand what is happening in the audio and respond accordingly.

---

## 🟩 Context Layers Used by CEPA Logic PRO v13

### 🔹 ML Context (AD / MUSIC / TALK / NORMAL)
CEPA receives machine‑learning flags:

- **AD** → controlled but immediate VOL_DOWN  
- **MUSIC** → softer reactions, ignore fast spikes  
- **TALK** → dialog protection, softer behaviour  
- **NORMAL** → balanced behaviour  

```python
ml_flags = {
    "is_ad": ad_mode,
    "is_dialog": (ml_label == "TALK"),
    "is_music": is_music
}
```

---

### 🔹 Perception Context (RMS / STD / DELTA / RANGE)
CEPA interprets the behaviour of the signal:

- **RMS** → energy  
- **STD** → variability  
- **DELTA** → sudden jumps  
- **RANGE** → dynamic spread  

This enables detection of:

- spikes  
- drifts  
- trends  
- stable zones  

---

### 🔹 Behavioural Context (CEPA State Machine)
CEPA transitions between states:

- NORMAL  
- AD
- TALK 
- MUSIC  
- TRANSITION_UP  
- TRANSITION_DOWN  
- RETURN  

Each state changes how CEPA reacts.

---

### 🔹 Time‑of‑Day Context
Thresholds adapt automatically:

- Morning  
- Afternoon  
- Evening  
- Night  

CEPA behaves differently depending on the time of day.

---

### 🔹 User Context (Manual Override)
If the user adjusts the slider:

```python
if manual_mode:
    return
```

CEPA pauses reactions until manual mode ends.

---

### 🔹 Spike Context
CEPA detects sudden loud spikes:

```python
ad_mode_spike = handle_spike(...)
```

Spikes trigger a different reaction than ads or music.

---

### 🔹 Drift & Trend Context
If loudness slowly creeps upward:

```python
if level > latest_threshold + 1.2:
    pending_cmds.append("VOL_DOWN")
```

CEPA reacts gently to drift, not aggressively.

---

### 🔹 Silence Context
If audio disappears:

```python
if (time.time() - last_audio_time) > 1.0:
    pending_cmds.append("VOL_DOWN")
```

Fallback logic activates only when appropriate.

---

## 🟧 Summary — Full Context Model (16 layers)

CEPA Logic PRO v13 makes decisions using **16 independent context layers**:

1. **ML classification** (AD / MUSIC / TALK / NORMAL)  
2. **Signal behaviour** (RMS / STD / DELTA / RANGE)  
3. **Time‑of‑day thresholds**  
4. **User interaction** (manual override)  
5. **Spike detection**  
6. **Drift detection**  
7. **Trend detection**  
8. **Music vs ads vs normal content**  
9. **Safety limits** (UP/DOWN limits, cooldowns)  
10. **Anti‑spam rules** (action window limits)  
11. **Silence context** (no audio → fallback logic)  
12. **IR error context** (temporary IR block)  
13. **ML hold** (stabilization of ML decisions)  
14. **AD hold** (advertisement persistence window)  
15. **Deadzone + stable zone** (ignore micro‑changes)  
16. **Preset context** (min/max volume, deadzone, stable zone)

**AdBuster Hybrid Engine v13 is a context‑aware audio engine, not a simple volume controller.**

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>

