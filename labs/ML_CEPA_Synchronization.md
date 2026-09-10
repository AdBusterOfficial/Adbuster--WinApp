⚡ ML → CEPA Synchronization — Real‑Time Coordination

AdBuster PRO uses a dual‑engine architecture where ML defines the audio context and CEPA executes the behavior. This synchronization ensures stable, human‑like reactions even during rapid transitions, spikes, or false ML triggers.

ML defines context:
- 🟡 AD (Advertisement)
- 🔵 MUSIC
- ⚪ NORMAL (Dialog)

CEPA never acts blindly — ML context is always provided first:
ml_flags = { "is_ad": ad_mode, "is_dialog": False, "is_music": is_music }

🛡️ ML Stability (0.25s Hold)
ML becomes valid only after a 0.25s stability window:
ad_mode_ml = ml_hold >= 0.25
This prevents false AD triggers and sudden drops.

🔒 ML Blocks CEPA Volume‑Up During Ads
If ML detects AD, CEPA cannot increase volume:
if ad_mode_ml: return

⬇️ ML Forces Immediate CEPA Volume‑Down
During ads CEPA reacts instantly:
pending_cmds.append("VOL_DOWN")

🎵 ML MUSIC Mode — CEPA Ignores Voice Peaks
ignore_voice = music_mode and abs(latest_gui - prev_gui) > 5
If GUI detects voice → CEPA ignores MUSIC to prevent false drops.

🧠 CEPA Corrects ML Mistakes
Short AD → ignored by ML hold  
False MUSIC → ignored by GUI heuristics  
Transitions → stabilized by CEPA smoothing

🚫 ML Disables SPIKE Logic
SPIKE cannot override ML:
if ml_state: return False

🔁 CEPA Stabilizes System After Ads
When AD ends:
- fallback resets
- drift resets
- deadzone resets
- CEPA returns to normal mode

🧩 Summary
ML decides the context. CEPA decides the behavior.

Hierarchy:
1. ML → AD: instant DOWN, UP blocked, SPIKE blocked  
2. ML → MUSIC: soft CEPA, voice protection  
3. ML → NORMAL: full CEPA logic  
4. ML unstable: CEPA ignores ML  
5. ML wrong: CEPA corrects ML

This synchronization makes AdBuster PRO feel human, predictable, and stable.

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

