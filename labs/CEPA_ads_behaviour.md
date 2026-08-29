# CEPA Logic PRO — ADS Behaviour

 ![CEPA Logic PRO — ADS Behaviour](https://github.com/AdBusterOfficial/Adbuster--WinApp/blob/main/labs/cepa_ads_behaviour.png)

Advertisements behave differently from music, dialogue, or regular TV content.  
They are mixed louder, have a higher crest factor, stronger compression, jingles, impact bursts, and fast transitions.  
CEPA Logic PRO treats them as a separate, high‑priority context that requires immediate reaction.

---

## 📈 Real‑Time Example

**Current level:** 52  
**Baseline:** 34  
**Difference:** +18  
**Context:** ADS  
**Kind:** IMPACT  
**ADS margin:** 3.0  
**Decision:** VOL_DOWN  

CEPA interprets this as **BAD_LOUDNESS + IMPACT** — a sudden, aggressive loudness spike typical of advertisements.  
Because 18 > 3.0, CEPA executes an immediate **VOL_DOWN**, without delay or trend analysis.

---

## 🧠 Behaviour Explanation

In the ADS context, CEPA Logic PRO:

- treats the signal as a potential threat,  
- uses the most aggressive margins,  
- reacts to SPIKE_SHORT, SPIKE_LONG, IMPACT, BAD_LOUDNESS,  
- skips trend evaluation for instant response,  
- applies rapid corrections before the ad hits.

**IMPACT** means a short, sharp, high‑energy burst — typical of ad jingles.  
CEPA prevents such spikes from reaching the listener.

---

## ⚙️ Decision Logic Summary

CEPA evaluates:

- baseline (expected TV level),  
- current level,  
- difference,  
- behaviour kind (IMPACT / SPIKE_SHORT / BAD_LOUDNESS),  
- ADS margin (aggressive),  
- context (ADS).

Rule applied:

**difference > ADS_margin → immediate VOL_DOWN**

No trend.  
No delay.  
No stabilization.  
Only fast reaction.

---

## 📌 Summary

ADS Behaviour is the most critical CEPA Logic PRO context.  
AdBuster PRO reacts instantly to advertisements — protecting the listener from aggressive loudness spikes, jingles, and impacts.  
This is what truly distinguishes AdBuster from ordinary “volume normalizers.”

