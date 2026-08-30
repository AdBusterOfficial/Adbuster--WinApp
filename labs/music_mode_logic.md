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

## ⚙️ Music Mode Behaviour

In Music Mode, CEPA applies the following rules:

- **VOL_UP allowed** — controlled volume increases are permitted  
- **VOL_DOWN allowed** — decreases remain available  
- **Stable CEPA output** — avoids rapid fluctuations  
- **Smooth transitions** — prevents sudden jumps when switching from MUSIC to other contexts

This ensures a comfortable and consistent listening experience.

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

