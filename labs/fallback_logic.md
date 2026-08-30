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

