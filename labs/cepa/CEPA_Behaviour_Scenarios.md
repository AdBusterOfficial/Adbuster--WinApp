## 🧪 CEPA Logic – Behaviour Scenarios (NO SPIKE)

🧠 **Logical behaviour map**  
The following scenarios describe the current behaviour of  
**AdBuster PRO – CEPA_MASTER_LIGHT (NO SPIKE)**  
with soft rise/drop detection, smooth threshold correction  
and fully disabled SPIKE FIX.

---

### 🟩 1. Long speech (voice, no ads)
- **Level rise:** `latest_gui - prev_gui > 3`  
- **Reaction:** `VOL_DOWN` (ANTI‑DRIFT + soft rise detection)  
- **Effect:** TV volume decreases by 1 step during loud speech.

---

### 🟦 2. End of speech (level drop)
- **Level drop:** `prev_gui - latest_gui > 3`  
- **Reaction:** `VOL_UP` (soft return after speech)  
- **Effect:** TV volume returns by 1 step after speaking ends.

---

### 🟧 3. Advertisement (ML AD = ON)
- **Detection:** `ad_mode = True` (ML 4‑feature engine)  
- **Reaction:** immediate `VOL_DOWN` + CEPA FIRST (AD‑only)  
- **Return:** fallback `VOL_UP` after the ad ends  
- **Effect:** ads are suppressed quickly, volume returns smoothly.

---

### 🟪 4. Music (wide dynamics, no AD)
- **Characteristics:** large delta/range, no ML AD  
- **Reaction:** no `VOL_DOWN` / `VOL_UP` (delta < 3, no AD)  
- **Effect:** CEPA does not interfere with music; no nervous behaviour.

---

### 🟥 5. Manual volume increase (remote control)
- **Change:** sudden rise `latest_gui - prev_gui > 3`  
- **Reaction:** `VOL_DOWN` (soft rise detection)  
- **Effect:** CEPA corrects manual overshoot by 1 step.

---

### 🟫 6. Echo / room reverberation
- **Change:** small drop (`delta` ≈ 1–2)  
- **Reaction:** no `VOL_UP` (condition > 3 not met)  
- **Effect:** echo does not cause unwanted volume bounce‑back.

---

### 🟨 7. Sudden spike (sneeze, pop)
- **Characteristics:** very large, short impulse  
- **SPIKE FIX:** disabled (NO SPIKE), smoothing absorbs the impulse  
- **Reaction:** no `VOL_DOWN` (delta in smooth_gui < 3)  
- **Effect:** single spikes are ignored; no panic reactions.

---

© 2026 — **D.P‑G & AdBuster Team Dublin**


