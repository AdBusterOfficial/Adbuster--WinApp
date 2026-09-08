# 🔊 AdBuster PRO — Human‑Like Volume Behavior  
### 📘 Labs / Behavioral Model Documentation  
*Next‑generation audio engine inspired by real human reactions.*

---

## ⭐ 1. What AdBuster PRO Does — “Human With a Remote” Behavior

AdBuster PRO is designed to behave exactly like a real person sitting in front of a TV with a remote control.  
Its logic is intentionally human‑like, not robotic.

### 👤 Human‑style reactions:
- 🔻 **Lowers loud advertisements immediately**
- 🔻 **Lowers sudden loud spikes** (explosions, screams, impacts)
- 🎤 **Ignores normal speech**
- 🎵 **Ignores music when MUSIC MODE is enabled**
- 🚫 **Never repeats the same command twice in a row**
- 🛡️ **Never spams IR commands**
- 🔒 **Never accidentally increases volume right after lowering an ad**

This creates a natural, predictable, human‑style reaction pattern.

---

## ⭐ 2. How AdBuster Handles LOUD ADVERTISEMENTS

### 🧠 ML detects the advertisement  
The 4‑feature ML model identifies ads based on acoustic patterns that differ from movies, dialogue, or music.

### 📈 SPIKE confirms loudness  
If the ad is extremely loud, the spike detector also confirms it.

### 🚨 AD MODE becomes active  
The system switches into “advertisement mode”.

### ⚡ Immediate volume reduction  
This is the core behavior:

```python
if ad_mode:
    pending_cmds.append("VOL_DOWN")
```

Meaning:

**Ad → instant VOL_DOWN**  
No waiting.  
No analysis.  
No CEPA.  
No fallback.  
Just immediate human‑like reaction.

### 🔁 Multiple steps allowed  
Ads have a higher volume‑down limit than normal content.

---

## ⭐ 3. How AdBuster Handles LOUDNESS SPIKES

A spike = sudden **“BANG”, “PEAK”, “SCREAM”, “IMPACT”**.

### 📊 Spike detector monitors:
- RMS  
- DELTA  
- RANGE  

If any threshold is exceeded → **SPIKE = TRUE**.

### 🥇 ML has priority  
If ML already detected an ad, spike logic does not interfere.

### 🔻 Spike triggers the same reaction as an ad  
**Spike → VOL_DOWN**

### ⏱️ Cooldown prevents spam  
Spike logic has a built‑in cooldown to avoid repeated triggers.

---

## ⭐ 4. When AdBuster Ignores VOICE

AdBuster intentionally ignores human voice in two cases:

### 🎵 1. MUSIC MODE enabled  
When MUSIC MODE is active:
- dialogue is ignored  
- voice spikes are ignored  
- CEPA does not react to loud speech  

### 🎤 2. GUI vs RAW difference is large  
This indicates:
- someone is speaking loudly  
- but it is not an ad  
- not a spike  
- not music  

Humans do not lower volume for loud dialogue — AdBuster behaves the same.

---

## ⭐ 5. System Harmony — No Conflicts Between Modules

AdBuster’s subsystems are synchronized:

### 🧠 ML has priority  
If ML says “ad”, spike logic steps aside.

### 📈 Spike works only when ML does not detect an ad  
No conflict.

### ⚙️ CEPA works only when there is no ad  
CEPA never fights with FORCE DOWN ON ADS.

### 🔁 Fallback works only when CEPA does nothing  
No double‑decisions.

### 📡 IR limits are relaxed for ads  
Ads are not blocked by global cooldown.

### 🔒 `allow()` prevents duplicate commands  
No double VOL_DOWN.

Everything is coordinated.  
Nothing blocks anything else.  
No subsystem interferes with another.

---

## ⭐ 6. Real‑World Example — How AdBuster Behaves

Imagine watching a movie.

---

### 🎬 Scene 1 — Normal Dialogue
- ML: NORMAL  
- SPIKE: FALSE  
- CEPA: observes  
- CEPA: no action  
- fallback: no action  
- IR: no command  

**AdBuster does nothing — like a human.**

---

### 🎬 Scene 2 — Actor Suddenly Screams
- ML: NORMAL  
- SPIKE: TRUE  
- AD MODE: TRUE (because spike)  
- FORCE DOWN ON ADS: VOL_DOWN  
- IR: sends command  
- fallback: may add one more step  

**AdBuster lowers volume — like a human.**

---

### 🎬 Scene 3 — Loud Advertisement Starts
- ML: AD  
- SPIKE: TRUE  
- AD MODE: TRUE  
- FORCE DOWN ON ADS: VOL_DOWN  
- IR: sends command  
- fallback: adds more steps  
- CEPA: ignored (ads override CEPA)  

**AdBuster lowers volume instantly — like a human.**

---

### 🎬 Scene 4 — Advertisement Ends
- ML: NORMAL  
- SPIKE: FALSE  
- AD MODE: FALSE  
- CEPA FIRST: stabilizes volume  
- fallback: helps if needed  
- IR: normal limits apply  

**AdBuster returns to normal behavior — like a human.**

---

## ⭐ 7. Summary — Human‑Like Behavior

AdBuster PRO now behaves exactly like a person with a remote:

- 🔻 **Ads → lowered immediately**  
- 🔻 **Spikes → lowered immediately**  
- 🎤 **Speech → ignored**  
- 🎵 **Music → ignored (optional)**  
- ⚙️ **CEPA stabilizes background volume**  
- 🔁 **Fallback supports CEPA**  
- 📡 **IR limits do not block ads**  
- 🔒 **No conflicts between modules**  
- 👤 **Natural, human‑like behavior**

---

## © 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

