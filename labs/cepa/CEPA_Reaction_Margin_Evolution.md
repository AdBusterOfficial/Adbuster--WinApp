# ⚙️ AdBuster PRO — CEPA Behavioural Logic  
## Reaction Margin Evolution

AdBuster PRO uses CEPA behavioural logic to adjust reaction sensitivity in real time.  
Instead of relying on a fixed margin, CEPA continuously evolves its thresholds to keep behaviour stable, predictable, and human‑like.

---

## 🧠 Baseline Margin — Starting Point

Inside AdBuster PRO, CEPA Logic begins with a **baseline reaction margin** (e.g. `3.0`).  
This defines how much deviation from the baseline loudness is tolerated before a correction is allowed.

-  Baseline margin = initial sensitivity  
-  Used in NORMAL conditions  
-  Reference point for all later adjustments  

This margin is **not static** — CEPA modifies it based on real‑time behaviour.

---

## 📉 Margin Tightening — Drift & Upward Behaviour

AdBuster PRO tightens the reaction margin when CEPA detects upward drift:

- Context: NORMAL, DRIFT_UP, rising trend  
- Behaviour: repeated micro‑spikes, slow loudness creep  
- Action: margin reduced  
  - `3.0 → 2.25 → 1.8`

**Example:**

- Baseline: `35`  
- Current: `42`  
- Diff: `+7`  
- Trend: rising  
- Margin: `3.0 → 2.25`  
- Decision: `7 > 2.25 → VOL_DOWN`

Margin tightening prevents uncontrolled loudness drift.

---

## 📈 Margin Expansion — Stable or Musical Behaviour

AdBuster PRO expands the margin when CEPA identifies stable or musical behaviour:

- Context: MUSIC, STABLE, GOOD_LOUDNESS  
- Behaviour: natural dynamics, no aggressive spikes  
- Action: margin increased  
  - `3.0 → 4.2`

**Example:**

- Baseline: `38`  
- Current: `40`  
- Diff: `+2`  
- Context: MUSIC  
- Margin: `3.0 → 4.2`  
- Decision: `2 < 4.2 → no action`

This keeps music natural and avoids unnecessary corrections.

---

## 🔄 Margin Reset — Context Transitions

When AdBuster PRO detects a behavioural context change through CEPA Logic:

- NORMAL → ADS  
- ADS → NORMAL  
- DIALOG → MUSIC  
- RETURN → NORMAL  

the reaction margin is reset to baseline:

-  Margin → `3.0`  
-  Clears previous tightening/expansion  
-  Prevents unstable behaviour during transitions

---

## 🔒 Margin Lock — ADS Protection Mode

During ADS behaviour, AdBuster PRO locks the reaction margin using CEPA Logic:

- Context: ADS, IMPACT, SPIKE_SHORT, SPIKE_LONG, BAD_LOUDNESS  
- Margin stays tight  
- No expansion allowed  
- Reactions are immediate (VOL_DOWN only)

**Example:**

- Baseline: `34`  
- Current: `52`  
- Diff: `+18`  
- Margin: `3.0`  
- Decision: `18 > 3.0 → VOL_DOWN`

This guarantees instant protection from loud advertisements.

---

## 🎯 Why Reaction Margin Evolution Matters

Dynamic margin evolution inside AdBuster PRO ensures:

-  No oscillation  
-  Drift suppression  
-  Dialogue protection  
-  Natural music dynamics  
-  Instant ADS reaction  
-  Predictable behaviour  

CEPA behavioural logic evolves its sensitivity based on **behaviour over time**, making every reaction intentional, stable, and human‑like.


