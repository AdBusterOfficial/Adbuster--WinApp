
# ⚙️ CEPA vs DSP — Fundamental Difference  

## AdBuster PRO Behavioural Logic

CEPA is the behavioural decision logic inside AdBuster PRO.  
DSP is signal processing.  
These are two completely different worlds — different goals, different data, different mechanisms.

CEPA does not analyse DSP signal structure.  
CEPA analyses **behaviour** and reacts like a human with a remote.

---

## 🧠 1. CEPA interprets behaviour  
DSP interprets waveform.

**DSP focuses on:**
- amplitude  
- filtering  
- transients  
- dynamics  
- spectrum  

**CEPA focuses on:**
- drift  
- spikes  
- trend  
- stability  
- context  
- correction history  

DSP sees *what is in the signal*.  
CEPA sees *what the signal is doing*.

---

## 🎚️ 2. CEPA uses acoustic metrics, not DSP features

CEPA operates on four real acoustic metrics:

- **RMS** — perceived loudness  
- **STD** — chaotic behaviour  
- **DELTA** — sudden changes  
- **RANGE** — dynamic spread  

DSP uses:
- FFT  
- filters  
- compression  
- limiting  
- envelope followers  
- transient analysis  

CEPA does not need any of these.

---

## 🔍 3. CEPA understands context  
DSP has no concept of context.

**CEPA recognises:**
- NORMAL  
- ADS  
- DIALOG  
- MUSIC  
- TRANSITION_UP / DOWN  
- RETURN  

DSP only sees raw signal — it cannot tell if it’s an ad, dialogue, or music.

---

## 📊 4. CEPA tracks behaviour over time  
DSP reacts instantly to the current signal.

**CEPA analyses:**
- rising/falling trend  
- stability  
- drift  
- micro‑trend  
- behavioural continuity  

DSP has no trend awareness — it reacts only to the present moment.

---

## 🔧 5. CEPA uses a dynamic reaction margin  
DSP uses fixed thresholds.

**CEPA margin:**
- tightening (drift)  
- expansion (music)  
- reset (transition)  
- lock (ADS)  

DSP threshold:
- static  
- context‑blind  
- non‑adaptive  

CEPA is adaptive.  
DSP is static.

---

## 🛡️ 6. CEPA has a safety layer  
DSP has no IR safety.

CEPA guarantees:
- only VOL_UP / VOL_DOWN  
- no MUTE / POWER  
- cooldown  
- anti‑spam  
- fallback  
- deterministic IR behaviour  

DSP cannot control a remote — CEPA can.

---

## 🤖 7. CEPA can use ML (optional)  
DSP cannot.

ML provides:
- ADS classification  
- behaviour hints  
- early ADS detection  
- stability validation  

CEPA works without ML, but ML enhances it.  
DSP has no such capability.

---

## 🎯 Summary — Why CEPA ≠ DSP

CEPA:
- interprets behaviour  
- understands context  
- analyses trends  
- reacts like a human  
- uses RMS/STD/DELTA/RANGE  
- has a safety layer  
- can use ML  
- controls IR deterministically  

DSP:
- analyses waveform  
- has no context  
- has no trend awareness  
- does not understand behaviour  
- has no safety  
- cannot control IR  
- is not adaptive  

CEPA is **behavioural logic**.  
DSP is **signal processing**.  
AdBuster PRO works because of CEPA — not DSP.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**
