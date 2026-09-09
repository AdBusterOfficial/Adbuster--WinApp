# ⚙️ CEPA Logic PRO — Reaction Margin Evolution

CEPA Logic PRO does not rely on a fixed reaction margin.  
Instead, it continuously adjusts sensitivity in real time to keep behaviour stable, predictable, and human‑like.

---

## 🧠 Baseline Margin — Starting Point

CEPA begins with a **baseline reaction margin** (e.g. `3.0`), which defines how much deviation from the baseline loudness is tolerated before a correction is allowed.

- 📊 Baseline margin = initial sensitivity  
- 🔧 Used in NORMAL conditions  
- 🔁 Reference point for all later adjustments  

This margin is **not static** — it evolves with the behaviour of the signal.

---

## 📉 Margin Tightening — Drift & Upward Behaviour

CEPA tightens the margin when loudness begins drifting upward:

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

Margin tightening prevents uncontrolled drift.

---

## 📈 Margin Expansion — Stable or Musical Behaviour

CEPA expands the margin when content is stable:

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

When CEPA detects a context change:

- NORMAL → ADS  
- ADS → NORMAL  
- DIALOG → MUSIC  
- RETURN → NORMAL  

CEPA resets the margin to baseline:

- 🔁 Margin → `3.0`  
- 🧹 Clears previous tightening/expansion  
- 🛡️ Prevents unstable behaviour during transitions

---

## 🔒 Margin Lock — ADS Protection Mode

Under ADS behaviour, CEPA locks the margin:

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

This guarantees instant protection from loud ads.

---

## 🎯 Why Reaction Margin Evolution Matters

Dynamic margin evolution ensures:

- 🛑 No oscillation  
- 📉 Drift suppression  
- 🗣️ Dialogue protection  
- 🎵 Natural music dynamics  
- ⚡ Instant ADS reaction  
- 🔁 Predictable behaviour  

CEPA evolves its sensitivity based on **behaviour over time**, making every reaction intentional and context‑aware.

