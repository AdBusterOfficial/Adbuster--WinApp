
# CEPA PRO — Full Engine Overview

CEPA PRO is a multi‑layer perception and decision engine that stabilizes TV loudness in real time.  
It does not rely on simple “loud/quiet” rules — instead, it analyzes context, trends, signal behavior, and user comfort to produce stable, human‑like automation decisions.

CEPA PRO consists of five layers:

1. Perception  
2. Intent  
3. Comfort  
4. Behaviour  
5. Action  

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

- short impulses (SPIKE_SHORT),  
- long spikes (SPIKE_LONG),  
- slow upward drift (DRIFT_UP),  
- slow downward drift (DRIFT_DOWN).

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

- NORMAL  
- AD  
- DIALOG  
- MUSIC  
- TRANSITION_UP  
- TRANSITION_DOWN  
- RETURN  

Examples:

- **AD** → highest priority  
- **DIALOG** → protect speech clarity  
- **MUSIC** → tolerant behavior  
- **DRIFT_UP** → switch to TRANSITION_UP  
- **RETURN** → stabilize after ads

The state affects how CEPA PRO interprets events and margins.

---

## ⚙️ Action Layer — VOL_UP / VOL_DOWN Decisions

The action layer decides:

- **VOL_DOWN**  
- **VOL_UP**  
- **None**

Based on:

- margins (base / ad / dialog),  
- behaviour state,  
- intent,  
- diff,  
- step delay,  
- correction limits.

Decision rules:

- diff > margin → VOL_DOWN  
- diff < -margin → VOL_UP  
- otherwise → no action  

CEPA PRO avoids chaotic volume changes by enforcing timing and frequency limits.

---

## 🔊 Practical Behavior

### 🎵 MUSIC  
Natural variations tolerated.  
Stable rise → GOOD_LOUDNESS.  
SPIKE_SHORT → GOOD_LOUDNESS.  
CEPA PRO avoids unnecessary corrections.

### 🎙️ DIALOG  
SPIKE_LONG → BAD_LOUDNESS → VOL_DOWN.  
SPIKE_SHORT → NEUTRAL.  
CEPA PRO protects speech clarity.

### 📺 NORMAL  
DRIFT_UP → TRANSITION_UP → margin tightens.  
SPIKE_LONG → BAD_LOUDNESS.  
CEPA PRO stabilizes general loudness.

### 📢 AD  
Always BAD_LOUDNESS.  
Margin tightened.  
Fast reaction.

---

## 📌 Summary

CEPA PRO behaves like a real user:

1. perceives the signal,  
2. understands its intent,  
3. respects comfort,  
4. chooses a behavior state,  
5. executes a controlled action.

This makes AdBuster PRO react not to raw loudness, but to:

- context,  
- trend,  
- signal behavior,  
- intent,  
- comfort,  
- baseline stability.

This is the complete, production‑ready CEPA PRO Overview.
