<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/header.png" width="1010">
</p>

<br>

# ⚙️ AD‑CEPA System Settings

This document lists all variables and recommended values for the **Hybrid AD‑CEPA Mode** (ML ad detection + CEPA volume stabilization).

---

## 🔧 ML — Ad Detection (4‑feature detector)

- **ML_AD_PROB_THRESHOLD** — `0.69`
- **ML_AD_REQUIRED** — `6`
- **ML_AD_HISTORY_MAX** — `12`
- **ML_INFERENCE_INTERVAL** — `0.10`  # seconds
- **AD_HOLD_SECONDS** — `0.20`
- **ml_enabled** — `True`
- **ad_mode_ml** — final ML AD state (after hold)
- **last_ad_detection_time** — timestamp of last AD
- **ML_DEBUG_INTERVAL** — `1.0`

---

## 🎚️ CEPA — Volume Stabilization Logic

- **threshold** — `12`  # main CEPA threshold
- **latest_threshold** — `12`  # GUI threshold
- **deadzone** — `6.0`
- **stable_zone** — `7.0`
- **MIN_INTERVAL_DOWN** — `3.5`
- **MIN_INTERVAL_UP** — `4.0`
- **COOLDOWN** — `4.0`
- **FALLBACK_INTERVAL** — `4.0`
- **MAX_ACTIONS_PER_WINDOW** — `2`
- **cepa_enabled** — `True`
- **cepa_ad_block** — `True`
- **last_command_time** — timestamp of last IR command
- **volume_down_count** — DOWN counter
- **volume_up_count** — UP counter
- **action_times** — safety window timestamps
- **manual_mode** — manual slider mode flag
- **manual_mode_until** — manual block timeout

---

## 🎛️ Audio / GUI

- **smooth_gui** — smoothed GUI level
- **latest_gui** — latest GUI level
- **latest_raw** — raw audio level
- **level_smooth** — deep smoothing level (used by CEPA)
- **hour_buffer** — 20‑minute audio buffer
- **hour_buffer_time** — timestamps for buffer
- **auto_mode** — AUTO mode flag
- **music_mode** — music mode flag
- **ignore_voice** — dialog filter flag
- **selected_device** — active microphone
- **last_audio_time** — last audio callback time

---

## 🕒 Time‑based Thresholds (AUTO)

- **THRESHOLD_MORNING** — `13`
- **THRESHOLD_AFTERNOON** — `15`
- **THRESHOLD_EVENING** — `14`
- **THRESHOLD_NIGHT** — `12`
- **get_time_threshold()** — function returning time‑based threshold
- **get_time_label()** — GUI label for current time slot

---

## 📡 IR / Safety

- **IR_ERROR_BLOCK** — `2.0`
- **last_ir_error_time** — last IR error timestamp
- **MIN_INTERVAL_UP** — `4.0`
- **MIN_INTERVAL_DOWN** — `3.5`
- **HIGH_TRIGGER** — high‑level trigger
- **LOW_TRIGGER** — low‑level trigger

---

## ⚡ Spike Engine (disabled in Hybrid 3)

- **last_spike_time**
- **spike_counter**

---

© 2026 — D.P‑G & AdBuster Team Dublin. All rights reserved.

---

<br>

<p align="center" style="padding-left: 1.5cm; padding-right: 1.5cm;">
  <img src="https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/footer.png" width="1010">
</p>


