![Music Mode Logic — AdBuster PRO](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/music_mode_logic.png)

# Music Mode Logic — AdBuster PRO

This diagram illustrates how CEPA PRO behaves when MUSIC conditions are detected in the audio stream.
Music Mode ensures stable volume handling, prevents unnecessary loudness boosts, and maintains a smooth listening experience during musical content.

---

## 🎵 What Music Mode Represents

Music Mode activates when CEPA identifies musical patterns in the audio signal.  
These patterns typically include:

- stable rhythmic structure,
- harmonic consistency,
- predictable MFCC signatures,
- low dialog‑like variability.

When MUSIC is confidently detected, CEPA switches into a mode optimized for musical playback.

---

# 🔵 Music Mode in AUTO MODE (WEAK)

When the user enables Music Mode while AUTO MODE is active, CEPA applies a **weak** version of Music Mode:

- **VOL_UP allowed** — controlled volume increases are permitted  
- **VOL_DOWN allowed** — decreases remain available  
- **CEPA ignores MUSIC flag** — standard threshold behaviour  
- **Ignore Voice: OFF** — dialog is not suppressed  
- **Fallback: Up & Down** — normal fallback behaviour  
- **Neutral response** — no cooperation with AD detection  

This results in smooth music playback while maintaining normal TV behaviour.

---

# 🔴 Music Mode in ML MODE (FULL)

When Music Mode is enabled in ML MODE, CEPA switches to **full** Music Mode:

- **Ignore Voice: ON** — dialog spikes are suppressed  
- **CEPA uses MUSIC flag** — dynamic ML threshold  
- **Ignores voice spikes** — prevents false reactions from loud dialog  
- **Fallback: Only Down if AD** — volume decreases only when ads are detected  
- **Stabilizes music flow** — prevents unnecessary fluctuations  
- **Cooperates with AD ML** — ensures correct behaviour during ads  

This mode prioritizes musical content, keeps the audio stable, and works together with ML‑based ad detection.

---

## 🔍 Why Music Mode Matters

Music Mode is essential for:

- maintaining natural loudness during songs,
- preventing CEPA from overreacting to musical peaks,
- ensuring predictable behaviour across transitions,
- keeping the audio flow smooth and stable.

It is one of the core CEPA modes used during real‑time classification.

---

## 📌 Purpose of This Diagram

The Music Mode Logic diagram is part of the CEPA PRO documentation and helps visualize how the system behaves when musical content is detected.  
It complements other CEPA behaviour diagrams:

- MUSIC Behaviour
- DIALOG Behaviour
- NORMAL Behaviour
- ADS Behaviour
- AD MODE Logic
- Fallback Logic

Together, these diagrams form a complete overview of CEPA’s real‑time decision system.
