![Fallback Logic — AdBuster PRO](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/fallback_logic.png)

# Fallback Logic — AdBuster PRO

This diagram illustrates how CEPA PRO handles fallback conditions when the audio context becomes unstable, ambiguous, or transitions between states.
Fallback ensures predictable behaviour by limiting volume actions and maintaining safe output levels during uncertain detection phases.

---

## 🔍 What Fallback Represents

Fallback is activated when CEPA cannot confidently classify the current audio context.
Instead of making aggressive decisions, the system switches into a protective mode designed to:

- prevent sudden loudness changes,
- stabilize CEPA behaviour,
- avoid incorrect volume boosts,
- maintain listener comfort.

Fallback is a **safety net** for all CEPA modes.

---

## 🧠 When Fallback Is Triggered

Fallback may activate during:

- transitions between MUSIC → DIALOG → NORMAL → ADS,
- noisy or unstable audio conditions,
- borderline MFCC feature values,
- uncertain ML predictions,
- rapid context changes.

In these cases, CEPA avoids risky decisions and applies conservative logic.

---

## ⚙️ Fallback Behaviour

When fallback is active:

- CEPA **blocks VOL_UP**
- CEPA **allows VOL_DOWN**
- CEPA maintains **stable output**
- CEPA waits for the next confident context classification

This ensures the system never amplifies potentially loud or harmful segments.

---

## 🔧 Fallback and AD MODE

Fallback behaviour changes depending on whether CEPA is currently suppressing advertisements:

### **AD MODE = OFF**
- Fallback allows **VOL_UP + VOL_DOWN**
- Normal TV behaviour is preserved
- CEPA performs gentle corrections in both directions
- Stable zones reset fallback steps

### **AD MODE = ON**
- Fallback allows **ONLY VOL_DOWN**
- **VOL_UP is blocked** to prevent ad loudness spikes
- CEPA suppresses upward jumps during advertisements
- Stable zones reset fallback steps

This dual fallback logic ensures CEPA behaves predictably both during normal content and during advertisement suppression.

---

## 🧪 Practical Examples of Fallback Logic

### Example 1 — ML Misclassification
The ML classifier briefly labels a segment as MUSIC, but the loudness pattern resembles an advertisement.
CEPA attempts a VOL_UP, but fallback blocks the action:

- VOL_UP → **blocked**
- VOL_DOWN → allowed

Fallback prevents a sudden jump caused by a misclassification.

---

### Example 2 — Rapid Context Switching
The audio rapidly switches between DIALOG → MUSIC → ADS within a short time window.
CEPA enters fallback mode to avoid chaotic reactions:

- CEPA stabilizes output
- CEPA waits for a confident classification

This prevents jittery volume changes during unstable transitions.

---

### Example 3 — Noisy or Distorted Input
The microphone captures distorted or noisy audio (compression artifacts, clipping, unstable MFCC values).
CEPA cannot reliably determine context:

- VOL_UP → **blocked**
- VOL_DOWN → allowed

Fallback ensures safe behaviour until the signal becomes stable again.

---

## 🎧 Why Fallback Matters

Fallback is essential for:

- preventing misclassification spikes,
- ensuring predictable behaviour across all CEPA modes,
- maintaining user comfort,
- stabilizing transitions between contexts.

It acts as a buffer between uncertain detection and confident CEPA logic.

---

## 📌 Purpose of This Diagram

The fallback logic diagram is part of the CEPA PRO documentation and helps visualize how the system behaves during ambiguous audio conditions.
It complements other CEPA behaviour diagrams (see main README):

- MUSIC Behaviour
- DIALOG Behaviour
- NORMAL Behaviour
- ADS Behaviour
- AD MODE Logic

Together, these diagrams form a complete overview of CEPA’s real‑time decision system.

---

© 2026 — **D.P‑G & AdBuster Team Dublin. All rights reserved.**
