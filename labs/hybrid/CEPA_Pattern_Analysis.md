<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

---

<br>

# 🎛️ CEPA Logic PRO — Contextual Event Pattern Analysis
CEPA Logic PRO does not classify audio the way ML does.  
Instead, it interprets **patterns of behaviour over time**, reacting to sequences of events rather than isolated blocks.

This document describes all contextual patterns used by AdBuster Hybrid Engine v13.

---

## 📈 1. Trend Pattern (Slope Behaviour)
A trend is a **consistent directional change** across multiple audio blocks.

CEPA detects:
- 📈 upward trends (loudness gradually increases)
- 📉 downward trends (loudness gradually decreases)

Trends allow CEPA to anticipate events before they fully form.

---

## 🌀 2. Drift Pattern (Slow Deviation)
Drift is a **slow, persistent shift** away from the threshold.

Characteristics:
- gradual movement  
- not a spike  
- not an advertisement  
- not a sudden change  

CEPA applies gentle corrections to counter drift without overreacting.

---

## ⚡ 3. Spike Pattern (Sudden Impulse)
A spike is a **rapid, unnatural jump** in RMS / DELTA / RANGE.

Typical sources:
- jingles  
- transitions  
- sudden noises  
- short bursts of loud content  

CEPA reacts with minimal, safe correction (max 1 step).

---

## 🧘 4. Stability Pattern (Background Consistency)
Stability means the signal stays within a **stable zone** for a period of time.

CEPA avoids corrections when:
- loudness is consistent  
- no drift is forming  
- no spikes occur  

This prevents oscillation and keeps behaviour calm.

---

## 🎚️ 5. Deadzone Pattern (Human Tolerance)
Humans do not react to small fluctuations.  
CEPA mimics this behaviour using a **deadzone**:

- small changes are ignored  
- jitter is eliminated  
- behaviour stays natural  

Deadzone = “no‑reaction zone”.

---

## 🔀 6. Context Shift Pattern (Behavioural State Change)
CEPA transitions between behavioural states:

- NORMAL  
- MUSIC  
- TALK  
- AD  
- TRANSITION_UP  
- TRANSITION_DOWN  
- RETURN  

Each context changes how CEPA interprets the same loudness value.

Examples:
- 🎵 MUSIC → softer behaviour  
- 📢 AD → aggressive protection  
- 🗣️ TALK → dialogue margin  

---

## ↩️ 7. Return Pattern (Recovery to Baseline)
When loudness returns to normal, CEPA performs **smooth, minimal corrections**.

This prevents sudden jumps and keeps behaviour predictable.

---

## 👤 8. Human‑like Correction Pattern
CEPA spaces out actions to mimic human behaviour:

- cooldown between commands  
- no repeated identical commands  
- limited steps per time window  
- anti‑bounce protection  
- anti‑spam limits  

This prevents oscillation and creates stable, human‑like reactions.

---

## 🎵 9. Music Pattern (Soft Behaviour)
CEPA detects music using GUI dynamics and RMS behaviour.

Music mode:
- reduces sensitivity  
- avoids reacting to transients  
- protects musical dynamics  

---

## 🗣️ 10. Dialogue Pattern (Talk Protection)
CEPA protects speech using the **dialogue margin**:

- avoids reacting to natural voice peaks  
- prevents over‑correction during conversations  
- stabilizes spoken content  

---

## 📢 11. Advertisement Pattern (AD Mode)
AD Mode is triggered by:
- ML AD detection  
- spike detection  
- sustained loudness behaviour  

AD Mode effects:
- immediate VOL_DOWN (1 step)  
- block VOL_UP  
- AD hold timer  
- AD action limits  

This is the core of AdBuster’s anti‑advertisement behaviour.

---

## 🧩 Summary
CEPA Logic PRO is a **contextual behavioural engine**.  
It does not classify audio — it interprets **patterns of behaviour**:

- trends  
- drift  
- spikes  
- stability  
- deadzone  
- context shifts  
- return behaviour  
- human‑like correction timing  
- music patterns  
- dialogue patterns  
- advertisement patterns  

These patterns allow AdBuster PRO to react calmly, intelligently and predictably, even in unstable audio environments.

---

# CEPA Logic PRO v13 — Context → Pattern → Decision → IR

This diagram shows how CEPA Logic PRO v13 processes audio inside
AdBuster Hybrid Engine v13.

==============================================================
1. CONTEXT LAYERS (INPUT)
==============================================================
- ML Context (AD / MUSIC / TALK / NORMAL)
- Perception Context (RMS / STD / DELTA / RANGE)
- Behavioural Context (CEPA State Machine)
- Time‑of‑Day Context
- User Context (Manual Override)
- Spike Context
- Drift & Trend Context
- Silence Context
- Safety Context (cooldowns, anti‑spam, IR error block)

                     |
                     v
==============================================================
2. PATTERN ANALYSIS (INTERPRETATION)
==============================================================
- Trend Pattern (rising / falling behaviour)
- Drift Pattern (slow deviation)
- Spike Pattern (sudden impulse)
- Stability Pattern (stable zone)
- Deadzone Pattern (ignore micro‑changes)
- Context Shift Pattern (NORMAL ↔ MUSIC ↔ TALK ↔ AD)
- Return Pattern (smooth recovery)
- Human‑like Timing Pattern (cooldowns, spacing)
- Music Pattern (soft behaviour)
- Dialogue Pattern (speech protection)
- Advertisement Pattern (AD hold, AD block, forced down)

                     |
                     v
==============================================================
3. CEPA DECISION LOGIC
==============================================================
Inputs:
- level_smooth
- ml_flags
- patterns
- thresholds

Decisions:
- VOL_DOWN
- VOL_UP
- PASS (no action)

                     |
                     v
==============================================================
4. IR COMMAND OUTPUT
==============================================================
Commands:
- VOL_DOWN
- VOL_UP

Safety:
- cooldown timers
- anti‑spam window
- AD block (no VOL_UP during ads)
- IR error protection

==============================================================
SUMMARY
==============================================================
CEPA Logic PRO v13 processes audio through four layers:

1. CONTEXT  
2. PATTERN  
3. DECISION  
4. IR COMMANDS

This ensures stable, predictable, human‑like volume behaviour.

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>


