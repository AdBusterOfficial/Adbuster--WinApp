
# CEPA Logic PRO — ADS Behaviour

Reklamy zachowują się inaczej niż muzyka, dialog czy zwykłe programy TV.  
Są miksowane głośniej, mają wyższy crest factor, mocniejszą kompresję, jingle, impact i szybkie przejścia.  
CEPA Logic PRO traktuje je jako osobny, priorytetowy kontekst, który wymaga natychmiastowej reakcji.

---

## 📈 Real‑Time Example

**Current level:** 52  
**Baseline:** 34  
**Difference:** +18  
**Context:** ADS  
**Kind:** IMPACT  
**ADS margin:** 3.0  
**Decision:** VOL_DOWN  

CEPA interpretuje to jako BAD_LOUDNESS + IMPACT — gwałtowny, agresywny wzrost charakterystyczny dla reklam.  
Ponieważ 18 > 3.0, CEPA wykonuje natychmiastowy VOL_DOWN, bez opóźnienia i bez analizy trendu.

---

## 🧠 Behaviour Explanation

W kontekście ADS CEPA Logic PRO:

- traktuje sygnał jako potencjalne zagrożenie,  
- używa najbardziej agresywnych marginesów,  
- reaguje na SPIKE_SHORT, SPIKE_LONG, IMPACT, BAD_LOUDNESS,  
- nie czeka na trend — reaguje natychmiast,  
- stosuje szybkie korekty, aby zbić głośność zanim reklama „uderzy”.

**IMPACT** oznacza gwałtowny, krótki, bardzo mocny skok — typowy dla jingli reklamowych.  
CEPA nie pozwala, aby taki skok dotarł do użytkownika.

---

## ⚙️ Decision Logic Summary

CEPA analizuje:

- baseline (normalny poziom TV),  
- current level,  
- difference,  
- behaviour kind (IMPACT / SPIKE_SHORT / BAD_LOUDNESS),  
- ADS margin (agresywny),  
- kontekst ADS.

W ADS obowiązuje zasada:

**difference > ADS_margin → natychmiastowy VOL_DOWN**

Bez trendu.  
Bez opóźnienia.  
Bez stabilizacji.  
Tylko szybka reakcja.

---

## 📌 Summary

ADS Behaviour to najważniejszy kontekst CEPA Logic PRO.  
AdBuster PRO reaguje na reklamy natychmiast — chroniąc użytkownika przed agresywnymi skokami głośności, jinglami i impactami.  
To właśnie ADS odróżnia AdBustera od zwykłych „volume normalizerów”.

